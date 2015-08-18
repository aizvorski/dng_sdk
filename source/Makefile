# Binary name
APP=dng_validate

# A DNG image
DNG_IMAGE=tests/test.dng

# The XMP SDK build directory if we don't want to install it system-wide.
XMP_PUB_DIR=../../xmp_sdk/public

INCL=-I $(XMP_PUB_DIR)/include
XMP_RELEASE=$(XMP_PUB_DIR)/libraries/i80386linux_x64/release/
LIB= -L $(XMP_RELEASE) -lXMPCore -lXMPFiles -ljpeg -lz -lpthread -ldl 

CPP_FILES := $(wildcard *.cpp)
OBJ_FILES := $(CPP_FILES:.cpp=.o)


# Execute the binary
all: $(APP)

test:
	LD_LIBRARY_PATH=$(XMP_RELEASE) ./$(APP) $(DNG_IMAGE)

# Linking
$(APP): $(OBJ_FILES)
	g++ $(OBJ_FILES) $(LIB) -o $(APP)

# Compilation
%.o: %.cpp
	g++ -c -Wall $(INCL) $^

clean:
	rm $(APP) *.o
