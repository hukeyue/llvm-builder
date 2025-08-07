# Usage

```
cd
git clone --branch 'release/20.x' https://github.com/llvm/llvm-project
```

```
cd docker
docker build -t llvm-builder .
cd ..
```

```
mkdir -p final
ln -sf ~/llvm-project final
```

for Linux:

```
docker run --rm -it --user 1000:1000 --ulimit nofile=10240:10240 --cpuset-cpus 0-5 -e HOME=$HOME -v $HOME:$HOME llvm-builder /bin/bash
cd ~/llvm-builder && ~/llvm-project/llvm/utils/release/test-release.sh -release 20.1.8 -final -triple x86_64-linux-gnu-ubuntu-20.04 -use-ninja -no-checkout -no-test-suite -j12
```

for macOS:

```
cd ~/llvm-builder && caffeinate -d ~/llvm-project/llvm/utils/release/test-release.sh -release 20.1.8 -final -triple arm64-apple-darwin20.1.0 -use-ninja -no-checkout -no-test-suite
```
