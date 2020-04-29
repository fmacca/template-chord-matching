# template-chord-matching :musical_keyboard:
This is the Github repository for my project "*Template matching algorithm for chord recognition*" for the Audio Signal course @ Politecnico di Milano.

## Content of this repo
In the repository you will find:
### Data
* ***Chord Examples***: A folder that contains two piano recordings of triads (as chords and as arpeggios) alongside their correct chord annotations.
* ***The Beatles Annotations***: The reference annotations for songs by The Beatles as provided by Chris Harte on [Isophonics](http://isophonics.net/content/reference-annotations-beatles "The Beatles Annotations").
* ***The Beatles dataset.csv***: A .csv dataset containing the chroma representation and the reference annotations for songs by The Beatles. The dataset has been created in preprocessing with the script "*Resources/Create The Beatles dataset.ipynb*"

### Preprocessing
* *Resources/**Create The Beatles dataset.ipynb***: Creates The Beatles dataset from music files and Chris Harte's annotations.
* *Resources/**Convert_to_triad.ipynb***: A utility to extract a basic major/minor triad from a fully annotated chord (ex. from 'C#:min7/3' we get 'C#:min')

### The algorithm implementation
* ***Template_matching_tutorial.ipynb***: A file that implements the algorithm step by step and shows the results on an example file.
* ***Model validation on The Beatles dataset.ipynb***: A file that applies the algorithm implemented in the previus file to a dataset with songs by The Beatles, aiming at finding the right hyperparameters for the model. We end up showing how bad the algorithm works on complete songs.
* ***Application.ipynb***: The implementation of the model that allows you to chose a music file and performs the analysis on the selected file. The hyperparameters are set to values that performed better in the tutorial and on The Beatles dataset. It is possible to change them.

## The Algorithm
