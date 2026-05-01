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

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls

if (pid == 0) { 
    printf("I am child, my PID is %d\n", getpid()); 
    printf("My parent PID is: %d\n", getppid()); 
    sleep(2);  // Keep child alive for verification
} else { 
    printf("I am parent, my PID is %d\n", getpid()); 
    wait(NULL); 
}



##OUTPUT

<img width="647" height="130" alt="1" src="https://github.com/user-attachments/assets/ed4d929e-7f03-46c1-8a6c-4e207907aa69" />
<img width="645" height="131" alt="2" src="https://github.com/user-attachments/assets/57e45a28-9342-4631-90ca-5cdb8398c3c2" />


## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family


printf("Running ps with execl\n");
if (fork() == 0) {
    execl("ps", "ps", "-f", NULL);
    perror("execl failed");
    exit(1);
}
wait(&status);

if (WIFEXITED(status)) {
    printf("Child exited with status: %d\n", WEXITSTATUS(status));
} else {
    printf("Child did not exit successfully\n");
}

printf("Running ps with execlp (without full path)\n");
if (fork() == 0) {
    execlp("ps", "ps", "-f", NULL);
    perror("execlp failed");
    exit(1);
}
wait(&status);

if (WIFEXITED(status)) {
    printf("Child exited for execlp with status: %d\n", WEXITSTATUS(status));
} else {
    printf("Child did not exit successfully\n");
}

printf("Done.\n");
return 0;


##OUTPUT

<img width="1357" height="1159" alt="WhatsApp Image 2026-05-01 at 23 15 41" src="https://github.com/user-attachments/assets/6bc3f230-74ec-484e-8d23-9092b0e6b02e" />



# RESULT:
The programs are executed successfully.
