# This makefile will allow to quickly generate any single image used in the presentation or paper without having to recompile the whole paper or presentation
#
# Author: mox
#
# A image-let is a file with only the TeX code needed to define the image itself and cannot be compiled alone without some boilerplate code

# Find all tex images and require them to be build
images := $(notdir $(wildcard image_sources/*.tex))
images := $(images:tex=pdf)
all: $(images)


# Build all images as stand-alone version
%.pdf: image_sources/%.tex common.tex boilerplate.tex
	lualatex -shell-escape --jobname '$(basename $@)' boilerplate.tex
	@rm -f  $(basename $@).aux $(basename $@).log


.PHONY: clean
clean:
	rm -f *.pdf
	rm -f *.log
	rm -f *.aux



# Debugging target. Use make print-FOO to print the value of variable FOO
# See http://collaboration.cmc.ec.gc.ca/science/rpn/biblio/ddj/Website/articles/DDJ/2007/0703/070201jg01/070201jg01.html
print-%:
	@echo $* == $($*)
