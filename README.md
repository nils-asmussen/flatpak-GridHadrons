Grid Hadrons Environment
========================
This package provides an environment that I use to compile and run Grid and Hadrons while developping without the need worry about libraries and compilers.
However it is *not* intended to be used in production runs or benchmarking. It is currently certainly not perfect, but good enough to be useful to me.

Installation
------------
- Make sure that flatpak and flatpak-builder are installed
- Install the software development kit
```
flatpak install flathub org.freedesktop.Platform//20.08 org.freedesktop.Sdk//20.08
```
- Download, compile, and install GridHadrons
```
git clone https://github.com/nils-asmussen/flatpak-GridHadrons
cd flatpak-GridHadrons
flatpak-builder build-dir com.github.nils-asmussen.GridHadrons.yaml --force-clean --install --user --jobs=4
cd ..
```

Usage
-----
- Show the help (includes more commands than this README)
```
flatpak run com.github.nilsasmussen.GridHadrons
flatpak run com.github.nilsasmussen.GridHadrons Grid-build -?
```
- Download and compile Grid
```
git clone https://github.com/paboyle/Grid
cd Grid
flatpak run com.github.nilsasmussen.GridHadrons Grid-build
cd ..
```
- Download and compile Hadrons
```
git clone https://github.com/aportelli/Hadrons
cd Hadrons
flatpak run com.github.nilsasmussen.GridHadrons Hadrons-build -D ../Grid
cd ..
```
- Run HadronsXmlRun
```
flatpak run com.github.nilsasmussen.GridHadrons -d Hadrons HadronsXmlRun MyAmazing.xml
```
- Compile Hadrons again after some small code changes
```
cd Hadrons
flatpak run com.github.nilsasmussen.GridHadrons Hadrons-compile
cd ..
```
