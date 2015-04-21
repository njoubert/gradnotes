

R = main
R_output = ResearchNotesOnQuadrotorCinematography
STY = *.cls
FIG = images/*.pdf

# For GNU completeness
.DEFAULT_GOAL := pdf

pdf: $(R_output).pdf

$(R).bbl: $(R).bib
	pdflatex $(R)
	bibtex $(R)
	texindy --language english $(R).idx
	pdflatex $(R)
	pdflatex $(R)


$(R).pdf: *.tex $(STY) $(R).bbl
	pdflatex $(R)

$(R_output).pdf: $(R).pdf
	cp $(R).pdf $(R_output).pdf

clean:
	rm -f $(R).log $(R).aux $(R).bbl $(R).blg $(R).out
