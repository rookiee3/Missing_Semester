# Create a new directory called missing under /tmp.
  ~$ mkdir /tmp/missing
# Use touch to create a new file called semester in missing.
  ~$ cd /tmp/missing
  ~$ touch semester
# Write the following into that file, one line at a time:
  /tmp/missing$ echo #!/bin/sh > semester
  /tmp/missing$ echo curl --head --silent https://missing.csail.mit.edu > semester
# Try to execute the file, i.e. type the path to the script (./semester) into your shell and press enter. Understand why it doesn’t work by consulting the output of ls (hint: look at the permission bits of the file).
  /tmp/missing$ ls -l
  total 0
  -rw-r--r-- 1 anruizhe anruizhe 51 Jan  2 10:53 semester
  this means owner can re(read or write) and group can r and others can r 
  but the hyphen(连字符) before "rw" indicates that the execute permission is not granted(授予) for anyone
  in rwx, x means eXecute
# Run the command by explicitly starting the sh interpreter, and giving it the file semester as the first argument, i.e. sh semester. Why does this work, while ./semester didn’t?
  we have the privilege to execute
# Use chmod to make it possible to run the command ./semester rather than having to type sh semester. How does your shell know that the file is supposed to be interpreted using sh? See this page on the shebang line for more information.
  /tmp/missing$ ./semester
# Use | and > to write the “last modified” date output by semester into a file called last-modified.txt in your home directory.
  ./semester | grep -i last-modified | cut -d' ' -f2- > last-modified.txt
# Write a command that reads out your laptop battery’s power level or your desktop machine’s CPU temperature from /sys. Note: if you’re a macOS user, your OS doesn’t have sysfs, so you can skip this exercise.
  cat /sys/class/thermal/thermal_zone0/temp
