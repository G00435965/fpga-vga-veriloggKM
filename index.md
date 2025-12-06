---
layout: home
title: "FPGA VGA Driver Project"
tags: fpga vga verilog
categories: demo
---

For this project I used a VGA driver on the Basys3 board and created my own 8 bit style Wolverine graphic on the monitor using the VGA setting. During my time creating this graphic I learned how timing on VGA works, the generation of pixel coordinates and how they work and most importantly how to draw custom images using Verilog.

## **Template VGA Design**
### **Project Set-Up**


The lab provided a full Vivado project containing a VGA timing module, a top module, and a simple “colour stripes” pixel generator. After importing it into Vivado, I followed the typical FPGA flow: simulate -> synthesise -> implement -> program the board. The Basys3 generated a 25 MHz pixel clock to drive a 640×480 VGA display, and the template helped confirm that the hardware setup was working correctly.









<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSum.png">
### **Template Code**





### **Simulation**
<table>
  <tr>
    <td>
      insert image
    </td>
    <td style="padding-left:20px; font-size:20px;">
      Simulation is the first step in verifying the VGA design before running it on physical FPGA hardware. Using the testbench in Vivado, I ran a behavioural simulation, this allowed me to observe signals such as `hsync`, `vsync`,`(row, col)`, and the RGB outputs in the waveform window. This shows me that the VGA timing pulses are correct and they only appear when `vid-on` is active. Simulation is important because it lets us verify the Verilog logic before Vivado turns it into real hardware components like LUT's, flip-flops, CBL's and interconnect. [1]
      <a href="https://vlegalwaymayo.atu.ie/pluginfile.php/1619154/mod_resource/content/1/11_7-Series%20Architecture%20Overview.pdf">Lecture Notes pages 4-16 </a>
    </td>
  </tr>
</table>



### **Synthesis**
<table>
  <tr>
    <td>
      insert image
    </td>
    <td style="padding-left:20px; font-size:20px;">
Synthesis is the step where Vivado converts my Verilog code into real FPGA hardware components. During this stage, the tool maps my design into resources used in 7-Series devices such as LUTs, flip-flops, CLBs, multiplexers, and carry chains. The synthesised schematic in Vivado shows how modules like the VGA timing generator and colour-stripe module are implemented using these hardware blocks. This process checks that the design can be built correctly using the FPGA’s logic before moving on to physical placement. [2]
 <a href="https://vlegalwaymayo.atu.ie/pluginfile.php/1619154/mod_resource/content/1/11_7-Series%20Architecture%20Overview.pdf">Lecture Notes pages 9-17 </a>

 The simulation shows that my VGA timing and colours behave correctly, so the design is ready for synthesis and hardware testing.
 
    
  </tr>
</table>


### **Implementation**
<table>
  <tr>
    <td>
      insert image
    </td>
    <td style="padding-left:20px; font-size:20px;">
      Implementation performs the placement and the routing. Here, the synthetic logic is placed onto the physical layout of the FPGA and connects everything using the programmable interconnect. It also sets up clock routing using resources such as BUFG global buffers and clock regions. [3] <a href="https://vlegalwaymayo.atu.ie/pluginfile.php/1619154/mod_resource/content/1/11_7-Series%20Architecture%20Overview.pdf">Lecture Notes pages 47-50 </a> The device view shows where each module is placed on the chip. Once routing meets timing requirements, the design is ready to be programmed onto the Basys3 board.
    </td>
  </tr>
</table>

### **Demonstration**
<table>
  <tr>
    <td>
      insert image
    </td>
    <td style="padding-left:20px; font-size:20px;">
      The image below shows my Wolverine graphic running on the Basys3 board, confirming that my VGA driver design works correctly on hardware.
    </td>
  </tr>
</table>





## **My VGA Design Edit**
I picked the Wolverine character from X-Men as my graphic design. I was originally going to do PAC-MAN and wanted to stick with the yellow. I am also fascinated with Wolverine as he is an intersting character, I knew that if I had been making something I like it would motivate me further. This strategy worked as I finished the design in two classes. The design was complicated in theory as there is lots of sharp edges. With this information I decided to map out the co-ordinates on paper and tick the boxes as I went along, this worked tremendously well and decreased the amount of time I would have spent on the project.
<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/G00435965/fpga-vga-veriloggKM/main/docs/assets/images/pacman.jpg" style="width:50%;">
    </td>
    <td style="padding-left:20px; font-size:20px;">
      PAC-MAN; This was my first attempt at my own graphic. Until realising I wanted more of a challenge.
    </td>
  </tr>
</table>

<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/G00435965/fpga-vga-veriloggKM/main/docs/assets/images/wolverineInspiration.webp" style="width:50%;">
    </td>
    <td style="padding-left:20px; font-size:20px;">
      This is my inspiration design I got online -> [4] <a href="https://prohama.com/wolverine-pattern-1/">Inspiration design</a>
    </td>
  </tr>
</table>




