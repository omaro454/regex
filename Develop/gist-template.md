# An Introduction to Regex (Regular Expression)

This challenge will be used to define regular expressions, or regex and what their benificial uses are in the web developing world. For starters, regex is a a sequence of characters that defines a specific search pattern. 

## Summary

The specific regex I will be breaking down is an expression for matching an email. The example looks like this:
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
 This type of regex is used to verify that the user input is a valid email address.


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

### Anchors

Regex anchors are meant to match a position between, before, or after characters. They keep the expression aligned to the position matching the input.

In this example, the ^, caret, identifies the beginning of the string, while $ matches the end. In our example, we are looking for a character at the start that matches one of the following, listed after the ^:

/^([a-z0-9_\.-]+)

and at least one of the following characters at the end, before the $.

.([a-z\.]{2,6})$/

### Quantifiers

Quantifiers dictate the amount of characters or instances of groups are used in the input to be allowed in a match. 

The first + in this expression is comsidered the quantifier. This means that the next characters must include:

a-z, 0-9, _, -, .


### OR Operator

The OR operator in regex, | is used for characters matching either side of the |. It is useful for characters with similar meanings adn when the user uses variations of their inout.


### Character Classes

Regex character classes are characters enclosed in square brackets where the regex engine chooses one out of other characters listed. 

In the email example prior:

@([\da-z\.-]

The regex engine would match the inputted character to any from the a-z after the @ symbol listed within the brackets.

### Flags

There a total of 6 different flags inside a regex expression. Below are the types and their function:

i
With this flag the search is case-insensitive: no difference between A and a (see the example below).
g
With this flag the search looks for all matches, without it – only the first match is returned.
m
Multiline mode (covered in the chapter Multiline mode of anchors ^ $, flag "m").
s
Enables “dotall” mode, that allows a dot . to match newline character \n (covered in the chapter Character classes).
u
Enables full Unicode support. The flag enables correct processing of surrogate pairs. More about that in the chapter Unicode: flag "u" and class \p{...}.
y
“Sticky” mode: searching at the exact position in the text (covered in the chapter Sticky flag "y", searching at position)

### Grouping and Capturing

Grouping and Capturing is used to match multiple characters as a whole. Usually they are identified with a set of parenthesis.

([a-z0-9_\.-]+)
([\da-z\.-]+)
([a-z\.]{2,6})

Each set of characters inside the parenthesis is 1 group. For each, one character from the first group must be present before proceeding to group 2, and that carries on to additional groups as well.

### Bracket Expressions

Bracket expressions are just characters needed to be matched within that specific set or class.

[a-z\.]

The above example will match any input if it is within the character a through z.

### Greedy and Lazy Match

Greedy is the term used for a match quantifying the longest possible string. Lazy on the otherhand, is a match using the shortest string available. 
An example of this would be:

<div>MY name is Omar</div>

Greedy translates to: <.+>

Regex will match all of <div>MY name is Omar</div> - from starting < to ending >. The string will result in more characters and this generally the most common.

Lazy: <.+?>

Here, however, our regex repeats as few times as possible, so it will only match to the first ending > or <div>, resulting in a shorter regex section.

### Boundaries

Regex boundaries, \b matches a word boundary allowing the engine to search entire words only. 

This typically looks like:

\bhello\b

The match would be specifiaclly the word "hello"

### Back-references

Regex back-references match the same characters as a previous capturing group. Basically, this allows us to back reference the captures we've made previously for later use.

### Look-ahead and Look-behind

Look-ahead and look-behind assertions are also known as lookarounds and only tell us whether a characters are a match or not. While not present in our matching emails regex, we can consider the following:

Lookahead
\d+(?=000)

In this example, any found digits must have 000 after to be considered a match. So 230 is not a match, but 23000 is.

Lookbehind
A lookbehind matches only if there's something before it:
(?=10)+\d

So 23 is not a match, but 1023 is.

## Author

Omar Orrantia

Github profile: https://github.com/omaro454
