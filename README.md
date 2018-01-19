# iacrtrans LaTeX Class Documentation

#### Introduction

The iacrtans LaTeX class will be used by the new "IACR Transactions on Symmetric
Cryptology" and "IACR Transactions on Cryptographic Hardware and Embedded Systems"
journal. The class is based on standard LaTeX classes and packages (mainly the
`article` class with `amsmath`), and should be similar in use to the `llncs` class
used for Springer's proceedings. The LaTeX source of this documentation is meant
as an example to show basic usage of the class.

The class is still in development and feedback and comments are welcome.

## FAQ: Frequently Asked Questions
### Converting `llncs` papers to `iacrtrans`
If you have a paper typeset with the `llncs` class, conversion should be relatively
easy. The following steps should be sufficient in most cases (for the submission
version):
 1. Replace `\documentclass{llncs}` with `\documentclass[submission]{iacrtrans}`;
 2. Replace `\bibliographystyle{splncs03}` with `\bibliographystyle{alpha}`;
 3. Add a `\keywords{}` command before the abstract, with keywords separated by `\and`;
 4. Remove commands that might override the class style, such as `\pagestyle{...}` or
    `\thispagestyle{...}`, change of margins (*e.g.* with the `geometry` package),
    change of fonts, ...
 5. See also the section "Typesetting the Bibliography" for more information about how
    to typeset the bibliography.

### Compilation Issues
If your document doesn’t compile with the `iacrtrans` class, you can try adding the
`[nohyperref]` option. This will disable some code in the class that is known to be fragile,
in particular the generation of metadata. If this fixes your compilation problems, please
try to define a clean version of `author`, `title` and/or `keywords` as optional arguments to
these commands (in particular, remove LaTeX macros, and write everything on a single
line), and see if you document now compiles without the `[nohyperref]` option.

## Main Commands
### Title Page

The following commands are used to input informations for the title page.

`\title` to define the title.
A shorter running title can be given as optional argument.

`\subtitle`
to give an optional subtitle.

`\author` to define the author list.
Author names must be delimited by \and macros. If there is one different affiliation
for each author, authors and affiliations will be numbered automatically. Otherwise, each
author name must be followed by `\inst{...}` with the corresponding affiliation(s).
A shorter list of authors for the running head can be given as optional argument.

`\institute` to give author’s affiliation(s).
If there are several affiliations, they must be separated by `\and` macros, and will be
numbered automatically.

`\keywords` to give a list of keywords.
Individual keywords should be separated by the `\and` macro.
If there are fragile commands in the keywords, use the optional argument to give a
text-only version of the keywords; this will be used for the PDF metadata.

`\email` should be used inside the `\institute` argument to typeset author’s email ad-
dress(es). An optional argument can be given for the hyperlink, if different from the
displayed email. For instance, you can group emails as follows:
`\email[alice@foo.com,bob@bob.com]{{alice,bob}@foo.com}`

`\thanks` can be used inside the `\title`, `\author` or `\institute` argument to generate
a footnote with additional information, if needed.

`\maketitle` is used to actually typeset the title.

*The `abstract` environment* should be used to typeset the abstract.
Note that the keywords should be given before starting the abstract environment.
