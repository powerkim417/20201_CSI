# 2. Data Manipulation

## 2.1 Computer Architecture(3~11)

![image-20200401102140258](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200401102140258.png) 

### Machine Instruction Types

- **Data transfer(전송)**
  - copy data from one location to another
- **Arithmetic/Logic(연산)**
  - use existing bit patterns to compute a new bit patterns
- **Control(제어)**
  - direct the execution of the program

### Computer Architecture

![image-20200404020052668](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200404020052668.png)

- **Central Processing Unit(CPU)** or processor
  - Arithmetic/Logic unit VS. Control unit
  - Registers
    - General purpose
    - Special purpose
- **Memory**
  - Main memory
  - Second memory
- **Input/Output**
  - Communication with other devices

### Stored Program

- Concept
  - Program은 bit pattern으로 encode될 수 있고, <u>main memory에 저장될 수 있다.</u>
  - CPU는 이 main memory로부터 instruction들을 extract하고 execute할 수 있게 된다.
    - Program이 다음 instruction을 수행하는 것이 반복됨
  
- Von Neumann Machine(= Stored Program Computer)
  - Stored Program의 concept을 Von Neumann이 1945년에 처음으로 제안함

    - = EDVAC

  - Basic Model(아래 3가지를 갖춘 최초의 stored program computer)

    - Memory
    - Processing Unit
    - Control Unit

  - 그림

    <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200407214606982.png" alt="image-20200407214606982" style="zoom: 33%;" /> 

    - <u>Instruction data와 program data가 같은 memory(memory unit)에 저장되어 있다.</u>
      - <u>이러한 설계는 현재까지도 사용되고 있음!</u>

## 2.2 Machine Language(12~34)

### Terminology

- Machine instruction: an instruction (or command) encoded as a <u>bit pattern</u> recognizable by the CPU
- Machine language: <u>the set of all instructions</u> recognized by a machine

### Machine Language Philosophies

|                    |           RISC(Reduced Instruction Set Computing)            |           CISC(Complex Instruction Set Computing)            |
| :----------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|  Instruction Type  |                            Simple                            |                           Complex                            |
| \# of Instruction  |                        Reduced(30~40)                        |                  Complex, Extended(100~200)                  |
| Instruction Format |                            Fixed                             |                           Variable                           |
|    Address Mode    |                            Simple                            |                           Complex                            |
|   Complexity(r)    | Compiler의 설계가 잘 되어야 함(Smart Compiler)<br />Simple Decoding Logic<br />Software가 복잡한 구조 | Complicated Decoding Modules<br />Complicated H/W Decoding Logic<br />Hardware가 복잡한 구조 |

![image-20200407222142275](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200407222142275.png)

- Instruction Decoding Model
  - RISC: simple decoding logic이 쓰이므로 상대적으로 면적이 더 작다.
  - CISC: Conversion, Instruction 등을 거치므로 더 많은 면적이 필요
- Cache memory
  - RISC: 여유 공간이 많아 cache memory의 공간이 넓음
    - 대부분의 instruction을 cache에 넣고 수행하여 off-chip communication(chip 외부에서의 통신)을 reduce할 수 있음
  - CISC: cache memory의 공간이 작음(on-chip cache)
    - cache의 공간이 좁아 memory miss가 발생하므로 off-chip memory에서 데이터를 다시 가져옴(off-chip communication 증가)

#### 정리

- RISC
  - Good Performance
  - Faster Operation
- CISC
  - Slower Operation

### CPU and Main Memory

- 일반적인 구조

  ![image-20200404020424455](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200404020424455.png)

  - CPU: ALU, Control Unit, Registers
  - Main Memory: Instruction data, Programming data
  - Bus: CPU가 memory에서 데이터를 읽어오고, memory로 데이터를 기록할때 사용

