# Problem
We want to be able to visualize the attributes of an audio file in real-time.

# Questions
1. What information do we need to know in order to start this module?
2. What technique(s) would be most effective to animate a song and see its 
   attributes displayed real time?

# Resources
[Realtime FFT]
[FFT Audio]


### 1. Mini-abstract and relevance of [Realtime FFT]:
If we use the ```wave``` module then we are able to open a wave file and retreive
information about the wav file. We can obtain the data size, sample rate, sample width,
and the duration of the track. In addition, we need to read in the sample data after the
retrieval of the wave file's information.

```python
import wave
wave_file = wave.open(filename, 'r')
dataSize = wave_file.getnframes()
sampleRate = wave_file.getframerate()
sampleWidth = wave_file.getsampwidth()
duration = dataSize / float(sampleRate)
sampleData = wave_file.readframe(dataSize)
```



### 2. Mini-abstract and relevance of [FFT Audio]:





 
[Realtime FFT]: http://www.swharden.com/blog/2010-03-05-realtime-fft-graph-of-audio-wav-file-or-microphone-input-with-python-scipy-and-wckgraph/
[FFT Audio]: http://www.swharden.com/blog/2013-05-09-realtime-fft-audio-visualization-with-python/
