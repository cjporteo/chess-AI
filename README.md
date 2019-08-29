# Chess AI Engine

This was created as a final project for CS246 at University of Waterloo.

The task was to create a chess engine from scratch that supports both human and AI players. AI was implemented using minimax with alpha-beta pruning. Graphics are handled with *X11*.

![AB Pruning](https://scontent-yyz1-1.xx.fbcdn.net/v/t1.15752-9/69336075_487777005102422_277070960195010560_n.png?_nc_cat=103&_nc_oc=AQnNEzIzuslfjTOVNKuk44F6mdqMWATLfQO7c65XMIDe073hFaIDkzefY_ECGhio1xI&_nc_ht=scontent-yyz1-1.xx&oh=82ca36d40f740d8ba5bbe7556b50d390&oe=5E015999)
Once a checkmate pattern is identified, the search is terminated and the move sequence is executed.

All chess rules are incorporated, including castling, en passant, and pawn promotion. The engine is controlled from the command line.

## Installation

``git clone https://github.com/cjporteo/chess-AI``
``cd ChessAI``
``./chess``

## Functionality

Game is instantiated by ``game``
Enter white player mode, one of: ``human``, ``computer1``, ``computer2``, ``computer3``, ``computer4``
Enter black player mode, one of: ``human``, ``computer1``, ``computer2``, ``computer3``, ``computer4``

Computer number corresponds to the level of sophistication of the AI. ``computer1`` makes moves at random. ``computer4`` is still quite crude, broadly speaking, but still makes decisions with some degree of cleverness.

The board will now be drawn and the pieces initialized.

Moves are made with the ``move`` command. If the current move is being made by a human player, the initial and destination square for the piece must be specified.

#### Example:
For a computer player: ``move``
For a human player: ``move e2 e4``

To surrender, use the ``resign`` command. A new game can then be started.

## Notes

 - There is lots of room for improvement with this software, concerning both the graphics and the AI; a trained neural network could be implemented in the future to vastly improve decision making ability.
 
- The decision tree is built in a naive iterative manner, meaning the left-to-right ordering of nodes in the tree isn't ordered in any specific way. Constructing the tree looking for *capturing* moves first, for example, would facilitate faster pruning and significant reduction in search time.

- Well known and researched openings could be hard-coded into the engine. Opening theory for chess has been rigorously studied and ideal opens have been well established for quite some time. AI only really starts to shine in the mid-game, even if state of the art neural networks.

- This engine is not bug-free. Odd things happen sometimes, such as:
	 - random crashes on piece capture
	 - highly questionable moves made by ``computer4``
	 - segmentation faults
	 - compiling new executable using ``make run`` results in games that crash on the first move. This likely stems from incompatibility with current updated versions of the OS; ``./chess`` still works, though
- ``game computer4 compter4`` is probably the highlight of this engine. Ever wondered what a chess game would look like between Garry Kasparov and Bobby Fischer if both were inebriated to the brink of unconsciousness? ``computer4`` vs. ``computer4`` will likely put this curiosity to rest.