- 자세한 내부 구조

  ![image-20200406105043404](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200406105043404.png)

  - Register: 
    - 16 **General purposed register**
      - 사용자가 program을 통해 data를 이동하는 것을 볼 수 있음
      - program을 execution할 때 instruction과 같은 data를 저장
      - 16개의 register(0~F)
      - 각 register는 1byte(8bits) 크기
    - Special register
      - 일반 user는 사용하지 못함
      - CPU 내부적으로 사용하는 register
      - **PC(Program counter)**
        - ==Indicate <u>next</u> address (of main memory) to fetch==
        - 다음에 접근해서 가져와야 할 memory의 주소
        - 8bits
          - Memory location이 256개이므로 이를 나타내기 위해!
      - **IR(Instruction register)**
        - 현재 실행 중인 machine instruction을 저장
        - 16bits
          - 각 Machine instruction의 크기가 2byte(16bit) 이므로
          - OP code(4 bits) + Operand field(12 bits)
  - Main memory
    - Instruction과 data를 저장할 수 있는 메모리
    - 256개의 memory location 사용(0~255, 00000000~11111111, 00~FF)
      - 이 주소가 Program Counter에 들어간다.
    - 각 cell은 1byte(8bits) 크기

### Machine Instruction

Instruction Encoding: 명령 → 명령어

#### Machine Instruction Format

- 각 Machine instruction은 2byte(16bit) 크기

- 12개의 instruction 사용(OP code가 0~C까지)

- Op-code와 Operand로 나뉨

  ![image-20200409015617239](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200409015617239.png) 

  - Op-code (4 bits)
    - Specifies <u>which operation</u> to execute
    - Hexadecimal notation
  - Operand (12 bits)
    - Gives more detailed information about the operation
    - 4bit씩 끊어서 3개의 hexadecimal digit이 된다.
    - 이러한 operand에 대한 interpretation은 op-code에 따라 달라진다.
      - 일반적으로 R, S, T는 Register를 의미하고, X, Y는 Hexadecimal digit을 의미한다.

#### Simple Machine Language Instruction

| OP Code<br />(Hexadecimal) | Operand | Meaning |        Description         |
| :------------------------: | :-----: | :-----: | :------------------------: |
|             1              |   RXY   |  LOAD   |         R ← M[XY]          |
|             2              |   RXY   |  LOAD   | R ← XY (No memory Access)  |
|             3              |   RXY   |  STORE  |         R → M[XY]          |
|             4              |   0RS   |  MOVE   |           R → S            |
|             5              |   RST   |   ADD   |         R ← S + T          |
|             6              |   RST   |  ADDF   |     R ← S + T (Float)      |
|             7              |   RST   |   OR    |         R ← S OR T         |
|             8              |   RST   |   AND   |        R ← S AND T         |
|             9              |   RST   |   XOR   |        R ← S XOR T         |
|             A              |   R0X   | ROTATE  | Rotate R 'X bits' to right |
|             B              |   RXY   |   JMP   |   if (R==0) then PC ← XY   |
|             C              |   000   |  HALT   |            Stop            |

- OP Code 5와 6의 경우 각각 레지스터 S와 T의 값을 정수와 실수로 다르게 해석하므로 같은 값이 저장되어 있어도 연산에 사용되는 수의 실제 값이 다르다.

- ![image-20200409024124307](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200409024124307.png) 

- Instruction Category

  - Data transfer, Arithmetic/Logic, Control의 3가지 type 존재
  - OP R X Y
    - Data Transfer(**Load**, **Store**), Control(**Jump**)
  - OP 0 R S
    - Data Transfer(**Move**)
  - OP R S T
    - Arithmetic/Logic operation(**ADD**, **AND**, **OR**, **XOR**)
  - OP R 0 X
    - Arithmetic/Logic operation(**Rotate**)
  - C 0 0 0
    - Control(**Halt**)

