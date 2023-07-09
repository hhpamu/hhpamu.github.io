---
title: "Soft Actuator Meshes"
excerpt: "Undergraduate research project, University of Illinois. Cover image by Hima Pamu <br/><img src='/images/msl_REPLACE.jpg'>"
collection: portfolio
---


**Introduction**


The biggest pitfall of traditional mechanical elements is that a single actuator drives a mechanism through a transmission system.This Independent Study explores the potential of a distributed soft actuator network to replace conventional actuator-transmission systems. Lightweight, soft robots configured as a planar and spatial network of Fiber-Reinforced Elastomeric Enclosures (FREEs) have many applications ranging from endoscopic surgery to morphing control surfaces for aircraft.


To leverage FREEs' capabilities, soft interfaces that enable robust interconnections between FREEs are designed and honed for typical operating pressures of FREEs. Various contracting FREE configurations were tested using the connectors under a fixed pressure to discern their effectiveness and find effective geometry and input parameters.


Inspired by the compliant flexure nodes in this <a href="https://ieeexplore.ieee.org/document/7918530" target="_blank">paper</a>, I designed and built flexible connectors for Fiber Reinforced Elastomeric Enclosures (FREEs) that are capable of emulating a pin joint. The end goal for the connectors was to be able to be incorporated into other robotics projects involving FREEs and for general demonstration purposes.


**2022 UIUC Undergraduate Research Symposium Poster presentation**


Here is the poster I presented at the event (open image in a new tab better resolution)


<img src='/images/2022_URS.jpg' alt="2022_URS_poster" class="center">


**Connector Fabrication**


The prototyping process involved modeling the connectors in PTC Creo Parametric 7.0 (CAD software), 3D printing the molds out of Polylactic Acid (PLA) and Polyvinyl Alcohol (PVA), and selecting an appropriate silicone type. See <i>Fig.1</i> and <i>2</i> for some of the mold designs. It can be seen that the design of the molds can be easily modified to make connectors of any planar or spatial configuration.

<!--TWO COLUMN IMAGE PLACEMENT-->
<table border="0">
 <tr>
  <td><img src='/images/90deg.png' alt="90deg_planar" class="center"></td>
  <td><img src='/images/60deg.png' alt="60deg_planar" class="center"></td>
 </tr>
</table>

<p style="text-align:center"> <i>Fig.1: Left: Mold for the 90 degree configuration, Right: Mold for the 60 degree configuration.
 Note that the cope, drag are highlighted blue and core is shown in yellow. </i></p>
 
 
<img src='/images/spatial1.jpg' alt="120deg_spatial" class="center">
<p style="text-align:center"> <i>Fig.2: Mold for the tetrahedral configuration. Note that the drag (highlighted in red and blue) has a modified design to allow for easy removal. The cope is highlighted grey and core is shown in yellow. </i></p>

<!--FULL WIDTH IMAGE PLACEMENT-->
<!--
<img src='/images/90deg.png' alt="90deg_planar" class="center">
<p style="text-align:center"> <i>Fig.1: Mold for the 90 degree configuration. Note that the cope, drag are highlighted blue and core is shown in yellow. </i></p>


<img src='/images/60deg.png' alt="60deg_planar" class="center">
<p style="text-align:center"> <i>Fig.2: Mold for the 60 degree configuration. Note that the cope, drag are highlighted blue and core is shown in yellow. </i></p>


<img src='/images/spatial1.jpg' alt="120deg_spatial" class="center">
<p style="text-align:center"> <i>Fig.3: Mold for the tetrahedral configuration. Note that the drag (highlighted in red and blue) has a modified design to allow for easy removal. The cope is highlighted grey and core is shown in yellow. </i></p>
-->

The manufacturing process starts with injecting the silicone into the assembled cope, drag, and core, removing the air bubbles in the mold using a vacuum chamber, and allowing the silicone to solidify. After curing the silicone, the core needs to be dissolved in water to get the crude part. Next, the connectors need to be processed to remove the flashes and remenants of pouring hole and risers, see <i>Fig.3</i>. As imperfections can compromise its strength, smaller bubbles are punctured and sealed with silicone.

<table border="0">
 <tr>
  <td><img src='/images/90deg_justmade.jpg' alt="90degjstmade" class="center"></td>
  <td><img src='/images/90processed.jpg' alt="90degprocessed" class="center"></td>
 </tr>
