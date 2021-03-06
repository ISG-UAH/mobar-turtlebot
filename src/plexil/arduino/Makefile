# Copyright (c) 2006-2011, Universities Space Research Association (USRA).
#  All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are met:
#     * Redistributions of source code must retain the above copyright
#       notice, this list of conditions and the following disclaimer.
#     * Redistributions in binary form must reproduce the above copyright
#       notice, this list of conditions and the following disclaimer in the
#       documentation and/or other materials provided with the distribution.
#     * Neither the name of the Universities Space Research Association nor the
#       names of its contributors may be used to endorse or promote products
#       derived from this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY USRA ``AS IS'' AND ANY EXPRESS OR IMPLIED
# WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
# MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
# DISCLAIMED. IN NO EVENT SHALL USRA BE LIABLE FOR ANY DIRECT, INDIRECT,
# INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING,
# BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS
# OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
# ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR
# TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE
# USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

include $(PLEXIL_HOME)/makeinclude/standard-defs.make

LIBRARY		:= ArduinoAdapter

# External dependencies
INC_DIRS	+= $(PLEXIL_HOME)/third-party/pugixml/src \
                   $(PLEXIL_HOME)/third-party/ipc/src \
                   $(PLEXIL_HOME)/src/utils $(PLEXIL_HOME)/src/exec $(PLEXIL_HOME)/src/app-framework \
		   $(MSRC)/$(ARDU) \
		../../OgateInterf ../pddl

LIB_PATH	+= 
LIBS		+= pugixml PlexilUtils PlexilExec PlexilAppFramework nsl Ogate

SRC		:= arduino_comunicacion_clnt.c arduino_comunicacion_xdr.c ArduinoAdapter.cc ../pddl/OgateCommon.cpp
INC		:= ArduinoAdapter.hh ../pddl/OgateCommon.h

SVN_FILES       := Makefile $(SRC) $(INC)

include $(PLEXIL_HOME)/makeinclude/standard-targets.make
ifneq ($(MAKECMDGOALS),clean)
-include Makedepend
endif

TARGETS := 
OBJECTS := 

all: $(TARGETS)

$(TARGETS): $(OBJECTS)
	$(CC) -Wall $@.cc -o $@ $^ -lstdc++ -lPlexilUtils -lpugixml -I../../utils -L../../utils -L../../../lib

cleaner: clean
	$(RM) $(TARGETS) *.o
	$(MAKE) -C demo clean
