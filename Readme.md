### Overview

Stockfish is a free UCI chess engine derived from Glaurung 2.1. It is
not a complete chess program and requires some UCI-compatible GUI
(e.g. XBoard with PolyGlot, eboard, Arena, Sigma Chess, Shredder, Chess
Partner or Fritz) in order to be used comfortably. Read the
documentation for your GUI of choice for information about how to use
Stockfish with it.

This version of Stockfish supports up to 128 CPU cores. The engine defaults
to one search thread, so it is therefore recommended to inspect the value of
the *Threads* UCI parameter, and to make sure it equals the number of CPU
cores on your computer.


### Files

This distribution of Stockfish consists of the following files:

  * Readme.md, the file you are currently reading.

  * Copying.txt, a text file containing the GNU General Public License.

  * src, a subdirectory containing the full source code, including a Makefile
    that can be used to compile Stockfish on Unix-like systems. For further
    information about how to compile Stockfish yourself read section below.

  * polyglot.ini, for using Stockfish with Fabien Letouzey's PolyGlot
    adapter.


### Opening books

This version of Stockfish has support for PolyGlot opening books. For
information about how to create such books, consult the PolyGlot
documentation. The book file can be selected by setting the *Book File*
UCI parameter.


### Compiling it yourself

On Unix-like systems, it should be possible to compile Stockfish
directly from the source code with the included Makefile.

Stockfish has support for 32 or 64-bit CPUs, the hardware POPCNT
instruction, big-endian machines such as Power PC, and other platforms.

In general it is recommended to run `make help` to see a list of make
targets with corresponding descriptions. When not using the Makefile to
compile (for instance with Microsoft MSVC) you need to manually
set/unset some switches in the compiler command line; see file *types.h*
for a quick reference.


### Using Stockfish

If you are not using a GUI, you can run Stockfish in command-line mode 
by changing to the directory where the binary is stored and then typing
in the terminal: `./stockfish` (for Unix-like systems) or `stockfish` 
(for Windows systems).

Stockfish uses the UCI protocol to communicate with a GUI. The complete
documentation can be obtained from http://download.shredderchess.com/div/uci.zip.

Some examples of useful commands are given below.

#### Setting up the position

Set the position with a FEN string:

`position fen rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1`

Set the position with moves starting from the start position:

`position startpos moves e2e4 e7e5 d2d4`

This notation is preferred so that the engine can take into account things
like the 50-move rule or threefold repetition.


#### Changing UCI settings

Output a list of available options:

`uci`

Set the hash size to 1 GB:

`setoption name Hash value 1024`

Use 4 threads (default is 1):

`setoption name Threads value 4`


#### Starting Analysis

Clear hash tables before starting a new analysis session:

`ucinewgame`

Analyze given position till depth 20:

`go depth 20`

Analyze given position for 10 seconds (10000 ms):

`go movetime 10000`

Start infinite analysis of given position:

`go infinite`

You can stop the analysis at any time by typing `stop` or pressing 
`CONTROL + C` to quit the program.


#### Debugging

Print the ASCII representation of the board position:

`d`

Obtain the position, material and pawn hash keys:

`key`

Obtain the static evaluation of a given position:

`eval`

Run the internal benchmark suite:

`bench`

This command will output 3 final values, for example:
```
Total time (ms) : 6322
Nodes searched  : 8732553
Nodes/second    : 1381295
```
The **bench** number is given by the *Nodes Searched*. It is used to 
uniquely indentify different versions of Stockfish.


### Terms of use

Stockfish is free, and distributed under the **GNU General Public License**
(GPL). Essentially, this means that you are free to do almost exactly
what you want with the program, including distributing it among your
friends, making it available for download from your web site, selling
it (either by itself or as part of some bigger software package), or
using it as the starting point for a software project of your own.

The only real limitation is that whenever you distribute Stockfish in
some way, you must always include the full source code, or a pointer
to where the source code can be found. If you make any changes to the
source code, these changes must also be made available under the GPL.

For full details, read the copy of the GPL found in the file named
*Copying.txt*
