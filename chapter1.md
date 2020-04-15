# Data Storage

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
  - ~~SDRAM~~

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

### Representing Text

각 character(letter, punctuation, etc.)는 unique한 bit pattern에 할당된다.

- ASCII
  - 영어만으로는 7bit의 패턴으로 표현이 가능하나, ISO에서 8bit로 확장하여 더 많은 언어를 담을 수 있게 됨
  - 그러나 점점 더 많은 언어에 대한 표현이 필요해지고 있으며, 8bit로는 부족하게 됨
    - 이를 보완할 수 있는 것이 unicode
- Unicode
  - 21-bits: represent the symbols used in languages <u>world wide</u>
  - 16-bits: represent the symbols used in world's <u>commonly used</u> languages
  - Ex) "Hello."를 ASCII 또는 UTF-8 encoding으로 표현![image-20200331015852232](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200331015852232.png)
    - H(48) e(65) l(6C) l(6C) o(6F) .(2E) $\to$ 48656C6C6F2E

### Representing Numeric Values

- Binary notation: bit를 사용해 2진법(base 2)으로 표현
- Limitations of computer representations of numeric values
  - Overflow: 표현할 수 있는 숫자의 범위를 벗어나는 경우(too big?)
  - Truncation: 숫자의 값이 정확하게 표현되지 못하는 경우

### Representing Images

![image-20200331022538670](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200331022538670.png)

- 한 pixel은 3개의 색깔이 각각 8bit(00~FF)씩 표현되어 24bit

- 256종류의 색~~(이건 8비트로 RGB가 각각 3,3,2bit 할당됐을때..)~~

- Image representing techniques

  <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200331023429402.png" alt="image-20200331023429402" style="zoom: 50%;" />

  <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200331023703324.png" alt="image-20200331023703324" style="zoom:50%;" />

  - Bitmap techniques

    - Pixel: "picture element"

    - RGB

    - 확대했을 때 noise 발생

      <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200331023744671.png" alt="image-20200331023744671" style="zoom:33%;" />

    - 확장자: bmp, eps, gif, jpg, pdf, psd, tiff, png

  - Vector techniques

    - Shape에 대한 equation으로 그림, 시작점과 끝점이 주어지고 이에 대한 edge를 그려 표현

      <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200331023858640.png" alt="image-20200331023858640" style="zoom: 50%;" />
      - 확대 및 축소 시 깨끗한 이미지
      - bitmap에 비해 scalable하다는 장점

    - TrueType, PostScript 표준

    - 확장자: eps, pdf, ai, svg

### Representing Sound

- sound는 analog인데, 이를 digital로 나타내야 하므로 sampling 과정이 필요하다

  <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200331025425217.png" alt="image-20200331025425217" style="zoom:67%;" />

- Digital audio signal을 듣게 되는 과정

  ![image-20200331025524808](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200331025524808.png)

- Sampling techniques: MIDI, Digital Audio
  
  - 음악을 만들 때 MIDI를 사용하는 것이 더 analog에 근접한 신호를 재생할 수 있다. (High quality recordings)

|                   MIDI                    |               Digital Audio               |
| :---------------------------------------: | :---------------------------------------: |
| 실제 audio를 기록(Vector graphics와 유사) | Musical score를 기록(Bitmap image와 유사) |
|             Device-dependent              |            Device-independent             |
|               Smaller size                |                Larger size                |

## 1.5 The Binary System(56~63)

2진법 기반

- 양의 정수를 2진법으로 표현하는 알고리즘

  1. 숫자를 2로 나누고, 그 나머지를 기록한다.

  2. 몫이 0이 아니라면, 그 몫을 또 다시 2로 나누고 나머지를 기록한다.

  3. 몫이 0이 되면, 기록한 나머지들을 오른쪽에서 왼쪽으로 순서대로 나열한 값이 2진법 표현이 된다.

     <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200325102004034.png" alt="image-20200325102004034" style="zoom:50%;" />

- 분수도 표현 가능

  - Ex) 101.101 $\to 4+1+{1\over2}+{1\over8}$

## 1.6 Storing Integers(64~74)

