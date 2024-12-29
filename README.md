# ccminer on Cortex-A53
Based on monkins1010, Oink70 dan Darktron github. Semua punya gaya sendiri, cuma coba merangkum saja.

Langkah 1 - Pasang Termux

Install Termux yang sesuai dengan OS Android :

Untuk Android 7, versi stabil:

https://github.com/termux/termux-app/releases/download/v0.118.0/termux-app_v0.118.0+github-debug_arm64-v8a.apk

Android 5 & 6 saja :

https://github.com/termux/termux-app/releases/download/v0.119.0-beta.1/termux-app_v0.119.0-beta.1+apt-android-5-github-debug_arm64-v8a.apk

Untuk cek rlis terbaru kunjungi link nerikut :

https://github.com/termux/termux-app/releases

Langkah 2 - Pasang Paket yang diperlukan
Pasang paket-paket yang diperlukan dan jangan lupa apdet dulu.

apt-get update
atau,
yes | pkg update && pkg upgrade -y

Pasang paket-paket yang diperlukan
monkins1010 :

pkg install automake build-essential curl git gnupg openssl nano

berhubung monkins1010 tidak melakkan kompilasi menggunakan clang, namun menggunakan GCC, langkah berikutnya tidak saya tiru. 

Oink70:

apt-get install libcurl4-openssl-dev libssl-dev libjansson-dev automake autotools-dev build-essential -y

apt-get install -y libllvm-16-ocaml-dev libllvm16 llvm-16 llvm-16-dev llvm-16-doc llvm-16-examples llvm-16-runtime clang-16 clang-tools-16 clang-16-doc libclang-common-16-dev libclang-16-dev libclang1-16 clang-format-16 python3-clang-16 clangd-16 clang-tidy-16 libclang-rt-16-dev libpolly-16-dev libfuzzer-16-dev lldb-16 lld-16 libc++-16-dev libc++abi-16-dev libomp-16-dev libclc-16-dev libunwind-16-dev libmlir-16-dev mlir-16-tools flang-16 libclang-rt-16-dev-wasm32 libclang-rt-16-dev-wasm64 libclang-rt-16-dev-wasm32 libclang-rt-16-dev-wasm64

Darktron :

yes | pkg install libjansson build-essential clang binutils git -y

Kesimpulan : 
pkg install build-essential openssl libcurl4-openssl libjanson libssl nano git automake autotools clang libllvm-16-ocaml-dev libllvm16 llvm-16 llvm-16-dev llvm-16-doc llvm-16-examples llvm-16-runtime clang-16 clang-tools-16 clang-16-doc libclang-common-16-dev libclang-16-dev libclang1-16 clang-format-16 python3-clang-16 clangd-16 clang-tidy-16 libclang-rt-16-dev libpolly-16-dev libfuzzer-16-dev lldb-16 lld-16 libc++-16-dev libc++abi-16-dev libomp-16-dev libclc-16-dev libunwind-16-dev libmlir-16-dev mlir-16-tools flang-16 libclang-rt-16-dev-wasm32 libclang-rt-16-dev-wasm64 libclang-rt-16-dev-wasm32 libclang-rt-16-dev-wasm64 -y

Langkah 3 - Atur Struktur Folder dan Berkas

monkins1010 :
git clone --single-branch -b ARM https://github.com/monkins1010/ccminer.git

Oink70 :
git clone https://github.com/Oink70/CCminer-ARM-optimized.git

Darktron:
cp /data/data/com.termux/files/usr/include/linux/sysctl.h /data/data/com.termux/files/usr/include/sys
git clone https://github.com/Darktron/ccminer.git

Langkah 4 - Buat Kompilasi CCMiner
Oink70:
cd CCminer-ARM-optimized
chmod +x build.sh
chmod +x configure.sh
chmod +x autogen.sh
CXX=clang++ CC=clang build.sh

Darktron:
cd ccminer
chmod +x build.sh configure.sh autogen.sh start.sh
Sesuaikan Arch & Cores:
nano configure.sh
CXX=clang++ CC=clang ./build.sh

Kesimpulan :
cd ccminer
chmod +x build.sh configure.sh autogen.sh start.sh
CXX=clang++ CC=clang build.sh

Langkah 5 - Atur Dompet dan Pool
wget https://raw.githubusercontent.com/mahaskoro/ccminer/sets/config.json

dan coba jalankan ccminer :
~/ccminer/start.sh
