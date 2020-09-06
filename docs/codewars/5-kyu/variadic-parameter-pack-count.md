# Variadic Parameter Pack Count

## [Variadic Parameter Pack Count](https://www.codewars.com/kata/5b535628a8eb75ab2c000062)

In this Kata you will reimplement the `sizeof...` function that determines the size of a variadic paramter pack. Your function will have to be efficient since thousands of arguments will be passed to it.

The default approach to this kind of problems is to use recursion but this wont work here since it will exceed the maximal recursion depth.

Examples:

```text
arg_length(1, 2, 3); // Should return 3
arg_length("Hello", "World"); // should return 2
arg_length("foo", 1); // should return 2
```

## Solutions

### 🧠 C++

```cpp
template <typename... Ts>
constexpr std::size_t arg_length(Ts...) noexcept
{
  return std::tuple_size<std::tuple<Ts...>>();
}
```