- 예시

  - Decoding (the instruction "35A7")

    - R5의 값을 M[A7]에 저장

  - Decoding (the instruction "B258")

    - B: JMP
      - 가리키는 register의 값이 0일 때 PC의 값을 바꿈
    - 2: Register 2
    - 58: PC의 값을 58로
    - 즉, 이 instruction이 실행될 때 R2의 값이 0이면 PC의 값을 58(hexanumber)로 바꾼다.

  - Encoding (메모리에 저장된 두 값을 더한 뒤 저장하기)

    1. Get one of the values to be added from memory and place it in a register.
       - Ex) **156C**: M[6C]의 값을 R5로 불러옴 **R5 ← M[6C]**
    2. Get the other value to be added from memory and place it in another register.
       - Ex) **166D**: M[6D]의 값을 R6로 불러옴 **R5 ← M[6D]**
    3. Activate the addition circuitry with the registers used in Steps 1 and 2 as inputs and another register designated to hold the result.
       - Ex) **5056**: R5와 R6에 있는 값(정수)을 더해 R0에 저장 **R0 ← R5 + R6**
    4. Store the result in memory.
       - Ex) **306E**: R0의 값을 M[6E]에 저장 **R0 → M[6E]**
    5. Stop.
       - **C000**: **Halt**

    즉, Machine Language로 "A+B → C"를 표현한 방법중의 하나로 "156C 166D 5056 306E C000" 가 있다.

- 예제(Translate each of them into machine language.)

  - Load register number 3 with the hexadecimal value 56: 2356
  - ROTATE register number 5 three bits to the right: A503
  - AND the contents of register A with the contents of register 5 and leave the result in register 0: 80A5

### 요약

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416022851056.png" alt="image-20200416022851056" style="zoom:80%;" />

## 2.3 Program Execution(35~53)

- Controlled by 2 special-purpose registers(PC, IR)
  - Program Counter: <u>address of **next** instruction</u> to fetch
    - **다음번에** 시행할 instruction의 주소를 저장
  - Instruction Register: <u>**current** instruction</u> to be executed
    - **현재** instruction 저장

### Machine Cycle

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416010514576.png" alt="image-20200416010514576" style="zoom:67%;" />



1. **Fetch**
   - Memory로부터 (PC에서 가리키는) next instruction을 IR로 불러옴
   - PC의 값을 증가시킴(+2)
     - +2인 이유: 한 cell에는 1byte가 들어있는데 instruction의 크기는 2byte이므로
2. **Decode**
   - IR에 있는 bit pattern을 decode
3. **Execute**
   - IR의 instruction이 의미하는 action을 수행

### 예시

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416022316992.png" alt="image-20200416022316992" style="zoom:50%;" /> 

##### 0. Ready For execution

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416021625417.png" alt="image-20200416021625417" style="zoom:50%;" /> 

- PC의 값이 A0로, 첫 instruction이 실행되기 전 모습

##### 1-1. Fetch

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416021707468.png" alt="image-20200416021707468" style="zoom:50%;" /> 

- PC에서 가리키는 'A0'의 명령어(156C)를 가져와서 IR에 저장
  - IR: 156C
- PC의 값이 증가
  - PC: A2

##### 1-2. Decode

- IR의 bit pattern을 decode
  - 156C: "M[6C]의 값을 R5로 불러옴"

##### 1-3. Execution

- instruction의 내용 실행
  - R5 ← M[6C]

##### 2-1. Fetch

- PC에서 가리키는 'A2'의 명령어(166D)를 가져와서 IR에 저장
  - IR: 166D
- PC의 값이 증가
  - PC: A4

##### 2-2. Decode

- IR의 bit pattern을 decode
  - 166D: "M[6D]의 값을 R6로 불러옴"

##### 2-3. Execution

- instruction의 내용 실행
  - R6 ← M[6D]

##### 3-1. Fetch

- PC에서 가리키는 'A4'의 명령어(5056)를 가져와서 IR에 저장
  - IR: 5056
- PC의 값이 증가
  - PC: A6

##### 3-2. Decode

- IR의 bit pattern을 decode
  - 5056: "R5와 R6에 있는 값(정수)을 더해 R0에 저장"

##### 3-3. Execution

- instruction의 내용 실행
  - R0 ← R5 + R6

##### 4-1. Fetch

- PC에서 가리키는 'A6'의 명령어(306E)를 가져와서 IR에 저장
  - IR: 306E
- PC의 값이 증가
  - PC: A8

##### 4-2. Decode

- IR의 bit pattern을 decode
  - 306E: "R0의 값을 M[6E]에 저장"

