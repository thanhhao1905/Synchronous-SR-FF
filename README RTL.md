```verilog
module sr_ff_sync_rst_n (input wire s ,r ,clk ,rst_n,
                         output reg q ,
                         output wire q_bar);
  
  //always @ (posedge clk or negedge rst_n);
  always @ (posedge clk ) begin
    if(rst_n ==0) begin
      q <= 0;
    end
    else begin
      case({s,r})
      	2'b00: q <= q;
        2'b01: q <= 0;
        2'b10: q <= 1;
        2'b11: q <= 1'bx;
        default: $display ("Invalid Value");
      endcase
    end
  end
  
  assign q_bar = ~q;
endmodule
  
  
