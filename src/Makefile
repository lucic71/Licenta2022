PROJECT=diploma-project

build:
	pdflatex ${PROJECT}.tex
	bibtex ${PROJECT}
	pdflatex ${PROJECT}.tex
	pdflatex ${PROJECT}.tex

clean:
	rm *.aux *.blg *.out *.bbl *.log *.toc *.pdf
