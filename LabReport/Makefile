# Copyright (c) Geoffrey Lentner 2015. All Rights Reserved.
# Makefile for the LabReport document

# = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =
# build variables

output  = Output
source  = Source
styles  = Styles
main    = Main
project = ExampleReport

# = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =
# include directories

otexflag = --output-directory ${output}
itexflag = #--include-directory ${styles}

# = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =
# latex and bibtex commands

latex  = pdflatex
bibtex = bibtex #biber

# = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =
# build commands

compile_document   = ${latex} ${itexflag} ${otexflag} ${source}/${main}.tex
compile_references = ${bibtex} ${output}/${main}

# = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =
# pdf viewing application/command

view = open 

# = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =
# main target

all: pdf open copy

# = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =
# compile latex document

pdf:
	${compile_document}

# = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =
# call bibtex and run pdflatex twice more

bib:
	cp ${source}/${main}.bib ${output}/
	${compile_document}
	${compile_references}
	${compile_document}
	${compile_document}

# = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =
# view pdf document

open:
	${view} ${output}/${main}.pdf &

# = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =
# copy of pdf

copy:
	cp ${output}/${main}.pdf ./${project}.pdf
