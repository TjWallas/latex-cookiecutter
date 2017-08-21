PDFLATEX = $(shell which pdflatex)
PDFLATEX_ARGS = -halt-on-error -jobname

BIBTEX = $(shell which bibtex)

FILENAME = {{cookiecutter.document_name}}
TARGET = $(FILENAME).pdf
SOURCE_TEX = $(FILENAME).tex
SOURCE_BIB = $(FILENAME).bib

.PHONY: clean rebuild all
.POSIX:

all: $(TARGET)

$(TARGET): $(SOURCE_TEX) $(SOURCE_BIB)
	$(PDFLATEX) $(PDFLATEX_ARGS) $(FILENAME) $(SOURCE_TEX)
	$(BIBTEX) $(FILENAME).aux
	$(PDFLATEX) $(PDFLATEX_ARGS) $(FILENAME) $(SOURCE_TEX)
	$(PDFLATEX) $(PDFLATEX_ARGS) $(FILENAME) $(SOURCE_TEX)


clean:
	$(RM) $(FILENAME).aux $(FILENAME).bbl $(FILENAME).blg $(FILENAME).pdf
	$(RM) $(FILENAME).log $(FILENAME).out $(FILENAME).idx

rebuild: clean all
