---
title: "Control Stabilization for Bi-Quadcopter Payload Delivery System"
excerpt: "24-774 course project, Carnegie Mellon University <br/><img src='/images/ACSI_project/coverimage_500x250.jpg'>"
collection: portfolio
---

**Introduction**

In recent years, drones have emerged as versatile tools, significantly impacting sectors like agriculture, surveillance, and delivery. While their applications are expansive, a primary limitation hindering broader usage is the restricted payload capacity. Traditional single-drone designs are often inadequate for tasks requiring substantial load carriage. This paper examines an innovative approach to address this challenge: the Bi-Quadcopter Payload Delivery System. This system features a novel integration of two drones connected by a specially designed truss structure. The primary objective of this design is to enhance the payload capacity beyond the limitations of conventional single-drone systems. By distributing the load between two interconnected drones, the system aims to achieve greater stability and efficiency in payload delivery. The motivation for this project stems from the growing demand for drones capable of transporting larger payloads across various industries. This demand is particularly evident in sectors where drones are increasingly preferred for their ability to navigate challenging terrains, enhance efficiency, and reduce human risk in operations. However, the limited payload capacity of current drone technology often necessitates compromises in operational scope and efficiency.


**Methodology**

The first step in enabling the bi-quadcopter flight was iteratively designing a robust truss structure that is light weight. Polylactic Acid (PLA) was used to maintain the lightweight nature. The truss strategically positioned the payload at the center, balancing it between the two drones. This positioning, coupled with the symmetry of the CrazyFlie drones’ motors and arms, resulted in a exploitable symmetry in controller design logic. 

<img src='/images/ACSI_project/Dual_CF_wTruss.png' alt="Dual_CF_wTruss" class="center">
<p style="text-align:center"> <i>SolidWorks Assembly of the Dual-Drone System. Note the cross shape of the truss allowing for an unobstructed view for the Flowdecks on the underside</i></p>



The bi-quadcopter setup's system modelling involved develop a state-space dynamics model that accurately represented the behavior and responses of the interconnected drones. This model is vital for predicting the system’s performance under various load conditions and flight scenarios. The existing Crazyflie cascaded Proportional-Integral-Derivative (PID) controller was redesigned and tuned to match the new dual drone dynamics. This controller modification was essential for achieving precise and stable flight control, considering the additional complexity about the roll and yaw flight operation due to the design. In addition, a setpoint change was made for yaw operations that significantly improved performance

<div style="text-align: center;">
<table border="0">
 <tr>
  <td><img src='/images/ACSI_project/yaw_noChange.png' alt="yaw_noChange" class="center"></td>
  <td><img src='/images/ACSI_project/yaw_firmware changeDrone Position.png' alt="yaw_firmware changeDrone Position" class="center"></td>
 </tr>
</table>
</div>

<p style="text-align:center"> <i>x and y coordinates of both drones during yaw. Left: With default setpoint, Right: With modified setpoint</i></p>

Simulink was used to assess the response of the new controller on the hardware, providing a virtual testing ground for our controller tuning process. For payload pickup, rigid donut-shaped magnets were used along with a payload comprised of a heap of magnetic paper clips. Each magnet and paperclip weighed approximately 3g and 0.5g respectively. to further stabilize the flight operations after the payload pickup process, an adaptive controller was implemented. This controller dynamically adjusted the PID settings based on the weight of the payload, ensuring consistent performance across a range of payloads.

<div style="text-align: center;">
<table border="0">
 <tr>
  <td><img src='/images/ACSI_project/defaultPWD.png' alt="defaultPWD" class="center"></td>
  <td><img src='/images/ACSI_project/linearPWD.png' alt="linearPWD" class="center"></td>
 </tr>
</table>
</div>

<p style="text-align:center"> <i>Left: Default power distribution in roll direction, Right: Modified power distribution in roll direction</i></p>


**Results**

Initially, the drone underwent calibration without added mass, aiming to minimize steady-state roll error before payload pick-up operations. This pre-tuning phase revealed a mean error of about 8.5%, coupled with significant oscillations and instability, as detailed in the following figure. The drone executed left and right translations over 2 meters at 0.3 meters/second. Notably, introducing a delay between directional changes enhanced stability.

<div style="text-align: center;">
<table border="0">
 <tr>
  <td><img src='/images/ACSI_project/left_right (baseline no mass)Average.png' alt="left_right (baseline no mass)Average" class="center"></td>
  <td><img src='/images/ACSI_project/left_right (Kp_600 Kd_6_no mass)Average.png' alt="left_right (Kp_600 Kd_6_no mass)Average" class="center"></td>
 </tr>
</table>
</div>

<p style="text-align:center"> <i>No mass roll PID tuning. Left: Default PID values, Right: Tuned PID values</i></p>

Following this, the drone was calibrated with an added mass of approximately 8 grams to further reduce steady-state roll error during payload transport. Pre-tuning, shown in below, indicated a mean error around 7.4% with similar instability to the initial tests. The control commands mirrored those of the no-mass phase, involving lateral movements across 2 meters at 0.3 meters/second. Tuning successfully reduced the mean error to 5.8% and enhanced stability.

