## Preparing project

### GCC and env variables

Set environment with your paths:
```
ZEPHYR_TOOLCHAIN_VARIANT=gnuarmemb
GNUARMEMB_TOOLCHAIN_PATH=e:\GCC
TOOLCHAIN_DIR=e:\GCC
```

### Install west

Instructions: https://docs.zephyrproject.org/latest/guides/west/install.html

### Get Manifest

```
west init -m git@bitbucket.org:embrox/dormakaba-ebox.git --manifest-rev=master <ProjDir>
cd <ProjDir>
west update
```

### Build and flash
    
Use `west build -b <board>` and `west flash` (inside `board` folder) for build/flash debug version.

Add config overlay for release version:

`west build -b <board> -- -DOVERLAY_CONFIG=../commonz/config/release.conf`

### Useful notes:

Using more than one J-Link: 

    board_runner_args(jlink "--device=STM32H753ZI   " "--speed=4000" "--tool-opt=-USB 4294967295")

in file board.cmake (add USB serial number)
