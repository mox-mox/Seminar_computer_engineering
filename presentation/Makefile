# Make the presentation
#
# Author: mox
#
# A image-let is a file with only the TeX code needed to define the image itself and cannot be compiled alone without some boilerplate code


add-in-dir := ../material/latex-add-ins


# The minimal boilerplate file for each image-let
outerfile1 := \
"\\RequirePackage{luatex85}"\
"\\documentclass{standalone}\n"\
"\\input{../material/latex-add-ins/common}\n"\
"\\\begin{document}\n"\

outerfile2 := \
"\\\end{document}\n"\

# Find all tex images and require them to be build
images := $(notdir $(wildcard ../material/latex-add-ins/image_sources/*.tex))
images := $(addprefix ../material/latex-add-ins/,$(images:tex=pdf))

image-lets: $(images)

../material/latex-add-ins/%.pdf: ../material/latex-add-ins/image_sources/%.tex
	@echo -e $(outerfile1) "\\input{"$(basename $<)"}\n" $(outerfile2)
	@#echo -e $(outerfile1) "\\input{"$(basename $<)"}\n" $(outerfile2) | lualatex -shell-escape -jobname $(notdir $(basename $@))
	mv $(notdir $@) $@
	@rm -f  $(notdir $(basename $@)).aux $(notdir $(basename $@)).log





2017-Moritz_Noeltner-Augustin_RISCV_Presentation.pdf: 2017-Moritz_Noeltner-Augustin_RISCV_Presentation.tex $(images)


.PHONY: clean
clean:
	rm -f *.pdf  *.log  *.aux  *.nav  *.out  *.snm  *.toc  *.vrb  *.synctex.gz
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
