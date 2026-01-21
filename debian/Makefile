# Makefile

PREFIX  ?= /usr/local
DESTDIR ?=

BINDIR  = $(PREFIX)/bin
LIBDIR  = $(PREFIX)/lib
DATADIR = $(PREFIX)/share

all: build

build:
	cargo build --offline --release --features systemd

install:
	install -D target/release/xwayland-satellite $(DESTDIR)$(BINDIR)/xwayland-satellite

	install -D resources/xwayland-satellite.service $(DESTDIR)$(LIBDIR)/systemd/user/xwayland-satellite.service
	sed -ri "s|ExecStart=/usr/local/bin|ExecStart=$(BINDIR)|" $(DESTDIR)$(LIBDIR)/systemd/user/xwayland-satellite.service

clean:
	cargo clean

.PHONY: all build install clean
