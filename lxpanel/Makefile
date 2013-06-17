program_NAME := assault.so
program_INCLUDE_DIRS := ../common_c
program_SRCS := $(wildcard *.c)
program_SRCS += $(foreach includedir,$(program_INCLUDE_DIRS),$(wildcard $(includedir)/*.c))
program_OBJS := ${program_SRCS:.c=.o}

CFLAGS += -fPIC
CFLAGS += `pkg-config --cflags lxpanel gtk+-2.0`
CFLAGS += $(foreach includedir,$(program_INCLUDE_DIRS),-I$(includedir))
LDFLAGS += -shared
LDFLAGS += `pkg-config --libs lxpanel gtk+-2.0`
LDFLAGS += $(foreach includedir,$(program_INCLUDE_DIRS),-L$(includedir))

.PHONY: all clean distclean

all: $(program_NAME)

$(program_NAME): $(program_OBJS)
	$(LINK.cc) $(program_OBJS) -o $(program_NAME)

clean:
	@- $(RM) $(program_NAME)
	@- $(RM) $(program_OBJS)

distclean: clean