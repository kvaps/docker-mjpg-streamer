# MJPG-streamer in a Docker

**Run command**
```bash
docker run \
    -v /dev/video0:/dev/video0 \
    --entrypoint=mjpg_streamer \
    -p 8090:8090 \
    --privileged \
    kvaps/mjpg-streamer -i "/usr/lib64/input_uvc.so -d /dev/video0 -r 320x240 -f 1" -o "/usr/lib64/output_http.so -p 8090 -w /usr/share/mjpeg-streamer/www/"
```
