# Sublime Build System
This is a step by step guide to setup our favourite sublime text for competitive programming.

## Algorithm
Let's setup our sublime with an example programming language (our old school: C++)
### Step 1: Create build system
open "Tools > Build System > New Build System" and copy-paste below command
'''json
{
	"shell_cmd": "g++ -std=c++17 \"${file}\" && \"${file_path}/a.out\"",
	"file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",
	"working_dir": "${file_path}",
	"selector": "source.c++, source.cpp, source.cc, source.cxx",

	"variants":
	[
		{
			"name": "Run I/O",
			"shell_cmd": "g++ -std=c++17 ${file} && ${file_path}/a.out<${file_path}/input"
		},
		{
			"name": "Run in Terminal",
			"shell_cmd": "g++ -std=c++17 ${file} && gnome-terminal -- bash -c \"${file_path}/a.out && echo && echo Press ENTER to EXIT && read line && exit\""
		}
	]
}
'''
//Incomplete