- Two's complement notation, Excess notation의 방법이 있으며, 둘 다 overflow error가 발생할 수 있다.

### Two's complement notation(2의 보수)

- 정수를 나타내는 가장 보편적인 방법

  <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200325171814677.png" alt="image-20200325171814677" style="zoom:80%;" />

- 음의 정수(-6)를 2의 보수로 나타내는 방법

  1. <u>절대값(6)</u>의 2진수 형태에서 1이 처음으로 복사될 때까지 오른쪽 값부터 그대로 복사한다. 

  2. 그 이후 비트는 반대로 복사한다.

     <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200325103814071.png" alt="image-20200325103814071" style="zoom: 80%;" />

- 2의 보수끼리 negate(부호 전환)하는 방법(x $\to$ -x)

  - 모든 비트를 invert하고 1을 더한다.

- Addition & Subtraction 예시

  - 일반적인 예시
    - 0111(7) + 1110(-2) = 1 0101(5)
    - 0111(7) - 1110(-2) = 1001(9$\equiv$-7) (overflow)
      - 4비트가 16개 숫자를 나타낼 수 있으므로 -8~7을 벗어난 숫자인 9는 -16을 뺀 -7과 같게 표현된다.
  - 음수의 덧셈을 이용하여 뺄셈 연산
    - 7 - 6 = 7 + (-6) = 0111(7) + 1010(-6) = 1 0001(1)
  - 오버플로우(result too large for finite computer word)
    - n비트 숫자 2개를 더한다고 꼭 결과가 n비트 숫자로 표현되는 것은 아님
    - 0111(7) + 0001(1) = 1000(8이어야 하는데.. -8)
    - carry가 넘친다는 뜻은 아님!

- Detecting overflow

  - 양수와 음수를 더하는 경우는 오버플로우가 발생하지 않음
  - 비슷한 원리로, 같은 부호의 숫자를 빼는 경우도 오버플로우가 발생하지 않음
  - 오버플로우가 발생하는 경우
    - (양수) + (양수) = (음수), 7 + 2 = -7
    - (음수) + (음수) = (양수), (-4) + (-5) = 7 
    - (양수) - (음수) = (음수), 7 - (-2) = -7
    - (음수) - (양수) = (양수), (-4) - 5 = 7

### Possible Representations

- | Decimal | Unsigned | Sign Magnitude | 1's Complement | 2's Complement | Excess four(3-bit excess code) |
  | ------- | -------- | -------------- | -------------- | -------------- | ------------------------------ |
  | 7       | 111      |                |                |                |                                |
  | 6       | 110      |                |                |                |                                |
  | 5       | 101      |                |                |                |                                |
  | 4       | 100      |                |                |                |                                |
  | 3       | 011      | 011            | 011            | 001            | 111                            |
  | 2       | 010      | 010            | 010            | 010            | 110                            |
  | 1       | 001      | 001            | 001            | 001            | 101                            |
  | 0       | 000      | 000            | 000            | 000            | 100                            |
  | -0      |          | 100            | 111            | 000            | 100                            |
  | -1      |          | 101            | 110            | 111            | 001                            |
  | -2      |          | 110            | 101            | 110            | 010                            |
  | -3      |          | 111            | 100            | 101            | 001                            |
  | -4      |          |                |                | 100            | 000                            |

- Unsigned

  - 범위: 0 ~ 7 (8가지)
  - MSB가 sign과 관련이 없음

- Sign Magnitude

  - 범위: -3 ~ 3 (7가지)
  - MSB 외의 bit는 크기를 표현하고, MSB로 sign을 나타냄
  - balance

- 1's Complement
  - 범위: -3 ~ 3 (7가지)
  - 음수의 경우 양수의 bit를 모두 뒤집어 나타냄
  - number of zeros
- 2's Complement
  - 범위: -4 ~ 3 (8가지)
  - 음수의 경우 양수의 bit를 모두 뒤집고, 1을 더해 나타냄
  - ease of operations
  - CPU, ALU, Design에서 사용