<div style="text-align: center;">
<table border="0">
 <tr>
  <td><img src='/images/ACSI_project/left_right_with_mass (Kp_600 Kd_6)Average.png' alt="left_right_with_mass (Kp_600 Kd_6)Average" class="center"></td>
  <td><img src='/images/ACSI_project/left_right_with_mass (Kp_800 Kd_8)Average.png' alt="left_right_with_mass (Kp_800 Kd_8)Average" class="center"></td>
 </tr>
</table>
</div>

<p style="text-align:center"> <i>With mass roll PID tuning. Left: Default PID values, Right:Tuned PID values</i></p>

Overall, the results demonstrated the practical viability of the Bi-Quadcopter Payload Delivery System. The system not only achieved its primary goal of increased payload capacity but also maintained the essential attributes of stability and control, paving the way for its potential application in various industrial and commercial sectors.

<div style="text-align: center;">
<table>
  <tr>
    <th></th>
    <th>Single Drone</th>
    <th>Bi-Quadcopter</th>
    <th>% change</th>
  </tr>
  <tr>
    <td>Payload Capacity [g]</td>
    <td>7</td>
    <td>10</td>
    <td>43 % increase</td>
  </tr>
  <tr>
    <td>Lateral Translation Mean Error [%]</td>
    <td>7.8</td>
    <td>5.8</td>
    <td>26 % decrease</td>
  </tr>
</table>
</div>


**Conclusion**

The project demonstrated that the dual drone system, after stabilization, supports a higher payload than a single drone. Further enhancements were observed with the application of the adaptive controller. This advanced control allowed the drone to efficiently execute the load pickup, compare baseline and measured PWM, and appropriately scale PID values. With the tuned PID gains, the drone successfully performed the left-right lateral translation test for roll flight operation, affirming the effectiveness of the overall control system.

To conclude, the integration of two CrazyFlie drones, connected via a rigid 3D printed truss and equipped with a magnet-based payload delivery mechanism, marks a significant advancement. Our dynamics model, leveraging state space representation and onboard Cascaded PID controllers, ensured precise control. Addressing initial stability issues through firmware adjustments and the adaptive controller adjusting for payload variations, resulted in a notably stable and smooth operation of the bi-quadcopter system.


**Team**

Our final presentation is available to view <a href="https://drive.google.com/file/d/1bT4KMnsltgcpMdeA26Qo8Tf2k_ncgda_/view?usp=sharing">here</a>


Our final report is available to view <a href="https://github.com/hhpamu/ACSI_dual_drone/blob/main/ACSI_Final_Report_revised.pdf">here</a>


The full playlist of videos of our testing and final demo result can be found on <a href="https://www.youtube.com/playlist?list=PLhjMVMo-iKefzUKCguJFhuCKCUdmlcipk" target="_blank">YouTube</a> 


The team consisted of <a href="https://www.linkedin.com/in/peter-blumenstein-59599011a/">Peter Blumenstein</a>, who worked on simulation tasks; <a href="https://www.linkedin.com/in/sribru/">Srikumar Brundavanam</a>, who was involved in firmware development and swarm flight implementation; <a href="https://www.linkedin.com/in/steven-shi-272b2b168/">Shang Shi</a> on firmware development and hardware testing and tuning; <a href="https://www.linkedin.com/in/ben-spin-71640b1a5/">Ben Spin</a>, on truss design and dynamics modeling; and myself working on dynamics modeling, controller design, and hardware testing & tuning.


**Acknowledgements**

We would like to express our sincere gratitude to Dr. Mark Bedillion, whose expertise, understanding, and patience, added considerably to our experience and understanding of control systems and their implementation. 
We would also like to thank Dr. Aaron Johnson for his assistance in developing the dynamics model of our project.
Additionally, we are indebted to Khai Nguyen, the teaching assistant for 24-774 Special Topics: Advanced Control Systems Integration for Fall 2023, for his invaluable assistance throughout this project. H


**References**

J.-P. Aurambout, K. Gkoumas, and B. Ciuffo, “Last mile delivery by drones: An estimation of viable market potential and access to citizens across European cities,” European Transport Research Review, vol. 11, no. 1, 2019. doi:10.1186/s12544-019-0368-2 


J. E. Scott and C. H. Scott, “Models for drone delivery of medications and other healthcare items,” Unmanned Aerial Vehicles, pp. 376–392, 2019. doi:10.4018/978-1-5225-8365-3.ch016 


Mohsan, S.A.H., Othman, N.Q.H., Li, Y. et al. Unmanned aerial vehicles (UAVs): practical aspects, applications, open challenges, security issues, and future trends. Intel Serv Robotics 16, 109–137 (2023). https://doi.org/10.1007/s11370-022-00452-4


D. G. Morín, J. Araujo, S. Tayamon and L. A. A. Andersson, "Autonomous Cooperative Flight of Rigidly Attached Quadcopters," 2019 International Conference on Robotics and Automation (ICRA), Montreal, QC, Canada, 2019, pp. 5309-5315, doi: 10.1109/ICRA.2019.8794266.


XIE, Heng ; DONG, Kaixu ; CHIRARATTANANON, Pakpong. / Cooperative Transport of a Suspended Payload via Two Aerial Robots with Inertial Sensing. In: IEEE Access. 2022 ; Vol. 10. pp. 81764-81776.


Luis, C., \& Le Ny, J. (August, 2016). "Design of a Trajectory Tracking Controller for a
NanoQuadcopter". Technical report, Mobile Robotics and Autonomous Systems Laboratory, Polytechnique Montreal. 
