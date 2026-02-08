
| Operator | Name                     | Example | Description                                                                 |
| -------- | ------------------------ | ------- | --------------------------------------------------------------------------- |
| ==       | Equal to                 | x == y  | Returns 1 if the values are equal                                           |
| !=       | Not equal                | x != y  | Returns 1 if the values are not equal                                       |
| >        | Greater than             | x > y   | Returns 1 if the first value is greater than the second value               |
| <        | Less than                | x < y   | Returns 1 if the first value is less than the second value                  |
| >=       | Greater than or equal to | x >= y  | Returns 1 if the first value is greater than, or equal to, the second value |
| <=       | Less than or equal to    | x <= y  | Returns 1 if the first value is less than, or equal to, the second value    |

The return value of a comparison is either `1` or `0`, which means **true** (`1`) or **false** (`0`).

```
int age = 18;

printf("%d\n", age >= 18); // 1 (true), old enough to vote
printf("%d\n", age < 18);  // 0 (false), not old enough
```
