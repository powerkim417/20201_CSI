# 1. Data Storage

## 1.1 Bits and Their Storage(5~22)

### Bits and Bit Patterns

- Bit: binary digit(0, 1)

  - Arithmetic operation(+ - * /)

  - Logical(boolean) operation

    - 1개 이상의 True/False value를 조작하는 연산
    - AND OR XOR NOT
    - Abstraction 단계 중 Gate Level Design에 사용됨

    <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200318111108504.png" alt="image-20200318111108504" style="zoom:67%;" />

- Bit pattern(010010110....)은 정보를 표현할 떄 사용됨(Ex. 숫자, 문자열, 이미지, 소리 등)

### Gates

- Gate: Boolean operation을 계산하는 장치(True: +5V, False: 0V)
  - 작은 전자회로로 구성
  - 컴퓨터를 구성하는 구성 요소로서 사용
  - VLSI(Very Large Scale Integration), 즉 초 대규모 집적회로에 쓰임
    - CMOS의 N채널 트랜지스터와 P채널 트랜지스터
      - N채널이 그대로이고, P채널은 반대로(끝에 작은 동그라미 붙음)
      - <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200321010119242.png" alt="image-20200321010119242" style="zoom:33%;" />
  - <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200321003106540.png" alt="image-20200321003106540"/>
- 각 게이트의 구조(N채널, P채널로 이루어진)
  - NAND 게이트(N채널 2개, P채널 2개)
    - <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200321010623488.png" alt="image-20200321010623488" style="zoom:80%;" />
    - out으로 5V가 전달되면 1, 0V가 전달되면 0
    - in이 각각 1,0인 경우는 위가 병렬이라 5V는 전달되고, 아래는 직렬이라 0V는 전달이 안되므로 결과적으로 5V가 전달되어 1
  - NOR 게이트(N채널 2개, P채널 2개)
    - <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200321010727997.png" alt="image-20200321010727997" style="zoom:80%;" />
    - NAND 게이트와 반대로 이해하면 됨. 둘중 하나라도 1이면 아래 회로가 병렬로 연결되어 0V가 전달됨.
  - NOT 게이트(N채널 1개, P채널 1개)
    - <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200321010000061.png" alt="image-20200321010000061" style="zoom:50%;" />
    - 위가 ON이면(in=0) out이 1이 되고, 아래가 ON이면(in=1) out이 0이 됨

### Flip-flops (Memory Logic)

하나의 bit를 저장할 수 있는, gate로 구성된 circuit

- 간단한 flip-flop의 구조

  <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200323102142956.png" alt="image-20200323102142956" style="zoom: 25%;" />

  - 한 input line은 저장된 값을 1로 set하도록 사용되며, 다른 input line은 저장된 값을 0으로 set(reset)하도록 사용된다.

  - 두 input line이 모두 0인 경우 가장 최근에 저장된 값이 보존된다.

  - 목적이 set 또는 reset이므로 두 input line이 모두 1인 경우는 사용되지 않는다.

  - | I1   | I2   | output                             |
    | ---- | ---- | ---------------------------------- |
    | 0    | 0    | Not changed (Same as stored value) |
    | 0    | 1    | 0 (Reset)                          |
    | 1    | 0    | 1 (Set)                            |
    | 1    | 1    | Not allowed                        |

- RS Flip-flop
  - <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200323102620514.png" alt="image-20200323102620514" style="zoom:67%;" />
  - <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200323103115520.png" alt="image-20200323103115520" style="zoom:67%;" />
  - Q와 Q'는 서로 보수 관계여야 하는데 S=1, R=1 인 경우 Q=Q'=0이 되므로 이는 허용하지 않는다.

### Hexadecimal Notation

- 긴 bit pattern을 짧게 표현할 수 있는 수단

- 해당 pattern을 4bit씩 나누고, 각 4bit를 하나의 문자로 표현

- 16진법

  ![image-20200323103417854](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200323103417854.png)

## 1.2 Main Memory(23~33)

### Main Memory Cells

- Cell: A unit of main memory (일반적으로 8비트(=1바이트))

  - Most significant bit(MSB): memory cell의 가장 왼쪽 비트(high-order end)
  - Least significant bit(LSB): memory cell의 가장 오른쪽 비트(low-order end)

  <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200323103742280.png" alt="image-20200323103742280" style="zoom: 50%;" />

### Main Memory Addresses

- Address: a "name" that uniquely identifies one cell in the computer's main memory

  - 특정 cell에 대한 주소
  - 숫자로 이루어져 있으며, 0에서 시작하여 연속적으로 증가

  <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200323164222642.png" alt="image-20200323164222642" style="zoom: 67%;" />

### Memory Terminology

- Random Access Memory(RAM): Memory in which individual cells can be easily accessed <u>in any order</u>
  - address를 주웠을 때 random한 방법으로 access한다.
- Dynamic RAM(DRAM): RAM composed of volatile memory
  - 시간이 지나면 정보가 날아감
- Synchronous Dynamic RAM(SDRAM)
  - pipeline 방식으로 clock에 동기화하여 access

#### Random Access Memory(RAM)

- Random Access
  - Random의 이점: 모든 location에 대해 access time이 같다.
  - DRAM: <u>Dynamic</u> Random Access Memory
    - **High density**, **low power**, **cheap**, slow
    - Dynamic: 휘발성이 있으므로 데이터를 유지하려면 주기적으로 갱신해야 한다.
    - cell이 간단한 구조라 high density -> 메인 메모리에 자주 사용됨
  - SRAM: <u>Static</u> Random Access Memory
    - Low density, high power, expensive, **fast**
    - Static: 파워가 꺼질 때까지 데이터가 쭉 유지된다.
    - 스스로가 정보를 계속 유지하는 기능이 필요하므로 복잡한 구조의 gate로 이루어진 cell로 설계해서 low density
  - SDRAM
    - (설명 따로 X)

### Measuring Memory Capacity

- Kilobyte = $2^{10}$ bytes = 1,024 bytes
- Megabyte = $2^{20}$ bytes = 1,048,576 bytes
- Gigabyte = $2^{30}$ bytes = 1,073,741,824 bytes

## 1.3 Mass Storage(34~40)

= Secondary storage

- Additional devices의 역할
  - Ex) Magnetic disks, Magnetic tape, CDs, Flash drives, DVDs, Solid-state disks
- Advantages (over Main memory)
  - Less volatility (휘발성이 적음)
  - Larger storage capacities (고용량)
  - Low cost (저렴한 가격)
  - In many cases can be removed (컴퓨터로부터 탈부착 가능)
- Disk storage, CD storage
  - 각 track이 있고, track은 sector들로 이루어짐
  - disk arm이 track을 이동하며 어떤 sector로 가서 특정한 주소값을 sequential 하게 access함
- Flash memory
  - 반도체(silicon dioxide chamber)를 이용한 secondary memory
  - 디지털 카메라, 스마트폰 등에 사용됨
  - SD카드의 경우 몇 GB의 저장소 제공

## 1.4 Representing Information as Bit Patterns(41~55)

## 1.5 The Binary System(56~63)

## 1.6 Storing Integers(64~74)

## 1.7 Storing Fractions(75~81)

## 1.8 Data and Programming(82)

Python Lab 수업에서 다룸

## 1.9 Data Compression(83~88)

## 1.10 Communications Errors(89~93)