#
# Makefile for report
#

MAIN  = report
FIGURES = $(patsubst %.eps,%.pdf,$(wildcard ./figures/*.eps))

.PHONY: all clean cclean

all: $(MAIN).pdf


$(MAIN).pdf:  $(MAIN).tex $(MAIN).bib $(FIGURES)
	pdflatex $(MAIN)
	bibtex   $(MAIN)
	pdflatex $(MAIN)
	@while ( grep "Rerun to get cross-references"\
	  $(MAIN).log > /dev/null ); do\
	    echo '** Re-running LaTeX **';\
	    pdflatex $(MAIN);\
	  done
	make clean



%.pdf: %.eps
	epstopdf $<


show: $(MAIN).pdf
	open $(MAIN).pdf &

clean:
	rm -fr *.bbl *.blg *.aux *.log *.lof *.lot *.loa *.out *.toc *.dvi *~

cclean: clean
	rm -f $(MAIN).pdf
