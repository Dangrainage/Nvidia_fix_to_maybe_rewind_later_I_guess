Ran command:
`sudo nano /etc/systemd/system/nvidia-reload.service`

Inside the file the following was written down:

```
[Unit]
Description=Reload NVIDIA kernel modules after boot Fucking kill me
After=multi-user.target

[Service]
Type=oneshot
ExecStart=/usr/local/bin/nvidia-reload.sh
RemainAfterExit=true

[Install]
WantedBy=multi-user.target
```

Ran command:

`sudo nano /usr/local/bin/nvidia-reload.sh`

After which the file was filled with:

```
#!/bin/bash
modprobe -r nvidia_drm nvidia_modeset nvidia_uvm nvidia
modprobe nvidia
systemctl start lightdm.service
```

The command `sudo chmod +x /usr/local/bin/nvidia-reload.sh` was then ran

The command `sudo systemctl enable nvidia-reload.service` was ran after

This fix works, It's hacky but I can't be bothered enough to be honest.
I'm writing this down because I just spent about 4 hours debugging It.
Thank fuck this Is over. 

Dan out.




