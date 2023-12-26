---
title: "Control Stabilization for Bi-Quadcopter Payload Delivery System"
excerpt: "24-774 course project, Carnegie Mellon University"
collection: portfolio
---

**Introduction**

In recent years, drones have emerged as versatile tools, significantly impacting sectors like agriculture, surveillance, and delivery. While their applications are expansive, a primary limitation hindering broader usage is the restricted payload capacity. Traditional single-drone designs are often inadequate for tasks requiring substantial load carriage. This paper examines an innovative approach to address this challenge: the Bi-Quadcopter Payload Delivery System. This system features a novel integration of two drones connected by a specially designed truss structure. The primary objective of this design is to enhance the payload capacity beyond the limitations of conventional single-drone systems. By distributing the load between two interconnected drones, the system aims to achieve greater stability and efficiency in payload delivery. The motivation for this project stems from the growing demand for drones capable of transporting larger payloads across various industries. This demand is particularly evident in sectors where drones are increasingly preferred for their ability to navigate challenging terrains, enhance efficiency, and reduce human risk in operations. However, the limited payload capacity of current drone technology often necessitates compromises in operational scope and efficiency.

[---FINAL TRUSS CAD IMAGE---]

**Methodology**

The first step in enabling the bi-quadcopter flight was iteratively designing a robust truss structure that is light weight. Polylactic Acid (PLA) was used to maintain the lightweight nature. The truss strategically positioned the payload at the center, balancing it between the two drones. This positioning, coupled with the symmetry of the CrazyFlie drones’ motors and arms, resulted in a exploitable symmetry in controller design logic. The bi-quadcopter setup's system modelling involved develop a state-space dynamics model that accurately represented the behavior and responses of the interconnected drones. This model is vital for predicting the system’s performance under various load conditions and flight scenarios. The existing Crazyflie cascaded Proportional-Integral-Derivative (PID) controller was redesigned and tuned to match the new dual drone dynamics. This controller modification was essential for achieving precise and stable flight control, considering the additional complexity about the roll and yaw flight operation due to the design. In addition, a setpoint change was made for yaw operations that significantly improved performance

[---YAW BEFORE AND AFTER IMAGES---]

Simulink was used to assess the response of the new controller on the hardware, providing a virtual testing ground for our controller tuning process. For payload pickup, rigid donut-shaped magnets were used along with a payload comprised of a heap of magnetic paper clips. Each magnet and paperclip weighed approximately 3g and 0.5g respectively. to further stabilize the flight operations after the payload pickup process, an adaptive controller was implemented. This controller dynamically adjusted the PID settings based on the weight of the payload, ensuring consistent performance across a range of payloads.

[---PWR DIST BEFORE AND AFTER IMAGES---]

**Results**


**Conclusion**


**Team**

Our final presentation is available to view <a href="">here</a>


Our final report is available to view <a href="">here</a>


The team consisted of <a href="https://www.linkedin.com/in/peter-blumenstein-59599011a/">Peter Blumenstein</a>, who worked on simulation tasks; <a href="https://www.linkedin.com/in/sribru/">Srikumar Brundavanam</a>, who was involved in firmware development and swarm flight implementation; <a href="https://www.linkedin.com/in/steven-shi-272b2b168/">Shang Shi</a> on firmware development and hardware testing and tuning; <a href="https://www.linkedin.com/in/ben-spin-71640b1a5/">Ben Spin</a>, on truss design and dynamics modeling; and myself working on dynamics modeling, controller design, and hardware testing & tuning.


**Acknowledgements**
We would like to express our sincere gratitude to Dr. Mark Bedillion, whose expertise, understanding, and patience, added considerably to our experience and understanding of control systems and their implementation. 
We would also like to thank Dr. Aaron Johnson for his assistance in developing the dynamics model of our project
Additionally, we are indebted to Khai Nguyen, the teaching assistant for 24-774 Special Topics: Advanced Control Systems Integration for Fall 2023, for his invaluable assistance throughout this project. H


**References**

J.-P. Aurambout, K. Gkoumas, and B. Ciuffo, “Last mile delivery by drones: An estimation of viable market potential and access to citizens across European cities,” European Transport Research Review, vol. 11, no. 1, 2019. doi:10.1186/s12544-019-0368-2 


J. E. Scott and C. H. Scott, “Models for drone delivery of medications and other healthcare items,” Unmanned Aerial Vehicles, pp. 376–392, 2019. doi:10.4018/978-1-5225-8365-3.ch016 


Mohsan, S.A.H., Othman, N.Q.H., Li, Y. et al. Unmanned aerial vehicles (UAVs): practical aspects, applications, open challenges, security issues, and future trends. Intel Serv Robotics 16, 109–137 (2023). https://doi.org/10.1007/s11370-022-00452-4


D. G. Morín, J. Araujo, S. Tayamon and L. A. A. Andersson, "Autonomous Cooperative Flight of Rigidly Attached Quadcopters," 2019 International Conference on Robotics and Automation (ICRA), Montreal, QC, Canada, 2019, pp. 5309-5315, doi: 10.1109/ICRA.2019.8794266.


XIE, Heng ; DONG, Kaixu ; CHIRARATTANANON, Pakpong. / Cooperative Transport of a Suspended Payload via Two Aerial Robots with Inertial Sensing. In: IEEE Access. 2022 ; Vol. 10. pp. 81764-81776.


Luis, C., \& Le Ny, J. (August, 2016). "Design of a Trajectory Tracking Controller for a
NanoQuadcopter". Technical report, Mobile Robotics and Autonomous Systems Laboratory, Polytechnique Montreal. 





<img src='/images/ME470_project/ME 470 3D-Printer Enclosure Poster.jpg' alt="2022_ME170_Trade_Show_poster" class="center">
<p style="text-align:center"> <i>The poster we presented at the trade show (open image in a new tab better resolution)</i></p>

