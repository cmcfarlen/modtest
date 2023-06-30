

# C++ modules with cmake test project


## Required Versions

### llvm - 16
- https://apt.llvm.org/ (use the automatic installion script)
- https://gist.github.com/luojia65/da11883508586f59891c08c1da12a91c#file-update-alternatives-clang-sh
  - run this script(optional): `update-alternatives-clang.sh 16 10`

### CMake 3.27

- curl -OL https://github.com/Kitware/CMake/releases/download/v3.27.0-rc3/cmake-3.27.0-rc3-linux-x86_64.sh
- sudo sh cmake-3.27.0-rc3-linux-x86_64.sh --prefix=/usr/local --skip-license

### ninja 1.11.1
- https://github.com/ninja-build/ninja/releases


## Notes

On my pop_os box installing llvm 16 via the llvm install script I had a situation where the dependency scanner
could not find some deps when including std headers.
This turned out ot be due to symlinks pointing to directories that didn't exist:

```angular2html
$ ls -l /usr/lib/clang/16
total 8
lrwxrwxrwx 1 root root 38 Jun 10 18:35 include -> ../../llvm-16/lib/clang/16.0.6/include
lrwxrwxrwx 1 root root 34 Jun 10 18:35 lib -> ../../llvm-16/lib/clang/16.0.6/lib
$ ls -l /usr/lib/llvm-16/lib/clang/
total 4
drwxr-xr-x 1 root root 56 Jun 29 15:18 16
```

So I created a symlink from 16 -> 16.0.6 and that fixed that.
