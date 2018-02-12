# Regular Expression

### Cheat sheet

#### Characters
| Anchor        | Description   |
| ------------- |:-------------:|
| \d | One digit |
| \w | word character: ASCII letter, digit or underscore |
| \s | whitespace character: space, tab, newline, carriage return, vertical tab|
| . | Any character except line break: .* anything |

#### Quantifiers
| Anchor        | Description   | Lengend   |
| ------------- |:-------------:|:-------------:|
| + | One or more | greedy |
| {3} | Exactly three times | |
| {2,4} | Two to four times | greedy |
| {3,} | three or more times | |
| * | Zero or more times | greedy |
| ? | Once or none | lazy |

#### Logic
| Anchor        | Description   |
| ------------- |:-------------:|
| &#124; | Alternation/OR |
| (...) | Capturing group: A(nt&#124;pple) = ant or apple |

#### White space
| Anchor        | Description   |
| ------------- |:-------------:|
| \t | tab |
| \n | Line separator |
| \r\n | Line separator on windows |

#### Anchors and Boundaries
| Anchor        | Description   |
| ------------- |:-------------:|
| ^ | Start of string |
| $ | End of string |
| \b | Word boundary |