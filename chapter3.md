# 3. Operating Systems

![image-20200416153501183](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416153501183.png)

## 3.1 The History of Operating Systems(4~14)

### Operating System

OS: A program that acts as <u>intermediate between user and hardware</u>

- OS가 관리하는 서비스
  - Program develop
  - Program execution
  - Access I/O device
  - File system access
  - Error detection & response

- Functions of Operating Systems
  - Oversee operation of computer
    - 컴퓨터의 동작을 모니터한다
  - Store and retrieve files
    - 파일 시스템 관리
  - Schedule programs for execution
    - 프로그램 실행 스케줄링
  - Coordinate the execution of programs
    - 프로그램 실행 관리
- Example of Operating System
  - MS Window
  - Unix Domain
    - Unix
    - Apple: Mac OS
    - Sun Micro(Oracle): Solaris
  - LINUX (Real-time 쪽에서 사용)
  - Smart Phone OS
    - Android OS: open source for smart phone
    - iOS: Apple phone OS

### Evolution of Shared Computing

Batch Processing → Interactive Processing → Time Sharing → Real Time OS → Multiprocessor Machine

#### 1. Batch Processing

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416155856221.png" alt="image-20200416155856221" style="zoom: 67%;" />  

- Collecting jobs in a single( or multiple) batch and then execute them **without further interaction** with the user

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416160621986.png" alt="image-20200416160621986" style="zoom:50%;" /> 

- 순서
  - 각 User가 자신의 job을 수행하려 하며, job들은 operator로 모임
  - Operator는 job들을 모아 순서를 정함
  - OS는 Batch 부분을 관리하는 special program을 가지고 있는데 순서를 정하고 batch를 통해 computer로 job을 보내 수행 → **Batch Processing**
- 특징
  - User와 Computer 사이의 direct interaction이 존재하지 않음
  - CPU가 Batch에서 동작하기 때문에 efficient하게 동작하지 못할 수 있음(Long time delay)
    - 일반적으로 PC에서는 이 방법을 사용할 수 없음(너무 비효율적이라)
- Batch system의 예시
  - Punch card
  - Tape
  - OCR
- Batch Processing의 예시
  - Payroll(직원들의 임금)
  - Utility Bill 관리할 때(Gas, Electricity)

#### 2. Interactive Processing

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416155928742.png" alt="image-20200416155928742" style="zoom:67%;" /> 

- Allows a program being executed to carry on a **dialogue** with the user through remote terminals.
- If OS insisted on executing only one job at a time, only one user would receive satisfactory real-time processing
- Requires real-time processing

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416195048051.png" alt="image-20200416195048051" style="zoom:67%;" /> 

- 각 User들이 다양한 application program을 통해 interactive하게 시스템에 접근
  - Remote Terminal을 통해!
- Multiple user를 상대로 했을 때는 상관없지만, 한번에 하나의 job만 받을 수 있는 경우(One job at a time)에서는 한 명의 user만이 computer system을 사용할 수 있다.(Real-time processing)

#### 3. Time sharing/Multitasking

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416160008490.png" alt="image-20200416160008490" style="zoom:80%;" /> 

- Time sharing: users seeking services from same machine at the same time
  - Implemented by Multiprogramming
- Multiple terminals connected to a same machine
- Multitasking: when multiprogramming is applied to single-user environment

##### Uniprogramming

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416205714463.png" alt="image-20200416205714463" style="zoom:80%;" /> 

- 하나의 프로그램이 run과 wait를 반복

- 시스템 내에 항상 하나의 프로세스만이 존재.
- 다른 프로세스가 생성되려면 현재의 프로세스는 종료되어야 함

##### Multiprogramming

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416210044570.png" alt="image-20200416210044570" style="zoom: 80%;" /> 

-  여러 프로그램이 서로 겹치지 않는 시간 선에서 CPU를 sharing할 수 있다
- Time sharing: 하나의 machine(CPU)에서 동시에 여러 프로그램을 sharing하는 concept

##### Multiprogramming vs. Multitasking

- Multiprogramming: Multiple user가 mutiple terminal을 통해서 same machine에 접근하는 것

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416210704980.png" alt="image-20200416210704980" style="zoom:80%;" /> 

- Multitasking: Single user가 여러 개의 task로 동시에 same machine에 접근하는 것

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416210317670.png" alt="image-20200416210317670" style="zoom:80%;" /> 

##### 정리

- **Time sharing**: Multiple user가 same time에 서비스를 공유하는 것
- **Multiprogramming**: More than one program이 CPU에서 수행되는 것
- **Multitasking**: <u>Single or multiple processor</u>가 multiple task를 concurrent하게 수행하는 것
  - **Multiprocessing**: <u>Multiple processor</u>가 multiple task를 concurrent하게 수행하는 것
    - Time sharing X

#### 4. Multiprocessor Machine

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416160028867.png" alt="image-20200416160028867" style="zoom:80%;" /> 

- Assign **different tasks** to **different processors**</u>
- **Load balancing** and **Scaling tasks** with the number of processors available

- 여러 개의 프로세서 간 load balancing 및 scaling task를 관리하기 위한 operating system이 필요
- Dual core: 1 CPU에 2 processor, Quad core: 1 CPU에 4 processor

##### Terms

