# chess-NN

A project with the goal of training a deep neural network, i.e. a convolutional neural network (CNN),
to play the game of chess. Currently, I am working on implementing a board evaluation function using a CNN.

The board evaluation CNN was trained using randomly generated legal positions and Stockfish's evaluation.

The next step is to train a separate CNN on the likelihood that a move is "good", again using Stockfish's evaluation.

### Config

This project was written using Python 3.7

In order to run this project, first execute the following inside the chess-NN directory:
```
pip install -r requirements.txt
```

This will install the required packages. You must also configure TensorFlow to work properly with a GPU (if desired):

- https://www.tensorflow.org/install/gpu for more information. Follow **ALL** installation instructions!
  - CUDA Toolkit version 11.0
  - cuDNN SDK 8.2.0

This option can be skipped, but the neural network will train very slowly without access to a GPU.

### Running

To generate the dataset, first you must specify the path of the Stockfish engine. You can download the engine here: https://stockfishchess.org/download/
Then, in the stockfish() function, change the PATH value to the location of the Stockfish executable.

Then run:
```
python3 generateData.py
```
The result will be a very large .npz dataset containing 1,000,000 chess board positions and their Stockfish evaluation at the specified depth (default = 0).
The process to generate the dataset takes quite a bit of time (~= 20 hours), so you can instead download a sample dataset here: (!!!!!!)

Then run:
```
python 3 main.py
```
This will create the neural network, train it using the dataset generated above, and then evaluate 100 test cases to validate accuracy.
