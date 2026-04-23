#🚀 CENG-302 Operating Systems - Project 1: Distributed Log-Processing Pipeline

🛠️ Technologies and Architecture
Language: C (POSIX Standards)

IPC Methods: 1. Named Pipe (FIFO)
2. POSIX Shared Memory (shm_open, mmap)

Synchronization: * pthread_mutex (For the Pipe architecture)

POSIX Named Semaphores (sem_open, sem_wait, sem_post - For Shared Memory)

Concurrency: POSIX Threads (pthreads)

Signal Handling: Graceful Shutdown (SIGINT)

📋 Core Features of the Project
Multi-threading: The Producer program creates a separate thread for each log file provided as an argument and reads the data concurrently.

Log Filtering: The Consumer program parses the raw logs received via IPC and prints only the lines containing a CRITICAL or ERROR tag to the screen.

Pagination: The filtered logs are displayed in blocks of 10 lines. The user can press the space bar to continue or the q key to exit.

Zombie Memory Protection (Graceful Shutdown): If the user abruptly terminates the process using Ctrl+C, the program triggers unlink operations, ensuring that no dangling semaphores or shared memory are left in RAM. This provides a safe and clean shutdown.

📂 File Hierarchy
Plaintext
OP_Proje/
├── myData_pipe.c         # Producer - Named Pipe Version
├── myMore_pipe.c         # Consumer - Named Pipe Version
├── myData_shm.c          # Producer - Shared Memory Version
├── myMore_shm.c          # Consumer - Shared Memory Version
├── test_script.sh        # Automated Compilation and Testing Script
├── web_server_logs.txt   # Sample Web Logs
└── db_server_logs.txt    # Sample DB Logs
