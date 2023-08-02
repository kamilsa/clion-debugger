# Clion-debugger

This intruction explains how to debug core dumps obtained after crashes on kagome environments (k0 westend, s0 polkadot and so on)

## Step 0

Receive binary and core dump of the crash and download it to your local laptop's folder. In my case folder is ` /Users/taisei/dev/kagome-fun/dumps`

## Step 1: pull docker image for debug

```bash
docker pull kamilsa/clion-debugger:latest
```

## Step 2: add Docker toolchain to Clion

1. In clion open Settings -> Build, Execution, Deployment -> Toolchains
2. Click on "+" to add new toolchain and select "Docker"

![image](https://github.com/kamilsa/clion-debugger/assets/9370151/406501d5-0d6e-4c4f-9731-4d663a3c5e80)

3. Select `kamilsa/clion-debugger:latest` image
4. Map volume with your folder containing dump and binary to Docker's folder (for some reason in my case it only worked when both folders had the same paths):

![image](https://github.com/kamilsa/clion-debugger/assets/9370151/997a720d-cd80-4ecb-b2cb-53f64c351385)


## Step 3: open core dump

1. From main menu (on top) select Run -> Open core dump
2. Select debugger from Docker

![image](https://github.com/kamilsa/clion-debugger/assets/9370151/18378f32-44c1-41b4-a9a4-b7a36038f141)

3. Select core dump file and symbol file (binary)
4. Wait few minutes (in my case it took ~5 mins to open core dump from KAGOME crash)
5. Enjoy debugging

![image](https://github.com/kamilsa/clion-debugger/assets/9370151/4fe71328-2ed8-46b1-bf3d-f82d2799cb6a)

