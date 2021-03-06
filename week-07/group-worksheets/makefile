##
# Ben Blazak
# week 7
# makefile for group worksheets
#

CPP := $(wildcard group-*.cpp)

PDF += $(CPP:%.cpp=%.pdf)

# -----------------------------------------------------------------------------

.PHONY: all clean cleanall test

all: $(PDF)
	pdfjoin group-*.pdf -o all-worksheets.pdf
	make test
	make clean

clean:
	-rm $(PDF)

cleanall: clean
	-rm all-worksheets.pdf all-test.pdf
	-rm $(CPP)

test:
	( echo '\\documentclass[12pt,letterpaper]{article}'; \
	  echo '\\usepackage[includehead,'; \
	  echo '            includefoot,'; \
	  echo '            margin=1in,'; \
	  echo '            top=.25in,'; \
	  echo '            headheight=.75in,'; \
	  echo '            headsep=0in,'; \
	  echo '            footskip=0in,'; \
	  echo '           ]{geometry}'; \
	  echo ''; \
	  echo '\\usepackage{multicol}'; \
	  echo ''; \
	  echo '\\begin{document}'; \
	  echo '\\pagestyle{empty}'; \
	  echo '\\begin{multicols}{5}'; \
	  echo '\\begin{verbatim}'; \
	) > all-test.tex
	( for i in `seq -w 1 30`; do \
		  echo "--- $$i ---"; \
		  clang++ -w "group-$$i.cpp"; \
		  echo " 1 3 a :" `echo  1 3 a|./a.out|rev|cut -b -2|rev`; \
		  echo " 7 5 b :" `echo  7 5 b|./a.out|rev|cut -b -2|rev`; \
		  echo " 2 4 c :" `echo  2 4 c|./a.out|rev|cut -b -2|rev`; \
		  echo " 8 3 d :" `echo  8 3 d|./a.out|rev|cut -b -2|rev`; \
		  echo "12 7 e :" `echo 12 7 e|./a.out|rev|cut -b -2|rev`; \
		  echo ''; \
	  done ) >> all-test.tex
	rm a.out
	( echo '\\end{verbatim}'; \
	  echo '\\end{multicols}'; \
	  echo '\\end{document}'; \
	) >> all-test.tex
	latexmk -lualatex -bibtex -pdf all-test.tex
	latexmk -lualatex -bibtex -pdf -c all-test.tex
	rm all-test.tex

# -----------------------------------------------------------------------------

.PHONY: worksheets

worksheets:
	for i in `seq -w 1 30`; do \
		( echo '/**'; \
		  echo ' * group members:'; \
 		  echo ' * week 7'; \
 		  echo ' * worksheet -- group '"$$i"; \
 		  echo ' */'; \
		  echo ''; \
		  echo '#include <iostream>'; \
		  echo 'using std::cout;'; \
		  echo 'using std::cin;'; \
		  echo 'using std::endl;'; \
		  echo ''; \
		  echo 'int main() {'; \
    		  echo '    int  a;'; \
    		  echo '    int  b;'; \
    		  echo '    char c;'; \
		  echo ''; \
    		  echo '    cout << "Enter two integers (separated by a space): ";'; \
    		  echo '    cin >> a >> b;'; \
		  echo ''; \
    		  echo '    cout << "Enter a character: ";'; \
    		  echo '    cin >> c;'; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
    		  echo '    cout << '"`./random-boolean-expression.py`"' << endl;'; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
		  echo ''; \
    		  echo '    return 0;'; \
		  echo '}'; \
		  echo ''; \
		) > "group-$$i.cpp"; \
	done

# -----------------------------------------------------------------------------

%.pdf: %.ps
	ps2pdf $<

%.ps: %.cpp
	mvim --nofork \
	     -c 'set printfont=courier:h10' \
	     -c 'set printoptions=portrait:n' \
	     -c 'set printoptions+=paper:letter' \
	     -c 'set printoptions+=left:5pc,right:5pc' \
	     -c 'set printoptions+=top:5pc,bottom:5pc' \
	     -c ':hardcopy >$@' \
	     -c ':q' \
	     $<;

