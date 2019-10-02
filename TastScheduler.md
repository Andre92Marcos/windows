You can use Task Scheduler to scheduler the execution of scripts in windows:

	1st) Open Task Scheduler
	2nd) Actions->Create Task
	3rd) Choose a name
	4th) On the triggers tab, choose a trigger
	5th) On the Actions tab,
	C:\cygwin64\bin\bash.exe -l -c "/cygdrive/c/path/to/script.sh"


In the Last Result column of your task. If it is not 0 then your task had an error while running.
