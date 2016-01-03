# MJPG-streamer in a Docker

**Run command**
```bash
docker run \
    -v /dev/video0:/dev/video0 \
    --cap-add SYS_ADMIN \
    --entrypoint=mjpg_streamer \
    -p 8090:8090 \
    kvaps/mjpg-streamer \
    -i "/usr/lib64/input_uvc.so -y -d /dev/video0 -r 320x240 -f 10" \
    -o "/usr/lib64/output_http.so -p 8090 -w /usr/share/mjpeg-streamer/www/ -c admin:admin"
```

**docker-compose.yml**
```yaml
mjpg-streamer:
  restart: always
  image: kvaps/mjpg-streamer
  cap_add: 
    - SYS_ADMIN
  volumes:
    - /dev/video0:/dev/video0
  ports:
    - 8090:8090
  command: -i "/usr/lib64/input_uvc.so -y -d /dev/video0 -r 320x240 -f 10" -o "/usr/lib64/output_http.so -p 8090 -w /usr/share/mjpeg-streamer/www/ -c admin:admin"
```
