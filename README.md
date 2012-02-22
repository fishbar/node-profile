# node-profile

A script that makes profiling node.js apps a little easier.
Compatible with node v0.6.x

刚fork出来，发现命令行用locate检查linux-tick-processor， 在我机器上有问题，得用which.
而且貌似好久么更新了，有点对不上新版的node了~

## Installation

Via [npm](http://github.com/isaacs/npm):

    $ npm install profile

## Usage
### Output to stdout
`> nodeprofile yourapp.js`
### Output to file
`> nodeprofile yourapp.js -o=profile.txt`
### Lazy profiling (profiling disabled on startup)
This is useful if you want to profile certain areas of your code using [bnoordhuis/node-profiler](https://github.com/bnoordhuis/node-profiler):

`> nodeprofile yourapp.js --prof_lazy`

## "Dependencies"
* python
* [SCONS](http://www.scons.org/) (used to build the V8 debugger on first use) 
* That the `locate` command can find a copy of `linux-tick-processor` (or `mac-tick-processor` on OS X). This is bundled with node.js.

## 依赖关系
* python 因为scons基于python
* scons ubuntu使用sudo apt-get install scons
* 绑定linux-tick-processor到系统PATH下(这个工具在最新版的node源码/deps/v8/tools/下，把这个路径加入path中)

## Pre-configuration

    $ cd /usr/src/node
    $ cd deps/v8
    $ scons prof=on
    $ export PATH="${PATH}:/usr/src/node/deps/v8"
## 预先配置
    $ cd path/node-source # node 源码目录
    $ cd deps/v8 # 进入 v8 目录
    $ scons prof=on # 编译v8, 打开prof选项 ，这不不知道干嘛用的
    $ scons d8  # 编译d8(v8的调试版本) 64位系统需要安装lib32stdc++ 包 并创建手动ln关联lib文件

## Output

<img src="http://mape.me/nodeprofile.png" alt="">
