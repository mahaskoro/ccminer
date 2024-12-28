# ccminer on Android

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
