# docker-sming
sming in a docker

## Dependencies
  - Docker
  
  If you don't want to use a docker, you can follow the list of command detail there: https://hub.docker.com/r/cometurrata/sming/
  to install Sming on your machine

## Advices:

1) Always flashinit before the first time you upload code (and every time you change flash mapping)

2) You should add the following to your `Makefile-user.mk`:
```
MODULES = app
EXTRA_INCDIR = include
COM_SPEED_ESPTOOL = 460800 
ENABLE_ESPCONN = 1
RBOOT_ENABLED = 1
## enable big flash support (for multiple roms, each in separate 1mb block of flash)
RBOOT_BIG_FLASH = 1
## two rom mode (where two roms sit in the same 1mb block of flash)
#RBOOT_TWO_ROMS  ?= 1
## size of the flash chip
SPI_SIZE  = 4M
DISABLE_SPIFFS = 1
```

3) have a look inside `Sming/samples/` from https://github.com/SmingHub/Sming/tree/develop/samples , its a good start

## Usage

You should copy the `Dockerfile`, `docker-compose.yml` and `.env` files to the project you want to build. Update the `.env` file with your project name and other options.

Then run the following commands:

build
```bash
docker-compose run --rm build
```

clean
```bash
docker-compose run --rm clean
```

upload
```bash
docker-compose run --rm upload
```

Flashinit
```bash
docker-compose run --rm flashinit
```
