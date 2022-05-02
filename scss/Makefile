PROJECT=scss-diploma-project

build:
	pdflatex ${PROJECT}.tex
	bibtex ${PROJECT}
	pdflatex ${PROJECT}.tex
	pdflatex ${PROJECT}.tex

show:
	evince ${PROJECT}.pdf

clean:
	rm -f *.aux *.blg *.out *.bbl *.log *.toc *.pdf
