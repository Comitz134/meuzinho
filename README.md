# CS2 External Overlay Framework (Conceptual)

This project provides a structural framework for building an external overlay for Counter-Strike 2. It demonstrates memory reading, entity iteration, and 2D bounding box (AABB) rendering.

## Conceptual Framework Components

### 1. Memory Management (`src/memory/mem.h`)
Uses Windows APIs (`ReadProcessMemory`, `CreateToolhelp32Snapshot`) to interface with the game process.
- **Process Attachment**: Finding `cs2.exe` and obtaining a handle.
- **Module Discovery**: Finding base addresses for `client.dll`.

### 2. Entity List Logic (`src/main.cpp`)
Source 2 uses a more complex entity list structure than Source 1. Entities are stored in chunks.
- The framework demonstrates how to traverse these chunks using the entity index and pawn handles.

### 3. World-to-Screen (`src/math/view.h`)
Converts 3D coordinates (x, y, z) from the game engine into 2D coordinates (x, y) for your screen.
- Uses the `ViewMatrix` read from game memory.
- Projects the 3D position onto a 2D plane.

### 4. AABB Rendering (`src/render/overlay.h`)
Renders Axis-Aligned Bounding Boxes.
- **Height Calculation**: Screen Y difference between player origin (feet) and head.
- **Width Calculation**: Derived from height (usually `height / 2`).
- Uses GDI for demonstration; for production, DirectX 11/12 or Vulkan with ImGui is recommended for performance and transparency.

## Building
1. Open with Visual Studio or use CMake.
2. Ensure you are targeting `x64` (CS2 is a 64-bit application).
3. Run as Administrator (required for `PROCESS_ALL_ACCESS`).

## Disclaimer
This is for educational purposes only. Modifying or reading game memory can lead to bans. Always practice in offline/protected environments.
