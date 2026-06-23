# OS 速查

## API

- `fork()`：创建子进程。
- `pthread_create`, `pthread_join`：创建/等待线程。
- `pthread_mutex_lock/unlock`：互斥。
- `pthread_cond_wait/signal`：条件变量。
- `sem_init`, `sem_wait`, `sem_post`：信号量。
- `shmget`, `shmat`, `shmdt`, `shmctl`：共享内存。
- `semget`, `semop`, `semctl`：System V 信号量。

## 算法

- 页面置换：FIFO、LRU、CLOCK、Enhanced CLOCK、LFU、MFU。
- 磁盘调度：FCFS、SSTF、SCAN、C-SCAN、LOOK。

## 常见坑

- 子进程继续执行父进程后续代码。
- 条件变量 wait 前后未用 while 检查条件。
- 信号量初值设置错误。
- IPC 资源未清理。
