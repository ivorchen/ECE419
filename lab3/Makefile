# Makefile for Mazewar
# $Id: Makefile 357 2004-01-31 19:34:39Z geoffw $

#JIKES=jikes +P -source 1.4
# The jikes is *way* faster if you have it.
#JAVAC=${JIKES}
# Otherwise use Sun's compiler.
#JAVA_HOME=/cad2/ece419s/java/jdk1.6.0/
JAVAC=javac -source 5
JAVADOC=javadoc -use -source 5 -author -version -link http://java.sun.com/j2se/1.6.0/docs/api/  
MKDIR=mkdir
RM=rm -rf
CAT=cat
INSTALLDIR=./install
# The only file we are interested in is Mazewar.class,
# the rest are handled by the dependencies.
FILES=Mazewar.class MazeServer.class

all: ${FILES}

# Rule for making classes.
%.class : %.java 
	${JAVAC} $<

# Build dependencies.  Need jikes to do this.
#dep:
#	${JIKES} +M *.java
#	${CAT} *.u > Makefile.dep
#	${RM} *.u

# Create documentation using javadoc
docs:
	${JAVADOC} -d docs *.java

install: all
	@if [ -d ${INSTALLDIR} ]; \
	   then \
	   mv *.class ${INSTALLDIR}; \
	   chmod a+x ${INSTALLDIR}/*; \
	   echo "Installed in ${INSTALLDIR}"; \
	 else \
	   mkdir ${INSTALLDIR}; \
	   echo "Create ${INSTALLDIR}, Installed in ${INSTALLDIR}"; \
	fi

uninstall:
	-${RM} ${INSTALLDIR}
# Clean up
clean: 
	-${RM} *.class *~ docs/*

# Classfile dependencies
include Makefile.dep

# docs isn't a real target
.PHONY : docs

