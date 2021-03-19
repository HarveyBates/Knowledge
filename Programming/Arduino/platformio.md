# Platform IO
## Description
How to use platform IO for arduino / teensy / feather etc..

# Install 
```bash
curl -fsSL https://raw.githubusercontent.com/platformio/platformio-core-installer/master/get-platformio.py -o get-platformio.py
python3 get-platformio.py
```

Then add the given path to PATH variables. Or use homebrew:

```bash
brew install platformio
```


# Setup 
```bash 
pio project init # Init project in current dir with folders and resources
```

Open platformio.ini, basic functions are shown below, differ alot between boards.

Website: https://docs.platformio.org/en/latest/core/userguide/index.html

```bash
[env:teensy41]
platform = teensy
board = teensy41
framework = arduino

board_build.mcu = imxrt1062

lib_deps =
   milesburton/DallasTemperature @^3.9.1

   upload_protocol = teensy-cli

   platform_packages = 
   	toolchain-gccarmnoneeabi@~1.90301.200702
	tool-teensy@https://github.com/maxgerhardt/pio-tool-teensy-arm/archive/master.zip

```

```bash
pio --help # Display help
pio run # Compile code
pio run -t upload # Run then upload
pio run -e board_name -t upload # Run and upload to specific board
```







