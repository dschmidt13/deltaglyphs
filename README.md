deltaglyphs
-----------

A simple, symbolic standard to streamline commit messages.

`v0.9.0`

```
+New code.
~Refactored or optimized.
-Code removed.
^Bug fix.
*Contains known bug.
```

## Purpose

This specification defines a set of conventions to communicate crucial context
of a VCS commit with a single symbol (referred to here as a "glyph").

This crucial context is the type of change being made. Changes to a technical
document, including code, can focus on various areas, such as additions,
removals, restructuring or refactors, corrections, unfinished work for the sake
of collaboration, and so on. Commit messages used to *describe* changes, on the
other hand, can often be overly terse and unhelpful. Therefore, unless all
project authors maintain the utmost discipline (which takes time and energy),
navigating a version history can at best depend on trusting a constrained tool
set (e.g., `git search` or automated regression tests), and at worst a tedious
exercise in reviewing whole change sets file by file.

These conventions may be adopted to ensure that *some* discipline is enforced in
the information communicated by commit messages while minimizing the time and
cognitive cost of doing so. According to leading psychologists (no reference
provided), one of the best ways to get people to do the right thing is to simply
make it easier. This standard aims to do that.


## General Rules

1) All commit messages must be prefixed by at least one glyph (without spaces).
2) All glyphs that apply to a commit must be included in the prefix (without
   spaces), ordered by glyph precedence.
3) Glyphs should be used as conventionally defined. Teams may agree to house
   rules, but this is discouraged (sensible house rules should be pushed
   upstream when possible).
4) Several glyphs are explicitly omitted to allow custom extension or simplify
   automated processing.
5) A few glyphs are reserved for future use.


## Glyph Definitions

- `~`: Indicates that the end result is approximately the same to most outside
       observers. This usually includes refactors and small optimizations.
- `+`: Indicates that new APIs, implementations, features, etc. were added.
- `-`: Indicates that APIs, implementations, features, etc. were removed.
- `*`: Indicates that the code included in the commit contains a known bug,
       shortcoming, or incomplete implementation. Sometimes, there is value in
       collaborating quickly, even if all the edge cases aren't supported!
- `^`: Indicates that something was fixed, such as a bug, a preceding `*`, or
       a major performance issue.


## Example Repo Commit History

*Lower messages are earlier.*

```
^Intro typo.
^Don't scroll if updating old answers.
+Scoring info in quiz intro.
+^Impl basic scoring algo; fixed content flags.
+*Quiz results. Result calc not written.
^Justifying question content.
^Updating Intro wording.
^Styling intro.
^Widening radio lines to improve clickability.
~Explicitly defining state only in Quiz.
+Default debug launcher.
+Auto-scroll as questions are answered.
+Introduction to the quiz.
+Radio improvements.
+Answer state tracking, dynamic quiz progress.
```


## Glyph Precedence

Glyphs should present in this order:

```
~+-*^
```


## Omitted Glyphs

These glyphs might conflict with automated parsers or have limited semantic
value, and so are explicitly omitted as potential deltaglyphs. Users of this
spec are free to use these as they see fit throughout their commit messages.

```
Quotes: `'"
Wrappers: ()[]{}<>
Token markers: @#$%
HTML/logic operators: &|
Other punctuation: _.,:;/\
```


## Reserved Glyphs

These glyphs are currently reserved for possible future use by this standard.

```
?!=
```


## Ongoing Development

This standard is a work in progress. Feedback is welcome via Git Issues, Pull
Requests, emails, and any other avenue you can find to make your point.

The initial specification was conceived of with care some years ago, but finally
described and published here in relative haste. For any confusion resulting from
subpar quality or poor or incomplete explanations, I apologize. These may also
be refined within some months after initial publication. (If they persist beyond
that, or if you are eager or anxious for a correction, please file a complaint.)
