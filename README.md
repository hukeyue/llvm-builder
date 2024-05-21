# Usage

```
cd docker
docker build -t llvm-builder .
cd ..
```

```
docker run --rm -it --user 1000:1000 --cpuset-cpus 0-11 -e HOME=$HOME -v $HOME:$HOME llvm-builder /bin/bash
cd ~/llvm-builder && ~/llvm-project/llvm/utils/release/test-release.sh -release 18.1.6 -final -triple x86_64-linux-gnu-ubuntu-20.04 -use-ninja -no-checkout -no-test-suite -j12
```
