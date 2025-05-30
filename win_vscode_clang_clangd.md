### 1、scoop
### 2、scoop install mingw
### 3、scoop install llvm
### 4、scoop install clangd
### 5、vscode安装clangd插件
### 6、clangd配置文件
.clangd文件：
```
CompileFlags:
  Add:
    - --target=x86_64-w64-mingw32  # 强制使用 MinGW 目标
    - -Wno-msvc-not-found          # 关闭警告
    - -std=c++17
```
### 7、编译
```bash
clang++ --target=x86_64-w64-mingw32 -std=c++17  main.cpp
```
