# Tuple sum

## [Tuple sum](https://www.codewars.com/kata/58602cd3ef06546bb7000152)

Your task is to implement a function that adds all tuple elements that are numbers.

For this kata chars are not considered numbers.

## Solutions

### 🧠 C++

```cpp
#include <tuple>
#include <type_traits>
#include <vector>
using namespace ::std;

//generic function to return double, no matter what was passed
template <typename T, typename std::enable_if<std::is_arithmetic<T>() && !is_same<T, char>()>::type* = nullptr>
double d_echo(T t)
{
    return  static_cast<double>(t);
}

template <typename T, typename std::enable_if<!std::is_arithmetic<T>() || is_same<T, char>()>::type* = nullptr>
double d_echo(T t)
{
    return 0;
}

template <class Tuple, size_t... Is>
constexpr auto take_front_impl(Tuple t, index_sequence<Is...>)
{
    return make_tuple(get<Is>(t)...);
}

//pop N front elements of the tuple into new tuple
template <size_t N, class Tuple>
constexpr auto take_front(Tuple t)
{
    return take_front_impl(t, make_index_sequence<N>{});
}

//spectialization for LAST element
template <typename T>
double tuple_sum(const tuple<T> &&tpl)
{
    auto elmnt = get<0>(tpl);
    return d_echo(elmnt);

}

template <typename... Ts>
double tuple_sum(const tuple<Ts...> &tpl)
{
#define tuple_size (tuple_size<tuple<Ts...>>::value)

    auto elmnt = get<tuple_size-1>(tpl);

    return d_echo(elmnt) + tuple_sum(take_front<tuple_size-1>(tpl));
}
```

