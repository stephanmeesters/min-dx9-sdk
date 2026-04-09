## d3dx9

nuget install Microsoft.DXSDK.D3DX -Version 9.29.952.8 -OutputDirectory .

copy the headers and .lib files from x86 release

## d3d9

Install Microsoft DirectX SDK June 2010 and copy from Include and Lib/x86 directories:

`d3d9.h`, `d3d9.lib`, `d3d9caps.h`, `d3d9types.h`

`dxfile.h`

`dinput.h`, `dinput8.lib`

`dxfile.h`

## dinput, dxfile

`dinput.h`, `dinput8.lib`, `dxfile.h`, `dxguid.lib` pulled from min-dx8-sdk

## extras

`winapifamily.h`, `winpackagefamily.h` pulled from Windows Kits 10.0.26100.0

`basetsd.h`, `d3d.h`, `d3dxerr.h`, `d3dxmath.h`, `d3dxmath.inl`, `ddraw.h`, `dsound.h` pulled from min-dx8-sdk

## see also

https://github.com/madebr/min-dx9-sdk

todo: make a include/lib split, add x64 binaries