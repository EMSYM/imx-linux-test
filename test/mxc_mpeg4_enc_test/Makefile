#
# Setup the proper directories for make.rules to function
#
OBJDIR=$(TOPDIR)/platform/$(PLATFORM)/$(MODULE_NAME)
CFLAGS += -I . -lpthread

EXES = $(OBJDIR)/cam2mpeg4.out
SCRIPTS = $(OBJDIR)/autorun-hantro.sh
ifeq "$(PLATFORM)" "MXC30030EVB"
LIBS = libmpeg4enc_cif.a
TEMP_EXE = $(OBJDIR)/cam2mpeg4_cif.out
OBJS = $(OBJDIR)/cam2mpeg4_cif.o
else
LIBS = libmpeg4enc_vga.a
TEMP_EXE = $(OBJDIR)/cam2mpeg4_vga.out
OBJS = $(OBJDIR)/cam2mpeg4_vga.o
endif

all: $(EXES) $(SCRIPTS)

$(EXES): $(TEMP_EXE)
	@mv $< $@

.PHONY: clean
clean:
	rm -f $(EXES) $(OBJS) $(SCRIPTS)

$(TEMP_EXE): $(LIBS)

#
# include the Rules
#
include $(TOPDIR)/test/make.rules

#include $(EXES:.out=.d)
