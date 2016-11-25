# voice-stts_no_nst-hsmm
Basic Norwegian hsmm voice built from data at http://www.nb.no/sprakbanken





## Prerequisites

You will need to have [Java](https://www.java.com/) installed.
On OSX with [Homebrew](http://brew.sh/), do
```
$ brew cask install java
```
as needed.

On Debian-based Linux (including Ubuntu), do
```
$ sudo apt-get install default-jdk
```
accordingly.


### The following section are specific voice packaging instructions, while the marytts-lang-no files are not yet in the main marytts code base.

### Building the voice

To assemble the voice, do
```
$ ./gradlew assemble
```
The "build" task will fail with missing dependency for marytts-lang-no, so make sure to use "assemble" instead.


The jar file will be placed under `build/libs`.
Copy the jar file into your MaryTTS installation's `lib` directory (`<MARYBASE>/build/install/marytts/lib/`).

Make sure your MaryTTS installation was cloned from https://github.com/HaraldBerthelsen/marytts and built with Norwegian language support (add `include 'marytts-languages:marytts-lang-no'` to marytts/settings.gradle before running `./gradlew build`).



### The following are generic voice packaging instructions. When the Norwegian language files for Marytts are finished and merged these instructions should apply.

### Building the voice

To assemble, test, and package the voice for another MaryTTS installation, do
```
$ ./gradlew build
```
The packaged files will be placed under `build/distributions`.
Copy the zip file and xml descriptor into your MaryTTS installation's `download` directory, then run the `marytts-component-installer` to install the voice.

### Running the voice

To build the voice and run it in an ad-hoc MaryTTS server, do
```
$ ./gradlew run
```
Then, go to [http://localhost:59125](http://localhost:59125/).
