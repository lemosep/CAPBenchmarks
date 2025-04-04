#
# Copyright(C) 2025 Eduardo Lemos Paschoalini
#
# Builds CAP Benchmark suite for x86 architecture.
#

# Directories.
export BINDIR    = $(CURDIR)/bin
export INCDIR    = $(CURDIR)/include
export LIBDIR    = $(CURDIR)/lib
export LIBSRCDIR = $(CURDIR)/libsrc
export SRCDIR    = $(CURDIR)/src

# Tool chain.
export CC = clang
export AR = ar
export LLC = llc

# Tool chain configuration.
export CFLAGS = -Wall -Wextra -Werror -O3 
export CFLAGS += -I$(INCDIR)
export CFLAGS += -fopenmp
export ARFLAGS = -vq
export LLVMFLAGS = -emit-llvm -c 

# Libraries.
export LIB = libcapb
export LIBS = $(LIBDIR)/$(LIB).a
export LIBARGS = -lm -fopenmp

# LLVM configuration.
export REG_ALLOC_ALGOS = fast basic greedy pbqp

.PHONY: lib

# Builds all kernels.
all: lib
	cd $(SRCDIR) && $(MAKE) all
	
# Builds kernel library.
lib:
	mkdir -p lib
	cd $(LIBSRCDIR) && $(MAKE) all
	
# Cleans compilation files.
clean:
	rm -rf $(BINDIR)
	cd $(LIBSRCDIR) && $(MAKE) clean
	cd $(SRCDIR) && $(MAKE) clean
