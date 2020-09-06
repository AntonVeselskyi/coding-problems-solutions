# Pick peaks

## [Pick peaks](https://www.codewars.com/kata/5279f6fe5ab7f447890006a7)

In this kata, you will write a function that returns the positions and the values of the "peaks" \(or local maxima\) of a numeric array.

For example, the array `arr = [0, 1, 2, 5, 1, 0]` has a peak at position `3` with a value of `5` \(since `arr[3]` equals `5`\).

```text
The output will be returned as an object with two properties: pos and peaks. Both of these properties should be arrays. If there is no peak in the given array, then the output should be `{pos: [], peaks: []}`.
```

```text
The output will be returned as an associative array with two key-value pairs: `'pos'` and `'peaks'`.  Both of them should be (non-associative) arrays.  If there is no peak in the given array, simply return `['pos' => [], 'peaks' => []]`.
```

```text
The output will be returned as an object of type `PeakData` which has two members: `pos` and `peaks`.  Both of these members should be `vector<int>`s.  If there is no peak in the given array then the output should be a `PeakData` with an empty vector for both the `pos` and `peaks` members.

`PeakData` is defined in Preloaded as follows:

```cpp
struct PeakData {
  vector<int> pos, peaks;
};
```
```

```text
The output will be returned as a ``Map<String,List<integer>>` with two key-value pairs: `"pos"` and `"peaks"`. If there is no peak in the given array, simply return `{"pos" => [], "peaks" => []}`.
```

```text
The output will be returned as a `Dictionary<string, List<int>>` with two key-value pairs: `"pos"` and `"peaks"`. 
If there is no peak in the given array, simply return `{"pos" => new List<int>(), "peaks" => new List<int>()}`.
```

Example: `pickPeaks([3, 2, 3, 6, 4, 1, 2, 3, 2, 1, 2, 3])` should return `{pos: [3, 7], peaks: [6, 3]}` \(or equivalent in other languages\)

All input arrays will be valid integer arrays \(although it could still be empty\), so you won't need to validate the input.

The first and last elements of the array will not be considered as peaks \(in the context of a mathematical function, we don't know what is after and before and therefore, we don't know if it is a peak or not\).

Also, beware of plateaus !!! `[1, 2, 2, 2, 1]` has a peak while `[1, 2, 2, 2, 3]` does not. In case of a plateau-peak, please only return the position and value of the beginning of the plateau. For example: `pickPeaks([1, 2, 2, 2, 1])` returns `{pos: [1], peaks: [2]}` \(or equivalent in other languages\)

Have fun!

## Solutions

### 🐍 Python

```python
def pick_peaks(arr):
    print(arr)
    no_rep_arr = [ arr[i] for i in range(len(arr)-1) if arr[i] != arr[i+1] ] + [ arr[-1] if arr else [] ]
    res_in_no_rep = [ (n,e) for n, e in enumerate(no_rep_arr) if n!=0 and n!=len(no_rep_arr)-1 and no_rep_arr[n-1] < e and no_rep_arr[n+1] < e ]
    return {'pos': [i[0] + arr[i[0]:].index(i[1]) for i in res_in_no_rep if i],
            'peaks': [i[1] for i in res_in_no_rep if i]}
```

