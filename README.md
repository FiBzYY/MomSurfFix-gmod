# MomSurfFix
Momentum mod surf/ramp fix ported to GMOD.

## About
That fix modifies ``CGameMovement::TryPlayerMove()`` function to behave like momentum mod ones. [Whole function](https://github.com/momentum-mod/game/blob/develop/mp/src/game/shared/momentum/mom_gamemovement.cpp#L1838-L2282) was recreated on sourcepawn and replaced default ``CGameMovement::TryPlayerMove()``. By modifying that function and applying all fixes that momentum mod team has done, you'll get quite good surf/ramp glitch fix.

## Requirements
* garrysmod_common
  
## Building
- [Premake](https://premake.github.io/)
- [garrysmod_common](https://github.com/danielga/garrysmod_common) (use `x86-64-support-sourcesdk` branch for 64bit)
- [Visual Studio Build Tools 2022](https://visualstudio.microsoft.com/downloads/) on Windows (MinGW untested)
  - "MSVC v143 - VS 2022 C++ x64/x86 build tools"
  - "C++/CLI support for v143 build tools"
- GNU make on Linux

### Windows 64bit
> [!NOTE]
> Currently requires manually updating `sourcesdk-minimal` in `garrysmod_common` to latest commit on `x86-64-branch`

```
premake5 vs2022
cd projects/windows/vs2022
msbuild surffix.sln /p:Configuration=ReleaseWithSymbols
```

### Windows 32bit
```
set BUILD_32BIT=1
premake5 vs2022
cd projects/windows/vs2022
msbuild surffix.sln /p:Configuration=ReleaseWithSymbols /p:Platform=Win32
```

### Linux 64bit
make config=release_x86_64

### Linux 32bit
make config=release_x86_64

## Available cvars
* **momsurffix_ramp_bumpcount** - Left from original momentum mods function, helps with fixing surf/ramp bugs;
* **momsurffix_ramp_initial_retrace_length** - Left from original momentum mods function, amount of units used in offset for retraces;

## Special thanks to
* [Momentum mod team for the actual fix](https://momentum-mod.org/);
* [Guys from bhoptimer discord for testing](https://discord.gg/jyA9q5k);

## Fixed:
Fix MoveHelper Touched patterns on linux64

### Credits:
* Rio for the logic. Github: [https://github.com/rio](https://github.com/jason-e)
* Me for adding linux64 patterns. - Discord: FiBzYY Steam: [https://steamcommunity.com/id/fibzy_](https://steamcommunity.com/id/fibzy_/)

* ### Note:
* The source code patterns for GMod will not be released due to game security of facepunch.
* Dev 64x branch has not been implemented or tested yet.
