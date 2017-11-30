# teres1-audioselect

Depends on:
restore-sound-after-resume.service
```bash
[Unit]
Description=Restore sound after resume
After=suspend.target
After=tmp.mount
ConditionPathExists=/tmp/.before-suspend-asound.state
ConditionFileIsExecutable=/usr/sbin/alsactl

[Service]
Type=oneshot
ExecStart=/usr/sbin/alsactl -f /tmp/.before-suspend-asound.state restore
ExecStart=/bin/rm -f /tmp/.before-suspend-asound.state
ExecStart=/usr/bin/teres1-audioselect

[Install]
WantedBy=suspend.target
```
