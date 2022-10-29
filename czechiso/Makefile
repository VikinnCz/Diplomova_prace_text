# Projekt czechiso 
# Èeský styl pro BibTeX respektující normu ÈSN ISO 690 (v rámci mo¾ností)
# Autor: David Martinek
# E-mail: martinek AT fit.vutbr.cz
# Verze: 1.0 (2.4.2006)

ALLFILES=czechiso.bst czechiso.dbj czech.mbs readme.txt Makefile czech.pdf

all: czechiso.bst czech.pdf

czechiso.bst: czechiso.dbj czech.mbs
	latex czechiso.dbj

czech.dvi: czech.mbs
	cslatex czech.mbs

czech.ps: czech.dvi
	dvips czech.dvi -o czech.ps

czech.pdf: czech.ps
	ps2pdf czech.ps

pack:
	tar -czvf czechiso.tar.gz $(ALLFILES)

clean:
	rm -f *.dvi *.ps *.log *.glo *~ *.aux