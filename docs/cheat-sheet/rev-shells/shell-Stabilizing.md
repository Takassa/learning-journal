# Shell Stabilizing

## Prerequisites
This is a post exploitation process. Follow the steps if you have already got a reverse shell connection from the target machine.
Before we begin, ensure that the target machine has Python 2 or 3 installed. This will be essential for implementing the steps outlined in this guide.

## Stabilize your shell

1. **Import the pty Module and Spawn a Bash Shell:**
On your target machine execute the following command:
```python
python3 -c 'import pty;pty.spawn("/bin/bash")'
```



2. **Background the Process:**
Once the shell is spawned, you might notice that the interaction isn’t entirely smooth yet.
Press **CTRL + Z** to temporarily background the process. This will allow you to regain control of your host machine while keeping the spawned shell active on the target.



3. **Adjust Terminal Line Settings and Bring the Shell to the Foreground:**
To enhance the interactive experience, you’ll need to tweak the terminal settings of your host machine.
now run the following command in your host machine:
```
stty raw -echo; fg
```
This combination of commands adjusts the terminal settings to enable a smoother flow of input and output and will bring back the shell that you minimized previously.



4. **Set the Terminal Emulator to xterm:**
After bringing the shell back, for optimal compatibility and usability, set the terminal emulator to xterm on your target machine using the following command:
```
export TERM=xterm
```
This step ensures that the system interprets the terminal environment correctly.



## Credits
This method is taken from [SAEED.](https://saeed0x1.medium.com/stabilizing-a-reverse-shell-for-interactive-access-a-step-by-step-guide-c5c32f0cb839)