.PHONY: all

# Shared flags etc.
include ../../build/Makefile.conf
LIBIGL_LIB+=-liglembree

all: obj example

.PHONY: example

INC=$(LIBIGL_INC) $(ANTTWEAKBAR_INC) $(EIGEN3_INC) $(GLUT_INC) ${TETGEN_INC} $(MOSEK_INC) $(EMBREE_INC)
LIB=$(OPENGL_LIB) $(GLUT_LIB) $(ANTTWEAKBAR_LIB) $(LIBIGL_LIB) $(TETGEN_LIB) $(MOSEK_LIB) $(EMBREE_LIB)

CPP_FILES=$(wildcard ./*.cpp)
OBJ_FILES=$(addprefix obj/,$(notdir $(CPP_FILES:.cpp=.o))) 

CFLAGS+=-std=c++11 -g

example: obj $(OBJ_FILES)
	g++ $(OPENMP) $(AFLAGS) $(CFLAGS) -o example $(LIB) $(OBJ_FILES) 

obj:
	mkdir -p obj

obj/%.o: %.cpp
	g++ $(OPENMP) $(AFLAGS) $(CFLAGS) -c $< -o $@ $(INC)

obj/%.o: %.cpp %.h
	g++ $(OPENMP) $(AFLAGS) $(CFLAGS) -c $< -o $@ $(INC)

clean:
	rm -f $(OBJ_FILES)
	rm -f example