- Excess four
  - 범위: -4 ~ 3 (8가지)
  - Unsigned 표현에서 4를 뺀 값을 가짐
    - 반대로, 의미하는 값에서 4를 더한 만큼 표현(Excess 4, <Bias 4>)
  - CPU, ALU, Design에서 사용
  - Excess eight의 경우 -8 ~ 7 (16가지)의 범위를 가지며, unsigned 표현에서 8을 뺀 값을 가짐

## 1.7 Storing Fractions(75~81)

Floating-point notation: Sign bit, Mantissa(가수) field, Exponent(지수) field로 이루어짐

### Normalized form

$\pm d_0.d_1d_2...d_i \times10^n (d_0\neq0)$

- 실수를 표현하는 방법(매우 작거나 매우 큰 숫자 포함)
- 소수점 왼쪽에는 1~9 사이의 정수 하나만 오도록 맞춘 표현이 normalized form
- Binary에서는 $\pm 1.xxxxxx_2\times2^{yyyy}$ 형태

- 1byte(8bit) storage에 floating point를 저장할 때
  - <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200327013423327.png" alt="image-20200327013423327" style="zoom: 25%;" />
  - Exponent에는 지수의 3-bit excess code(excess 4 code)를 넣고,
  - Mantissa에는 해당 수를 $0.1abcd..\times2^y$ 꼴로 표현했을 때 "1abc"를 저장한다.
    - 정수부분이 0이고, 소수 첫째자리가 1이 오도록 하는 형태로 맞추기
    - Mantissa field의 크기는 4bit 이므로 4자리를 넘는 부분은 truncate한다.
  - Ex) Decode 10111100
    - Sign = - (음수)
    - Exponent = 011 $\to$ -1
    - Mantissa = 1100 $\to$ 0.11
    - $-0.11\times2^{-1} = -0.011 = -{3\over8}$
  - Ex) Encode $1{1\over8}$
    - $1 {1\over8} = 1.001 = 0.1001\times2^1$
    - Sign = 0
    - Exponent = 1 $\to$ 101
    - Mantissa = 1001
    - 01011001

#### Truncation error(Round off error)

- Ex) $2 {5\over8}$을 저장할 때

  - $2 {5\over8} = 10.101 = 0.10101\times2^2$
  - Sign = 0
  - Exponent = 2 $\to$ 110 (3-bit excess code)
  - Mantissa = 1010 (이후의 bit들은 truncate됨)

  <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200327014508171.png" alt="image-20200327014508171" style="zoom: 67%;" />

  - 여기서 누락되는 1은 Lost bit이라고 하며, ROE(Round off error), Truncation error라고도 한다.
  - 결국 storage에는 01101010 이 저장되며, 이를 decode하면 $2{1\over2}$가 된다.
    - "1bit에 대한 Round off error가 발생하였다"

### Floating Point Standard

- IEEE standard 754-1985
  - 1985년에 비로소 Floating Point에 대한 표현 방식의 표준이 정의됨
- Two representations
  - Single precision (32-bit)
  - Double precision (64-bit)
- Format
  - ![image-20200327022209976](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200327022209976.png)
  - Mantissa에 올 값으로 1+Fraction을 사용
    - 즉, 0.xxxx 형태가 아니고 1.xxxx 형태로 변환해야 함(1을 hidden bit이라 부름)
  - Exponent는 excess representation을 사용
    - 실제 지수에 Bias를 더한 값이 저장됨
    - Bias는 single precision일 때 127, double precision일 때 1203

## ~~1.8 Data and Programming(82)~~

## 1.9 Data Compression(83~88)

데이터를 압축하는 알고리즘

- Lossy VS. lossless
  - Lossy는 데이터의 압축 후 해제 시 데이터의 손실이 일어나는 경우
  - Lossless는 데이터의 압축 후 해제 시에도 데이터가 손실되지 않는 경우

### Lossless

- Run-length encoding

  - 데이터와, 이 데이터가 반복되는 횟수를 기록
  - <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200331234208704.png" alt="image-20200331234208704" style="zoom:50%;" />

