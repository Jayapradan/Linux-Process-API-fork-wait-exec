# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.



### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls
```
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
 ## OUTPUT

 ![Screenshot 2025-04-28 112356](https://github.com/user-attachments/assets/9ae014ef-cf46-4f26-9e50-a717e9e32460)

## C Program to create new process using Linux API system calls fork() and exit()
```
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
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

## OUTPUT

![Screenshot 2025-04-28 111617](https://github.com/user-attachments/assets/434ef2f6-e43b-4381-b34a-eea632f32103)


## C Program to execute Linux system commands using Linux API system calls exec() family
```

#include <stdio.h>
#include <unistd.h>
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

## OUTPUT
![Screenshot 2025-04-28 111824](https://github.com/user-attachments/assets/34e4309d-19f4-4468-92c6-1b486f44a20e)
![Screenshot 2025-04-28 111848](https://github.com/user-attachments/assets/eeb4e2bd-4d00-4d66-b19b-8f5bf1954dfa)
![Screenshot 2025-04-28 111906](https://github.com/user-attachments/assets/08dcd6bc-f800-4b52-aedd-ab6a545f37f7)
![Screenshot 2025-04-28 111923](https://github.com/user-attachments/assets/feea87a8-ff7f-4b36-9199-99dd1f7d6171)
![Screenshot 2025-04-28 111951](https://github.com/user-attachments/assets/0d950c51-d432-4660-96d1-1e1dee6adc5e)
![Screenshot 2025-04-28 112030](https://github.com/user-attachments/assets/736d262f-1cc1-4993-9af7-76d321715447)
![Screenshot 2025-04-28 112040](https://github.com/user-attachments/assets/70b020f9-9784-4ab2-971d-0ca4d01c97dd)


# RESULT:
The programs are executed successfully.
