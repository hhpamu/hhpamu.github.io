---
title: "CMU Buggy Control Project"
excerpt: "24-677 course project, Carnegie Mellon University <br/><img src=''>"
collection: portfolio
---

**Introduction**

As the implementation component of Carnegie Mellon's 24-677 Modern Control Theory, students were required to design Proportional–Integral–Derivative (PID), state feedback, Linear–Quadratic Regulator (LQR) and Model Predictive Control (MPC) controllers and extended Kalman filter (EKF) for Simultaneous Localization And Mapping (SLAM) for a self-driving vehicle in a series of projects. This project uses CMU's annual <a href="https://www.cmu.edu/buggy/">Buggy</a> racing competition track, which involves engineers and atheletes to race a .84 mile track around Schenley Park's <a href="https://en.wikipedia.org/wiki/Flagstaff_Hill,_Pennsylvania">Flagstaff Hill</a> during the <a href="https://www.cmu.edu/engage/alumni/events/campus/spring-carnival/index.html">Spring Carnival</a>.

Each project tackled implementation of concepts from the course. 
Project 1: Linearization of the state space system equations. Develop a PID controller for the system.
Project 2: Check the controllability and stabilizability of the system. Design a full-state feedback controller using pole placement.
Project 3: Design an optimal controller.
Project 4: Implement an EKF SLAM

**Model**

<div style="text-align: center;">
<table border="0">
 <tr>
  <td><img src='/images/MCT_project/Bicycle1.png' alt="bicycle model" class="center"></td>
  <td><img src='/images/MCT_project/Bicycle2.png' alt="slip conditions" class="center"></td>
 </tr>
</table>
</div>

<p style="text-align:center"> <i>System Model. Left: Bicycle model, Right: Tire slip angle</i></p>

The car in our simulation is modeled as a two wheeled vehicle with longitudinal and lateral dynamics. The system equations are as follows:

[INSERT SYS EQS]

The observable states are given as:

[INSERT OBSERVABLE EQS]

The system satisfies physical constraints that are defined as:

[INSERT PHYS EQS]

for the model parameters defined in table below.

| Name       | Description                                  | Unit        | Value                |
|------------|----------------------------------------------|-------------|----------------------|
| (ẋ, ẏ)    | Vehicle's velocity along the direction of the vehicle frame | m/s   | State                |
| (X, Y)     | Vehicle's coordinates in the world frame    | m           | State                |
| ψ, ψ̇      | Body yaw angle, angular speed               | rad, rad/s  | State                |
| δ or δ_f   | Front wheel angle                           | rad         | Input                |
| F          | Total input force                           | N           | Input                |
| m          | Vehicle mass                                | kg          | 1000                 |
| l_r        | Length from rear tire to the center of mass | m           | 0.82                 |
| l_f        | Length from front tire to the center of mass| m           | 1.18                 |
| C_α        | Cornering stiffness of each tire            | N           | 20000                |
| I_z        | Yaw inertia                                 | kg·m²       | 3004.5               |
| F_pq       | Tire force, p ∈ {x, y}, q ∈ {f, r}          | N           | Depends on input force |
| f          | Rolling resistance coefficient              | N/A         | 0.025                |
| delT       | Simulation timestep                         | sec         | 0.032                |

[INSERT TABLE]
<table style="text-align: center; margin: auto;">
  <thead>
    <tr>
      <th>Name</th>
      <th>Description</th>
      <th>Unit</th>
      <th>Value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>(ẋ, ẏ)</td>
      <td>Vehicle's velocity along the direction of the vehicle frame</td>
      <td>m/s</td>
      <td>State</td>
    </tr>
    <tr>
      <td>(X, Y)</td>
      <td>Vehicle's coordinates in the world frame</td>
      <td>m</td>
      <td>State</td>
    </tr>
    <tr>
      <td>ψ, ψ̇</td>
      <td>Body yaw angle, angular speed</td>
      <td>rad, rad/s</td>
      <td>State</td>
    </tr>
    <tr>
      <td>δ or δ_f</td>
      <td>Front wheel angle</td>
      <td>rad</td>
      <td>Input</td>
    </tr>
    <tr>
      <td>F</td>
      <td>Total input force</td>
      <td>N</td>
      <td>Input</td>
    </tr>
    <tr>
      <td>m</td>
      <td>Vehicle mass</td>
      <td>kg</td>
      <td>1000</td>
    </tr>
    <tr>
      <td>l_r</td>
      <td>Length from rear tire to the center of mass</td>
      <td>m</td>
      <td>0.82</td>
    </tr>
    <tr>
      <td>l_f</td>
      <td>Length from front tire to the center of mass</td>
      <td>m</td>
      <td>1.18</td>
    </tr>
    <tr>
      <td>C_α</td>
      <td>Cornering stiffness of each tire</td>
      <td>N</td>
      <td>20000</td>
    </tr>
    <tr>
      <td>I_z</td>
      <td>Yaw inertia</td>
      <td>kg·m²</td>
      <td>3004.5</td>
    </tr>
    <tr>
      <td>F_pq</td>
      <td>Tire force, p ∈ {x, y}, q ∈ {f, r}</td>
      <td>N</td>
      <td>Depends on input force</td>
    </tr>
    <tr>
      <td>f</td>
      <td>Rolling resistance coefficient</td>
      <td>N/A</td>
      <td>0.025</td>
    </tr>
    <tr>
      <td>delT</td>
      <td>Simulation timestep</td>
      <td>sec</td>
      <td>0.032</td>
    </tr>
  </tbody>
</table>



The trajectory of the vehicle was provided to students as a csv file that the contains (x, y) of the track as shown in [TRACK IMAGE]

<div style="text-align: center;">
<table border="0">
 <tr>
  <td><img src='/images/MCT_project/buggy_track1.png' alt="buggy track irl" class="center"></td>
  <td><img src='/images/MCT_project/buggy_track2.png' alt="buggy track webots" class="center"></td>
 </tr>
</table>
</div>

<p style="text-align:center"> <i>Buggy track trajectory. Left: Satellite image, Right: Webots simulation</i></p>

**Methodology**


In this project, we used Python to develop our controllers and observers and Webots to run our simulations. We also used Matlab to perform calculations for controller design as needed. The simulation code flow is shown below.
[simulation code flow image]

The driver functions that control the car take the desired steering angle δ and a throttle input ranging from 0 to 1 derived from the desired longitudinal force F.

**Results**
To evaluate the performance of the simulation model, I tested the model on the buggy track around CMU, and evaluated the time to complete the track and the deviation from the main path. The model was able to complete the track in less than 120 seconds and had an average deviation less than 3 meters from the optimal track path. This proved to work substantially better than the real world buggy that are raced every year around CMU.

This project was successfully able to design a controller for a tractor to autonomously complete the buggy track around CMU in a time of less than 120 seconds and have a minimum deviation of less than 3 meters. It was able to implement different iterations of the lateral controller to clear the performance evaluations.


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


**References**

24-677 Project Manuals

Rajamani Rajesh. Vehicle Dynamics and Control. Springer Science & Business Media, 2011.

Kong Jason, et al. “Kinematic and dynamic vehicle models for autonomous driving
control design.” Intelligent Vehicles Symposium, 2015.

cmubuggy.org, https://cmubuggy.org/reference/File:Course_hill1.png

“PID Controller- Manual Tuning.” Wikipedia, Wikimedia Foundation, August 30th, 2020. https://en.wikipedia.org/wiki/PID_controller#Manual_tuning
