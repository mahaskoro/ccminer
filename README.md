# ccminer on Cortex-A53
Based on monkins1010

Langkah 1 - Pasang Termux
Install Termux 
Android 5 & 6 saja :

https://github.com/termux/termux-app/releases/download/v0.119.0-beta.1/termux-app_v0.119.0-beta.1+apt-android-5-github-debug_arm64-v8a.apk

Langkah 2 - Pasang Paket yang diperlukan
Pasang paket-paket yang diperlukan dengan menjalankan perintah berikut di termux

pkg install automake build-essential curl git gnupg openssl nano

Langkah 3 - Pasang GCC
Gnu Compiler Collection diperlukan untuk meng-kompilasi bahasa C 
Jalankan perintah berikut di termux

curl -s https://its-pointless.github.io/setup-pointless-repo.sh | bash

Lalu pasang paket GCC-6 (atao GCC-7, GCC-8 dst.. sesuai versi Android)
pkg install gcc-6

Step 4 - Build
Clone the ccminer git repo (ARM branch):

git clone --single-branch -b ARM https://github.com/monkins1010/ccminer.git

Then change the current directory:

cd ccminer

To build ccminer from sources we need to switch the default clang compiler to the gcc we installed on step 3 by executing following commands:

setupgcc-6

(or setupgcc-7, setupgcc-8, setupgcc-9, setupgcc-10)

and then (to make configure process happy)

setup-patchforgcc

Then start the build:

./build.sh

After successful build you can run built ccminer binary file to start the mining

Version Basred on Oink70

sudo apt-get update
sudo apt-get install libcurl4-openssl-dev libssl-dev libjansson-dev automake autotools-dev build-essential -y
sudo apt-get install -y libllvm-16-ocaml-dev libllvm16 llvm-16 llvm-16-dev llvm-16-doc llvm-16-examples llvm-16-runtime clang-16 clang-tools-16 clang-16-doc libclang-common-16-dev libclang-16-dev libclang1-16 clang-format-16 python3-clang-16 clangd-16 clang-tidy-16 libclang-rt-16-dev libpolly-16-dev libfuzzer-16-dev lldb-16 lld-16 libc++-16-dev libc++abi-16-dev libomp-16-dev libclc-16-dev libunwind-16-dev libmlir-16-dev mlir-16-tools flang-16 libclang-rt-16-dev-wasm32 libclang-rt-16-dev-wasm64 libclang-rt-16-dev-wasm32 libclang-rt-16-dev-wasm64
git clone https://github.com/Oink70/CCminer-ARM-optimized.git
cd CCminer-ARM-optimized
chmod +x build.sh
chmod +x configure.sh
chmod +x autogen.sh
CXX=clang++ CC=clang build.sh
