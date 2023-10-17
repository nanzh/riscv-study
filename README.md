# RISC-V体系结构编程与实践

## Ubuntu 20.04, 环境准备

    $ sudo apt-get install net-tools libncurses5-dev libssl-dev build-essential openssl qemu-system-misc gcc-riscv64-linux-gnu git bison flex bc vim universal-ctags cscope gdb-multiarch libsdl2-dev libreadline-dev 


## 使用NEMU的编译方法：
```
$ cd tools
$ sudo apt-get install libsdl2-dev libreadline-dev
$ git clone https://github.com/runninglinuxkernel/NEMU.git
$ export NEMU_HOME=$(pwd)
$ make riscv64-benos_defconfig
  /home/nanzh/Works/riscv-study/tools/NEMU/scripts/config.mk:5:   Warning: .config does not exists!
  /home/nanzh/Works/riscv-study/tools/NEMU/scripts/config.mk:6:   To build the porject, first run 'make menuconfig'.
  + CC confdata.c
  + CC expr.c
  + CC preprocess.c
  + CC symbol.c
  + CC util.c
  + YACC build/parser.tab.h
  + LEX build/lexer.lex.c
  + CC build/lexer.lex.c
  + CC build/parser.tab.c
  + CC conf.c
  + LD /home/nanzh/Works/riscv-study/tools/NEMU/tools/kconfig/  build/conf
  + CC fixdep.c
  + LD /home/nanzh/Works/riscv-study/tools/NEMU/tools/fixdep/  build/fixdep
$ cp configs/riscv64-benos_defconfig .config
$ make riscv64-benos_defconfig
  Cloning into 'resource/softfloat/repo'...
  remote: Enumerating objects: 449, done.
  remote: Counting objects: 100% (449/449), done.
  remote: Compressing objects: 100% (366/366), done.
  remote: Total 449 (delta 411), reused 97 (delta 82),   pack-reused 0
  Receiving objects: 100% (449/449), 202.69 KiB | 71.00 KiB/s,   done.
  Resolving deltas: 100% (411/411), done.
$ make -j$(nproc)
$ sudo cp build/riscv64-nemu-interpreter /usr/local/bin/
$ ll /usr/local/bin/riscv64-nemu-interpreter
  -rwxr-xr-x 1 root root 3027880 Oct 18 01:04 /usr/local/bin/riscv64-nemu-interpreter*
```