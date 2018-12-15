#Get source list
pactl list | grep -A2 'Source #' | grep 'Name: ' | cut -d" " -f2

#Server
gst-launch-1.0 -v pulsesrc device="alsa_output.pci-0000_00_1b.0.analog-stereo.monitor" ! audioconvert ! vorbisenc ! oggmux ! filesink location=alsasrc.ogg

#Client
gst-launch-1.0 filesrc location=alsasrc.ogg ! decodebin ! autoaudiosink
