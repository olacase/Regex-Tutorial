# Regex-Tutorial
This Regular Expression (Regex) tutorial is created as a walk through of the functions of Regular Expressions, This is great for pulling out information from a given body of code and also can serve as well as a tool for validation. A Regex is a series of characters which defines a specific type of search pattern when included in a code or search algorithm, moreso regular expressions can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string. They are also used frequently to validate input data.

# Summary
The following code will be used throughout the tutorial to give specific examples for how the components of regex can be used. The following code can be used for matching emails. One use for this code is that it can be used to validate to make sure that an email follows the correct format.

Matching Email-

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

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
Anchors are what starts and ends the regular expression. 
In this email code,

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/,

the anchors are the ^ and the $. This code is telling the computer that we are looking for strings that starts with

^([a-z0-9_\.-]+)

and end with

.([a-z\.]{2,6})$.

therefore, it must begin and end with the given parameters within the code. otherwise, it is not a match.

### Quantifiers
A quantifier is used to determine how many times a specific character or sequence of characters needs to be present in order to match.
take the following code for matching the email:

([a-z0-9_\.-]+)

it will match any string that contains a-z, 0-9, _, ., or -. The quantifier + means it must contain at least one of these to be a match.
### OR Operator
The next component we will be discussing is the "or" operator. The "or" operator within a regular expression is defined using the | element. The component indicates that it could be either of the components that we are separating with the |. For our hex value regular expression we have 
([a-f0-9]{6}|[a-f0-9]{3}). Note the or operator separating these 2 components. 
This means that our hex value could either be 6 characters [a-f0-9]{6} or 3 characters [a-f0-9]{3}.
### Character Classes
With a Character Classes, you can tell the regex engine to match only one out of several characters. Simply place the characters you want to match between square brackets. If you want to match an a or an e, use [ae]. You could use this in gr[ae]y to match either gray or grey. Very useful if you do not know whether the document you are searching through is written in American or British English.

A character class matches only a single character. gr[ae]y does not match graay, graey or any such thing. The order of the characters inside a character class does not matter. The results are identical.

You can use a hyphen inside a character class to specify a range of characters. [0-9] matches a single digit between 0 and 9. You can use more than one range. [0-9a-fA-F] matches a single hexadecimal digit, case insensitively. You can combine ranges and single characters. [0-9a-fxA-FX] matches a hexadecimal digit or the letter X. Again, the order of the characters and the ranges does not matter.

Character classes are one of the most commonly used features of regular expressions. You can find a word, even if it is misspelled, such as sep[ae]r[ae]te or li[cs]en[cs]e. You can find an identifier in a programming language with [A-Za-z_][A-Za-z_0-9]*. You can find a C-style hexadecimal number with 0[xX][A-Fa-f0-9]+.

### Flags
A flag is an optional parameter to a regex that modifies its behavior of searching. A flag changes the default searching behaviour of a regular expression. It makes a regex search in a different way. A flag is denoted using a single lowercase alphabetic character, typically it comes in the following form:

/regex/

Where the slashes denote where the regular expresssion starts and ends. A flag can be used after the slash to give more guidelines for our matching. The flags are:

g (global)- allows for matching all the instances within a string that follow the matching guidelines set in the regular expression.
m (multiline)-  this expression search line by line rather than searching through a string as a whole.
i (insensitive)- makes the regular expression case-insensitive, so caps and lower-case letters will not affect the matching.
### Grouping and Capturing
referencing the code for matching an email:

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

We can talk about grouping and capturing.

([a-z0-9_\.-]+) is the first group that appears in our regex. This must be true before moving on to "match" the next part of the code. ([\da-z\.-]+) is the second group that appears in our regex. ([a-z\.]{2,6}) is the third group that appears in our regex.

When matching, we have to make sure we are following the guidelines of the group before moving on to the next group.
### Bracket Expressions
Contininuing with the code for matching an email:

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

We can talk about grouping and capturing.

[a-z0-9_\.-]

The guidelines for matching the group. For this code snippet, it can contain letters a-z, numbers 0-9, an underscore, hyphen, or period.

The period is an escaped character, so it required the backslash in order to be able to be matched.
### Greedy and Lazy Match
The standard quantifiers in regular expressions are greedy, meaning they match as much as they can, only giving back as necessary to match the remainder of the regex. By using a lazy quantifier, the expression tries the minimal match first.
### Boundaries
a boundary \b matches positions where one side is a word character  and the other side is not a word character (for instance, it may be the beginning of the string or a space character).

The regex \bcat\b would therefore match cat in a black cat, but it wouldn't match it in catatonic, tomcat or certificate. Removing one of the boundaries, \bcat would match cat in catfish, and cat\b would match cat in tomcat, but not vice-versa. Both, of course, would match cat on its own.

Word boundaries are useful when you want to match a sequence of letters (or digits) on their own, or to ensure that they occur at the beginning or the end of a sequence of characters.

Be aware, though, that \bcat\b will not match cat in _cat or in cat25 because there is no boundary between an underscore and a letter, nor between a letter and a digit: these all belong to what regex defines as word characters. If you want to create a "real word boundary" (where a word is only allowed to have letters), see the recipe below in the section on DYI boundaries.
### Back-references
A backreference in a regular expression identifies a previously matched group and looks for exactly the same text again. A simple example of the use of backreferences is when you wish to look for adjacent, repeated words in some text. The first part of the match could use a pattern that extracts a single word.
### Look-ahead and Look-behind
Lookahead allows to add a condition for “what follows”. Lookbehind is similar, but it looks behind. That is, it allows to match a pattern only if there's something before it.
## Author

Olamide Bello
https://github.com/olacase

## contributions
https://www.google.com
https://www.rexegg.com/
https://www.stackoverflow.com