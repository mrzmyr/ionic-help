## Emualtor Setup Android Mac

The follow instrustions should help you get the Android emulator set up on mac.

Install `ant`
  
Get the latest version of Apache Ant (binary distribution) from its official website (example link)
Unzip the binary distribution and rename the folder to “ant” change directory to the directory containing "ant" [Download Ant](http://ant.apache.org/bindownload.cgi)

Move the folder to `“/usr/local”` terminal commands

```
$ mv ant /usr/local
$ cd /usr/local
$ ln -s ant ant
```

Add the following lines of code to your bash_profile file (`~/.bash_profile`)

```
$ export ANT_HOME=/usr/local/ant
$ export PATH=${PATH}:${ANT_HOME}/bin
```

And source your bash profile again
  
```
$ source ~/.bash_profile
```