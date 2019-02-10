This is an inverse companion to the rx package for translating
regexps in string form to the rx notation.  Its chief uses are:

- Migrating existing code to rx form, for better readability and
  maintainability
- Understanding complex regexp strings
  
Please refer to `rx' for more information about the notation.

The exported functions are `xr', which simply returns the converted
rx expression, and `xr-pp', which pretty-prints the rx expression.
Suggested use is from an interactive elisp buffer.

Example (regexp found in compile.el):

  (xr-pp "\\`\\(?:[^^]\\|\\^\\(?: \\*\\|\\[\\)\\)")
=>
  (seq bos
       (or
        (not (any "^"))
        (seq "^"
             (or " *" "["))))

The rx notation admits many synonyms; the xr functions mostly
prefer brief variants, such as `seq' to `sequence' and `nonl' to
`not-newline'.  The user is encouraged to edit the result for
maximum readability, consistency and personal preference when
replacing existing regexps in elisp code.

Similar functionality is provided by the `lex' package in the form of the
`lex-parse-re' function, but `xr' does not depend on `lex' and does
a more thorough job of handling all corner cases of Elisp's regexp syntax.