# Problem
We want to be able to visualize the attributes of an audio file in real-time.

# Questions
1. What information do we need to know in order to start this module?
2. What technique(s) would be most effective to animate a song and see its 
   attributes displayed in real time?
3. What additional information do you need to know in order to implement 
   this module for the future?

# Resources
[Realtime FFT]
[FFT Audio]


### 1. Mini-abstract and relevance of [Realtime FFT]:
If we use the ```wave``` module then we are able to open a wave file and retreive
its information. We can obtain the data size, sample rate, sample width, and the
duration of the track. In addition, we need to read in the sample data after the
retrieval of the wave file's information.

```python
import wave
wave_file = wave.open(filename, 'r')
dataSize = wave_file.getnframes()
sampleRate = wave_file.getframerate()
sampleWidth = wave_file.getsampwidth()
duration = dataSize / float(sampleRate)
sampleData = wave_file.readframe(dataSize)
wave_file.close()
```

*This answers question 1*

### 2. Mini-abstract and relevance of [FFT Audio]:
We need to be able to calculate and display the various pieces of information. I want
to be able to plot the Fast Fourier Transform data for a WAV file into multiple png images.
The output of hundreds to thousands of png images will be converted using ```ffmpeg``` into 
a mix of the associated audio along with the png images playing at the same time. The movie
file does is not a result of a real-time application; however, it does play the audio along
with the attributes that are displayed. You need the latest version of ffmpeg in order to 
create a movie file.

*This answers question 2*


###3. Mini-abstract and relevance of []:



*This answers question 3*
 

[Realtime FFT]: http://www.swharden.com/blog/2010-03-05-realtime-fft-graph-of-audio-wav-file-or-microphone-input-with-python-scipy-and-wckgraph/
[FFT Audio]: http://www.swharden.com/blog/2013-05-09-realtime-fft-audio-visualization-with-python/
[]:
