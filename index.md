---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: demo
---

For this project I used a VGA driver on the Basys3 board and created my own 8 bit style Wolverine graphic on the monitor using the VGA setting. During my time creating this graphic I learned how timing on VGA works, the generation of pixel coordinates and how they work and most importantly how to draw custom images using Verilog.

## **Template VGA Design**
### **Project Set-Up**
Summarise the project set-up and design flow. Include a screenshot of your own set-up, for example see the image of my Project Summary window below. Guideline 1 short paragraph.

The lab provided a full Vivado project containing a VGA timing module, a top module, and a simple “colour stripes” pixel generator. After importing it into Vivado, I followed the typical FPGA flow: simulate -> synthesise -> implement -> program the board. The Basys3 generated a 25 MHz pixel clock to drive a 640×480 VGA display, and the template helped confirm that the hardware setup was working correctly.









<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSum.png">
### **Template Code**




Outline the structure and design of the Verilog code templates you were given. What do they do? Include reference to how a VGA interface works. Guideline: 2/3 short paragraphs, consider including screenshot(s).
### **Simulation**
Explain the simulation process. Reference any important details, include a well-selected screenshot of the simulation. Guideline: 1/2 short paragraphs.
### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences.







## **My VGA Design Edit**
Introduce your own design idea. Consider how complex/achievabble this might be or otherwise. Reference any research you do online (use hyperlinks).
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
      This is my inspiration I got online at (add hyperlink of the website)
    </td>
  </tr>
</table>




### **Code Adaptation**
Briefly show how you changed the template code to display a different image. Demonstrate your understanding. Guideline: 1-2 short paragraphs.
Originally we had a template code of different coloured stripes running vertically across the screen. Through trial and error I managed to make make it into a staircase and then into what was meant to be the start of a PAC-MAN graphic. At that point I had gotten the gist of how to control each pixel. If i could have one big one then I could split that into many small ones and display a nice graphic, so thats what I did.

I could see how much work it was going to be so I mapped it out on paper, from there it was just lots of `if else` statements. Each with their own co-ordinate where they will be displayed on the screen. Set into rows and columns. I decided to make the boxes 16 x 16, there was 30 blocks of 16 for the rows and 40 blocks of 16 for columns, this was because in the inspired design it was set into 23 blocks for colomns, therefore 40 was more than enough space for the graphic to fit on the monitor. The same went with how big the insipiration graphic was for rows, if you count how many blocks tall the character is you will count 26 blocks tall, that means me giving 30 blocks for rows was just enough with leaving 2 blocks of tolerance for the head and the feet. I used `ChatGPT` to generate me the colours beige and gray.


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








### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.





### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.






### **Demonstration**
<p>If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.</p>

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








## **More Markdown Basics**
This is a paragraph. Add an empty line to start a new paragraph.

Font can be emphasised as *Italic* or **Bold**.

Code can be highlighted by using `backticks`.

Hyperlinks look like this: [GitHub Help](https://help.github.com/).

A bullet list can be rendered as follows:
- vectors
- algorithms
- iterators

Images can be added by uploading them to the repository in a /docs/assets/images folder, and then rendering using HTML via githubusercontent.com as shown in the example below.

<img src="https://raw.githubusercontent.com/G00435965/fpga-vga-veriloggKM/main/docs/assets/images/board.jpg" width="50%">





