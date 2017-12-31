# Deepdrive sim [![Build Status](https://travis-ci.com/crizCraig/deepdrive-beta.svg?token=hcA6yn9X8yYZspyyCMpp&branch=release)](https://travis-ci.com/crizCraig/deepdrive-beta) [![Build status](https://ci.appveyor.com/api/projects/status/s7jbcjbxlq3vetw5?svg=true)](https://ci.appveyor.com/project/crizCraig/deepdrive-beta)


Unreal based simulator and Python interface to Deepdrive


## Usage

Checkout our [main repo](https://github.com/deepdrive/deepdrive)

## Development

- [Associate your GitHub username with your Unreal account](https://www.unrealengine.com/en-US/ue4-on-github)

### Windows

- Get Unreal v4.14 via the Epic Launcher -> Unreal Enngine tab -> Library
- Install the Substance Plugin through the Marketplace in Epic Launcher

Opening the project in Unreal will update the Substance textures to Windows-only versions. 
Once you see these files changed, you can run the following to avoid ever checking them in
```
cd Content/TuningCars/Materials/Hangar/material/Substance
git update-index --assume-unchanged $(git ls-files | tr '\n' ' ')
```

***Refresh / Create Visual Studio project***

***On Windows, Right click the DeepDrive project and set as Startup Project, debug...***

### Linux

The Unreal Editor in Linux works, but not as well as in Windows, so it's easiest to do most development in Windows, then test / bug fix issues in Linux.

- Clone the Allegorithmic version of Unreal with the Substance plugin <kbd>4.14.0.17</kbd>:
```
    git clone git@github.com:Allegorithmic/UnrealEngine --branch 4.14.0.17
    # or if you are using https: 
    # git clone https://github.com/Allegorithmic/UnrealEngine --branch 4.14.0.17
```

Build Unreal

```
cd UnrealEngine
./Setup.sh
./GenerateProjectFiles.sh
make  # Takes about an hour
```

More details on building Unreal [here](https://wiki.unrealengine.com/Building_On_Linux) - though the above commands should be sufficient.

Run 
```
./Engine/Binaries/Linux/UE4Editor
```

Open deepdrive uproject file - choose other -> Skip Conversion

**Building the Python Extension**

Locally
```
cd Plugins/DeepDrivePlugin/Source/DeepDrivePython
python build/build.py --type dev
```

Linux wheel
```
cd Plugins/DeepDrivePlugin/Source/DeepDrivePython
sudo -E python build/build.py --type linux_bdist
```

Windows wheel
```
cd Plugins/DeepDrivePlugin/Source/DeepDrivePython
python build\build.py --type win_bdist
```


**How to change the shared memory names (mostly useful for debugging)**

**Development**

***Run game full speed when the window is not focused***
```Uncheck Edit->Editor Preferences->Use Less CPU when in Background```

**Push deepdrive PyPi module**
`git push origin master && git push origin master:release`
