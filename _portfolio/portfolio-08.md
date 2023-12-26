---
title: "Redesign to improve a Nintendo Entertainment System (NES) Controller"
excerpt: "ME 270 course final project, University of Illinois. Cover image by Hima Pamu <br/><img src='/images/NES_500300.jpg'>"
collection: portfolio
---
<!--
This is a final project for <a href="https://courses.illinois.edu/schedule/2019/fall/ME/270">ME 270: Design for Manufacturability</a>.


In this project, the design challenge required students to pick a scrap object from <a href="https://www.macksrecycling.com/">Mack's Twin City Recycling</a> and perform the following:
* A complete Design for Manufacture and Assembly (DFMA) analysis on our product
* Creation of a detailed CAD model of parts of the existing product to generate a detailed Manufacturing Cost Analysis using aPriori software
* Generation and evaluation of new ideas to improve the recyclability of the existing product's parts
* Creation of a detailed CAD model of parts for the redesigned product to generate a detailed Manufacturing Cost Analysis
* A rudimentary Design of Experiment to test the redesigned product
* A comparison of the original product with the redesigned product in terms of cost, function, and quality


I decided to work on an old Nintendo Entertainment System (NES) controller from Mack's recycling. At the conclusion of the course, my project was recognized as one of the top 5 projects among 180 individual student final projects in the course.


The project is available to view <a href="https://illinois.digication.com/me-270-fa19-team-ab7-3_january222020/abet-learning-goals-2-4">here</a>
-->

Older products were built without the goal of repairability and recyclability with respect to their materials. This is deeply rooted in the material choices, construction process, and the expectation of customer repairability during the manufacturing year. In this project, I was tasked with improving the above concerns for a product that was manufactured at least two decades ago and conducting a comprehensive manufacturing analysis Furthermore, their manufacturing process can be improved in the process as the process of manufacturing could be outdated and more efficient methods can be employed in modern manufacturing. 


<!--TABLE VIDEO PLACEMENT-->
<table border="0">
 <tr>
  <td><img src='/images/NES/IMG_20191025_113530.jpg' alt="demoasm_stdview" class="center">
   
   
   <i>Top casing</i>
  
  
  </td>
  <td><img src='/images/NES/IMG_20191025_112942.jpg' alt="demoasm_stdview" class="center">
   
   
   <i>Unscrewed</i>
   
   
  </td>
 </tr>
 
 
 <tr>
  <td><img src='/images/NES/IMG_20191025_113454.jpg' alt="demoasm_stdview" class="center">
   
   
   <i>PCB</i>
  
  
  </td>
  <td><img src='/images/NES/IMG_20191025_113439.jpg' alt="demoasm_stdview" class="center">
   
   
   <i>Buttons</i>
  
  
  </td>
 </tr>
</table>
<p style="text-align:center"> <i>Fig.1: Nintendo Entertainment System controller parts</i></p>


<img src='/images/NES/IMG_20191025_113428.jpg' alt="demoasm_stdview" class="center">
<p style="text-align:center"> <i>Fig.2: NES controller disassembled.</i></p>


My product choice for the project was the Nintendo Entertainment System (NES) controller, first made in 1986. I started by disassembling the controller to get a complete understanding of the internal structure. I noticed that there were a lot of rubber buttons that could be recycled, and the plastic components made of Acrylonitrile Butadiene Styrene (ABS) could be redesigned to improve customer repairability and ease of assembly. The parts that couldn't be recycled were the main Printed Circuit Board (PCB), wiring, and the stainless steel Phillips head screws.


<img src='/images/NES/BOM.png' alt="demoasm_stdview" class="center">
<p style="text-align:center"> <i>Fig.3: Bill of Materials.</i></p>


The next step was to redesign the product for modern manufacturing techniques. The product’s original design had a plastic casing that was injection molded, but the plastic used was ABS. ABS is not recyclable and is toxic to the environment if improperly disposed of, so in the redesigned product, I decided to use Polylactic Acid (PLA) plastic as it is a biodegradable thermoplastic made from renewable resources like cornstarch or sugar cane. The top and bottom casing can be combined with a living hinge as they are made of the same material. Also, they don't move with respect to one another and need not be separated for assembly if a living hinge is implemented. The living hinge will also eliminate the Phillips head screws. The D-pad and its silicone contact can be merged into one single part and can be made out of a single material - silicone. This is possible as they also do not move and can be made of the same material without impeding their function. Moreover, manufacturing the whole D-pad and contacts together is faster and more feasible.


<!--TABLE VIDEO PLACEMENT-->
<table border="0">
 <tr>
  <td><img src='/images/NES/topcasing2.png' alt="demoasm_stdview" class="center">
   
   
   <i>Original Top Casing</i>
  
  
  </td>
  <td><img src='/images/NES/ASSEM.png' alt="demoasm_stdview" class="center">
   
   
   <i>Redesigned Top and Bottom Casing</i>
   
   
  </td>
 </tr>
 
 
 <tr>
  <td><img src='/images/NES/ABbutton1.png' alt="demoasm_stdview" class="center">
   
   
   <i>Original plastic button design</i>
  
  
  </td>
  <td><img src='/images/NES/ABbuttonNEW2.png' alt="demoasm_stdview" class="center">
   
   
   <i>Redesigned Combined Natural rubber part</i>
  
  
  </td>
 </tr>
</table>
<p style="text-align:center"> <i>Fig.4: Some CAD renders of original and redesigned parts.</i></p>


<img src='/images/NES/DFA.png' alt="demoasm_stdview" class="center">
<p style="text-align:center"> <i>Fig.5: Bill of Materials.</i></p>


For the manufacturing analysis, aPriori software was used. For each component, the analysis was done for an annual manufacturing load of 10,000 parts for 5 years. By cost, the redesigned parts are more expensive than the original. Based on aPriori analysis, the original design would have cost approximately \\$13 per part, but the redesigned parts are approximately \\$28 per part. However, it is to be noted that the assembly costs of the original part would be significantly higher along with the costs of the other parts like the PCB, separate silicone contacts (for the old design), and the screws added to the final consideration. Functionally, there should not be a huge difference in the operation of the product as the redesign only addresses the assembly method. The redesigned part has a reduced assembly time. The living hinge makes it easier to put the part together, and the reduced number of fastenings. Environmentally, the redesign has parts made of PLA, meaning it is more environmentally positive than the old design. The product can be completely recycled if properly processed through a recycling facility. To conclude, I have focused the redesign on ease of assembly and disassembly so that the components are quickly sorted at recycling facilities. This way, my design has achieved two goals: assembly efficiency and improved recycling process speed. 


<img src='/images/NES/COMP.png' alt="demoasm_stdview" class="center">
<p style="text-align:center"> <i>Fig.6: Cost comparision between original and redesigned parts.</i></p>






