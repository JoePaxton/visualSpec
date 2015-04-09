# Problem
We want to be able to visualize the attributes of an audio file in real-time.

# Questions
1. What information do we need to accomplish?
2. What technique(s) would be most effective to animate a song and see its 
   attributes displayed in real time?
3. What additional information do you need to know in order to implement 
   this module for the future?

# Resources
1. [wav data]
2. [SpecAnim]
3. [struct]

### 1. Mini-abstract and relevance of [wav data]:
If we use the Python ```wave``` module, then we are able to open a wave file and retrieve
its information. We can obtain the data size, sample rate, sample width, and the
duration of the track. In addition, we need to read in the sample data after the
retrieval of the wave file's information. The ```wave_file``` should only have one channel
so for now we do not have to keep track of the ```getnchannels()``` function, since it is
mono.

```python
import wave #import echonest.remix.audio as audio
wave_file = wave.open(filename, 'r') #audio = audio.LocalAudioFile("song.wav")
dataSize = wave_file.getnframes() #for loop using -> dataSize = audio.getsample
sampleRate = wave_file.getframerate() #sampleRate = audio.sampleRate
sampleWidth = wave_file.getsampwidth()
duration = dataSize / float(sampleRate) #duration = audio.duration
sampleData = wave_file.readframes(dataSize)
wave_file.close()
```

*This answers question 1*

### 2. Mini-abstract and relevance of [SpecAnim]:
We need to be able to calculate and display the various pieces of information. I want to be 
able to plot the Fast Fourier Transform (FFT) data for a WAV file and use it to create multiple
png image files. This output, which could be hundreds to possibly thousands, of png images can 
be used to make a movie file using ffmpeg that also incorporates the associated audio file that
helped create those images so that the movie file can be played back with the audio synced to the 
image files. This movie file is not truly the result of a real-time application; however, it can 
play the audio along with the associated png images, thus demonstrating the audio attributes displayed 
as the song is played back. You need a full version of ffmpeg (or a version of ffmpeg capable of 
handling audio visual files in order to create the movie file).

*This answers question 2*

###3. Mini-abstract and relevance of [struct]:
We need to be able to ```unpack()``` the binary data from the wave audio file into an array. Then,
we need to be able to process many samples so there will be lots of fourier transform animations.
We need to initialize a single png image with the wav data before the iteration from ```range(0, totalFFTs)```,
where ```totalFFTs``` is the total amount of transforms. The x-axis (0,12) will have colored bars representing
each pitch or octave in the wav file and the y-axis represents the amplitude. We will worry about the band 
widths and the frequency downgrades to its proper indices later, if needed. Here is how I implemented the 
decoding of binary data and all of the sample data. 

```python
sampleData = struct.unpack('%dh' % dataSize, sampleData) 
framesPerSec = 24
fourierWidth = 1.0 / framesPerSec
fourierWidthIndex = fourierWidth * float(sampleRate)
```

*This answers question 3*

[wav data]: http://stackoverflow.com/questions/2226853/interpreting-wav-data 
[SpecAnim]: http://classicalconvert.com/2008/04/how-to-visualize-music-using-animated-spectrograms-with-open-source-everything/
[struct]: https://docs.python.org/2/library/struct.html 
