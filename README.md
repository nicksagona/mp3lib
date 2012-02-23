MP3Lib v1.0
===========

MP3 Library & CD Archive Scripts
--------------------------------
MP3Lib is a collection of scripts that harness together a handful of programs to archive your CD collection, and, from that archive, create a fully organized and completely tagged MP3 library, complete with embedded cover art. In addition, it works in an incremental fashion, so as CDs are added to the archive and the mp3lib script is executed again, it will only process the new albums found and add them to the library.

The programs utilized by mp3lib are:
------------------------------------
* cdrdao & toc2cue - For ripping an exact copy of the CD and its data
* mkisofs - For handling any multi-session CDs and their data
* cdrecord - For burning an exact copy of the CD from your hard drive to CD.
* bchunk - For convert the raw data from the BIN file to WAV files to be utilized by the mp3lib script.
* lame - For creating the actual mp3s.
* eyeD3 - For embedding the cover art within the mp3s.

The main scripts are:
---------------------
* cdrip - Rip an exact copy of a audio CD or enhanced audio CD to your hard drive.
* cdwrite - Burn an exact copy of the CD from your hard drive to a CD.
* mp3lib - Create an organized & completely tagged MP3 library, complete with embedded cover art.

(With any of the above scripts, the "-t" flag will test the system for the necessary software.)

Basic usage:
------------
* cdrip -f "1969 - Led Zeppelin I" (Rips a regular audio CD.)
* cdrip -f "1969 - Led Zeppelin I" -v LEDZEP (Rips an enhanced audio CD, naming the data volume)
* cdwrite:  cdwrite -f "1969 - Led Zeppelin I" (Burns a regular audio CD.)
* cdwrite -m -f "1969 - Led Zeppelin I" (Burns an enhanced audio CD.)
* mp3lib /source/folder /destination/folder 256 (Creates an MP3 library from the archives in the source folder and places them in destination folder, at the bit rate specified.)

A Note on Usage and the Naming Convention:
------------------------------------------
All of the scripts associated with mp3lib utilize a particular naming convention. When using the cdrip script, you should use the following naming convention (within a folder for the artist)

cdrip "YEAR - Album Name"

This will create 3 files within the artist folder:
"/Artist/YEAR - Album Name.bin"
"/Artist/YEAR - Album Name.toc"
"/Artist/YEAR - Album Name.cue"

If you want to have album art included when the mp3lib script runs through the archive, just include the cover art file next to the 3 files with the same naming convention:

"/Artist/YEAR - Album Name.jpg"

If the CD is an enhanced audio CD and you rip it with the "-v" flag, and then an additional ISO file will be created:

"/Artist/YEAR - Album Name.iso"

Once you run the mp3lib script through the archive, the MP3 library will have the following naming convention:

/mp3s/Artist
/mp3s/Artist/YEAR - Album Name/
/mp3s/Artist/YEAR - Album Name/01 - Track Name.mp3
/mp3s/Artist/YEAR - Album Name/02 - Track Name.mp3
