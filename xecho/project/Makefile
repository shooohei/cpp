CC := gcc

CFLAGS :=
CFLAGS += -Wall
CFLAGS += -std=c++11

CFLAGS_DEBUG := -g3 -O0
CFLAGS_RELEASE := -g0 -O2

TARGET := xecho

DEVROOT := ../..

INCLUDE_FILES :=
INCLUDE_FILES += $(DEVROOT)/include
INCLUDES := $(foreach INCLUDE_FILE, $(INCLUDE_FILES), -I$(INCLUDE_FILE))

OBJS :=
OBJS += xecho.o
SRCS := $(OBJS:.o=.cpp)

vpath %.cpp $(DEVROOT)/$(TARGET)/src

.PHONY: release debug all install clean distclean

release: CFLAGS += $(CFLAGS_RELEASE)
release: all

debug: CFLAGS += $(CFLAGS_DEBUG)
debug: all

all: $(TARGET)
	@echo finish!!!

$(TARGET): $(OBJS)
	$(CC) $(CFLAGS) $(INCLUDES) $^ -o $(TARGET)

.cpp.o:
	$(CXX) $(CFLAGS) $(INCLUDES) -c $< -o $@

install:
	cp $(TARGET) /usr/local/bin

clean:
	rm -f *.o

distclean: clean
	rm -f $(TARGET)
