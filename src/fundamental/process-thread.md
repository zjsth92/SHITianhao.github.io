# Process and Thread

### Definition

* Process is an instant of a computer program that is being excuted.
* Thread is a piece of programmed instructions

### Difference
* Each process has independent memory space; Threads run in a shared memory space
* The application can have one or more process. One or more threads run in the context of process.

### Thread Pool
* Thread pool is a collection of worker thread. 
* The thread pool is primarily used to reduce the number of application threads and manage them.

### Inter-Process communication 

Processes are isolated between each other as a sandbox. But sometimes processes or applications need to talk each other. There are some ways we can do the inter-process communication

* Network: One application calls anthor one through http protocal.
* Socket: On linux you can use sock file to create an effective connections between two application or process.
* Message Passing such as SOAP, ActiveMQ etc.. This is a heavy methods.
* File Sharing

### Concurrent programming

* Mutex: An object (lock) is created so that multiple threads can take turens sharing the same resource
* Single thread ;) such as JavaScript or PHP using single thread avoiding concurrent programming.
