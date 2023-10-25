title:: Document/PEP 8 – Style Guide for Python Code
author:: [[@python.org]]
abbreviated-title:: PEP 8
full-title:: "PEP 8 – Style Guide for Python Code"
start:: [[Oct 22nd, 2023]]
end:: Unfinished
status:: Reading
doccument_type:: Article
url:: https://peps.python.org/pep-0008/
tags:: [[Python/PEP8]]
- Highlights
	- Some other good reasons to ignore a particular guideline:
	  
	  1.  When applying the guideline would make the code less readable, even for someone who is used to reading code that follows this PEP.
	  2.  To be consistent with surrounding code that also breaks it (maybe for historic reasons) – although this is also an opportunity to clean up someone else’s mess (in true XP style).
	  3.  Because the code in question predates the introduction of the guideline and there is no other reason to be modifying that code.
	  4.  When the code needs to remain compatible with older versions of Python that don’t support the feature recommended by the style guide. ([View Highlight](https://read.readwise.io/read/01hdaryxyb9phjw84fxdhqy6qd))
	- Use 4 spaces per indentation level. ([View Highlight](https://read.readwise.io/read/01hdas08adkj6tembk56d5p5qb))
	- Continuation lines should align wrapped elements either vertically using Python’s implicit line joining inside parentheses, brackets and braces, or using a *hanging indent* [[1]](https://peps.python.org/pep-0008/). When using a hanging indent the following should be considered; there should be no arguments on the first line and further indentation should be used to clearly distinguish itself as a continuation line ([View Highlight](https://read.readwise.io/read/01hdas2g2q2xjfntsghd74432e))
	- Correct: # Aligned with opening delimiter. foo = long_function_name(var_one, var_two, var_three, var_four) # Add 4 spaces (an extra level of indentation) to distinguish arguments from the rest. def long_function_name( var_one, var_two, var_three, var_four): print(var_one) # Hanging indents should add a level. foo = long_function_name( var_one, var_two, var_three, var_four) ([View Highlight](https://read.readwise.io/read/01hdas190asxw9wx218pkxbrgp))
	- When the conditional part of an `if`-statement is long enough to require that it be written across multiple lines, it’s worth noting that the combination of a two character keyword (i.e. `if`), plus a single space, plus an opening parenthesis creates a natural 4-space indent for the subsequent lines of the multiline conditional. This can produce a visual conflict with the indented suite of code nested inside the `if`-statement, which would also naturally be indented to 4 spaces. This PEP takes no explicit position on how (or whether) to further visually distinguish such conditional lines from the nested suite inside the `if`-statement. Acceptable options in this situation include, but are not limited to:
	- When the conditional part of an `if`-statement is long enough to require that it be written across multiple lines, it’s worth noting that the combination of a two character keyword (i.e. `if`), plus a single space, plus an opening parenthesis creates a natural 4-space indent for the subsequent lines of the multiline conditional. This can produce a visual conflict with the indented suite of code nested inside the `if`-statement, which would also naturally be indented to 4 spaces ([View Highlight](https://read.readwise.io/read/01hdascfd66ap4y64x9frkgmnk))
	- The closing brace/bracket/parenthesis on multiline constructs may either line up under the first non-whitespace character of the last line of list ([View Highlight](https://read.readwise.io/read/01hdasf6mgraw4h2v493d3rf1n))
	- or it may be lined up under the first character of the line that starts the multiline construct ([View Highlight](https://read.readwise.io/read/01hdasfdsgbp1jfq6vm655yn5q))
	- Spaces are the preferred indentation method. ([View Highlight](https://read.readwise.io/read/01hdasgkzq0gtf91vgf1r338z9))
	- Python disallows mixing tabs and spaces for indentation ([View Highlight](https://read.readwise.io/read/01hdash1gxfkzgce1hjvcfn9jw))
	- Limit all lines to a maximum of 79 characters. ([View Highlight](https://read.readwise.io/read/01hdash7dytvkmgtqwx59fff9p))
	- For flowing long blocks of text with fewer structural restrictions (docstrings or comments), the line length should be limited to 72 characters ([View Highlight](https://read.readwise.io/read/01hdashr6r0qyxvbbqrzyxqh7g))
	- The preferred way of wrapping long lines is by using Python’s implied line continuation inside parentheses, brackets and braces. Long lines can be broken over multiple lines by wrapping expressions in parentheses. These should be used in preference to using a backslash for line continuation ([View Highlight](https://read.readwise.io/read/01hdasn8d60g0p80pnaqx5y42p))
	- Backslashes may still be appropriate at times. For example, long, multiple `with`-statements could not use implicit continuation before Python 3.10, so backslashes were acceptable for that case ([View Highlight](https://read.readwise.io/read/01hdasp1dh8byv2kww52c0dcgs))
	- Another such case is with `assert` statements. ([View Highlight](https://read.readwise.io/read/01hdaspgfa5pvw93qx6y0x952m))
	- For decades the recommended style was to break after binary operators. But this can hurt readability in two ways: the operators tend to get scattered across different columns on the screen, and each operator is moved away from its operand and onto the previous line. ([View Highlight](https://read.readwise.io/read/01hdasqnaz5tv0nrt4brk1jqa6))
	- To solve this readability problem, mathematicians and their publishers follow the opposite convention ([View Highlight](https://read.readwise.io/read/01hdasrnp53bnzeycmf8bhxm8r))
	- Surround top-level function and class definitions with two blank lines ([View Highlight](https://read.readwise.io/read/01hdasssem5h41bxdvma8m702h))
	- Method definitions inside a class are surrounded by a single blank line. ([View Highlight](https://read.readwise.io/read/01hdasszqtd2hqdgmjj53kvbc9))
	- Extra blank lines may be used (sparingly) to separate groups of related functions. Blank lines may be omitted between a bunch of related one-liners (e.g. a set of dummy implementations). ([View Highlight](https://read.readwise.io/read/01hdastknzvffsrshgtvp4m82m))
	- Use blank lines in functions, sparingly, to indicate logical sections. ([View Highlight](https://read.readwise.io/read/01hdasty8wns5db9yye8049t2b))
	- Python accepts the control-L (i.e. ^L) form feed character as whitespace; many tools treat these characters as page separators, so you may use them to separate pages of related sections of your file. Note, some editors and web-based code viewers may not recognize control-L as a form feed and will show another glyph in its place. ([View Highlight](https://read.readwise.io/read/01hdaswk5ktqsh39z0f752jywf))
	- Code in the core Python distribution should always use UTF-8, and should not have an encoding declaration. ([View Highlight](https://read.readwise.io/read/01hdaswy02dx767eh6c0rtrnjp))
	- All identifiers in the Python standard library MUST use ASCII-only identifiers, and SHOULD use English words wherever feasible (in many cases, abbreviations and technical terms are used which aren’t English). ([View Highlight](https://read.readwise.io/read/01hdasy6re6ydke9p4c2dpg4z2))