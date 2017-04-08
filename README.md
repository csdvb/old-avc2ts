
# avc2ts

avc2ts is a video encoder for the Raspberry Pi that encodes the video into H.264
and encapsulates it into a constant bitrate MPEG-TS trnamsport stream. The input
source can be a Raspberry Pi camera, internal pattern, UVC webcam, Raspberry Pi
display or a VNC client display.

avc2ts was originally written by Evariste Courjaud F5OEO as part of the [rpidatv]
(https://github.com/F5OEO/rpidatv) package.

This copy of avc2ts is modified for the specific needs of [Copenhagen Suborbitals]
(https://copenhagensuborbitals.com/) rocket flights. For most other uses, in
particular DATV, the original version is probably the better choice.

# Usage

```
  avc2ts -o file -b videorate -m muxrate -x width -y height -f fps -n MulticastGroup [-d PTS/PCR][-v][-h] 
    -o      Path to Transport File Output 
    -b      Video bitrate in bits/s 
    -m      Multiplex bitrate in bits/s (should be around 1.4 of videorate)
    -x      Image width (should be 16 pixel aligned)
    -y      Image height (should be 16 pixel aligned)
    -f      Frame rate
    -n      Optional multicast group, e.g. 230.0.0.1:10000
    -d      Delay PTS/PCR in ms
    -v      Enable motion vectors
    -i      IDR period
    -t      Input type (0=Pi camera, 1=Pattern, 2=USB webcam, 3=Rpi display, 4=VNC)
    -e      Extra arguments:
              - For usb camera name of device (/dev/video0)
              - For VNC, the IP address of the server. Password must be datv.
    -p      Set the PidStart: Set PMT=PIDStart,Pidvideo=PidStart+1,PidAudio=PidStart+2
    -s      Set service name; typically the callsign
    -h      Help

Example:
  avc2ts -o result.ts -b 1000000 -m 1400000 -x 640 -y 480 -f 25 -n 230.0.0.1:1000
```
