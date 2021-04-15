# Name of the project
PROJECT_NAME = Calculator

# Output directory
BUILD = build

# All source code files
SRC = src/calculator_operations.c

# All test source files
TEST_SRC = test/test_calculator_operations.c\
unity/unity.c\

TEST_OUTPUT =$(call FixPath,$(BUILD)/(TEST_$(PROJECT_NAME)).$(EXEC)) 

# All include folders with header files
INC	= -Iinc\
-Iunity\

#Library Inlcudes
#INCLUDE_LIBS = 
INCLUDE_LIBS = -lcunit
#To check if the OS is Windows or Linux and set the executable file extension and delete command accordingly
ifdef OS
   RM = del /q
   FixPath = $(subst /,\,$1)
   EXEC = exe
else
   ifeq ($(shell uname), Linux)
      RM = rm -rf
      FixPath = $1
	  EXEC = out
   endif
endif

# Project Output name
PROJECT_OUTPUT = $(BUILD)/$(PROJECT_NAME).$(EXEC)

# Document files
DOCUMENTATION_OUTPUT = documentation/html

# Default target built
$(PROJECT_NAME):all

# Run the target even if the matching name exists
.PHONY: run clean test doc all

all: $(BUILD)
	gcc project_main.c $(SRC) $(INC) -o $(PROJECT_OUTPUT)

# Call `make run` to run the application
run:all
	$(PROJECT_OUTPUT)

# Document the code using Doxygen
doc:
	make -C ./documentation

# Build and run the unit tests
test: $(SRC) $(TEST_SRC)
	gcc $^  $(INC) -o $(TEST_OUTPUT) $(INCLUDE_LIBS)
	$(TEST_OUTPUT)
	
$(BUILD):
	mkdir build

# Remove all the built files, invoke by `make clean`
clean:
	rm -rf $(BUILD) $(DOCUMENTATION_OUTPUT)

# Create new build folder if not present
