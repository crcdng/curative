# Setup Windows 11

*Note: These steps worked for me after trial and error and research at a certain time. Technical setups can change quickly. If you hit a problem, please leave a bug report on Github so we can fix this together.*

Here is the setup for a Windows 11 computer. When the computer starts, it is running a movie in a loop unattended and without artifacts (see booklet).  

```
Install VLC player https://www.videolan.org/vlc/ 
Copy the movie file 'movie.m4v' to the Desktop 

Settings -> Accounts -> Sign In Options
set a Hello PIN XXXX
restart
Settings -> Accounts -> Sign In Options -> “for improved security only allow ….” -> off
Windows-R -> netplwiz
“Users must supply” -> off

Start with VLC playing a movie on the Desktop
Apps -> Startup -> all off

Windows-R -> shell:startup
New-> Shortcut
"C:\Program Files\VideoLAN\VLC\vlc.exe" --fullscreen --repeat "%Userprofile%\Desktop\movie.m4v"
```