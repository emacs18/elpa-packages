A tagged, non-deterministic finite state automata (NFA) is an
abstract computing machine that recognises regular languages. In
layman's terms, they are used to decide whether a string matches a
regular expression. The "tagged" part means that the NFA can do
group-capture: it returns information about which parts of a string
matched which subgroup of the regular expression.

Why re-implement regular expression matching when Emacs comes with
extensive built-in support for regexps? Primarily, because some
algorithms require access to the NFA states produced part way through
the regular expression matching process (see `trie.el' for an
example). Secondarily, because Emacs regexps only work on strings,
whereas regular expressions can equally well be used to specify other
sequence types.

A tagged NFA can be created from a regular expression using
`tNFA-from-regexp', and it's state can be updated using
`tNFA-next-state'. You can discover whether a state is a matching
state using `tNFA-match-p', extract subgroup capture data from it
using `tNFA-group-data', check whether a state has any wildcard
transitions using `tNFA-wildcard-p', and get a list of non-wildcard
transitions using `tNFA-transitions'. Finally, `tNFA-regexp-match'
uses tagged NFAs to decide whether a regexp matches a given string.

Note that Emacs' regexps are not regular expressions in the original
meaning of that phrase. Emacs regexps implement additional features
(in particular, back-references) that allow them to match far more
than just regular languages. This comes at a cost: regexp matching
can potentially be very slow (NP-hard, though the hard cases rarely
crop up in practise), whereas there are efficient (polynomial-time)
algorithms for matching regular expressions (in the original
sense). Therefore, this package only supports a subset of the full
Emacs regular expression syntax. See the function docstrings for more
information.

This package essentially implements Laurikari's algorithm, as
described in his master's thesis, but it builds the corresponding
tagged deterministic finite state automaton (DFA) on-the-fly as
needed.