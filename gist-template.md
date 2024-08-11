# regex-tutorial

This tutorial will guide you through a particular regular expression, explaining the importance of each character used.

## Summary

In this demonstration, we will break down and explain a regular expression designed to match an email address within a string. The regular expression is as follows:

/^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components
The following outlines the various components of a regular expression and their usage in this scenario.

### Anchors
* ^: Matches the beginning of a string. In this case, it ensures that the email address starts with the characters defined in the first group (`[a-z0-9_.-]+`).

* $: Matches the end of a string. Here, it ensures that the email address ends with the characters specified in the third group (`[a-z.]{2,6}`).

Using `^` at the start and `$` at the end ensures that the entire string adheres to the pattern, not just a segment of it. This means the string being tested must fully match the pattern defined between these anchors. In this example, we ensure the string conforms to the format: `user@domain.top-level-domain`.

### Quantifiers
* +: The plus sign following a character class indicates that one or more of those characters must be present. For example, the `+` after the character class `[a-z0-9_.-]` means that the username part of the email must contain one or more of the specified characters (lowercase letters, digits, underscores, periods, or hyphens). Similarly, the `+` after `[\\da-z.-]` means that the domain part must include one or more of the specified characters (digits, lowercase letters, periods, or hyphens).

* {x,y}: Curly brackets with two numbers specify that the preceding group must have a length between `x` and `y` characters. In this example, `{2,6}` after `[a-z.]` means that the top-level domain (TLD) part of the email must contain between 2 and 6 of the specified characters (lowercase letters and periods).

### OR Operator
This regular expression does not contain the `|` (OR) symbol, indicating that no alternative pattern is being matched.

### Character Classes
Character classes in regular expressions define a set of characters to match. They are enclosed in square brackets `[]` and match any single character from the set.

* `[a-z0-9_.-]`
  * [ and ]: Defines the boundaries of a character class.
  * a-z: Matches any lowercase letter.
  * 0-9: Matches any digit.
  * _: Matches an underscore.
  * .: Matches a literal period (dot). The backslash escapes the dot, which is otherwise a special character in regex.
  * -: Matches a hyphen.
  
  Any character defined within the class will satisfy a match.

* `'@'`: Matches the `@` symbol in an email address.

* `[\da-z.-]`
  * \d: Matches any digit (equivalent to `[0-9]`).
  * a-z: Matches any lowercase letter.
  * .: Matches a literal period (dot).
  * -: Matches a hyphen.

* `[a-z.]`
  * a-z: Matches any lowercase letter.
  * .: Matches a literal period (dot).

### Flags
In regular expressions, flags (or modifiers) adjust the behavior of pattern matching. They are usually placed after the closing delimiter of the regular expression. In this example, no flags are used.

### Grouping and Capturing
Grouping and capturing in regular expressions allow you to treat multiple characters as a single unit, extract matched substrings, and perform additional operations on the matched text. Grouping is achieved using parentheses `()`, enabling you to apply quantifiers to a group of characters and create subpatterns within the main pattern. Capturing is a specific type of grouping that lets you extract the text matched by a group. Below are some of the groups used in this example:

* `([a-z0-9_.-]+)`
  - Matches the username part of the email.
  - Captures one or more characters that are lowercase letters, digits, underscores, periods, or hyphens.
  - Example match: `user.name`

* `([\da-z.-]+)`
  - Matches the domain part of the email.
  - Captures one or more characters that are digits, lowercase letters, periods, or hyphens.
  - Example match: `example-domain`

* `([a-z.]{2,6})`
  - Matches the top-level domain (TLD) part of the email.
  - Captures between 2 and 6 characters that are lowercase letters or periods.
  - Example match: `com`, `co.uk`

Full Example:

* The entire regex matches: `user.name@example-domain.com`
    - First capture group: `user.name`
    - Second capture group: `example-domain`
    - Third capture group: `com`

### Bracket Expressions
Bracket expressions, also known as character classes, define a set of characters enclosed in square brackets `[]`. They allow you to match any one of the specified literal characters or a range of characters. Since the character classes used in this example have already been explained above, we'll refrain from going into further detail here.

### Greedy and Lazy Match
By default, quantifiers are greedy, meaning they will try to match as much of the input string as possible while still allowing the overall pattern to succeed. In this example, all of our quantifiers are greedy:

* `+` (Plus)
  - Matches one or more occurrences of the preceding element.
  - Example: `a+` in `aaa` matches `aaa`.

* `{n,m}` (Between n and m times)
  - Matches between `n` and `m` occurrences of the preceding element.
  - Example: `a{2,4}` in `aaaaa` matches `aaaa`.

Lazy quantifiers, also known as non-greedy quantifiers, match as little of the input string as possible while still allowing the overall pattern to succeed. You can make a quantifier lazy by appending a question mark.

### Boundaries
In regular expressions, boundaries are markers or assertions that do not match any characters directly but instead assert something about the surrounding characters or the position within the string. In this example, the only boundaries used are the anchor characters `^` and `$`, which have been described in the section above.

### Back-references
Backreferences in regular expressions let you refer to previously captured groups within the same pattern. They are useful for matching repeated substrings or ensuring that certain parts of the string match other parts exactly. To create a backreference, you use parentheses to capture a group and then refer to that capture with a backslash followed by the group number. This example does not include any backreferences.

### Look-ahead and Look-behind
Look-ahead and look-behind assertions in regular expressions match patterns based on what precedes or follows them, without including those preceding or following characters in the match. These assertions are not used in this example.

## Author
Alyssa Hanewinkel (https://github.com/alyssawink)