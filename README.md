# raspberry-stream
System to pull recordings from tivo on a local network and play on a raspberry pi connected tv.

## Idea:
To build a device that will pull recordings from my tivo, download them to its own hard drive, convert them to mpeg encoding, and then play through hdmi to a tv. This will need a few different components to make it into a usable system for a basic user. 

###Web interface:
* used to accept commands to determine videos available and the actions to perform on those videos (play, pause, stop, delete recording).
  * use this to pass from pi to hdmi https://github.com/jbaiter/pyomxplayer
  * maybe create a (rails or node) web app that writes commands to a queue for messaging. (https://abarbanell.wordpress.com/2014/08/26/rabbitmq-on-raspberry-pi/)
  
###Python Processes
* a process to run on a regular schedule (hourly?) to check for new recordings to download to device hard drive. (unless a stream option can be found).
  * Can write in python pretty easily.
  * Compare filenames (without extension) to files on server (might need to parse html for elements)
  * put messages on queue with file path
* a process to run on a regular basis (maybe called from the downloading service) to convert the .TiVo files to mpeg files
  * maybe subscribe to rabbitmq messaging

###Mobile (future):
* an app to give a nice user interface to the whole thing. Have it check for the web interface on the local network.
