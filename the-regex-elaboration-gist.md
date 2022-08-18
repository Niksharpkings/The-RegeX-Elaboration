# [The Regex Elaboration - The Intro To Regular/Rational Expressions -](#regex-elaboration)

## Intro

> You may have heard people say or use regex before, but didn't know what it meant
> or maybe had been perplexed on how a computer, search engine, or program managed to get your search result in a timely manner if not almost instantly?
>
> > Well in short, the answer is **_Regex_**?
> >
> > > ### So what is **_Regex_** ?
> > >
> > > > #### Let Me **_Elaborated_** it for you

## Summary

Regex is a powerful regular math -> English language finite automation, which can be also referred as Stephen Cole Kleene's theorem, used to sequentially characterized specific search patterns of text/symbols/documents by using a string-search algorithm, also known as "find" or "find and replace" strings/input validation technique that is developed in theoretical computer science and formal language theory

Regex was popular in Unix text-processing utilities in the 1980 and has now become textualized pattern and match-making sequentialized processing behemoth.
It is widely used in Python, C, C++, Java, JavaScript, web application and widely known and frequently used search engines and platforms.

> __Note__ The following can be used to validate a matching search result of an email:
```regex
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```
> __Warning__ ! I will used this email address as an example:

`👉alias@domain.tld👈`
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

### Anchors
Regex Anchors are used to match the beginning and end of a string.

`
/👉^👈([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})👉$👈/
`

`
👉alias@domain.tld👈
`
> "<code>^</code>" - The circumflex typographical symbol, all so know as the known as a caret in computing and mathematics, denotes as an Anchor that matches the beginning of a string.

> "<code>$</code>" - The dollar sign typographical symbol, all so know as the known as a dollar sign in computing and mathematics, denotes as an Anchor that matches the end of a string.

### Quantifiers
`
/^(👉[a-z0-9_\.-]👉+👈)@(👉[\da-z\.-]👉+👈)\.(👉[a-z\.]👉{2,6}👈)$/
`

`
👉alias👈@👉domain👈.👉tld👈
`
> - __Note__ "<code>+</code>" -> validates that text group signifying  must contain at least one or more characters.
> >The plus sign typographical symbol denotes as a Quantifier that connects to the previous character within the parenthesis `[a-z0-9_\.-]` -> `👉alias👈` and `[\da-z\.-]`-> `👉domain👈`since the `+` its "in" the parenthesis and in front of the closing bracket `]` as so `]+`.  validates that text group signifying  must contain at least one or more characters.
> - __Note__ "<code>{2}</code>" -> Using the bracket notation specific number, in this case 2.
> - __Note__ "<code>{2,}</code>" -> Placing a comma after the number denotes that the value of characters must be 2 or more.
> - __Note__ "<code>{2,6}</code>" -> Validates a range of 2-6.
> > In this case the `{2,6}` is a range of characters that must be between 2 and 6 while validating the within the parenthesis the `[a-z\.]` bracket group which is signifying that it must contain at least one or more characters.

### OR Operator


`
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
`

`
alias@domain.tld
`

> unfortunately the OR operator is not available in this email example. The OR operator is used to match the first of two or more patterns. 

> - __Note__ This means that, well lets say we have `[a-z.]`. Regex will searches alphabetically for characters or one special character included in this pattern.
> - __Note__ `a(b|c)` matches a string with the following, either with b "`or`"/"`|`" c after it.
> - __Note__ `a[bc]` would do the same as above, just without having to put | between each character.

### Character Classes


> Character classes are defined by there names and represents a class of characters
> - __Note__ `\d` -> matches a single character that is a numerical digit.
> - __Note__ `\w` -> matches a single character that is a word character.
> - __Note__ `\s` -> matches a single character that is a whitespace character, tabs, and line breaks.
> - __Note__ `\.` -> matches a single character that is a period.
> - __Note__ `\b` -> matches a single character that is a word boundary.
> - __Note__ `\p` -> matches a single character that is a Unicode property.
> - __Note__ `[abc]` -> matches a single character that is either a, b, or c.
> - __Note__ `[a-z]` -> matches a single character that is lowercase letter.
> - __Note__ `[A-Z]` -> matches a single character that is UpperCase letters.
> - __Note__ `[a-zA-Z]` -> matches a single character that is an alphabetic character.
> - __Note__ `[a-zA-Z0-9]` -> matches a single character that is an alphanumeric character.
> - __Note__ `[a-zA-Z0-9_]` -> matches a single character that is an alphanumeric character or underscore.

