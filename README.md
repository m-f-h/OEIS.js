# OEIS.js
(c) 2019 by M.F.Hasler

For the moment being, two contributions for improving the pages at http://OEIS.org :

1) a **universal** javascript (sequence independent!) for client-side created **dynamic content**

2) CSS code (style sheet) to make OEIS pages (by a factor 2 - 4) shorter, better structured and readable.

As a proof of concept, we provide for the moment a simple example page which:
* has a < STYLE > section allowing the rest of the page to be very "clean": no dozens of extraneous TABLE, FONT, TT and other tags; each displayed record has one TABLE tag for the header line (A-number & NAME), and one more TABLE for the rest of the record, each section being simply of the form < TR > < TH > OFFSET/COMMENT/... < TD > < P > content1 < P > content2 ...
* has one single **<code>oejs()</code>** javascript function, _independent of the sequence_, which implements the following functions:
* a button [EXTEND] in the DATA section: upon each click, one more value is added to the DATA section. This can obviously very easily be modified to print an arbitrary number of terms in any desired format, in particular it can produce a b-file of any desired length. (The idea is that an additional input element will enable the user to specifiy the format and number of terms he wants.)
* a button [PARI] in the PROG section: by clicking it, it adds PARI code for a function <code>a()</code> which returns the n-th term or optionally all term from the first to the n-th term.
This can obviously very easily (a matter of minutes if not seconds!) be extended to produce (various) code in any desired programming language.
Obviously, it's also very easy to implement additional features like:
* Automatic generation of FORMULAS : G.f., recurrence equation, ...
* Conversely, if the recurrence signature is not given in the LINKS section, the JS could get it from a G.f. or recurrence relation given in FORMULA section. It could also find it from the DATA.
* In case this would be needed, the script can very easily (matter of seconds) be amended to use the bignum.js extension for computations.
* The script could also be amended to be useful for sequences other than linear recurrences. In particular, a possible extension could consist in taking JavaScript (or other) code from the PROG section and use this to create dynamic content for in principle any arbitrary sequence.
* The script could also make consistency checks comparing DATA, FORMULAs, the signature given in LINKS and PROGRAMs.

No need to say for those who know: the CSS and javascript need not to be part of the HTML page, it is sufficient (actually: preferred) to put these in a separate file on the server and only have a link in the main HTML page. This would improve performance and decrease traffic even further.