- Frequency-dependent encoding(=Huffman code)

  - 각 symbol의 <u>frequency</u>를 이용해 variable rate prefix code를 만듦
    - <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200331234420285.png" alt="image-20200331234420285" style="zoom: 80%;" />
      - 각 symbol은 binary string에 매핑됨
        - 예시에서는 A=0, B=10, C=111, D=110
      - 더 자주 등장하는 symbol이 더 짧은 code를 갖도록
        - 예시에서는 A가 가장 자주 사용되는듯
        - 영어에서는 e, t, a, i가 frequency가 높아 더 짧은 code를 가지고, z, q, x가 frequency가 낮아 더 긴 code를 갖게 됨
      - 어떤 code도 다른 code의 prefix가 되면 안됨

- ~~Relative encoding~~

- Dictionary encoding(=LZW Encoding)

  - Dictionary containing the Basic Blocks from which the message is constructed but <u>as larger units</u> are found in the message.

    - 가급적이면 큰 덩어리를 코드화 시키는 방식?

  - Ex 1)

    ![image-20200401004532656](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200401004532656.png)

    - Encoding
      1. 처음 4개의 문자를 통해 X=1, Y=2, _(blank)=3 으로 table이 채워짐
      2. <u>Blank가 등장하면 그 전의 덩어리를 larger unit으로 계산함</u>
         - XYX = 4
      3. 그러면 이후의 XYX들은 모두 4로 encoding된다.
      4. 121343434
    - Decoding
      1. encode된 메시지와 table을 토대로 decode한다.
      2. XYX_XYX_XYX_XYX(**same as original input string**)

  - Ex 2)

    ![image-20200401005150186](C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200401005150186.png)

### Lossy

data가 약간의 손실이 있어도 정보를 전달하는 데 문제가 없을 때 사용하는 기법

Ex) Multimedia, audio, graphics, ...

- Compressing Images
  - GIF: cartoon
  - JPEG: photograph
  - TIFF: image archiving
- Compressing Audio and video
  - MPEG(Motion Picture Experts Group)
    - High-Definition TV broadcasting
    - Video conferencing
  - MP3(within MPEG)
    - Take advantage of the property of the human ear, removing these details that human ear cannot perceive
      - 사람의 귀에서 구분하지 못할 정도의 선에서 data를 remove하여 optimize

## 1.10 Communications Errors(89~93)

### Error Detecting

- Parity bits(even VS. odd)
  - Ex) ASCII(8 bits) codes에서의 odd parity
    - pattern에 <u>총 홀수 개의 1</u>이 들어있도록 parity bit(가장 왼쪽)를 set<img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200330103107395.png" alt="image-20200330103107395" style="zoom: 33%;" />
    - ASCII code로 'A'는 01000001로, 짝수 개의 1이 있으므로 parity bit를 1로 설정해 전체 pattern이 101000001이 된다.
    - ASCII code로 'F'는 01000110로, 홀수 개의 1이 있으므로 parity bit를 0으로 설정해 전체 pattern이 001000110이 된다.
- ~~Checkbytes~~

### Error Correcting

detection of errors + reconstruction of the original error-free data

- Hamming code(error-correcting code)

  - <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200330103416990.png" alt="image-20200330103416990" style="zoom: 25%;" />

  - Any 2 patterns are separated by a Hamming Distance of at least 3

    - hamming distance가 최소 3이 되도록 설계해야 함
      - Hamming distance: 각 위치의 bit를 비교했을 때 서로 다른 위치의 갯수
    - A와 B의 hamming distance는 4, A와 C의 hamming distance는 3, D와 E의 hamming distance는 4, ...

  - Ex) Pattern "010100"을 수신한 경우

    <img src="C:\Users\KJH\AppData\Roaming\Typora\typora-user-images\image-20200401011123644.png" alt="image-20200401011123644" style="zoom:67%;" />

    - 일단 010100은 illegal pattern. 즉, error detected
    - Original pattern을 찾기 위해 각 character들과의 hamming distance를 모두 비교하고, 가장 distance가 작은 character를 찾는다. (그 character가 original pattern일 가능성이 가장 높으므로)
    - D의 hamming distance가 가장 짧으므로 수신한 pattern "010100"은 "011100"(D)로 correction할 수 있다.