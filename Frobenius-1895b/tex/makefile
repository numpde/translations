SHELL=/bin/bash
OPEN=xdg-open
-include ~/.Makefile.local

MAIN=main
TDIR=./tex-aux

none: l

e:
	$(OPEN) $(MAIN).tex 1> /dev/null 2> /dev/null &

l:
	@mkdir -p $(TDIR)
	@(pdflatex -output-directory=$(TDIR) -synctex=1 -shell-escape -halt-on-error -interaction=nonstopmode $(MAIN).tex 1> $(TDIR)/pdflatex.log && echo PDFLATEX OK) || cat $(TDIR)/pdflatex.log
	@echo ;

eb:
	$(OPEN) *.bib 2> /dev/null &

o: 
	$(OPEN) $(TDIR)/$(MAIN)*.pdf 2>/dev/null &

clean-tdir:
	@[[ ! -d $(TDIR) ]] || rm -rf $(TDIR)

clean: clean-tdir
	@rm -fv *.log *.aux *.out *.dvi *.ps *.blg *.brf *.bbl
	@rm -fv *.synctex.gz
	@rm -fv *~ *.bib~* *.backup *.bak
	@[[ ! -f $(MAIN).pdf ]] || rm -i $(MAIN).pdf

