#
# 'make depend' uses makedepend to automatically generate dependencies 
#               (dependencies are added to end of Makefile)
# 'make'        build executable file $(TARGET)
# 'make clean'  removes all .o and executable files
# 'make run'	build executalbe file $(TARGET) and run it ./$(TARGET)
#

# define the C compiler to use
CC = g++

# define thr remove command
RM = rm

# define object files directory
OBJS_DIR = obj

# define any compile-time flags
CFLAGS = -Wall -std=c++11

# define any directories containing header files other than /usr/include
# eg: INCLUDES = -I/home/newhall/include  -I../include
# 
INCLUDES = -I../include

# define library paths in addition to /usr/lib
#   if I wanted to include libraries not in /usr/lib I'd specify
#   their path using -Lpath, something like:
#	eg: LFLAGS = -L/home/newhall/lib  -L../lib
# 
LFLAGS = 

# define any libraries to link into executable:
#   if I want to link in libraries (libx.so or libx.a) I use the -llibname 
#   option, something like (this will link in libmylib.so and libm.so:
#	eg: LIBS = -lmylib -lm
#
LIBS =

# define the C source files
SRCS = $(wildcard *.cpp)

# define the C object files 
#
# This uses Suffix Replacement within a macro:
#   $(name:string1=string2)
#         For each word in 'name' replace 'string1' with 'string2'
# Below we are replacing the suffix .c of all words in the macro SRCS
# with the .o suffix
#
OBJS = $(SRCS:%.cpp=$(OBJS_DIR)/%.o)

#
# The following part of the makefile is generic; it can be used to 
# build any executable just by changing the definitions above and by
# deleting dependencies appended to the file from 'make depend'
#

.PHONY: depend

all: $(OBJS)
	@echo [INFO]: $(OBJS) compiled succesfully

# this is a suffix replacement rule for building .o's from .c's
# it uses automatic variables $<: the name of the prerequisite of
# the rule(a .c file) and $@: the name of the target of the rule (a .o file) 
# (see the gnu make manual section about automatic variables)
#
$(OBJS_DIR)/%.o: %.cpp
	@mkdir -p $(OBJS_DIR)
	$(CC) $(CFLAGS) $(INCLUDES) -c $< -o $@

clean:
	$(RM) -f $(OBJS_DIR)/*.o
	$(RM) -r $(OBJS_DIR)

depend: $(SRCS)
	makedepend $(INCLUDES) $^

# DO NOT DELETE THIS LINE -- make depend needs it

eNodeB.o: ../include/eNodeB.h ../include/request.h
normalUser.o: ../include/normalUser.h ../include/userAgent.h
normalUser.o: ../include/request.h
userAgent.o: ../include/userAgent.h ../include/request.h
