PLATFORM?=linux

WAMR_PLATFORM=linux
ifeq ($(PLATFORM), macos)
    WAMR_PLATFORM=darwin
endif

build: build/iwasm wamr-compiler/build/wamrc

# Build WASM Micro Runtime.
build/iwasm:
	cd src && mkdir -p build && cd build && \
		cmake -DCMAKE_BUILD_TYPE=Release -DWAMR_BUILD_LIB_WASI_THREADS=1 ../product-mini/platforms/$(WAMR_PLATFORM)/ && \
		cmake --build .

wamr-compiler/build/wamrc:
	cd src/wamr-compiler && \
	./build_llvm.sh && \
	mkdir -p build && cd build && \
	cmake -DCMAKE_BUILD_TYPE=Release -DWAMR_BUILD_PLATFORM=$(WAMR_PLATFORM) .. && \
	cmake --build .


# Note that we also need to clean up the Git tree as well.
clean:
	cmake --build src/build --target clean && \
	cmake --build src/wamr-compiler/build --target clean && \
	cd src && git restore .
