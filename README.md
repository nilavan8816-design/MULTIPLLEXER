# EXPERIMENT NO. 4

# SIMULATION AND IMPLEMENTATION OF ADDERS, SUBTRACTORS, MULTIPLEXERS AND DEMULTIPLEXERS – ENCODERS AND DECODERS

### Submitted By

**R.K. Vageesh Ragav**
B.E. Electronics and Communication Engineering (ECE)
Saveetha Engineering College, Chennai

### Course

**EC1801 – Digital Logic Circuits Design Laboratory**

---

## AIM

To design, simulate and verify Adders, Subtractors, Multiplexers, Demultiplexers, Encoders and Decoders using VHDL. This corresponds to Experiment No. 4 in the laboratory manual. 

---

## SOFTWARE REQUIRED

1. Xilinx Vivado / Xilinx ISE
2. ModelSim
3. GHDL (Optional)

---

# THEORY

### Half Adder

A Half Adder adds two binary bits and produces Sum and Carry outputs.

### Full Adder

A Full Adder adds three binary inputs and produces Sum and Carry outputs.

### Half Subtractor

A Half Subtractor performs subtraction of two binary bits and generates Difference and Borrow outputs.

### Full Subtractor

A Full Subtractor subtracts three binary inputs and generates Difference and Borrow outputs.

### Multiplexer

A Multiplexer selects one input from several inputs and forwards it to a single output.

### Demultiplexer

A Demultiplexer transfers one input signal to one of many outputs.

### Encoder

An Encoder converts active input lines into a coded binary output.

### Decoder

A Decoder converts binary information into corresponding output lines.

---

# PROGRAMS

## HALF ADDER

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity half_adder is
    Port(
        A,B : in STD_LOGIC;
        SUM,CARRY : out STD_LOGIC
    );
end half_adder;

architecture Behavioral of half_adder is
begin
    SUM <= A xor B;
    CARRY <= A and B;
end Behavioral;
```

---

## FULL ADDER

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity full_adder is
    Port(
        A,B,Cin : in STD_LOGIC;
        SUM,CARRY : out STD_LOGIC
    );
end full_adder;

architecture Behavioral of full_adder is
begin
    SUM <= A xor B xor Cin;
    CARRY <= (A and B) or (B and Cin) or (A and Cin);
end Behavioral;
```

---

## HALF SUBTRACTOR

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity half_subtractor is
    Port(
        A,B : in STD_LOGIC;
        DIFF,BORROW : out STD_LOGIC
    );
end half_subtractor;

architecture Behavioral of half_subtractor is
begin
    DIFF <= A xor B;
    BORROW <= (not A) and B;
end Behavioral;
```

---

## FULL SUBTRACTOR

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity full_subtractor is
    Port(
        A,B,Bin : in STD_LOGIC;
        DIFF,BORROW : out STD_LOGIC
    );
end full_subtractor;

architecture Behavioral of full_subtractor is
begin
    DIFF <= A xor B xor Bin;
    BORROW <= ((not A) and B) or (B and Bin) or ((not A) and Bin);
end Behavioral;
```

---

## 4:1 MULTIPLEXER

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity mux4to1 is
    Port(
        I0,I1,I2,I3 : in STD_LOGIC;
        S1,S0 : in STD_LOGIC;
        Y : out STD_LOGIC
    );
end mux4to1;

architecture Behavioral of mux4to1 is
begin
    Y <= I0 when S1='0' and S0='0' else
         I1 when S1='0' and S0='1' else
         I2 when S1='1' and S0='0' else
         I3;
end Behavioral;
```

---

## 1:4 DEMULTIPLEXER

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity demux1to4 is
    Port(
        D : in STD_LOGIC;
        S1,S0 : in STD_LOGIC;
        Y0,Y1,Y2,Y3 : out STD_LOGIC
    );
end demux1to4;

architecture Behavioral of demux1to4 is
begin
    Y0 <= D when S1='0' and S0='0' else '0';
    Y1 <= D when S1='0' and S0='1' else '0';
    Y2 <= D when S1='1' and S0='0' else '0';
    Y3 <= D when S1='1' and S0='1' else '0';
end Behavioral;
```

---

## 4:2 ENCODER

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity encoder4to2 is
    Port(
        D : in STD_LOGIC_VECTOR(3 downto 0);
        Y : out STD_LOGIC_VECTOR(1 downto 0)
    );
end encoder4to2;

architecture Behavioral of encoder4to2 is
begin
    Y <= "00" when D="0001" else
         "01" when D="0010" else
         "10" when D="0100" else
         "11" when D="1000" else
         "00";
end Behavioral;
```

---

## 2:4 DECODER

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity decoder2to4 is
    Port(
        A,B : in STD_LOGIC;
        Y : out STD_LOGIC_VECTOR(3 downto 0)
    );
end decoder2to4;

architecture Behavioral of decoder2to4 is
begin
    Y(0) <= (not A) and (not B);
    Y(1) <= (not A) and B;
    Y(2) <= A and (not B);
    Y(3) <= A and B;
end Behavioral;
```

---

# OUTPUT

Simulation waveforms verify the correct operation of:

* Half Adder
* Full Adder
* Half Subtractor
* Full Subtractor
* 4:1 Multiplexer
* 1:4 Demultiplexer
* 4:2 Encoder
* 2:4 Decoder

*(Insert waveform screenshots here)*

---

# RESULT

Thus, the Adders, Subtractors, Multiplexer, Demultiplexer, Encoder and Decoder circuits were designed using VHDL and their functionality was successfully verified through simulation. This corresponds to the combinational circuits experiment in the laboratory manual. 

---

# AUTHOR DETAILS

**Name:** R.K. Vageesh Ragav
**Department:** Electronics and Communication Engineering (ECE)
**College:** Saveetha Engineering College
**Course Code:** EC1801 – Digital Logic Circuits Design Laboratory
**Experiment No.:** 4

---

# REPOSITORY STRUCTURE

```text
EXP-04-Adders-Subtractors-MUX-DEMUX-Encoder-Decoder/
│
├── README.md
├── half_adder.vhd
├── full_adder.vhd
├── half_subtractor.vhd
├── full_subtractor.vhd
├── mux4to1.vhd
├── demux1to4.vhd
├── encoder4to2.vhd
├── decoder2to4.vhd
├── testbench.vhd
└── waveform.png
```