### **Code Adaptation**
Originally we had a template code of different coloured stripes running vertically across the screen. Through trial and error I managed to make make it into a staircase and then into what was meant to be the start of a PAC-MAN graphic. At that point I had gotten the gist of how to control each pixel. If i could have one big one then I could split that into many small ones and display a nice graphic, so thats what I did.

I could see how much work it was going to be so I mapped it out on paper, from there it was just lots of `if else` statements. Each with their own co-ordinate where they will be displayed on the screen. Set into rows and columns. I decided to make the boxes 16 x 16, there was 30 blocks of 16 for the rows and 40 blocks of 16 for columns, this was because in the inspired design it was set into 23 blocks for colomns, therefore 40 was more than enough space for the graphic to fit on the monitor. The same went with how big the insipiration graphic was for rows, if you count how many blocks tall the character is you will count 26 blocks tall, that means me giving 30 blocks for rows was just enough with leaving 2 blocks of tolerance for the head and the feet. I used  [5] <a href="https://chatgpt.com/">ChatGPT</a> to generate me the colours beige and gray. EXPLAIN WHY ITS BEHIND BY ONE EG.479


<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/G00435965/fpga-vga-veriloggKM/main/docs/assets/images/firstplan.jpg" style="width:50%;">
    </td>
    <td style="padding-left:20px; font-size:20px;">
      Here was my first plan I did in class for the left side of the graphic.
    </td>
  </tr>

  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/G00435965/fpga-vga-veriloggKM/main/docs/assets/images/planpic.jpg" style="width:50%;">
    </td>
    <td style="padding-left:20px; font-size:20px;">
      Here is the plan for the right side of the graphic I did at home.
    </td>
  </tr>

  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/G00435965/fpga-vga-veriloggKM/main/docs/assets/images/finalPlan.jpg" style="width:50%;">
    </td>
    <td style="padding-left:20px; font-size:20px;">
      This is the final plan with the two put together.
    </td>
  </tr>
</table>










### **My Simulation**
<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/G00435965/fpga-vga-veriloggKM/main/docs/assets/images/simulationProcess.png" style="width:100%;">
    </td>
    <td style="padding-left:20px; font-size:20px;">
     This is my Vivado behavioural simulation, my waveform shows the VGA controller operating correctly. The clock is running contantly, once the reset signal goes low, the timing logic steps through each pixel. The column counter rapidly increases across each line, while the row counter increments once per full sweep of the screen, this demonstrates proper horizontal and vertical counting. The hsync signal is generating regular pulses for each line that is complete, and once per frame the vsync generates a pulse. The vid_on signal goes high only during the 640×480 visible display area, and during this time the RGB outputs change according to my colour-stripe module. [6]
      <a href="https://chatgpt.com/">ChatGPT</a> This confirms that the VGA module is producing correct pixel positions, sync pulses, and video-active periods. 
    </td>
  </tr>
</table>



### **My Synthesis**
<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/G00435965/fpga-vga-veriloggKM/main/docs/assets/images/Screenshot 2025-12-01 151252.png" style="width:100%;">
    </td>
    <td style="padding-left:20px; font-size:20px;">
Synthesis translated my Verilog VGA controller into the actual schematic with the FPGA components it will use: counters for pixel positions, logic gates to generate sync pulses, LUTs for my colour-stripe display, and registers for timing. The schematic shows how these blocks are connected, confirming that Vivado has successfully mapped my code into real 7-Series FPGA hardware. [7] <a href="https://chatgpt.com/">ChatGPT</a>
 
    
  </tr>
</table>


### **My Implementation**
<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/G00435965/fpga-vga-veriloggKM/main/docs/assets/images/synthesis_design.png" style="width:100%;">
    </td>
    <td style="padding-left:20px; font-size:20px;">
     need to get a zoomed in pic
    </td>
  </tr>
</table>
### **My Demonstration**

<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/G00435965/fpga-vga-veriloggKM/main/docs/assets/images/wolverinefinal.jpg" style="width:50%;">
    </td>
    <td style="padding-left:20px; font-size:20px;">
      This was my final Wolverine design. I am very happy with the outcome as I eliminated almost all of the errors from my last attempt at the final version.
    </td>
  </tr>
</table>






<img src="https://raw.githubusercontent.com/G00435965/fpga-vga-veriloggKM/main/docs/assets/images/board.jpg" width="50%">
Here is the Basys3 board I used.


### **My References**
Michelle Lynch lecture notes, Used for info on processes such as Simulation, Synthesis and Implementation, Available Online: <a href="https://vlegalwaymayo.atu.ie/pluginfile.php/1619154/mod_resource/content/1/11_7-Series%20Architecture%20Overview.pdf">Lecture Notes</a> [1] [2] [3]

Prohama, Used for inspiration on what graphic to design, Available Online: <a href="https://prohama.com/wolverine-pattern-1/">Inspiration design</a> [4]

ChatGPT, Used to break down and explain how the processes worked and generate colours, Available Online: <a href="https://chatgpt.com/">ChatGPT</a> [5] [6] [7] [8]



