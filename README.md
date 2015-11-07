This is something of either a work-in-progress, or a failed experiment.

In short, the [ATTinyCore](https://github.com/SpenceKonde/ATTinyCore) has a confused history, at some point it started out as an arduino core with modifications, but there's no record of what point it branched, or what modifications were made why. (NB: SpenceKonde's detached fork appears to be the most recent/actively updated, there are a ton of these arduino-tiny derived cores around the place in various states of disrepair).

This means it has both diverged in various ways, and not been kept up-to-date with whatever is happening/fixed in the Arduino standard core (which over time has become more accommodating for Tiny's, but still lacks built in SoftwareSerial and other optimisations for small footprint).

Anyway, long story short, in this repo we have 3 branches:
  
  arduino-vendor-drop
  attiny-vendor-drop
  master
  
In arduino-vendor-drop I have placed commits tracking certain drop-points of the arduino core (renamed to "tiny" for merging), the first commit there being what I could determine as the *closest* files from the Arduino standard core to the ATTinyCore files, then subsequent drops for 1.0.6 (probably the last of the 1.0.x line) and 1.6.6 (currently the most recent stable).  In other words, arduino-vendor-drop commits would be all the files forming the standard core for a given Arduino release, unmodified (except renaming the folder to "tiny").

In attiny-vendor-drop I have similarly placed commits tracking certain drop-points of the ATTinyCore as found at the SpenceKonde branch, the first commit being the first record at github of ATTinyCore, followed by a commit just before SpenceKonde started working to make it 1.6.x compatible, and finally (currently) the most recent commit by @SpenceKond on the 5th of November 2015.  In other words, attiny-vendor-drop commits would be all the files forming the ATTinyCore core for a given ATTinyCore version (no releases, so just some point in the repository), unmodified, also the variants folder from that same version.

In master, my intention is (was?) to first merge in an arduino-vendor-drop commit, then merge in an attiny-vendor-drop commit, and then the next arduino- and the next attiny- etc, so as to effectively get us to the point where we have an (modified) ATTinyCore which is actually (re)based on a known version of the Arduino standard core, hopefully with some indication of why changes where made.  Going forward then, keeping in sync with Arduino standard core fixed would be much much easier.

However, my grand plan has been stymied, or at least put on hold for now, simply because there is such a lot of uncertainty and differences, particularly in a few areas (for example HardwareSerial has a LOT of changes, Printable.h isn't used in ATTinyCore instead it has a different definition but it seems more than just "hasn't been updated" and maybe is tiny-ification, but there's no record of why it is so).

Anyway, as it stands in "master" right now we have the initial arduino files (as determined by least difference) "merged" (replaced by) the initial ATTinyCore files - in other words, master has the initial commit of the ATTinyCore.

The next step would be to merge the commit from arduino-vendor-drop tagged 1.0.6 into master, and then the commit from attiny-vendor-drop tagged 1.0.x into master.

Following that arduino-vendor-drop tagged 1.6.6 into master, and finally the HEAD of attiny-vendor-drop into master.  And that would bring you up to the point of having ATTinyCore sitting on top of Arduino 1.6.6's core.