</table>

<p style="text-align:center"> <i>Fig.3: Left: The crude part before processing, Right: The cope, drag, core and the processed part</i></p>

<!--FULL WIDTH IMAGE PLACEMENT-->
<!--
<img src='/images/90deg_justmade.jpg' alt="90degjstmade" class="center">
<p style="text-align:center"> <i>Fig.4: The crude part before processing</i></p>


<img src='/images/90processed.jpg' alt="90degprocessed" class="center">
<p style="text-align:center"> <i>Fig.5: The cope, drag, core and the processed part</i></p>
-->

I have been testing the connectors under various pressure, orientation, and configuration to discern their effectiveness. As a result, I improved their effectiveness at higher pressures (from 5 psi to 14 psi), a 64% improvement. According to testing results, further improvements are to be made in the design. See the videos below.


**Testing**


The following are the videos from preliminary testing of the FREE-FREE-Rigid member setup.

<!--FULL WIDTH VIDEO PLACEMENT-->
<!--
θ=30° configuration:
<iframe src="https://www.youtube.com/embed/LGxrzmNKqIA" title="30° configuration" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


θ=60° configuration:
<iframe src="https://www.youtube.com/embed/z79o3h1H0P4" title="60° configuration" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


θ=90° configuration:
<iframe src="https://www.youtube.com/embed/i2VV9eXshtU" title="90° configuration" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


θ=120° configuration:
<iframe src="https://www.youtube.com/embed/_99Zogn_KZM" title="120° configuration" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
-->


<!--TABLE VIDEO PLACEMENT-->
<table border="0">
 <tr>
  <td><iframe src="https://www.youtube.com/embed/LGxrzmNKqIA" title="30° configuration" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
   
   
   <i>30° configuration</i>
  
  
  </td>
  <td><iframe src="https://www.youtube.com/embed/z79o3h1H0P4" title="60° configuration" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
   
   
   <i>60° configuration</i>
   
   
  </td>
 </tr>
 
 
 <tr>
  <td><iframe src="https://www.youtube.com/embed/i2VV9eXshtU" title="90° configuration" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
   
   
   <i>90° configuration</i>
  
  
  </td>
  <td><iframe src="https://www.youtube.com/embed/_99Zogn_KZM" title="120° configuration" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
   
   
   <i>120° configuration</i>
  
  
  </td>
 </tr>
</table>


**Conclusions**


Improved actuator effectiveness was observed for θ ≥ 90°, demonstrating the viability of using pneumatic actuators in small-scale tasks. This capability is expected to be scalable for large-scale applications with an extensive network of tessellated meshes. These results were analyzed and compared to the expected theoretical reaction of the FREEs using an approximate model of FREE deformation in MATLAB based on the constrained maximization formulation. In addition, the results are to be compared to those from a mechanical replica performing the same function to assess the viability of using soft actuators.


**References**


Singh, Gaurav, and Girish Krishnan. "A constrained maximization formulation to analyze deformation of fiber reinforced elastomeric actuators." Smart Materials and Structures 26.6 (2017): 065024.


Singh, Gaurav, and Girish Krishnan. "An isoperimetric formulation to predict deformation behavior of pneumatic fiber reinforced elastomeric actuators." 2015 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS). IEEE, 2015.


Krishnan, Girish, et al. "Kinematics of a generalized class of pneumatic artificial muscles." Journal of Mechanisms and Robotics 7.4 (2015): 041014.


Bishop-Moser, Joshua, et al. "Design of soft robotic actuators using fluid-filled fiber-reinforced elastomeric enclosures in parallel combinations." 2012 IEEE/RSJ International Conference on Intelligent Robots and Systems. IEEE, 2012.


Satheeshbabu, Sreeshankar, et al. "Architectures of Soft Pneumatic Actuators Inspired by Muscle Fiber Arrangements." 2019 2nd IEEE International Conference on Soft Robotics (RoboSoft). IEEE, 2019.



<!--<img src='/images/fullasm2.jpg' alt="demoasm_perview" class="center">
#<p style="text-align:center"> <i>Fig.3: Visualization of the apparatus with a 100:1 geartrain attached.</i></p>-->

