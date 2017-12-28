> > ** REGULAR EXPRESSIONS PYTHON **  
---
Identifiers | Modifiers | White Space Characters | Escape Required
------------ | ------------- | ------------ | -------------
`\d` any number (a digit) | `\d` represents a digit ie(\d{1,9} will declare a digit between 1 and 9 | `\n` new line | `.` `+` `*` `?` `[]` `$` `^` `()` `{}` `\|` `\\`
`\D` anything but a number (NOT DIGIT) | `+` matches 1 or more | `\s` space | 
`\s` space (tab, space, newline, etc) | `?` matches 0 or 1 | `\t` tab | 
`\S` anything but space (NOT SPACE) | `*` matches 0 or more | `e` escape | 
`\w` letters (matching alphanumeric; including "_" | `$` matches end of a string | `\r` carriage return | 
`\W` anything but letters (NOT ALPHANUMERIC) | `^` matches start of a string | `\f` form feed | 
`.` anything but letters (periods) | `\|` matches either or x/y | | 
`\b` any characters except for new line; thus matches the empty string, but only at the beginning or end of a word | `[]` matches a range or variance | | 
`\.` | `{x}` matches x amount of preceding code | | 
`\number` matches the contents of the group of the same numbers.  Groups are numbered starting at 1. | | |
`\A` matches only the start of the string | | | 
`\Z` matches only at the end of a string | | | 
`\B` matches the empty string, but only when it is *not* at the beginning or end of a word | | | 

---
Characters | What they do | Flags
------------ | ------------- | ------------ 
`.` | In default mode, matches any character except a newline | `DOTALL` matches any character including newline
`^` | Matches the start of a string | `MULTILINE` also matches immediately after each newline
`$` | Matches the end of the string or just before the newline at end of the string | `MULTILINE` also matches before a newline
`*` | Causes the resulting RE to match 0 or more repetitions of preceding RE (as many as possible) | 
`+` | Causes the resulting RE to match 1 or more repetitions of preceding RE | 
`?` | Causes the resulting RE to match 0 or 1 repetitions of the preceding RE | 
`*?` `+?` `??` | the `*` `+` and `?` qualifiers are all greedy; they match as much text as possible but adding the `?` after a greedy qualifier makes it non-greedy | 
`{m}` | Specifies that exactly `m` copies of the previous RE should be matched; fewer matches cause the entire RE to not match (ie `a{6}` will match exactly six `a` characters | 
`{m,n}` | Causes the resulting RE to match from `m` to `n` repetitions of the preceding RE, attempting to match as many as possible (ie `a{3,5}` will match from 3 to 5 `a` characters).  Omitting `m` specifies a lower bound of zero, and omitting `n` specifies an infinite upper bound (ie `a{4,}b` will match `aaaab` or a thousand `a` characters followed by a `b` but not `aaab`.  The comma may not be omitted | 
`{m,n}?` | Causes the resulting RE to match from `m` to `n` repetitions of the preceding RE, attempting to match as few repetitions as possible.  This is the non-greedy version of the previous qualifier.  For example, on the 6-character string `aaaaaa`, `a{3,5}` will match 5 `a` characters while `a{3,5}?` will only match 3 characters | 
`\` | Either escapes special characters (`*`, `?`, etc) or signals a **special sequence** | 
`[]` | Used to indicate character sets.  Characters can be listed individually (ie `[amk]` will match `a`, `m`, or `k`).  Ranges of characters can be indicated by giving to characters and separating them with a `-` (ie `[a-z]` matches any lowercase ASCII, or `[0-5][0-9]` will match all the two digit numbers from `00` to `59`). If `-` is escaped (ie `[a\-z]`) or if it is placed as the first or last character (ie `[-a]` or `[a-]` it will match a literal **-**.  Special characters lose their special meaning inside sets (ie `[(+*)]` will match literal characters `(`, `+`, `*` or `)`.  Character classes (ie `\w`) are also accepted in sets.  Characters that are not within a range cab be matched by __complimenting__ the set.  If the first character of a set is `^`, all the characters that are **not** in the set will be matched (ie `[^5]` will match any character except `5`.  To match a literal `]` inside a set, precede it with a backslash or place it at the beginning of the set (ie `[()[\]{}]` and `[]()[{}]`) will both match parenthesis | 
`OR` | `A OR B`, where A and B can be arbitrary REs, creates a REGEX that will match either A or B.  These can be used inside groups.  As scanned RE's are tried left to right.  Once one pattern completely matches, that branch is accepted and no further testing is completed | 

---

---
**GROUPS GROUPS GROUPS** | What do they do/allow you to do | Example(s)
---------------------- | --------------------- | --------------------------
`Match Groups` | Allow us to not just match text, but also to extract information for further processing.  This is done by defining **groups of characters** and capturing them using the special `( and )` metacharacters.  Any subpattern inside a pair of parentheses is captured as a group. | `^(IMG\d+\.png)$` captures anything starting with IMG followed by at least 1 or more digits ending in `.png` or `(\w+)\.py)$` find alls files using alpha numerics that end in `.py` 
`Nested Match Groups` | Good for complex data where you need to extract multiple layers of information.  Generally, the results of capturedgroups are in the order in which they are defined (in order by open parenthesis). | `(\w+\s(\d+))` or `(\w+ (\d+))` or `(\w+\W(\d+))` test for alphanumerics followed by white space followed by digits and captures the whole string match and digits as two different groups
`*` `+` `{m,n}` `?` | Are all quantifiers that can be used in capture groups.  This is the only way to apply quantifiers on sequences of characters instead of the individual characters themselves. Some platforms allow for **NONCAPTURING** groups which will allow you to match the group but not show up in the results | `(\d{3})?` would test area codes
`Its All Condtional` | When using groups, you can use the `pipe` (logical OR) to denote different possible sets of characters.  You can use any sequence of characters or metacharacters in a group. | `I love (cats\|dogs)` matchs only I love cats and I love dogs

---

Extension Notation | What it means 
----------- | --------------
`(...)` | Matches whatever RE is inside the parentheses, and indicates the start and end of a **group**.  The contents of a group can be retrieved after a match has been performed and can be matched later in the string with the `\number` special sequence.  To match `(` or `)` as literals you must escape `\(` `\)` or enclose in a class `[(]` `[)]` 
`(?...)` | This is an extension notation (a `?` following a `(` isn't meaningful otherwise).  The first character after the `?` determines what the meaning and further syntax of the construct is. Extensions don't usually create a new group (except for `(?P<name>...)`
`(?aiLmsux)` | One or more letters from the set `a`, `i`, `L`, `m`, `s`, `u`, `x`.  The group matches the empty string; the letters set the corresponding flags: `re.A` ASCII-only matching, `re.I` Ignore case, `re.L` Locale dependent, `re.M` Multiline, `re.S` Dot matches all, `re.U` Unicode matching, and `re.X` Verbose - these match for the entire REGEX.  These are useful when you want to pass a flag as part of the RE instead of passing a flag argument to `re.compile()`.  Flags should be used *first* in the expression string
`(?:...)` | A non-capturing version of regular parentheses.  Matches whatever RE is inside the parentheses, but the substring matched by the group *cannot* be retrieved after performing a match or reference later in a pattern 
`(?imsx-imsx)` | Zero or more letters from the set `i`, `m`, `s`, `x`, optionally followed by `-` followed by one ore more letters from the same set.  These either set or remove the corresponding flags, for part of the expression 
`(?P<name>...)` | Similar to regular parentheses, but the substring matched by the group is accessible via the symbolic group name ***name***.  Group names must be valid Python identifiers, and each group name must be defined only once within a REGEX.  A symbolic group is also a numbered group, just as if the group were not named. 
`(?P=name)` | A backreference to a named group; it matches whatever text was matched by the earlier group named ***name***
`(?#...)` | A comment; the contents of the parentheses are simply ignored
`(?=...)` | Matches if `...` matches next, but doesn't consume any of the string.  This is called a *lookahead assertion*. (ie `Isaac (?=Asimov)` will match `Isaac` only if its followed by an `Asimov`
`(?!...)` | Matches if `...` doesn't match next.  This is a *negative lookahead assertion*. (ie `Isaac (?!Asimov)` will match `Isaac` only if it's not followed by `Asimov`
`(?<=...)` | Matches if the current position in the string is preceded by a match for `...` that ends at the current position.  This is called a *positive lookbehind assertion*. `(?<=abc)def` will find a match in `abdcef`, since the lookbehind will back up 3 characters and check if the contained patter matches  The contained pattern must only match strings of some fixed length. 
`(?<!...)` | Matches if the current position in the string is *not* preceded by a match for `...`.  This is called a *negative lookbehind assertion*

---

RE Module Contents (.re) | What it does
--------------- | -----------------
`re.compile(pattern, flags=0)` | Compile a REGEX pattern into a REGEX object, which can be used for matching using `match()`, `search()`, and other methods.  Using `re.compile()` and saving the resulting regex object for reuse is the most efficient if it is to be reused
`re.VERBOSE` | Allows you to write REGEX that look nicer and are more readable by allowing you to visually separate logical sections of the pattern and add comments
`re.search(pattern, string, flags=0)` | Scan through a string looking for the **FIRST** location where the regular expression *pattern* produces a match, and return a corresponding match object.  Return `None` if no position in the string matches the pattern.
`re.match(pattern, string, flags=0)` | If zero or more characters at the begining of the string match the regular expression *pattern*, return a corresponding match object.  Return `None` if the string doesn't match the pattern
`re.split(pattern, string, maxsplit=0, flags=0)` | Split string by the occurrences of *pattern*.  If capturing parentheses are used in pattern, then the text of all groups in the pattern are also returned as part of the resulting list.  If *maxsplit* is nonzero, at most maxsplits can occur and the remainder of the string is returned as the final element of the list
`re.findall(pattern, string, flags=0)` | Return all non-overlapping matches of *pattern* in string, as a ***list of strings***.  The string is scanned left-to-right, and matches are returned in the order found.  If one or more groups are present in the pattern, return a list of groups; this will be a list of tuples if the pattern has more than one group.  Empty matches are included in the result unless they touch the beginning of another match
`re.finditer(pattern, string, flags=0)` | Return an *iterator* yielding match objects over all non-overlapping matches for the RE pattern in string. The string is scanned left-to-right, and matches are returned in the order found. Empty matches are included in the result unless they touch the beginning of another match.
`re.sub(pattern, repl, string, count=0, flags=0)` | Return the string obtained by replacing the leftmost non-overlapping occurrences of *pattern* in string by the replacement `repl`.  If the pattern isn't found, string is returned unchanged. `repl` can be a string or a function; if a string, any backslash escapes in it are processed (ie `\n` is converted to newline).  If `repl` is a function, it is called for every non-overlapping occurrence of *pattern*.  The function takes a single match objet argument and returns the replacement string.  Optional argument `count` is the maximum number of pattern occurences to be replaced and must be a non-negative integer.  If omitted or 0, all instances will be replaced.
`re.subn(patteren, repl, string, count=0, flags=0)` | Perform the same operation as `sub()`, but return a `tuple(new_string, number_of_subs_made)`
`re.escape(pattern)` |  Escape all the characters in pattern except ASCII letters, numbers and `_`. This is useful if you want to match an arbitrary literal string that may have regular expression metacharacters in it.

---

Regular Expression Objects | What they do
------------------------ | ---------------------
`regex.search(string[, pos[, endpos]])` | Scan through a string looking for the first location where this regular expression produces a match, and return a corresponding `match object`.  Return `None` if no position in the string matches the pattern; not this is different from finding a zero length match at some point in the string.  The second parameter `pos` gives an index in the string where the search is to start; defaulting to `0`.  The `^` pattern character matches the real beginning of the string and at postions just after a newline, but not necessarily at the index where the search is to start.  The option parameter `endpos` limits how far the string will be searched; it will be as if the string is `endpos` characters long; so only characters from `pos` to `endpos - 1` will be search for a match.
`regex.match(string[, pos[, endpos]])` | If zero or more characters at the *beginning of string match* this regular expression, return a single corresponding `match object`.  Return `None` if the string does not match the pattern; this is different from a zero-length match.  `pos` and `endpos` work the same as in search.  This is for matching anywhere in a string.
`regex.fullmatch(string[,pos[,endpos]])` | If the whole string matches this regular expression, return a corresponding `match object`.  Return `None` if the string doesn't match the pattern.  Optional `pos` and `endpos`.
`regex.split(string, maxsplit=0)` | Identical to the `split()` function, using the compiled pattern
`regex.findall(string[,pos[,endpos]])` | Similar to the `findall()` function, using the compiled pattern, but also accepts optional `pos` and `endpos` parameters that limit the search regions
`regex.finditer(string[, pos[, endpos]])` | Similar to the `finditer()` function, using the compiled pattern, but also accepts optional `pos` and `endpos` parameters that limit the search region
`regex.sub(repl, string, count=0)` | Identical to the `sub()` function, using the compiled pattern.
`regex.subn(repl, string, count=0)` | Identical to the `subn()` function, using the compiled pattern.
`regex.groups` | The number of capturing groups in the pattern
`regex.groupindex` | A dictionary mapping any symbolic group names defined by `(?P<id>)` to group numbers. The dictionary is empty if no symbolic groups were used in the pattern.
`regex.pattern` | The pattern string from which the RE object was compiled

---

Regular Expression Match Objects | What they do (since match objects always have a boolean value of `True` and `None` if no matches
-------------------------- | -----------------------------
`match.expand(template)` | Return the string obtained doing backslash substitution on the template string `template`, as done by `sub()` method.  Escapes are converted, and numeric backreferences `(\1, \2)` and named backreferences `(\g<1>, \g<name>)` are replaced by the contents of the corresponding group
`match.group([group1, ...])` | Returns one or more subgroups of the match. If there is a single argument, the result is a single string; if there are multiple arguments, the result is a tuple with one item per argument. Without arguments, group1 defaults to zero (the whole match is returned). If a groupN argument is zero, the corresponding return value is the entire matching string; if it is in the inclusive range [1..99], it is the string matching the corresponding parenthesized group. If a group number is negative or larger than the number of groups defined in the pattern, an IndexError exception is raised. If a group is contained in a part of the pattern that did not match, the corresponding result is None. If a group is contained in a part of the pattern that matched multiple times, the last match is returned. Names groups can be refered to by their index.  If group matches multiple times, only the last match is accessible.
`match.__getitem__(g)` | This is identical to m.group(g) 
`match.groups(default=None)` | Return a tuple containing all the subgroups of the match, from 1 up to however many groups are in the pattern.  The *default* argument is used for groups that didn't participate in the match, it defaults to `None`
`match.groupdict(default=None)` | Return a dictionary containing all the `named` subgroups of the match, keyed by the subgroup name.  The default argument is used for groups that didn't participate in the match and defaults to `None`
`match.start([group])` | 
`match.end([group])` | Return the indices of the start and end of the substring matched by group; group defaults to zero (meaning the whole matched substring). Return `-1` if group exists but did not contribute to the match. 
`match.span([group])` | For a match `m`, return the 2-tuple `(m.start(group), m.end(group))`. Note that if group did not contribute to the match, this is `(-1, -1)`. group defaults to zero, the entire match.
`match.pos` | The value of pos which was passed to the `search()` or `match()` method of a regex object. This is the index into the string at which the RE engine started looking for a match.
`match.endpos` | The value of `endpos` which was passed to the `search()` or `match()` method of a regex object. This is the index into the string beyond which the RE engine will not go.
`match.lastindex` | The integer index of the last matched capturing group, or `None` if no group was matched at all. For example, the expressions `(a)b`, `((a)(b))`, and `((ab))` will have `lastindex == 1` if applied to the string `'ab'`, while the expression `(a)(b)` will have `lastindex == 2`, if applied to the same string.
`match.lastgroup` | The name of the last matched capturing group, or `None` if the group didn’t have a name, or if no group was matched at all.
`match.re` | The regular expression object whose `match()` or `search()` method produced this match instance
`match.string` | The string passed to `match()` or `search()`

---
