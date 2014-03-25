
Forking

the program forks the following tree using

1) 6 calls to fork

2) 3 calls to fork(recurssion)

to build the following tree:

			A
			|__B
			|
			|__C
			|  |__E
			|  |__F
			|	
			|__D
			|  |__G
			|  |__H
			|  |__I

How do we go about it ?

1) Using 6 fork calls - This is pretty straight forward assuming you know how fork() and exit() works.
   



