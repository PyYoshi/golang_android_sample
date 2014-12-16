

## Prepare

### Step 1: Create Standalone Android NDK Toolchain

```bash
$ANDROID_NDK_HOME/build/tools/make-standalone-toolchain.sh --platform=android-9 --install-dir=./toolchain --toolchain=arm-linux-androideabi-4.9
export NDK_CC=$(pwd)/toolchain/bin/arm-linux-androideabi-gcc
```

### Step 2: Checkout Go 1.4

```bash
hg clone -u go1.4 https://code.google.com/p/go go1.4
```

### Step 3: Build Go 1.4

```bash
cd go1.4/src
CC_FOR_TARGET=$NDK_CC GOOS=android GOARCH=arm GOARM=7 ./make.bash
cd ../..
export PATH=$(pwd)/go1.4/bin:$PATH
export GOPATH=$(pwd)/gopath
mkdir -p $GOPATH
```

### Step 4: Build Android App

none

## Requires

- [Android NDK r10d](https://developer.android.com/tools/sdk/ndk/index.html)
