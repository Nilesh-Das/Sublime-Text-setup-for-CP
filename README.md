# Sublime Build System
This is a step by step guide to setup our favourite sublime text for competitive programming.

## Algorithm
Let's setup our sublime with an example programming language (our old school: C++)
### Step 1: Create build system
open "Tools > Build System > New Build System" and copy-paste below command
```sublime-build
{
	"shell_cmd": "g++ \"${file}\" -o \"${file_path}/${file_base_name}\"",
	"file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",
	"working_dir": "${file_path}",
	"selector": "source.c++, source.cpp, source.cc, source.cxx",

	"variants":
	[
		{
			"name": "Run I/O",
			"shell_cmd": "g++ \"${file}\" -o \"${file_path}/${file_base_name}\" && ${file_path}/${file_base_name}<${file_path}/input.txt>${file_path}/output.txt"
		}
	]
}
```
