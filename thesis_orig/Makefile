#
# Makefile for report
#

MAIN  = report
FIGURES = $(patsubst %.eps,%.pdf,$(wildcard ./figures/*.eps))

.PHONY: all clean cclean

all: $(MAIN).pdf


$(MAIN).pdf:  $(MAIN).tex  $(MAIN).bib $(FIGURES)
	pdflatex -file-line-error -shell-escape $(MAIN)
	bibtex   $(MAIN)
	pdflatex -file-line-error $(MAIN)
	@while ( grep "Rerun to get cross-references"\
	  $(MAIN).log > /dev/null ); do\
	    echo '** Re-running LaTeX **';\
	    pdflatex -file-line-error $(MAIN);\
	  done
	make clean



%.pdf: %.eps
	epstopdf $<


show: cclean $(MAIN).pdf
	open $(MAIN).pdf &

clean:
	rm -fr *.bbl *.blg *.aux *.log *.lof *.lot *.loa *.out *.toc *.dvi *~

cclean: clean
	rm -f $(MAIN).pdf
