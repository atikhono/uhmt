MAIN = Thesis

.PHONY: all clean cclean

all: cclean $(MAIN).pdf


$(MAIN).pdf: $(MAIN).tex $(MAIN).bib
	pdflatex -file-line-error -shell-escape $(MAIN)
	bibtex   $(MAIN)
	pdflatex -file-line-error $(MAIN)
	@while ( grep "Rerun to get cross-references"\
	  $(MAIN).log > /dev/null ); do\
	    echo '** Re-running LaTeX **';\
	    pdflatex -file-line-error $(MAIN);\
	  done
	make clean

clean:
	rm -fr *.bbl *.blg *.aux *.log *.loc *.lof *.lot *.loa *.soc *.out *.toc *.dvi *~

cclean: clean
	rm -f $(MAIN).pdf