##### 4-3. Execution

- instruction의 내용 실행
  - R0 → M[6E]

##### 5-1. Fetch

- PC에서 가리키는 'A8'의 명령어(C000)를 가져와서 IR에 저장
  - IR: C000
- PC의 값이 증가
  - PC: AA

##### 5-2. Decode

- IR의 bit pattern을 decode
  - C000: "프로그램 종료"

##### 5-3. Execution

- instruction의 내용 실행
  - Halt

### 요약

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416022906350.png" alt="image-20200416022906350" style="zoom:80%;" />



## 2.4 Arithmetic/Logic Instructions(54~56)

Logic, Rotate/Shift, Arithmetic

- Logic: AND, OR, XOR

  - Masking에 주로 사용

- Rotate/Shift: Circular shift, Logical shift, Arithmetic shift

  - Ex) Rotating the bit pattern 65(hex) one bit to the right

    <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416024746699.png" alt="image-20200416024746699" style="zoom: 50%;" /> 

    - Rotate right의 경우 bit들이 오른쪽으로 한 칸씩 이동
    - 0110 010'1'의 가장 오른쪽 bit 1의 경우 한 바퀴 돌아 가장 왼쪽으로 들어감
    - '1'011 0010 = B2

- Arithmetic: Add, Subtract, Multiply, Divide

  - 값을 2's complement로 encode할 지 floating-point로 encoding할 지에 따라 결과가 달라짐

## 2.5 Communicating with Other Devices(57~68)

### Terms

<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416030312888.png" alt="image-20200416030312888" style="zoom: 50%;" />

- **Controller**: An intermediary apparatus that handles communication between the computer and a device
  - computer와 device 사이에서 통신을 관리하는 중간 기기
  - Specialized controller: device의 type에 따라 다름
  - General purpose controller: 범용(e.g., USB, FireWire)
- **Port**: The point at which a device connects to a computer
  - device가 computer에 연결한 지점
- **Memory-mapped I/O**: CPU communicates with peripheral devices as though they were memory cells ($\leftrightarrow$DMA)
  - CPU가 주변기기(I/O)와 통신할 때, 주변기기와 memory의 address space를 분리하지 않고 하나의 memory space에 취급하여 배치
  - 즉, 전체 memory의 address space에 주변기기의 memory나 register를 memory로 취급하여 전체 memory의 일부분으로 특정영역에 할당하여 배치
  - <u>Main memory의 일부 address를 주변기기에 할당하는 방법!</u>
  - <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200416030340241.png" alt="image-20200416030340241" style="zoom: 67%;" /> 
- **Direct Memory Access(DMA)**: Main memory access by a controller over the bus ($\leftrightarrow$Memory-mapped I/O)
  - ==<u>CPU의 개입 없이</u>== 주변기기가 memory에 직접 접근하는 방식!
- **Von Neumann Bottleneck**: Insufficient bus speed impedes performance
  - "bus의 bottleneck에 의해 성능이 저하될 수 있다"
- ~~**Handshaking**: The process of coordinating the transfer of data between components~~
- **Parallel Communication**: Several communication paths transfer bits simultaneously ($\leftrightarrow$Serial Communication)
  - 여러 communication path에서 data를 동시에 전송
- **Serial Communication**: Bits are transferred one after the other over a single communication path ($\leftrightarrow$Parallel Communication)
  - 하나의 communication path를 통해 serial하게 전송

### Data Communication Rates

- Measurement units
  - Bps: bits per second
  - Kbps: Kilo-bps (1,000 bps)
  - Mbps: Mega-bps (1,000,000 bps)
  - Gbps: Giga-bps (1,000,000,000 bps)
- Bandwidth: Maximum available rate

### 예시

- Apple이 NFC(Near Field Communication) 기술을 특허냄
  - 휴대폰으로 교통카드, 문 잠금 해제 등의 기능 수행
  - CPU와 Memory의 기능 활용

## ~~2.6 Programming Data Manipulating(69~78)~~

## ~~2.7 Other Architecture(79~80)~~
