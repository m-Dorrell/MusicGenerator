# <center>MusicGenerator</center>

Generates music using neural networks and learns from retro game soundtracks as MIDI files

## Description of Project

As part of the University of Western Australia's software engineering unit CITS4404 - Artificial Intelligence and Adaptive Systems, we are required to produce a piece of software that uses machine learning for an *interesting task*.
The goal of this project is to use neural networks to develop a generative model to compose music after being trained on music of a certain type.

This project is composed of three jupyter notebooks:
* RNN Model - The core generative model
* SimilarityTest - A supporting app that determines the similarity between songs
* ChangeInstrument - A supplementary app that reads a MIDI file and outputs it identically using a different instrument

We also looked into using a GAN Model, however we found that the discriminator converged too quickly and we found great success with the RNN Model so we decided to direct all efforts towards improving that model. The code for the GAN Model is available upon request and will likely be pushed in a future update once it has been improved considerably.

## Description of Structure

This system has a specific structure that allows all apps to be relatively self-contained and to streamline the process for the user:

**Best Samples** - Some generated songs that are our favourites.<br>
**Converter** - Relates to the ChangeInstrument notebook and includes folders for input/output of files.<br>
**MIDIs** - Holds all of the MIDI files used for training.<br>
**Models** - Contains all of the notebooks.<br>
**Output** - Where the RNN Model generates music, saves checkpoints. Also where the pretrained model exists.<br>
**Similarity** - Relates to the SimilarityTest notebook and includes folders for comparing files.<br>

*Note:* Included in the /Models folder are the original 'lstm' and 'mlp_gan' [code](https://github.com/corynguyen19/midi-lstm-gan) that this project was based on.

## Directions for Use

#### RNN Model

1. Select the data to load in from the /MIDIs/ folder
2. Print the key of each song loaded for analytics
3. Clean the data by converting the absolute offsets to relative and the durations to an integer representation
4. Prepare the input data as sequences by converting pitch, offset and duration to integers and normalize between 0-1
5. Construct the RNN Model
6. Either train the model from scratch or load the pretrained model at the selected epoch
7. Generate music:
  * One song at a time
  * An album of random songs at once
  * Generate songs using the models from all checkpoints of the training

#### SimilarityTest

1. Place the desired MIDI file in the folder /Similarity/input
2. Place the training MIDIs into the folder /Similarity/compare_to
3. Run all code snippets
4. The final code snippet will output the percentage the input song matches the comparison songs

#### ChangeInstrument

1. Place the desired MIDI file(s) in the folder /Converter/input
2. Run the first two code snippets to read in the file(s)
3. Choose the desired output instrument using the third code snippet:
    * Piano
    * Bagpipes
    * Flute
    * Clarinet
    * Ocarina
    * Harmonica
    * Steel Drum
    * Vocals
    * Soprano (vocals)
    * Bass (vocals)
    * Guitar
    * Glec_guitar
    * Violin
    * Saxophone
    * Trombone
    * Trumpet
    * Enlish Horn
4. Run the final code snippet to convert the instrument
5. Play the output MIDI file located in the folder /Converter/output

## References

We make reference to the following articles and github repos:
  * [Generating Pokemon-Inspired Music from Neural Networks](https://towardsdatascience.com/generating-pokemon-inspired-music-from-neural-networks-bc240014132)
  * [MIDI File LSTM & GAN (GitHub Repo)](https://github.com/corynguyen19/midi-lstm-gan)
  * [How to Generate Music using a LSTM Neural Network in Keras](https://towardsdatascience.com/how-to-generate-music-using-a-lstm-neural-network-in-keras-68786834d4c5)
