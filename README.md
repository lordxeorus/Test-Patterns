# Test-Patterns
PAL/NTSC FFMpeg test pattern generation - straight to screen

#PAL100
```
ffmpeg -re -f lavfi -i pal100bars=rate=50 -f lavfi -i "sine=frequency=1000:sample_rate=48000" \
-vf "scale=720:576"  -colorspace bt470bg -color_primaries bt470bg -color_trc gamma28 \
-c:v rawvideo -c:a pcm_s16le -f matroska - | ffplay -fs -
```

#PAL75
```
ffmpeg -re -f lavfi -i pal75bars=rate=50 -f lavfi -i "sine=frequency=1000:sample_rate=48000" \
-vf "scale=720:576"  -colorspace bt470bg -color_primaries bt470bg -color_trc gamma28 \
-c:v rawvideo -c:a pcm_s16le -f matroska - | ffplay -fs -
```

#NTSC
```
ffmpeg -re -f lavfi -i smptebars=rate=30000/1001 -f lavfi -i "sine=frequency=1000:sample_rate=48000" \
-ac 2 -vf "scale=720:480" -colorspace smpte170m -color_primaries smpte170m -color_trc smpte170m \
-c:v rawvideo -c:a pcm_s16le -f matroska - | ffplay -fs -
```