> - __Warning__ The  `\d`, `\w`, and `\s` have negations with its counter partner `\D`, `\W`, and `\S`. therefore we use the `.`  dot operator with caution.
> - Example:
>  - - `([a-z0-9_\.-]+)`this could include any lowercase letters, any numbers, an underscore, `.`s, and `-`s.
>  - - `([\da-z\.-]+)`this could include any lowercase letters, any numbers, an underscore, `.`s, and `-`s.
>  - - `([a-z\.]{2,6})`this could include any lowercase letters, any numbers, an underscore, `.`s, and `-`s.

### Flags
The expression flags have the ability to change how the expression is interpreted. Additionally, flags follow the closing forward slash of the expression.

> - `i` -> *Ignores case* -> This makes the entire expression case-insensitive
> - `g` -> *Global search* - It retains the index of the last match, which allows the subsequent searches to start and from the end of the previous match without global flagging subsequent searches that return with the same resulting match.
> - `m` -> *Multiline flag* -> This Multiline flag initiates both the beginning(`^`) and end(`$`) anchors that will match the start and end of a line, instead of the start and end of the whole string.
> - `u` -> *Unicode* -> unicode escapes are in forms of \u#### and \x## which are supported.
> - `y` -> *sticky* -> Expression only matches its last indexed position & ignores the global `g` flag because each Regex search is discrete & has no impact the results.
> - `s` -> *dotall* -> Dot (`.`) matches any character, including the newline (kinda like a CSS wild card `*`).

> > In other words:
> > - `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/g ` 👉a👈lias@domain.tld ✔ accepts but
> > - `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/g ` 👉A👈lias@domain.tld ❌ not accepted

> > - `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/gi ` 
> > - - accepts both
> > - - - 👉a👈lias@domain.tld ✔ accepts 
> > - - - 👉A👈lias@domain.tld ✔ accepts

### Grouping and Capturing

> - `()` -> the regex separates whatever is in the parenthesis groups can have separate string rules that apply to each group.

> - example:
> - - Group 1: `([a-z0-9_.-]+)` -> regex match one or more lowercase letters between a-z, numbers between 0-9, underscores _, periods ., and hyphens -.

> - - Group 2: `([\da-z.-]+) ` -> The domain name must be matched and must use one or more numerical digits, as so it's indicated by the `\d,` letters between `a-z`, period `.`, and hyphen `-`.

> - - Group 3: `([a-z.]{2,6})` - The top level domain(tld) section looks for any group of letters or dots that are 2-6 characters long that can be accounted for region-specific top level domains.

### Bracket Expressions
 `[a-z0-9_\.-]` `[\da-z\.-]` `[a-z\.]` ->  Define a set of characters that can be used to be matched
### Greedy and Lazy Match
`(` `*` `+` `{}` `)` -> Are greedy and lazy match operators. Greedy match will match the longest possible string. Lazy match will match the shortest possible string.
### Boundaries
`^` `$` -> The `^` and `$` anchors are used to match the start and end of a line.
### Back-references
`\1` `\2` `\3` `\4` `\5` `\6` `\7` `\8` `\9` -> The back-references are used to match the contents of a group.

### Lookahead and Lookbehind
`(?=)` `(?!)` -> The `?=` and `?!` lookahead and lookbehind operators are used to match strings that are ahead or behind the current position in the string.

## Author


Hello Word, my name is Nik Sharpio a very enthusiastic and passionate programmer who is striving to become a software engineer and web developer. I am currently a student at the University of California, Los Angeles. I am a very driven and self-motivated individual who is looking for a position in the software or/and industry some time in the future. I can't wait to get started in the industry and I am looking forward to working in a great company or business of some sort.