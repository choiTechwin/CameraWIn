# CameraWinVision

Windows + VSCode + C++ + OpenCV sample project for camera monitoring and simple intelligent vision.

## Features

- Live camera preview
- FPS, frame size, and motion ratio overlay
- Frame-difference motion detection
- Motion bounding boxes
- Snapshot capture to `capture.png`

## Required Tools

- Visual Studio Build Tools 2022 or Visual Studio 2022 with C++ desktop workload
- CMake
- VSCode extensions:
  - C/C++
  - CMake Tools
- OpenCV for Windows

## Recommended OpenCV Setup With vcpkg

```powershell
git clone https://github.com/microsoft/vcpkg C:\dev\vcpkg
C:\dev\vcpkg\bootstrap-vcpkg.bat
C:\dev\vcpkg\vcpkg install opencv4:x64-windows
```

Then configure and build:

```powershell
$env:VCPKG_ROOT="C:\dev\vcpkg"
cmake --preset vs2022-debug-vcpkg
cmake --build --preset debug-vcpkg
.\build\Debug\Debug\camera_win.exe

cmake --preset vs2022-release-vcpkg
cmake --build --preset release-vcpkg
.\build\Release\Release\camera_win.exe
```

## Setup With a Direct OpenCV Install

If you installed OpenCV manually, point CMake to the directory that contains `OpenCVConfig.cmake`.

```powershell
cmake --preset vs2022-debug -DOpenCV_DIR=C:\opencv\build\x64\vc16\lib
cmake --build --preset debug
.\build\Debug\Debug\camera_win.exe

cmake --preset vs2022-release -DOpenCV_DIR=C:\opencv\build\x64\vc16\lib
cmake --build --preset release
.\build\Release\Release\camera_win.exe
```

## VSCode

1. Open this folder in VSCode.
2. Select a Visual Studio 2022 kit in CMake Tools.
3. Select `vs2022-debug`, `vs2022-release`, or the matching `*-vcpkg` preset.
4. Build with `Ctrl+Shift+B`.
5. Run with `Terminal > Run Task > Run Debug`, `Run Release`, or press `F5`.

## Controls

- `m`: Toggle motion detection overlay
- `s`: Save current frame to `capture.png`
- `q` or `ESC`: Exit

## Camera Index

Pass a camera index to open another camera:

```powershell
.\build\Debug\Debug\camera_win.exe 1
```

## Extension Ideas

- YOLO or ONNX object detection
- Face detection or QR recognition
- Event logging
- RTSP/IP camera input
- Video recording
