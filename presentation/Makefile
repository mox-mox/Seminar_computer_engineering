# Make the presentation
#
# Author: mox
#
# A image-let is a file with only the TeX code needed to define the image itself and cannot be compiled alone without some boilerplate code

all: 2017-Moritz_Noeltner-Augustin_RISCV_Presentation.pdf

add-in-dir := ../material/latex-add-ins


# The minimal boilerplate file for each image-let
outerfile1 := \
"\\RequirePackage{luatex85}"\
"\\documentclass{standalone}\n"\
"\\input{$(add-in-dir)/common}\n"\
"\\\begin{document}\n"\

outerfile2 := \
"\\\end{document}\n"\

# Find all tex images and require them to be build
images := $(notdir $(wildcard $(add-in-dir)/image_sources/*.tex))
images := $(addprefix $(add-in-dir)/,$(images:tex=pdf))

image-lets: $(images)

$(add-in-dir)/%.pdf: $(add-in-dir)/image_sources/%.tex
	@#echo -e $(outerfile1) "\\input{"$(basename $<)"}\n" $(outerfile2)
	@echo -e $(outerfile1) "\\input{"$(basename $<)"}\n" $(outerfile2) | lualatex -shell-escape -jobname $(notdir $(basename $@))
	mv $(notdir $@) $@
	@rm -f  $(notdir $(basename $@)).aux $(notdir $(basename $@)).log





2017-Moritz_Noeltner-Augustin_RISCV_Presentation.pdf: 2017-Moritz_Noeltner-Augustin_RISCV_Presentation.tex $(images)
	latexmk -lualatex -latexoption="-interaction=nonstopmode --shell-escape"  -use-make $<

.PHONY: distclean
distclean: clean
	rm -f *.pdf

.PHONY: clean
clean:
	rm -f *.log  *.aux  *.nav  *.out  *.snm  *.toc  *.vrb  *.synctex.gz  *.fls  *.fdb_latexmk
	rm -rf _minted*

.PHONY: clean-imagelets
clean-imagelets:
	rm -f $(images:pdf=log)
	rm -f $(images:pdf=aux)
	rm -f $(images)




# Debugging target. Use make print-FOO to print the value of variable FOO
# See http://collaboration.cmc.ec.gc.ca/science/rpn/biblio/ddj/Website/articles/DDJ/2007/0703/070201jg01/070201jg01.html
print-%:
	@echo $* == $($*)
