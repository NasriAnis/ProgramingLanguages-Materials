| **Container**             | **Header**        | **Type**              | **Utilization / When to Use**                                                         |
| ------------------------- | ----------------- | --------------------- | ------------------------------------------------------------------------------------- |
| `std::array`              | `<array>`         | Sequence              | Fixed-size array known at compile time; safer and more expressive than C-style arrays |
| `std::vector`             | `<vector>`        | Sequence              | Dynamic array; fast random access; most commonly used container                       |
| `std::deque`              | `<deque>`         | Sequence              | Fast insertion/removal at both front and back                                         |
| `std::list`               | `<list>`          | Sequence              | Doubly linked list; frequent insertions/removals in the middle                        |
| `std::forward_list`       | `<forward_list>`  | Sequence              | Singly linked list; minimal memory overhead                                           |
| `std::set`                | `<set>`           | Associative           | Sorted unique elements; fast lookup (log n)                                           |
| `std::multiset`           | `<set>`           | Associative           | Sorted elements with duplicates allowed                                               |
| `std::map`                | `<map>`           | Associative           | Key–value pairs; sorted by key; fast lookup                                           |
| `std::multimap`           | `<map>`           | Associative           | Key–value pairs; sorted; duplicate keys allowed                                       |
| `std::unordered_set`      | `<unordered_set>` | Unordered Associative | Unique elements; very fast average lookup (hash table)                                |
| `std::unordered_multiset` | `<unordered_set>` | Unordered Associative | Allows duplicate elements; hash-based                                                 |
| `std::unordered_map`      | `<unordered_map>` | Unordered Associative | Key–value pairs; very fast average lookup                                             |
| `std::unordered_multimap` | `<unordered_map>` | Unordered Associative | Key–value pairs; duplicate keys allowed                                               |
| `std::stack`              | `<stack>`         | Container Adapter     | LIFO operations (push/pop only)                                                       |
| `std::queue`              | `<queue>`         | Container Adapter     | FIFO operations                                                                       |
| `std::priority_queue`     | `<queue>`         | Container Adapter     | Always retrieves highest-priority element                                             |
| `std::span` (C++20)       | `<span>`          | View                  | Non-owning view over a contiguous sequence                                            |
| `std::string`             | `<string>`        | Specialized           | Text manipulation and storage                                                         |