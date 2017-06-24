# android_prebuilts_clang_linux-x86_host_sdclang-3.8
SDCLANG compiler 3.8


Over the years, there have been many who have wanted to compile the Android platform with the Snapdragon LLVM Compiler, which has several performance enhancements for Snapdragon chipsets, such as improved Krait targeting and enhanced auto-vectorization for the NEON SIMD.  With Qualcomm's release of Android Nougat repos, it is now possible to compile target modules with their optimized compiler.  Please see the commits in the following repository for more information: https://source.codeaurora.org/quic/la/platform/build/log/?h=LA.BF64.1.2....

In order to use the Qualcomm Compiler to build Android for Snapdragon chipsets, please follow the steps below.  Please note that Darwin (Mac OS X) is not supported at this time.

1. Download the Qualcomm LLVM Compiler here: https://developer.qualcomm.com/download/sdllvm/snapdragon-llvm-compiler-...

2. Extract Snapdragon-llvm-3.8.4-toolchain.tar.gz

3. Move toolchains\llvm-Snapdragon_LLVM_for_Android_3.8\prebuilt\linux-x86_64 to prebuilts/clang/linux-x86/host/sdclang-3.8 within your Android build environment.

4. Add the following lines to your device's BoardConfig:

ifneq ($(HOST_OS),darwin)

SDCLANG := true

SDCLANG_PATH := prebuilts/clang/linux-x86/host/sdclang-3.8/bin

SDCLANG_LTO_DEFS := device/qcom/common/sdllvm-lto-defs.mk

endif

5. Compile Android
