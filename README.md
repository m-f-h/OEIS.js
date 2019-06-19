# OEIS.js
(c) 2019 by M.F.Hasler

For the moment being, just two contributions for improving the pages at http://OEIS.org :

1) a **universal** javascript (sequence independent!) for client-side created **dynamic content**

2) CSS code (style sheet) to make OEIS pages (typically 50%) shorter, better structured and readable.

As a proof of concept, we provide for the moment a simple example page which:
* has a < STYLE > section allowing the rest of the page to be very "clean": no dozens of useless < TABLE >, < FONT >, < TT >, ...: <br> Each displayed record has one TABLE tag for the header line (A-number & NAME), and one more TABLE for the rest of the record, each section being simply of the form < TR > < TH > OFFSET/COMMENT/... < TD > < P > content1 < P > content2 ...
* has one single **oejs()** javascript function, independent of the sequence, which implements the following functions:
* a button [EXTEND] in the DATA section: upon each click, one more value is added to the DATA section. This can obviously very easily be modified to print an arbitrary number of terms in any desired format, in particular it can produce a b-file of any desired length.
* a button [PARI] in the PROG section: by clicking it, it adds PARI code for a function a() which returns the n-th term or optionally all term from the first to the n-th term.
This can obviously very easily (a matter of minutes if not seconds!) be extended to produce (various) code in any desired programming language.
Obviously, it's also very easy to implement additional features like:
* Automatic generation of FORMULAS : G.f., recurrence equation, ...
* Conversely, if the recurrence signature is not given in the LINKS section, the JS can get it from a G.f. or recurrence relation given in FORMULA section. It could also find it from the DATA.
* In case this would be needed, the script can very easily (matter of seconds) be amended to use the bignum.js extension for computations.
* The script could also be amended to be useful for sequences other than linear recurrences. In particular, a "universal" extension could consist in taking JavaScript (or other) code from the PROGRAM section and use this to create dynamic content as above for (in principle) any arbitrary sequence.

No need to say for those who know: the CSS and javascript need not to be part of the HTML page, it would be sufficient to put a link to these two files if they are stored on the server, which would improve performance and decrease traffic even more. (They would be cached by the user's browser.)
