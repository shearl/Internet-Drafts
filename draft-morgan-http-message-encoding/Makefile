xml2rfc ?= "/usr/bin/xml2rfc"
saxpath ?= "$(HOME)/java/saxon-8-9-j/saxon8.jar"
saxon ?= java -classpath $(saxpath) net.sf.saxon.Transform -novw -l

draft := draft-morgan-http-message-encoding
TARGETS := $(draft).txt $(draft).html

.PHONY: all clean

all: $(TARGETS)

%.txt: %.redxml
	$(xml2rfc) $< $@

#stylesheet := lib/rfc2629.xslt
stylesheet := lib/myxml2rfc.xslt
%.html: %.xml $(stylesheet)
	$(saxon) $< $(stylesheet) > $@

reduction := lib/clean-for-DTD.xslt
%.redxml: %.xml $(reduction)
	$(saxon) $< $(reduction) > $@

clean:
	-rm -f $(draft).redxml
	-rm -f $(TARGETS)
