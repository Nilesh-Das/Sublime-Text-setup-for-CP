# Sublime Build System
This is a step by step guide to setup our favourite sublime text for competitive programming.

## Algorithm
Let's setup our sublime with an example programming language (our old school: C++)
### Step 1: Create build system
open "Tools > Build System > New Build System" and copy-paste below command
```json
{
	"shell_cmd": "g++ -std=c++17 \"${file}\" -o a",
	"file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",
	"working_dir": "${file_path}",
	"selector": "source.c++, source.cpp, source.cc, source.cxx",

	"variants":
	[
		{
			"name": "Build Fast",
			"shell_cmd": "g++ -O2 -std=c++17 -Wno-unused-result -Wshadow -Wall -o a \"${file}\""
		},
		{
			"name": "Build Check",
			"shell_cmd": "g++ -DLOCAL -std=c++17 -Wshadow -Wall -fsanitize=undefined -D_GLIBCXX_DEBUG -g -o a \"${file}\""
		},
		{
			"name": "Run",
			"shell_cmd": "\"./a\" < \"${file_path}/in\""
		},
		{
			"name": "Out",
			"shell_cmd": "\"./a\" < \"${file_path}/in\" > \"${file_path}/out\""
		},
		{
			"name": "Build and Run I/O",
			"shell_cmd": "g++ -std=c++17 \"${file}\" -o a && \"./a\"<\"${file_path}/in\""
		},
		{
			"name": "Terminal Run",
			"shell_cmd": "gnome-terminal -- bash -c \"time ./a && echo && echo Press ENTER to EXIT ... && read line && exit\""
		},
		{
			"name": "Terminal I/O",
			"shell_cmd": "gnome-terminal -- bash -c \"time ./a < in && echo && echo Press ENTER to EXIT ... && read line && exit\""
		}
	]
}
```

Note : Create "in" file for input to your cpp program in current directory
### Step 2: Add Key Bindings
You can add key bindings to your specific build system like this
```json
[
{ "keys": ["f5"], "command": "build", "args": {"build_system": "Packages/C++/C++.sublime-build", "variant": "Run", "choice_build_system": true, "choice_variant": true}},
  { "keys": ["f6"], "command": "build", "args": {"build_system": "Packages/C++/C++.sublime-build", "variant": "Build and Run I/O", "choice_build_system": true, "choice_variant": true}},
  { "keys": ["f7"], "command": "build", "args": {"build_system": "Packages/C++/C++.sublime-build", "variant": "Terminal I/O", "choice_build_system": true, "choice_variant": true}},
  { "keys": ["f8"], "command": "build", "args": {"build_system": "Packages/C++/C++.sublime-build", "variant": "Build Check", "choice_build_system": true, "choice_variant": true}},
  { "keys": ["f9"], "command": "build", "args": {"build_system": "Packages/C++/C++.sublime-build", "variant": "Build Fast", "choice_build_system": true, "choice_variant": true}},
  ...
  ]
  ```
### Step 3: Window Setup
You can change your layout as two columns : one for code and other for input,
simply go "View > Layout > Colums: 2" or alternatively 
```
shift + alt + 2
```
### Step 3: Practice, practice and practice
Just believe in yourself and practice on coding platforms
