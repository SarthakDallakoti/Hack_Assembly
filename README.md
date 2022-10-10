# Hack_Assembly


# 1. Produce an HDL file that contains the design of a circuit that implements the fol- lowing description.

The circuit should implement a parallel to serial converter. The circuit should store an 8-bit binary value from the 8-bit wide input bus called indata when the load input is asserted (has value 1). When the enable input is asserted (has the value 1) then the circuit, over the next 8 clock cycles, should output each of the bits of the stored 8-bit binary value, from bit 0 to bit 7, sequentially via sout. When the circuit has completed the transmission of the 8 bits then the complete output should be asserted (set to value 1) for 1 clock cycle.
The chip should have the following preamble.
  CHIP cw2 {
      IN indata[8], enable, load;
      OUT sout, complete;
PARTS: }


# 2. 
Write a program in HACK assembly, without using symbols, that computes the bitwise exclusive or (XOR) of the values stored in RAM[1] and the value of the memory location with address stored in RAM[2]. The result of the computation should be stored in RAM[0].
You can think of RAM[2] as being a pointer to where the second operand of the XOR is stored.


# 3. 
Write a program in HACK assembly, without using symbols, that sums the consec- utive set of memory locations starting from the memory address stored in RAM[1] up to, but not including, the memory address RAM[1] + RAM[2]. The result of the computation should be stored in RAM[0]. Note, you need not consider the case of an overflow.
You can think of RAM[1] as being a pointer to an array of numbers, and RAM[2] as being the length of the array you are summing over.


# 4. 
The Feistel cipher is a symmetric block cipher encryption framework which is the basis of many modern day encryption algorithms. In this coursework you will implement a Feistel cipher system as a hardware component and as a software implementation. In a Feistel cipher the plaintext, P, to be encrypted is split into two equal size parts L0 and R0 such that P = L0R0. A function F is applied to one half of the plaintext, combined with a key, and the result is XOR’d with the other half of the plaintext. Feistel ciphers often employ multiple rounds of this scheme. In general the scheme works as follows, for all i = 0,...,n,
Li+1 = Ri
Ri+1 =Li ⊕F(Ri,Ki)
To decrypt an encrypted message using this cipher we can apply the same procedure inreverse. Fori=n,n−1,...,0,
Ri = Li+1
Li =Ri+1 ⊕F(Li+1,Ki)
For this coursework we are interested in the 16-bit Feistel cipher which uses 4 rounds. The function F (A, B) = A ⊕ B. The keys are derived from a single 8-bit key K0 such that,
K0 = b7b6b5b4b3b2b1b0 K1 = b6b5b4b3b2b1b0b7 K2 = b5b4b3b2b1b0b7b6 K3 = b4b3b2b1b0b7b6b5
1

1. Produce an implementation, in HDL, of the described Feistel encryption scheme. The chip should have the following preamble.
  CHIP FeistelEncryption {
      IN plaintext[16], key[8];
      OUT ciphertext[16];
PARTS: }

2. Write a program in HACK assembly, without using symbols, that implements the described Feistel encryption system. The initial key, K0, will be stored in RAM[1], and the 16-bit plaintext will be stored in RAM[2]. The result of the encryption should be stored in RAM[0]. Your solution should be submitted in a file called “FeistelEncryption.asm”.
You may use any RAM locations not specified in the description for intermediate variables.
