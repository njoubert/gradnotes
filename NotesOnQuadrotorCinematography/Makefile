
R = main
R_output = NotesOnQuadrotorCinematography
STY = *.cls
CHAPTER_FILES = $(shell find chapters/ -name '*.tex' -type f -print)

# For GNU completeness
.DEFAULT_GOAL := pdf

pdf: $(R_output).pdf

$(R).bbl: $(CHAPTER_FILES)  $(R).bib
	pdflatex $(R)
	bibtex $(R)
	texindy --language english $(R).idx
	pdflatex $(R)
	pdflatex $(R)

$(R).pdf: *.tex $(STY) $(CHAPTER_FILES) $(R).bbl
	pdflatex $(R)
	pdflatex $(R)

$(R_output).pdf: $(R).pdf
	cp $(R).pdf $(R_output).pdf

clean:
	rm -f $(R).log $(R).aux $(R).bbl $(R).blg $(R).out
