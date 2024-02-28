# Regexplained

A Regular Expression is a filter that allows you to match strings with specific patterns.  A regex allows you to use anchors, quantifiers, flags and classes to execute very specific searches of strings.  

## Summary

In this explanation, we will use an email and phone number.  For example:
gordon.jackman@mail.com (407)867-5309. 

An expression to look for an email and phone number looks like this:
/^[\w\.]+@([\w]+\.)+(com|net|org)\s\(\d{3}\)\d{3}-\d{4}$/

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

Anchors are used in a regular expression to specify a position where the character match occurs on a string.  The most common anchors are:

* "^" - the match will occur at the beginning of a string.
* "$" - the match will occur at the end of a string.


You can see the hat and the dollar sign above at the beginning and ending of the expression.

### Quantifiers

Quantifiers are used in a regular expression to dictate how many occurances of a character there are.  Quantifiers include:

* "*" - matches zero or more times.
* "+" - matches one or more times.
* "?" - matches zero or one time.
* {n} - matches n times only.
* {n, m} - matches from n to m times.

Above, we use the "+" and the {n} in our expression.  The "+" makes sure that we have at least one alphanumeric character or ".".  {3} and {4} are used to limit the digits to a xxx-xxx-xxxx format, like a phone number.

### OR Operator

OR Operators are used as an either/or function for the search.  The syntax is:

(com|net|org)

Above, we use the OR operator to add options for the end of an email.  The expression will filter .com, .net, or .org.  

### Character Classes

Character Classes are a set of specific characters that a match can only be. 
These characters can be placed inside of [ ].  Examples:

* [-.]  - matches one of "-" or "."
* [a-z] - matches a lowercase letter from a to z.
* [az]  - matches only a lowercase a or z.  
* \w    - matches any word character.
* \d    - matches any digit character.

Above, we use [\w\.]+.  This means that all alphanumeric characters and dots will be filtered.  gordon.jackman would be found using this regex

### Flags

Expression flags change how the expression is interpreted. Flags follow the closing forward slash of the expression. Here are some examples:

* "i" - is a flag that ignores case.
* "g" - is a global search that allows multiple searches starting at the end of the first match.  Without it, it will return the same match.
* "m" - is the multiline flag.  Using this, anchors will match on a line instead of the whole string.
* "s" - Dot (.) will match any character, including newline.


### Grouping and Capturing
Any subpattern enclosed within the parentheses () is considered a group.  In the instance of more than one group, they are ascending in number starting with the whole expression ($0) and moving left to right (1...2...3 etc.).  Example:

(407)867-5309. We can group parts of the number together in the expression.  The regular expression would be \(\d{3}\)\d{3}-\d{4}.  If you wanted to group the last 4 digits, \(\d{3}\)\d{3}-(\d{4}) would be the expression.

### Bracket Expressions

These have been mentioned in the Character Classes section of this readME. Anything inside of the brackets will be matched.

### Greedy and Lazy Match

A greedy quantifier will match the longest possible string. Conversely, a lazy quantifier will match the shortest possible string. 
A regular quantifier can be made, lazy, by adding a "?".  Regular expressions are greedy by default.

### Boundaries

"\b" is an anchor known as a word boundary.  Using \b matches before or after an alphanumeric sequence depending on where it is used.

### Back-references

When a group has been captured in (), you can use a back-reference to use the matched string again.  These groups are numbered moving left to right.  The parent group has the number 0.  The other groups are numbered in ascending order from left to right (\1, \2 etc).  

### Look-ahead and Look-behind

* (?=ABC) - is a postive lookahead that matches a pattern after the main expression without including it in the result.
* (?!ABC) - is a negitive lookahead that specifies a pattern that can not match after the main expression.
* (?<=ABC>) - is a postive look-behind that matches a pattern before the main expression without including it in the result.
* (?<!ABC)  - is a negitive look-behind that specifies a pattern that can not match before the main expression.

## Author

Gordon Jackman  
UCF Coding Bootcamp Student  
[Github](https://github.com/spaghedward)