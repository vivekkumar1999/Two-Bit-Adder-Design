# Two-Bit-Adder-Design
Two bit adder using one half and one full adder 


module two_bit_adder(input clr,[1:0]x, [1:0]y, output [2:0]z );

half_adder hf1(clr,x[0],y[0],z[0],w1);
full_adder fl1(clr,x[1],y[1],w1,z[1],z[2]);

endmodule

module full_adder(Clr,A,B,Cin,Sum,Carry);  
input Clr,A,B,Cin;
output Sum,Carry;
wire w1,w2,w3,w4,w5,w6;
and and1(w1,A,Clr);
and and2(w2,B,Clr);
and and3(w3,Cin,Clr);
half_adder hf1(Clr,w1,w2,w4,w5);
half_adder hf2(Clr,w3,w4,Sum,w6);
or or1(Carry,w5,w6);
endmodule


module half_adder(clr,a,b,sum,carry);
input a,b,clr ;
output sum,carry ;
wire w1,w2;
    and and1(w1,a,clr);  
    and and2(w2,b,clr);
    xor sum1(sum,w1,w2);
    and carry1(carry,w1,w2);
endmodule
