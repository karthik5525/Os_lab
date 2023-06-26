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


#include<stdio.h>
#include<stdlib.h>
#include<unistd.h>
#include<semaphore.h>
#include<pthread.h>
sem_t mutex;
void* thread()
{sem_wait(&mutex);
printf("Entered");
sleep(2);
printf("Exiting");
sem_post(&mutex);
}
void main()
{sem_init(&mutex,0,1);
pthread_t t1,t2;
pthread_create(&t1,NULL,thread,NULL);
pthread_create(&t2,NULL,thread,NULL);
pthread_join(t1,NULL);
pthread_join(t2,NULL);
}
