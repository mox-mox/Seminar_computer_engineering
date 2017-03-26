# Make the presentation
#
# Author: mox
#


PROJECT_NAME := 2017-Moritz_Noeltner-Augustin_RISCV_Paper.pdf


all: $(PROJECT_NAME)
#all: build


############################### Tikz image-lets compilation ##############################
#
## An image-let is a file with only the TeX code needed to define the image itself and cannot be compiled alone without some boilerplate code
#
#add-in-dir := ../material/latex-add-ins
#
## Find all tex images and require them to be build
#images := $(notdir $(wildcard $(add-in-dir)/image_sources/*.tex))
#images := $(addprefix $(add-in-dir)/,$(images:tex=pdf))
#
#$(add-in-dir)/%.pdf: $(add-in-dir)/image_sources/%.tex $(add-in-dir)/common.tex $(add-in-dir)/boilerplate.tex
#	$(MAKE) -C $(add-in-dir) $(notdir $@)
#
##########################################################################################

#$(PROJECT_NAME): $(PROJECT_NAME:pdf=tex) $(images)
$(PROJECT_NAME): $(PROJECT_NAME:pdf=tex)
	@#lualatex -interaction=nonstopmode --shell-escape $< 
	@#latexmk -lualatex -latexoption="-interaction=nonstopmode --shell-escape -file-line-error"  -use-make $< 
	@#latexmk -lualatex -latexoption="--shell-escape -file-line-error" $<
	latexmk -lualatex -f  -latexoption="-interaction=nonstopmode --shell-escape --file-line-error"  $<
	notify-send "Done building"
	@#bash -c "latexmk -lualatex -latexoption=\"-interaction=nonstopmode --shell-escape\"  -use-make $< 2>/dev/null > /dev/null"



#./2017-Moritz_Noeltner-Augustin_RISCV_Paper.tex:228: Paragraph ended before \begin was complete. 


.PHONY: build
build:
	lualatex -shell-escape  -shell-escape 2017-Moritz_Noeltner-Augustin_RISCV_Paper.tex
	notify-send "Done building"



.PHONY: view
view: $(PROJECT_NAME)
	@echo "Starting zathura"
	@bash -c "zathura $^ 2>/dev/null > /dev/null &"




.PHONY: distclean
distclean:
	rm -f *.log  *.aux  *.nav  *.out  *.snm  *.toc  *.vrb  *.synctex.gz  *.fls  *.fdb_latexmk *.pyg
	rm -rf _minted*

.PHONY: clean
clean: distclean
	rm -f *.pdf

.PHONY: clean-imagelets
clean-imagelets:
	rm -f $(images:pdf=log)
	rm -f $(images:pdf=aux)
	rm -f $(images)




# Debugging target. Use make print-FOO to print the value of variable FOO
# See http://collaboration.cmc.ec.gc.ca/science/rpn/biblio/ddj/Website/articles/DDJ/2007/0703/070201jg01/070201jg01.html
print-%:
	@echo $* == $($*)




commit-%:
	@echo git commit -am $*


