# WavReader
Console utilities for reading wave format (.wav) header and data written in C++, Java.

## Includes
* [WavReader.cpp](https://github.com/tkacz-/WavReader/blob/master/WavReader/WavReader.cpp "For C++") - written in C++
* [MetaReader.java](https://github.com/tkacz-/WavReader/blob/master/WavReader_Java/MetaReader.java "For Java") - written in Java

## The header of a WAV file

![](https://github.com/tyler9338/WavReader/raw/master/wav-sound-format.gif)

	The following table are in Bits HeaderType

 * **The "RIFF" chunk descriptor:**
 
 	1-4 	`"RIFF"`		*Marks the file as a riff file. Characters are each 1 byte long*
 	
	5-8	`File size (integer)`	*Size of the overall file - 8 bytes, in bytes (32-bit integer).*
	
	9-12	`"WAVE"`		*File Type Header. For our purposes, it always equals "WAVE".*
	
 * **The "fmt" sub-chunk:**
 
	13-16	`"fmt "`		*Format chunk marker. Includes trailing null*
	
	17-20	`16`			*Length of format data as listed above*
	
	23-24	`2`			*Number of Channels - 2 byte integer*
	
 	25-28	`44100`			*Sample Rate - 32 byte integer. CSample Rate = Number of Samples per second, or Hertz.*
 	
	29-32	`176400`		*(Sample Rate * BitsPerSample * Channels) / 8. Byte rate*
	
	33-34	`4`			*(BitsPerSample * Channels) / 8.1 - 8 bit mono2 - 8 bit stereo/16 bit mono4 - 16 bit stereo*
	
	35-36	`16`			*Bits per sample*
	
 * **The "data" sub-chunk:**
 
 	37-40	`"data"`		*Marks the beginning of the data section.*
 	
 	41-44	`File size (data)` 	*Size of the data section.*
 	
 	44-..	`Data samples`
 	
The file could have another sub-chunks.
