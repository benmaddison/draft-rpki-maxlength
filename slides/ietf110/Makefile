#
# Makefile for I-D update presentations
# $Id: Makefile,v 1.1.1.1 2002-11-11 05:11:48 randy Exp $
#

# Your nroff document is called foo.txt. Change below as appropiate.
THEME=Nord
SHELL=/bin/bash -O globstar

SRC:=$(wildcard *.md)

.PHONY: all
all: pdf

.PHONY: present
present:
	@echo "*** Starting Presentation ***"
	alacritty --class patat_xfloating \
			  --dimensions 200 60 \
			  --command bash -ic 'patat -w $(SRC)'

.PHONY: pdf
PDF:=$(patsubst %.md,%.pdf,$(SRC))
pdf: $(PDF)

%.pdf: %.md
	@echo "*** Generating PDF Slide Deck $* ***"
	pandoc --to "beamer" \
		   --pdf-engine xelatex \
		   --output "$@" \
		   --variable "theme:$(THEME)" \
		   --incremental \
		   "$^"

.PHONY: clean
clean:
	@echo "*** Cleaning up ***"
	rm -rf $(PDF)
