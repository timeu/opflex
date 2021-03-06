#
# libopflex: a framework for developing opflex-based policy agents
# Copyright (c) 2014 Cisco Systems, Inc. and others.  All rights reserved.
#
# This program and the accompanying materials are made available under the
# terms of the Eclipse Public License v1.0 which accompanies this distribution,
# and is available at http://www.eclipse.org/legal/epl-v10.html
#
###########
#
# Process this file with automake to produce a Makefile.in

SUBDIRS = . test

AM_CPPFLAGS = $(BOOST_CPPFLAGS) \
        -Wall \
        -Werror \
        -I$(srcdir)/include -I$(top_srcdir)/include \
	-I$(top_srcdir)/modb/include \
	-I$(top_srcdir)/logging/include \
	-I$(top_srcdir)/util/include \
	-I$(top_srcdir)/comms/include

if ENABLE_TSAN
  AM_CPPFLAGS += -fsanitize=thread
endif

if ENABLE_ASAN
  AM_CPPFLAGS += -fsanitize=address
endif

if ENABLE_COVERAGE
  AM_CPPFLAGS += --coverage
endif

noinst_LTLIBRARIES = libengine.la

libengine_la_CXXFLAGS = $(UV_CFLAGS) $(OPENSSL_CFLAGS) $(RAPIDJSON_CFLAGS)

libengine_la_LIBADD = $(UV_LIBS) $(OPENSSL_LIBS)
libengine_la_SOURCES = \
	include/opflex/engine/internal/MOSerializer.h \
	include/opflex/engine/internal/AbstractObjectListener.h \
	include/opflex/engine/internal/OpflexMessage.h \
	include/opflex/engine/internal/OpflexPEHandler.h \
	include/opflex/engine/internal/OpflexHandler.h \
	include/opflex/engine/internal/OpflexConnection.h \
	include/opflex/engine/internal/OpflexClientConnection.h \
	include/opflex/engine/internal/OpflexServerConnection.h \
	include/opflex/engine/internal/OpflexListener.h \
	include/opflex/engine/internal/OpflexPool.h \
	include/opflex/engine/internal/ProcessorMessage.h \
	include/opflex/engine/internal/GbpOpflexServerImpl.h \
	include/opflex/engine/internal/OpflexServerHandler.h \
	include/opflex/engine/internal/InspectorServerHandler.h \
	include/opflex/engine/internal/InspectorClientHandler.h \
	include/opflex/engine/internal/InspectorClientConn.h \
	include/opflex/engine/Inspector.h \
	include/opflex/engine/InspectorClientImpl.h \
	include/opflex/engine/Processor.h \
	AbstractObjectListener.cpp \
	MOSerializer.cpp \
	Processor.cpp \
	OpflexMessage.cpp \
	OpflexHandler.cpp \
	OpflexPEHandler.cpp \
	OpflexConnection.cpp \
	OpflexClientConnection.cpp \
	OpflexServerConnection.cpp \
	OpflexListener.cpp \
	OpflexPool.cpp \
	GbpOpflexServer.cpp \
	OpflexServerHandler.cpp \
	Inspector.cpp \
	InspectorServerHandler.cpp \
	InspectorClientImpl.cpp \
	InspectorClientConn.cpp \
	InspectorClientHandler.cpp

