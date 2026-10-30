# Pokemon Emerald Tileset Viewer
A simple tool for viewing the many tilesets used in *Pokemon Emerald* for the Game Boy Advance.  
This project parses the tileset format found in [this decompilation of Pokemon Emerald by pret](https://github.com/pret/pokeemerald).

## Prerequisites
- [CMake](https://cmake.org/) (build system)
- A C++ compiler (Tested with GCC via [MSYS2](https://www.msys2.org/) on Windows 10)

## Installation
> [!IMPORTANT]
> This project has only been tested for Windows 10. Functionality on other operating systems is unknown.

Follow these steps to install and build the application:

1. Clone the repository by either:
    - Running `git clone https://github.com/JosephStorta/Pkmn-Emerald-Tileset-Viewer.git` from the terminal (if you have [Git](https://git-scm.com/install/windows) installed).
    - Going to `Code > Download ZIP` on this repository's web page then extracting the zipped contents.

2. Create a directory for the build files, then from that directory run `cmake [root directory] && make`, replacing "[root directory]" with the relative path to the repository's root directory.  
To specify a makefile configuration, use the `-G` option followed by your desired congifuration.
(e.g. `cmake [root directory] -G "MinGW Makefiles && make"` for MinGW)

Once those steps are completed, there should be a "bin" folder in the project's root directory that contains the executable (Main.exe).

## How to Use
> [!IMPORTANT]
> Loading a tileset requires downloading or cloning [pret's Pokemon Emerald decompilation](https://github.com/pret/pokeemerald).

To load a tileset, go to "File > Open..." then navigate to and select the root folder of the tileset you want to load.
> [!NOTE]
> The tilesets are located in "data/tilesets/primary".

Once a tileset is loaded, you can view the full tileset in the left window, and view the metatiles in the right window.  
Additionally, you can view the different color palettes by checking the "Apply Palette?" checkbox and using the "Palette" spinbox.

## Known Issues
- Secondary tilesets (stored in data/tilesets/secondary in the decomp) currently do not parse correctly and will crash the application.
