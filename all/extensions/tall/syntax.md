# TALL (Timed Analogic Logic Language)
Extension used to declare delays and time-based functions.

## Simple delay
To declare that a simple function will take a certain time to change to a (the next) value, it's used `@` + number (integer or fractional) + time unit, before the equal symbol.

The following units can be used:
| day         | d  |
| hour        | h  |
| minute      | m  |
| second      | s  |
| millisecond | ms |
| microsecond | us |
| nanosecond  | ns |
Example:
```
a @2s= a + 1;
```
Where that example would give the following table:
| second | value of a |
|--------|------------|
|    0   |      0     |
|    1   |      0     |
|    2   |      1     |
|    3   |      1     |
|    4   |      2     |
|    5   |      2     |
|    6   |      3     |

Its possible to repeat the symbol `@` and declare a starter value:
```
A : 5;
b @2s@A= a + 1;
```
Here, by the second 0, the value of `b` will be 5.

## Wave function
Add `~` before the `=`, with the aproximation type that there will be between one value and another.

Allowed aproximations:
- linear

Example:
```
a @2s@15~linear= a ? 15, < 15, ! -15;
```
Will generate a triangular wave of 4hz, that go from 15 to -15.