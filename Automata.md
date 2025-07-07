| Symbol    | Meaning                      | Example                    |
| --------- | ---------------------------- | -------------------------- |
| `a`       | The character `a`            | `a`                        |
| `ε`       | Empty string                 | Matches nothing            |
| `R1 + R2` | Union (OR)                   | `a + b` = `a` or `b`       |
| `R1R2`    | Concatenation                | `ab` = `a` then `b`        |
| `R*`      | Kleene Star: repeat 0+ times | `a*` = `ε`, `a`, `aa`, ... |
| `(R)`     | Grouping                     | `(ab)*`                    |

| Regex         | Language (Accepted Strings)              |                                               |
| ------------- | ---------------------------------------- | --------------------------------------------- |
| `(a + b)*`    | All strings over `{a, b}`                |                                               |
| `a(a + b)*`   | Strings that start with `a`              |                                               |
| `b*a b*`      | Exactly one `a`                          |                                               |
| `(ab)*`       | Even length strings of alternating a-b   |                                               |
| `b*ab*ab*`    | Even number of `a`s                      |                                               |
| `(a + b)*abb` | Strings that end in `abb`                |                                               |
| `1(0 + 1)*1`  | Binary strings that start and end in `1` |                                               |
| Operation     | What it does                             | Trick (for DFA)                               |
| Union (A ∪ B) | Accepts if A or B accepts                | Combine both, final if qA ∈ FA **or** qB ∈ FB |
| Intersect     | Accepts if both A and B accept           | Final if qA ∈ FA **and** qB ∈ FB              |
| Complement    | Accepts if A rejects                     | DFA only: swap final and non-final            |
| Difference    | Accept in A but not in B                 | A ∩ ¬B                                        |
| Concatenation | Accepts strings from A then B            | ε-move from A’s finals to B’s start (in NFA)  |
| Kleene Star   | Repeat language 0 or more times          | New start/final with ε-loops                  |

| Type  | ε-transitions | Multiple Transitions | Deterministic |
| ----- | ------------- | -------------------- | ------------- |
| DFA   | ❌             | ❌                    | ✅             |
| NFA   | ❌             | ✅                    | ❌             |
| ε-NFA | ✅             | ✅                    | ❌             |