# REGEX METACHARACTERS

_most usual regex metacharacters_

### Representative Metacharacters

. | Matches all characters

[...] | Allow only the characters inside the list

[^...] | Doesn't allow the characters inside the list

### Quantifier Metacharacters

? | Do the previous character optional

\- | May does not have several characters of the previous character

\* | Repeat the previous character at least one time

{} | Repeat the previous regex or previous characters on the interval between
last and first element - if passed only one element repeat for element-time

### Anchors Metacharacters

^ | Begin of line

$ | End of line

\b | Start or end with the element - it's depends if passed or begin or end of the line

\ | Remove the special function of the character

\1 | Return **the value, not regex** of a group in the passed position - the count always happens the left to right

() | Group a regex, it's necessary with the rearview

### (?=RE) / (?!RE) / (?<=RE) / (?<!RE)

**input:** homer simpson | simpson homer

**regex:** homer(?= simpson) | **match:** **homer** simpson

**regex:** homer(?! simpson) | **match:** simpson **homer**

**regex:** (?<!simpson )homer | **match:** **homer** simpson

**regex:** (?<=simpson )homer | **match:** simpson **homer**

**obs:** The form (? ...) it's supported only for some languages and tools - new metacharacters
