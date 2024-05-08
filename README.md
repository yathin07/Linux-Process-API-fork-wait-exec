# Linux-Process-API-fork-wait-exec-

# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise

## DATE:

## AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

## DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

## PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls

cat > pidcheck.c

```
C Program to print process ID and parent Process ID using Linux API system calls
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; }
```
gcc -o pidcheck.o pidcheck.c

./pidcheck.o

## OUTPUT
![Screenshot 2024-05-08 132910](https://github.com/yathin07/Linux-Process-API-fork-wait-exec/assets/139841679/660b9e46-1ab0-4096-b35c-59f8bea015e8)


ps

## OUTPUT
![Screenshot 2024-05-08 132929](https://github.com/yathin07/Linux-Process-API-fork-wait-exec/assets/139841679/4536148b-1844-434e-97ae-5bedec64dffe)


## C Program to create new process using Linux API system calls fork() and exit()

cat > forkcheck.c

```
//C Program to create new process using Linux API system calls fork() and exit()
#include <stdio.h>
#include<stdlib.h>
int main()
{ int pid; 
pid=fork(); 
if(pid == 0) 
{ printf("Iam child my pid is %d\n",getpid()); 
printf("My parent pid is:%d\n",getppid()); 
exit(0); } 
else{ 
printf("I am parent, my pid is %d\n",getpid()); 
sleep(100); 
exit(0);} 
}
```
gcc -o forkcheck.o forkcheck.c

./forkcheck.o

## OUTPUT
![Screenshot 2024-05-08 133010](https://github.com/yathin07/Linux-Process-API-fork-wait-exec/assets/139841679/7644f507-0a6e-4cb6-ad48-b02832bd0245)


## C Program to execute Linux system commands using Linux API system calls exec() family

cat > execcheck2.c

```

//C Program to execute Linux system commands using Linux API system calls exec() family
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
int main()
{       int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
printf("Running ps with execlp. Now with path specified\n");
        execl("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);}

```

gcc -o execcheck2.o execcheck2.c

./execcheck2.o

## OUTPUT
![Screenshot 2024-05-08 134902](https://github.com/yathin07/Linux-Process-API-fork-wait-exec/assets/139841679/e4edacda-f5ea-4213-8f09-97fa387c453e)


## RESULT:
The programs are executed successfully.
