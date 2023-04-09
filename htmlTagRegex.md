# htmlTagRegex

A gist describing a regex used to search for HTML tags

## Summary

This gist searches for both opening and closing HTML tags.  The regex is `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`  I will break down the components to explain exactly what it is searching for.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components
`/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`

Read as "Opens with a `<` followed by 1 or more characters from `a-z`.  Those characters can not be followed by a `<`.  The `*` indicates it can match zero or more times.  The regex will then search for a `>`, but will not include it in the response, due to the `?:`. Next, there can be any amount or type of characters in between, or none at all, given `.*`.  Following in the search is a literal `<`, a literal `/`, the first matching group `([a-z]+)`, and a `>` OR any amount of whitespace, a `/`, then a `>`.

### Anchors
This regex has two anchors.  The first is an opening anchor and signifies it is the beginning of the string being searched: `/^`.  Alternatively: `$/` signifies the end.

### Quantifiers
Quatifiers set limits on the number of characters in the string.  This regex uses three.  `+` to symbolize 1 or more matches, `*` to symbolize 0 or more matches, and `?` to symbolize none or 1 matching character.

### Grouping Constructs
Grouping constructs, or subexpressions, allow you to check sections of characters together.  There are 4 in total here.

`([a-z]+)` = 1 or more characters, a through z.
`([^<]+)` = does not include `<` one or more times.
`(.*)` = any amount of chacters, of any type except a `\n`.
`(?:>(.*)<\/\1>|\s+\/>)` = search for a `>` but don't include it in the response, followed by any type and/or amount of characters (except `\n`), followed by a `<`, then a `\`, next it repeats the text from the first group `([a-z]+)` and a `>`.  OR, any amount of white space, followed by a `/>`.

### Bracket Expressions
Bracket Expressions allow for any qualifying character that fit within the range set inside of the bracket.  The boundaries of the range are identified by opening and closing square brackets.  There are two bracket expressions here, `[a-z]` and `[^<]`.  If a bracket expression starts with a `^`, as in the second example, it means to return anything that does NOT include the characters in that expression.

### Character Classes
Character classes are a grouping of character types.  Each time one is used, the regex searches for one instance.  Here, we have a `.`, which means it matches any character except a `\n`.  Also, we use a `\s` which stands for white space (spacebar, tab, return), and a `\1` which tells us to match the result found with the first expression (in this case, `([a-s]+)`).

### The OR Operator
Represented by a `|`, the OR operator finds one instance out of each option segmented by the `|`.  Here, we use it to separate the options of `?:>(.*)<\/\1>` and `\s+\/>`.

### Flags
Flags can be used to set universal parameters on a regex.  There are no flags used in this regex.

### Character Escapes
The use of `\` allows for a character to have its literal meaning, instead of its typical use, assuming it isn't being used for a character class.  Here, we use it twice to denote a literal `/`

## Author

If you have any questions, please email me at quickfire25@yahoo.com.
You can also find more information at https://github.com/SotoTheMayor
