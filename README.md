ARITHMETIC LOGICAL UNIT

ALU is a combinatorial digital circuit that performs arithmetic and bitwise operations on integer binary numbers. The input to an ALU are the data to be operated on, called Oprands, and a code indicating the operation to be performed;the ALU's output is the result of the performed opertaions.

OPCODE :- THE OPCODE input is a parallel bus that conveys to the ALU an operation selection code, which is an enumerated  value; that specifies the desired arithmetic or logic operation to be performed by the ALU. THe opcode size determines the maximum number of distinct operations the ALU can perform; for example; a four-bit opcode can specify up to sixteen different ALU operations

IMPLEMENTATION:- An ALU is usually implemented either as a stand-aloe Integrated Circuit(IC), such as the 74181, or as part of a more complex IC. The ALU Code is written in VHDL, Verilog or some other hardware description language. For example, VHDL Code describe a simple 8-bit ALU:
                     
                      entity alu is 
                      port (  -- the alu connections to external circuitry:
                      A : in signed(7 downto 0);
                      - operand A
                      B : in signed(7 downto 0);
                      - operand B
                      OP : in unsigned(2 downto 0);
                      - opcode
                      Y : out signed(7 downto 0));
                      -- operation result
                      end alu;

                      architecture behavioral of alu is 
                      begin
                        case OP is -- decode the opcode 
                        and perform the operation:
                        when "000" =>  Y <= A + B;  --
                        add
                        when "001" => Y <= A - B;   --
                        subtract
                        when "010" => Y <= A - 1;   --
                        decrement
                        when "011" => Y <= A + 1;   --
                        increment
                        when "100" => Y <= not A;   --
                        1's complement
                        when "101" => Y <= A and B; --
                        bitwise AND
                        when "110" => Y <= A or B;  --
                        bitwsie OR
                        when "111" => Y <= A xor B; --
                        bitwise XOR
                        when others => Y <= (others => 'X');
                        end case;
                      end behavioral;
