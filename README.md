design code:

//gate level modelling

module mux21(a,b,s,c);
input a,b,s;
output c;
wire w1,w2,w3;
not(w1,s);
and(w2,a,w1);
and(w3,b,s);
or(y,w2,w3);
endmodule

//data flow modelling

module halfadder(a,b,s,c);
input a,b,s;
output c;
assign c=(a&~s)|(b&s);
endmodule

//behavioural modeling

module mux21(a,b,s,c);
input a,b,s;
output c;
always@(a|b|s)
begin
if(s==1)
c=a;
else
c=b;
end
endmodule

test bench :

module mux21_tb();
reg a,b,s;
wire c;
mux21 uut(a,b,s,c);
initial begin
a=0;b=1;s=1;
#10
a=1;b=1;s=1;
#10
a=1;b=0;s=1;
#10
a=0;b=0;c=1;
#10
end
$finish();
endmodule


