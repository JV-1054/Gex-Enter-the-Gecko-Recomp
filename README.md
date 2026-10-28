# Gex: Enter the Gecko Recompiled

Static recompilation of the US PlayStation release (**SLUS-00598**) using
[PSXRecomp](https://github.com/mstan/psxrecomp).

## Prebuilt Windows executable

`artifacts/Gex_Enter_the_Gecko_Recompiled.exe` is ready to run. Its matching
OpenBIOS and license are in `artifacts/bios/`. Place your own game image in the
repository root `isos/` folder, next to `artifacts/`.

## Build from source

```powershell
cmake -S . -B build-gex -G Ninja -DCMAKE_BUILD_TYPE=Release -DPSX_REWIND=OFF
cmake --build build-gex --target psx-runtime --parallel 12
```

The project config points to `isos/Gex - Enter the Gecko (USA).cue`, which
references `Gex - Enter the Gecko (USA).bin` in the same directory. Disc files
are local inputs and are not included in this repository.

## Symbols

Edit `symbols.toml` and regenerate `psx_symbols.h` with:

```powershell
python tools/sync_symbols.py
```

Run `python tools/sync_symbols.py --check` to verify the generated header.

## Legal

You must own the original game. Disc images and retail BIOS dumps are local
inputs and are not redistributed. The bundled OpenBIOS is redistributable; its
license is included beside it.
