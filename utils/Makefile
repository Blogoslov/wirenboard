DESTDIR=/
prefix=usr

ifeq ($(DEB_BUILD_GNU_TYPE),$(DEB_HOST_GNU_TYPE))
       CC=gcc
else
       CC=$(DEB_HOST_GNU_TYPE)-gcc
endif


all: inj

inj:
	$(MAKE) -C adc/injection

install: $(BIN_NAME)
	$(MAKE) -C adc/injection install
	install -m 0644 board/wb_env.sh $(DESTDIR)/etc/wb_env.sh
	install -m 0755 board/wb-gen-serial $(DESTDIR)/$(prefix)/bin/wb-gen-serial

	install -m 0755 adc/wb-adc-get-value $(DESTDIR)/$(prefix)/bin/wb-adc-get-value
	install -m 0755 adc/wb-adc-read-channel $(DESTDIR)/$(prefix)/bin/wb-adc-read-channel
	install -m 0755 adc/wb-adc-set-mux $(DESTDIR)/$(prefix)/bin/wb-adc-set-mux

	install -m 0755 gsm/wb-gsm $(DESTDIR)/$(prefix)/bin/wb-gsm




clean:
	$(MAKE) -C adc/injection clean

.PHONY: install clean all

# run "debuild" in chroot to make deb package
