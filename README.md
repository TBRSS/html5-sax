HTML5-SAX is a bridge between [CL-HTML5-PARSER][html5] and
[CXML][cxml]. It takes the DOM returned by the HTML5 parser and
serializes it to SAX events.

     (defun html->xml (html)
       (html5-sax:serialize-dom (html5-parser:parse-html5 html)
                                (cxml:make-string-sink)))

HTML5-SAX understands namespaces, the `lang` attribute, and the `base`
element, and handles several corner cases where XML is more strict
than HTML.

HTML5-SAX is intended as a complete replacement for [CHTML][chtml]:
CHTML is somewhat faster, but experience at TBRSS has shown that the
HTML5 parser is stabler and gets better results, even on older
documents.

HTML5-SAX also extends `html5-parser:parse-html5` directly:

    (html5-parser:parse-html5 source :dom :cxml-stp)

It adds support for CXML’s [DOM][dom] (as `:cxml-dom`), [STP][stp] (as
`:cxml-stp`), [XMLS][xmls] (as `:cxml-xmls`), and direct serialization
to XML (as `:xml`)).

[html5]: https://github.com/copyleft/cl-html5-parser
[cxml]: http://common-lisp.net/project/cxml/
[chtml]: http://common-lisp.net/project/closure/closure-html/
[dom]: http://common-lisp.net/project/cxml/dom.html
[stp]: http://www.lichteblau.com/cxml-stp/
[xmls]: http://common-lisp.net/project/cxml/xmls-compat.html
