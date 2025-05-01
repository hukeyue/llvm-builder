# Usage

```
cd docker
docker build -t llvm-builder .
cd ..
```

```
mkdir -p final
ln -sf ~/llvm-project final
```

```
docker run --rm -it --user 1000:1000 --cpuset-cpus 0-11 -e HOME=$HOME -v $HOME:$HOME llvm-builder /bin/bash
cd ~/llvm-builder && ~/llvm-project/llvm/utils/release/test-release.sh -release 19.1.7 -final -triple x86_64-linux-gnu-ubuntu-20.04 -use-ninja -no-checkout -no-test-suite -no-flang -j12
```

```
cd ~/llvm-builder && caffeinate -d ~/llvm-project/llvm/utils/release/test-release.sh -release 19.1.7 -final -triple arm64-apple-darwin20.1.0 -use-ninja -no-checkout -no-test-suite -no-openmp -no-flang
```
