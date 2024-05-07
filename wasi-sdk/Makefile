# Download and unpack wasi-sdk.
TAR=tar
ifeq ($(PLATFORM), macos)
    TAR=gtar
endif

bin/clang-18: wasi-sdk-22.0-$(PLATFORM).tar.gz
	$(TAR) --extract --verbose --touch --strip-components=1 --file=wasi-sdk-22.0-$(PLATFORM).tar.gz

wasi-sdk-22.0-linux.tar.gz:
	wget https://github.com/WebAssembly/wasi-sdk/releases/download/wasi-sdk-22/$@
	touch $@

wasi-sdk-22.0-macos.tar.gz:
	wget https://github.com/WebAssembly/wasi-sdk/releases/download/wasi-sdk-22/$@
	touch $@

clean:
	rm -rf wasi-sdk-22.0-$(PLATFORM).tar.gz wasi-sdk-22.0
