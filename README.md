# configure-tinydm (wayland don't know if this applies to x11)
I am recording how I'm confiuring tinydm. This is here cause I know I'll forget how to do it and I don't want to search. If it helps you, your welcome. else sorry for wasting your time

## compositor details, location,config,etc,etc (of tinydm)
file location - ` var/lib/tinydm/default-session.desktop`<\br>
Original contents:-
``` 
[Desktop Entry]
Name=Sway
Name[en]=Sway
Comment=This session logs you into Sway
Comment[en]=This session logs in you into Sway
Exec=dbus-run-session /usr/bin/sway
TryExec=/usr/bin/sway
Icon=
Type=Application
DesktopNames=Sway
Keywords=launch;Sway;desktop;session;

```
<\br>
If you want to change the compositor change the `TryExec=/usr/bin/<compositor_name>` refer to [Wayland-compositors](https://wiki.archlinux.org/title/Wayland#Compositors) for more details.
New contents:-
```
[Desktop Entry]
Name=KWin Wayland
Name[en]=KWin Wayland
Comment=This session logs you into Kwin Wayland
Comment[en]=This session logs in you into Kwin Wayland
Exec=dbus-run-session /usr/bin/kwin_wayland --xwayland
TryExec=/usr/bin/kwin_wayland
Icon=
Type=Application
DesktopNames=KWin
Keywords=launch;KWin;desktop;session;
```

Finally restart tinydm using (reboot prefered tho)
`sudo rc-service tinydm restart` or `sudo systemctl restart tinydm`
you could always just open a new tty and try running ` sudo tinydm-set-session -f -s var/lib/tinydm/default-session.desktop`

