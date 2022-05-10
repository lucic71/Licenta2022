BASENAME = main
PDF = $(addsuffix .pdf, $(BASENAME))
DVI = $(addsuffix .dvi, $(BASENAME))
TEX = $(addsuffix .tex, $(BASENAME))
LATEX = latex
PDFLATEX = pdflatex
SHOW=evince

.PHONY: all clean

all: $(PDF)

$(DVI): $(TEX)
	$(LATEX) $<
	# Twice, so TOC is also updated
	$(LATEX) $<

$(PDF): $(TEX)
	$(PDFLATEX) $<
	# Twice, so TOC is also updated
	$(PDFLATEX) $<

show:
	$(SHOW) $(PDF) &

clean:
	-rm -f *~ *.aux *.log *.blg *.bbl *.out *.pdf
