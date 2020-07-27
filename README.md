This repository is used as a submodule to ~~the dolphin emulator~~ [a development fork of the dolphin emulator](https://github.com/Felk/dolphin/tree/scripting) and contains the external dependencies necessary for embedding Python.
The contents are as follows:

- `include/`: Python header files, for development. Code usually just includes `Python.h`.
- `libs/`: Libraries to link against.
- `embed/`: Files needed by Python at runtime in the output directory. The `.dll` files get copied to the root, the rest to a directory called `python-embed/`.

To construct this collection of files from scratch, the following steps are required:
- Install a 64-bit version of [Python 3](https://www.python.org/downloads/), and also download the respective [embeddable zip file](https://www.python.org/downloads/windows/) (requires Windows). Make sure to check "Download Debug Binaries" when installing.
- Copy the contents of your Python installation's `libs/` directory into `libs/`, except tkinter (probably named `_tkinter.lib`).
- Copy the contents of your Python installation's `include/` directory into `include/`.
- Copy the contents of the embeddable zip file into `embed/`. The `.exe` files may be removed.
- For each `.dll` file in `embed/`, also copy over the respective `*_d.dll` file from your Python installation's directory (or the `DLLs` subdirectory), if it exists. For me those were `python3_d.dll`, `python36_d.dll` and `DLLs/sqlite3_d.dll`.
- For each `.pyd` file in `embed/` (python dynamic linked libraries), also copy over the respective `*_d.pyd` file from your Python installation's `DLLs` subdirectory.
