GRAFFLE_SCRIPT = graffle.scpt


PAPER=inferenceNotes
FIGURES_DIR=figures
TEXT_DIR=text


TEXFILES = $(PAPER).tex $(wildcard $(TEXT_DIR)/*.tex)
BIBFILES = $(wildcard *.bib)
GRAFFLE = $(wildcard $(FIGURES_DIR)/*.graffle)
GRAFFLE_NAMES = $(notdir $(GRAFFLE))

BUILD_DIR = build
GRAFFLE_PDF = $(addprefix $(BUILD_DIR)/,$(GRAFFLE_NAMES:.graffle=.pdf))
LATEX=latex -output-format=pdf -output-directory=$(BUILD_DIR) -halt-on-error -file-line-error -synctex=1
BIBTEX=bibtex

$(PAPER).pdf: $(BIBFILES) $(TEXFILES) $(GRAFFLE_PDF) $(BUILD_DIR)/.d
	$(LATEX) $(PAPER).tex
	$(BIBTEX) $(BUILD_DIR)/$(PAPER).aux
	cp $(BUILD_DIR)/$(PAPER).blg .
	$(LATEX) $(PAPER).tex
	$(LATEX) $(PAPER).tex
	rm -f $(PAPER).blg
	cp $(BUILD_DIR)/$(PAPER).pdf .
	if [ -e $(BUILD_DIR)/$(PAPER).synctex.gz ] ; then cp $(BUILD_DIR)/$(PAPER).synctex.gz . ; fi
once:
	$(LATEX) $(PAPER).tex
	cp $(BUILD_DIR)/$(PAPER).pdf .
	if [ -e $(BUILD_DIR)/$(PAPER).synctex.gz ] ; then cp $(BUILD_DIR)/$(PAPER).synctex.gz . ; fi
	
$(BUILD_DIR)/%.pdf:	$(FIGURES_DIR)/%.graffle $(BUILD_DIR)/.d
	if [ -e "/Applications/OmniGraffle Professional 5.app" ] ; then osascript $(GRAFFLE_SCRIPT) $(abspath $<) $(abspath $@) ; fi
	touch $@

run: $(PAPER).pdf
	open $(PAPER).pdf

clean:
	rm -rf $(BUILD_DIR)
	rm -f $(PAPER).pdf
	rm -f $(PAPER).synctex.gz
	
#DIRECTORY BUILD RULES
%/.d:	
	mkdir -p $(@D)
	touch $@

.PRECIOUS:	%/.d
.PHONY: all