# template-chord-matching :musical_keyboard:
This is the Github repository for my project "*Template matching algorithm for chord recognition*" for the Audio Signal course @ Politecnico di Milano.

## Content of this repo
In the repository you will find:
### Data
* ***Chord Examples***: A folder that contains piano, guitar and synth recordings alongside their correct handmade chords annotations.
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
The algorithm implemented is the one described in Section 5.2 of "Müller, Meinard. (2015). *Fundamentals of Music Processing*. 10.1007/978-3-319-21945-5.". In particular the templates used are those that can include harmonics and some preprocessing of chorma is apllied (compression and temporal smoothing).
In addition to the method presented in the book, I have included a postprocessing smoother in the form of a KNN classifier, that uses time as its only feature and the chords labels estimated through template matching as target. The details of the implementation are explained in *Template_matching_tutorial.ipynb*

I have tried to add to the preprocessing phase a decomposition into harmonic and percussive components and to run the algorithm only on the harmonic component. It did not prove to give substancial improvements so it is not present in this version of the code.

## Results
The implemented algorithm seems to perform sufficiently well on music samples containing a recording of a single intrument. In most of the cases the misclassification error is low. However when dealing with full mixed songs, that contain also melodic and percussive components, the performance is really poor. The misclassified frames are around the 70% of the total, showing that more advanced methods (such as Hidden Markov Models) should be used to takle harmony in songs.

You can try it by yourself by appliyng the algorithm to the piano, guitar and synth example recordings. It performs generally well on piano and guitar (that simply play chords), on synth recordings (that contains some melodic elements) the algorithm is already bad!
