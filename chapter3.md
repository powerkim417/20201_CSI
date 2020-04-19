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

#### 4. Real Time OS

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416160028867.png" alt="image-20200416160028867" style="zoom:80%;" /> 

#### 5. Multiprocessor Machine 

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416160205109.png" alt="image-20200416160205109" style="zoom:67%;" /> 



## 3.2 Operating System Architecture(15~30)

## 3.3 Coordinating the Machine's Acitivities(31~35)

## 3.4 Handing Competition Among Processes(36~44)

## 3.5 Security(45~51)