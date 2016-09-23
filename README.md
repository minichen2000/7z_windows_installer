# 7z_windows_installer
##This is a guide to make a windows installer for a multi files application with 7z.


###1. Need 7z installed. (Append directory of **7z.exe** in **Path** evironment)
###2. Download [7-Zip Extra](http://www.7-zip.org/a/7z920_extra.7z), we need file **7zS.sfx** in it.
###3. Build a package:<br>

  Go to your application directory, execute: ```7z a mypackage.7z *```

  Edit a configuration file *config.txt* :
```
;!@Install@!UTF-8!

Title="My package"

BeginPrompt="Do you want to install the xxx?"

ExecuteFile="<the executable file name/path (in application's directory) which will be executed after unpackage>"

;!@InstallEnd@!
```
Copy **7zS.sfx** to the directory where mypackaged.7z and config.txt are. Execute:
```copy /b 7zS.sfx + config.txt + mypackaged.7z mypackaged.exe```

There, you've got the installer **mypackaged.exe**.


***


##Here I note the commands for making LLM.exe for myself:<br>
```
7z a llm.7z *
copy /b 7zS.sfx + config.txt + llm.7z + LLM.exe
```

**config.txt**:<br>
```
;!@Install@!UTF-8!

Title="协议栈(Low Layers Manager) Nokia Shanghai Bell"

BeginPrompt="是否要安装协议栈(Low Layers Manager 5.0.0)?"

ExecuteFile="SETUP.EXE"

;!@InstallEnd@!
```
