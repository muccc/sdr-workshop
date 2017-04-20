# Simple Stereo FM sender

If you want to run it from gnuradio-companion, enable the "File Source" and on the shell run


```
mkfifo stream.fifo
mplayer -vc null -vo null -ao pcm:nowaveheaderfile=stream.fifo -srate 48000 -af format=s16le FILENAME
```

Then start the flowgraph

If you want to directly play from a shell, enable the "File Descriptor Source", click Run>Generate then run

```
mplayer -quiet -vc null -vo null -ao pcm:nowaveheader:file=/dev/fd/3 -srate 48000 -af format=s16le FILENAME 3>&1  1>&2  | python -u top_block.py
```
