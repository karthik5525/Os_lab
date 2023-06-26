# Os_lab
Operating systems programs

*****i/o_system_call*****

#include<stdio.h>

#include<stdlib.h>

#include<unistd.h>

#include<sys/types.h>

#include<fcntl.h>

void main()

{int fd;
	char message[]="Hai Hello";
	char buffer[100];
	
	fd=open("myfile.txt",O_RDWR|O_CREAT);
	if(fd!=-1)
	{write(fd,message,sizeof(message));
	lseek(fd,0L,0);
	read(fd,buffer,sizeof(message));
	printf("The content of file is :%s",buffer);
	close(fd);
	}
	else
	{printf("Failed to Open file");
	}
}



****Semaphore***
