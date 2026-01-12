| **Function**              | **Header**    | **Category**   | **Utilization / When to Use**                                  |
| ------------------------- | ------------- | -------------- | -------------------------------------------------------------- |
| `std::sort`               | `<algorithm>` | Sorting        | Sort a range efficiently (introsort: quick + heap + insertion) |
| `std::stable_sort`        | `<algorithm>` | Sorting        | Sort while preserving relative order of equal elements         |
| `std::partial_sort`       | `<algorithm>` | Sorting        | Get top N sorted elements                                      |
| `std::nth_element`        | `<algorithm>` | Selection      | Place nth element as if sorted; very fast                      |
| `std::find`               | `<algorithm>` | Searching      | Find first occurrence of a value                               |
| `std::find_if`            | `<algorithm>` | Searching      | Find using a condition (predicate)                             |
| `std::binary_search`      | `<algorithm>` | Searching      | Fast search in **sorted** ranges                               |
| `std::lower_bound`        | `<algorithm>` | Searching      | First position where value can be inserted                     |
| `std::upper_bound`        | `<algorithm>` | Searching      | Last position where value can be inserted                      |
| `std::count`              | `<algorithm>` | Counting       | Count exact value occurrences                                  |
| `std::count_if`           | `<algorithm>` | Counting       | Count elements matching a condition                            |
| `std::copy`               | `<algorithm>` | Copying        | Copy elements between ranges                                   |
| `std::move`               | `<algorithm>` | Moving         | Move elements instead of copying                               |
| `std::transform`          | `<algorithm>` | Transform      | Apply operation to a range                                     |
| `std::remove`             | `<algorithm>` | Removal        | Shift elements to remove value (erase–remove idiom)            |
| `std::remove_if`          | `<algorithm>` | Removal        | Remove elements by condition                                   |
| `std::unique`             | `<algorithm>` | Deduplication  | Remove consecutive duplicates                                  |
| `std::accumulate`         | `<numeric>`   | Numeric        | Sum or reduce a range                                          |
| `std::reduce` (C++17)     | `<numeric>`   | Numeric        | Faster parallel-friendly reduction                             |
| `std::min` / `std::max`   | `<algorithm>` | Comparison     | Get smaller/larger of two values                               |
| `std::min_element`        | `<algorithm>` | Comparison     | Find smallest element in range                                 |
| `std::max_element`        | `<algorithm>` | Comparison     | Find largest element in range                                  |
| `std::swap`               | `<utility>`   | Utility        | Efficiently exchange two values                                |
| `std::fill`               | `<algorithm>` | Initialization | Fill a range with a value                                      |
| `std::generate`           | `<algorithm>` | Initialization | Fill a range using a generator function                        |
| `std::all_of`             | `<algorithm>` | Predicates     | Check if all elements satisfy a condition                      |
| `std::any_of`             | `<algorithm>` | Predicates     | Check if any element satisfies a condition                     |
| `std::none_of`            | `<algorithm>` | Predicates     | Check if no elements satisfy a condition                       |
| `std::clamp` (C++17)      | `<algorithm>` | Utility        | Restrict value to a range                                      |
| `std::for_each`           | `<algorithm>` | Iteration      | Apply function to each element                                 |
| `std::distance`           | `<iterator>`  | Iterator       | Compute number of elements between iterators                   |
| `std::advance`            | `<iterator>`  | Iterator       | Move iterator forward/backward                                 |
| `std::next` / `std::prev` | `<iterator>`  | Iterator       | Get adjacent iterator safely                                   |