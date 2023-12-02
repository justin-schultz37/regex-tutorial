# Regular Expression: Password validation

In both coding and beyond, creating a password with specific requirements is a common task. This guide will walk you through understanding and implementing a regular expression for validating passwords based on certain rules. The regex pattern enforces the following criteria:

- At least one digit (0-9)
- At least one lowercase letter (a-z)
- At least one uppercase letter (A-Z)
- At least one special character from the set: `*.!@$%^&(){}[]:;<>,.?/~_+-=|\`
- Must be 8 to 32 characters long

Let's break down the regex pattern:

```regex
^(?=.*[0-9])(?=.*[a-z])(?=.*[A-Z])(?=.*[*.!@$%^&(){}[]:;<>,.?/~_+-=|\]).{8,32}$
```
## Summary

This regex pattern ensures that a password meets specific criteria, including the use of digits, lowercase and uppercase letters, and at least one special character. The length must be between 8 and 32 characters.

## Table of Contents

- [Metacharacters](#metacharacters)
- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Metacharacters

Metacharacters are text and symbols that have special meaning when it comes to creating code. One of the reoccuring metacharaters used in this regex is the asterisk ```*```. It is used as a quantifier to allow any or none of the characters in the follow character classes. It allows the character classes to be flexible in the validation so that no specific character needs to be used or how frequently it gets used.

### Anchors

Anchors assert a position in the string. In this regex, ```^``` asserts the start of the string, and ```$``` asserts the end.

### Quantifiers

Quantifiers define how many instances of the preceding element are allowed.

In the regex above ```{8,32}``` specifies that the password must be between 8 and 32 characters long.

Other quantifiers used in this regex are ```?``` and ```*``` used to both match and allow zero or more parts of the regex classes in this password validation

### OR Operator

The OR operator, denoted by ```|```, allows for a choice between alternatives. This regex doesn't explicitly use the OR operator.

### Character Classes

Character classes match a single character from a set. ```[0-9]```, ```[a-z]```, and ```[A-Z]``` ensure  digits, lowercase, and uppercase letters are being used.

### Flags

Flags modify the behavior of the regex. This regex doesn't use any flags, but keep in mind that different programming languages may have their own set of flags.

A simple example would be using ```i``` to match characters regardless of case sensitivity. ```'/abc/i'``` would match both 'ABC' and 'abc'.

### Grouping and Capturing

Grouping is denoted by parentheses ```( )```. In this regex, each positive lookahead is a group, ensuring the presence of specific types of characters.

There are 4 groups captured in this password validation: ```(?=.*[0-9])```, ```(?=.*[a-z])```, ```(?=.*[A-Z])```, and ```(?=.*[*.!@$%^&(){}[]:;<>,.?/~_+-=|\])```.

### Bracket Expressions

Bracket expressions define a character class. ```[*.!@$%^&(){}[]:;<>,.?/~_+-=|\]``` includes various special characters that are allowed in the password. Take note that this regex includes metacharacters ```*``` inside of bracket expression. Would you assume it retains its special meaning "zero to many"? When you add characters inside of a bracket expression they get treated literally instead of having and meta meaning.

### Greedy and Lazy Match

Greedy matching is used by default. It matches as much as possible while still allowing the overall pattern to match. Lazy matching would not be applicable in this regex as it does not involve repitition. The look aheads ensure at least one of each character is used, and the quantifier ```{8,32}``` specifies the range.

### Boundaries

Boundaries help define limits for matches. In this regex, ```^``` and ```$``` serve as boundaries, ensuring the entire string is matched.

### Look-ahead and Look-behind

Positive lookaheads (```(?= ...)```) assert that a particular pattern can be matched ahead in the string. They are useful in creating more complicated regular expressions. In this scenario, the the positive lookaheads are used to make sure make sure that one of each validation is used without explicitly determine the position in the validation process. Simply put, it doesnt matter where a number gets used in your password as long as one gets used.

## Author
[Justin Schultz](https://github.com/justin-schultz37)

[Source of Regex Analyzed](https://www.ocpsoft.org/tutorials/regular-expressions/password-regular-expression/)