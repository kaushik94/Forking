#include<stdio.h>
#include<unistd.h>
#include<stdlib.h>

int child_count=0;
static pid_t pid_x;
int build_tree_six(int processes){ 

	int status;
	int i;
	int j;
	//printf("i am root %d\n",getpid());
	for(i=0;i<processes;i++){									// make a loop of 3 forks(for the first generation)
	if(fork() == 0 ){										// ensures that only child executes this code.
		printf("i am %d, child of %d\n",getpid(),getppid());
		if(i==1){
			processes = 2;
			int status_one;
			for(j=0;j<processes;j++)							// make another for loop of 2 forks(for the 2nd child in gen 2)
			if(fork() == 0){
				printf("i am %d, child of %d\n",getpid(),getppid());
				exit(0);								// the 2 children die as soon as they are printed
				}
			else wait(&status_one);			
		}
		if(i==2){
			processes = 1;
			int status_two;
			for(j=0;j<processes;j++)							// make another for loop of 1 fork(for the 3rd child in gen 2)
			if(fork() == 0){
				printf("i am %d, child of %d\n",getpid(),getppid());
				exit(0);								// child dies as soon as it is printed.				
				}
			else wait(&status_two);			
		}
		
		exit(0);										// the 3 children in 1st gen die after getting printed and
		}											// getting their children printed.
	}

	for(i=0;i<processes;i++){									// wait for the children to exit. (Reaping)
		wait(&status);
	}
	
}


void build_tree_three(int processes,int generation){

	int i;
	for(i=0;i<processes;i++)
		{
			int status;
			pid_t _pid;
			_pid = fork();
			if(_pid == 0){
				
				printf("child %d @ parent %d\n",getpid(),getppid());
				if((i==2)&&(generation == 1)){
					build_tree_three(2,2);}
				if((i==1)&&(generation == 1)){
					build_tree_three(1,2);}
				exit(0);
			}
			else{
				wait(&status);			
			}
		}
}

build_tree(){

	build_tree_three(3,1);
}	

int main(){

	int processes = 3;
	build_tree();	
}