- **Job**: user가 어떠한 목적을 가지고 hardware에 assign하는 것
- **Program**: user가 어떠한 job을 수행하기 위해서 만든 instruction의 sequence
- **Task**: program을 수행할 때 operation의 단위
  - 한 프로그램에 I/O, Memory R/W, Arithmetic, ...
- **Process**: Logical block of task
  - Process 1 = {Task 1, Task 2} 이런 식으로 묶임

#### 5. Embedded Systems OS

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416160205109.png" alt="image-20200416160205109" style="zoom:67%;" /> 

- An embedded system is a **special-purpose computer system** designed to perform **one or few dedicated functions**, often with <u>real-time computing constraints.</u>

- Using in Medical devices, Vehicle, home appliance or other hand-held computers.(Ex. VXWOKS, Window CE)

##### Real Time System

- Embedded system to control

- 정의: A system is required to complete its work, and deliver its service on time

- Soft real time system과 Hard real time system으로 분류

  - Soft real time system

    - Tasks are performed <u>as fast as possible</u>
    - Late completion of jobs is <u>undesirable</u>
    - System performance <u>degrades</u> as more as jobs miss deadlines

    $\Rightarrow$ Best effort system(대부분의 OS가 Soft RTS에 해당)

    e.g.) Multimedia, transmission & reception, network, cellular network, website & service, computer game

  - Hard real time system

    - <u>No flexibility</u> in time constraints

    e.g.) Air traffic control, vehicle subsystem control(ABS Brake system control), nuclear power control

### Evolution of OS

- A major OS will evolve over time for a number of reason.
  - Hardware upgrade
  - New type of Hardware
  - New services

1. Single Processing
2. Batch Processing
3. Multiprogramming
4. Multitasking & Multiprocessing
5. Real-time OS

## 3.2 Operating System Architecture(15~30)

### Types of Software

![image-20200427222854318](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200427222854318.png) 

- **Application software**
  - Performs <u>specific tasks for users</u>
- **System software**
  - Provides <u>infrastructure</u> for application software
  - Consists of **operating system** and **utility software**

- **Operating System Components**
  - **User interface**
    - Communicates with users
    - Text based(shell) 또는 Graphical user interface(GUI)
  - **Kernel**
    - Performs basic required functions
    - File manager, device drivers, memory manager, scheduler/dispatcher

![image-20200427223704800](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200427223704800.png)

### User Interface Layer

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200427223824648.png" alt="image-20200427223824648" style="zoom:67%;" />  

- <u>User와 OS kernel을 연결하는 layer</u>
- Text based(**Shell**)
  - Old style interface
  - (e.g.) Microsoft DOS, Unix shell command
    - cd: change directory, del: file delete
- Graphical user interface(**GUI**)
  - File 또는 Program을 icon으로 표현
  - mouse click and action 또는 identifying screen location을 통해 event를 생성
  - (e.g.) Microsoft Window manager(mouse click, screen location, mouse move(click or drag icons on the screen) 등을 판독하는 프로그램), Linux(GNOME, KDE)

### Kernel 

4가지 주요 역할 담당(File Manager / Device Driver / Memory Manager / Scheduler & Dispatcher)

#### File Manager

- Directory (or Folder): A user-created bundle of files and other directories(subdirectories)
  - File은 Mass storage(Secondary memory, 즉 Hard disk, CD ROM, Flash memory, ...)에 저장되어 있음
- Directory Path: A sequence of directories within directories

#### Device Drivers

![image-20200428014210779](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200428014210779.png) 

- Kernel이 다른 주변 기기(e.g., printer, mouse, monitor, ...)와 통신할 수 있도록 하는 소프트웨어
- 이 덕분에 OS는 하드웨어의 작동에 대해 자세히 알 필요가 없음
- OS 또는 kernel이 하드웨어와 통신할 수 있는 common interface를 제공

#### Memory Manager

![image-20200428014618004](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200428014618004.png)

- Main memory에 공간을 할당
- Main memory와 secondary memory 사이에서 프로세스를 관리하는 역할
- Physical Memory
  - Main memory(cache, DRAM)
  - Block이라는 unit으로 관리
- Virtual Memory
  - Secondary memory
  - Page라는 unit으로 관리
- Ex) Process 1, 2, 3, 4가 Secondary memory에 있다고 가정
  - OS가 P1과 P2를 start하면 P1과 P2가 main memory로 불려 온다.
    - 이 경우 Main memory의 크기가 더 작아 그 뒤 프로세스들은 들어올 수가 없음
  - P1이 I/O wait에 들어가게 되면 P1이 main memory에서 사라짐
  - main memory에 공간이 생기면 P3가 들어올 수 있게 됨
  - P1이 I/O로부터 돌아오면 P3이 다시 나가고 P1이 들어오게 된다.
  - 이렇게 main memory와 secondary memory 사이를 오갈 때, <u>프로세스는 page 단위로 옮겨지게 된다.(data is divided into uniformly sized unit called "page")</u>

#### Scheduler and Dispatcher

![image-20200428014646932](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200428014646932.png) 

- **Scheduler**: determines <u>which process</u> are to be considered for execution
- **Dispatcher**: controls the <u>allocation of time</u> to these processes

## 3.3 Coordinating the Machine's Acitivities(31~35)

## 3.4 Handing Competition Among Processes(36~44)

## 3.5 Security(45~51)