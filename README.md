# Introduction to Self-Made OS from Scratch

I refered to the following: https://github.com/sarisia/mikanos-devcontainer

Open devcontainer with VSCode. (Refer to this page: https://code.visualstudio.com/docs/remote/containers#_quick-start-open-an-existing-folder-in-a-container)

## Initialization

```sh
cd $HOME && git clone https://github.com/uchan-nos/mikanos.git
cd $HOME/edk2 && ln -s ../mikanos/MikanLoaderPkg ./
cd $HOME/edk2 && source edksetup.sh
```

Open `Conf/target.txt` with an editor and fix the following items.
For example,
```sh
nano $HOME/edk2/Conf/target.txt
```


| Setting item    | setting value                     |
|-----------------|-----------------------------------|
| ACTIVE_PLATFORM | MikanLoaderPkg/MikanLoaderPkg.dsc |
| TARGET          | DEBUG                             |
| TARGET_ARCH     | X64                               |
| TOOL_CHAIN_TAG  | CLANG38                           |


If you are using M1 mac, please refer to this page.
https://github.com/sarisia/mikanos-docker#m1-mac-%E3%81%A7%E3%81%AE%E5%8B%95%E4%BD%9C%E3%81%AF


```sh
cd $HOME/edk2 && build
source $HOME/osbook/devenv/buildenv.sh
cd $HOME/mikanos && ./build.sh
```

## start up
Start with QEMU.
```sh
cd $HOME/mikanos && ./build.sh run
```

To put apps in the apps directory and create a disk image that includes resources such as fonts, specify the APPS_DIR and RESOURCE_DIR variables.
```sh
cd $HOME/mikanos && APPS_DIR=apps RESOURCE_DIR=resource ./build.sh run
```