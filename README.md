# OEIS.js
(c) 2019 by M.F.Hasler

For the moment being, two contributions for improving the pages at http://OEIS.org :

1) a **universal** (sequence independent) javascript for client-side created **dynamic content**:<br/>
compute an arbitrary number of additional terms; create PROGRAMs in various languages.

2) CSS code (style sheet) to make the source code of OEIS pages by a factor 2 - 4 shorter, better structured and readable.

Both of these _can_ be included in the HTML pages sent by the server, but should better be stored in separate files on the server, so they are fetched by the client only once for all pages he will visit, reducing data traffic.

As a proof of concept, we provide for the moment a simple example page. (To test it, [save the OEIS_js_example_page.html](https://raw.githubusercontent.com/m-f-h/OEIS.js/master/OEIS_js_example_page.html) to your computer (Ctrl-S) and open it in the browser.)
* The page has the CSS code in a < STYLE > section allowing the rest of the page to be very "clean":<br/>
each displayed record has **one** TABLE tag for the header line (A-number & NAME),<br/> 
and **one** more TABLE for the rest of the record,<br/> 
each section being simply of the form < TR > < TH > OFFSET/COMMENT/... < TD > < P > content1 < P > content2 ...:<br/>
no more dozens of extraneous TABLE, FONT, TT and other tags!
* It has __one single__ **<code>oejs()</code>** javascript function, _independent of the sequence_, which implements the following:
1) it adds a button **[EXTEND]** in the DATA section: on each click, one more value is added to the DATA section.<br/> 
This can easily be modified to print an arbitrary number of terms in any desired format. In particular it can produce a _b-file of any desired length_: An additional input element (button ...) will enable the user to specifiy the format and number of terms he wants.
2) it adds a button **[PARI]** in the PROG section: clicking it adds PARI code for a function <code>a()</code> which returns the n-th term or optionally all terms from the first to the n-th term.<br/>
This can easily (a matter of minutes if not seconds) be extended to produce various code in any desired programming language.

It is easy to implement additional features like:
* Automatic generation of FORMULAs: G.f., recurrence equation, ...
* Conversely, if the recurrence signature is not given in the LINKS section, the JS can get it from a G.f. or recurrence relation given in FORMULA section. It can also find it from the DATA.
* In case this is needed, the script can easily (matter of seconds) be amended to use the bignum.js extension for computations.
* The script can also be amended to be useful for **sequences other than linear recurrences**. One extension would consist in taking JavaScript (or other) code from the PROGram section and use this to create dynamic content for in principle any arbitrary sequence.
* The script could also make consistency checks comparing DATA, FORMULAs, the signature given in LINKS and PROGrans.
