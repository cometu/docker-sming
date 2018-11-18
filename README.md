# docker-sming
sming in a docker

## Dependencies
  - Docker

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

You should copy the `Dockerfile` and the `docker-compose.yml` files to the project you want to build, then run the following commands:

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
