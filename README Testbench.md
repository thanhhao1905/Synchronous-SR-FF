```verilog
`timescale 1ns/1ps
module tb_sr_ff_sync_rst_n;
  reg s ,r ,clk ,rst_n ;
  wire q;
  wire q_bar =~q;
  
  sr_ff_sync_rst_n DUT (s,r,clk,rst_n,q,q_bar);
  
  always #2 clk = ~clk;
  
  initial begin
    clk = 0;
    s = 0;
    r = 0;
    #1 rst_n = 0;
    $display("Reset=%b --> q=%b | q_bar=%b",rst_n,q,q_bar);
    
    #2 rst_n = 1;
    $display("Reset=%b --> q=%b | q_bar=%b",rst_n,q,q_bar);
    #3 drive(2'b01);
    #3 drive(2'b10);
    #3 drive(2'b01);
    #2 drive(2'b10);
    #3 drive(2'b00);
    #3 drive(2'b11);
    
    #1;
    $finish;
  end
  
  task drive (bit [1:0] ip); // bit _ 2 state , logic _4 state
    @(posedge clk);
    {s,r} = ip;
    #1
    $display ("s=%b ,r=%b | q =%b , q_bar=%b",s ,r ,q ,q_bar);
  endtask
  
  initial begin
    $dumpfile("dump.vcd");
    $dumpvars;
  end
endmodule
    
