---
title: "CMU Buggy Control Project"
excerpt: "24-677 course project, Carnegie Mellon University <br/><img src='/images/MCT_project/buggy_cover.png'>"
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

<img src='/images/MCT_project/Bicycle1.png' alt="bicycle model" class="center">
<p style="text-align:center"> <i>System Model. Bicycle model</i></p>

<!--
<img src='/images/MCT_project/Bicycle2.png' alt="bicycle model" class="center">
<p style="text-align:center"> <i>System Model. Tire slip angle</i></p>
-->

The car in our simulation is modeled as a two wheeled vehicle with longitudinal and lateral dynamics. The system equations are as follows if $\dot{x} \geq 0.5$ m/s. Otherwise, since the lateral tire forces are zeros, we only consider the longitudinal model.

$$
\dot{y} = -\psi \dot{x} + \frac{2C_{\alpha}}{m} \left( \cos \delta \left( \delta - \frac{\dot{y} + l_r \dot{\psi}}{\dot{x}} \right) - \frac{\dot{y} - l_r \dot{\psi}}{\dot{x}} \right)
$$

$$
\dot{x} = \psi \dot{y} + \frac{1}{m} (F - fm g)
$$

$$
\dot{\psi} = \frac{2l_f C_{\alpha}}{I_z} \left( \delta - \frac{\dot{y} + l_r \dot{\psi}}{\dot{x}} \right) - \frac{2l_r C_{\alpha}}{I_z} \left( \frac{\dot{y} - l_r \dot{\psi}}{\dot{x}} \right)
$$

$$
\dot{X} = \dot{x} \cos \psi - \dot{y} \sin \psi
$$

$$
\dot{Y} = \dot{x} \sin \psi + \dot{y} \cos \psi
$$


The observable states are given as:

$$
y = 
\begin{bmatrix}
\dot{x} \\
\dot{y} \\
\psi \\
X \\
Y \\
\dot{\psi}
\end{bmatrix}
$$

The system satisfies physical constraints that are defined as:

$$
|\delta| \leq \frac{\pi}{6} \text{rad}
$$

$$
F \geq 0 \quad \text{and} \quad F \leq 16000 \text{N}
$$

$$
\dot{x} \geq 10^{-5} \text{m/s}
$$

for the model parameters defined in table below.

| Name       | Description                                  | Unit        | Value                |
|------------|----------------------------------------------|-------------|----------------------|
| $\left(\dot{x}, \dot{y}\right)$    | Vehicle's velocity along the direction of the vehicle frame | m/s   | State                |
| $\left(X, Y\right)$     | Vehicle's coordinates in the world frame    | m           | State                |
| $\psi$, $\dot{\psi}$     | Body yaw angle, angular speed               | rad, rad/s  | State                |
| $\delta$ or $\delta_f$   | Front wheel angle                           | rad         | Input                |
| $F$          | Total input force                           | N           | Input                |
| $m$          | Vehicle mass                                | kg          | 1000                 |
| $l_r$        | Length from rear tire to the center of mass | m           | 0.82                 |
| $l_f$        | Length from front tire to the center of mass| m           | 1.18                 |
| $C_\alpha$        | Cornering stiffness of each tire            | N           | 20000                |
| $I_z$        | Yaw inertia                                 | kg·m²       | 3004.5               |
| $F_pq$       | Tire force, p ∈ {x, y}, q ∈ {f, r}          | N           | Depends on input force |
| f          | Rolling resistance coefficient              | N/A         | 0.025                |
| delT       | Simulation timestep                         | sec         | 0.032                |

<!--
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
-->


The trajectory of the vehicle was provided to students as a csv file that the contains (x, y) of the track as shown below.

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

<img src='/images/MCT_project/sim_codeflow.png' alt="sim model" class="center">
<p style="text-align:center"> <i>Simulation code flow</i></p>

The driver functions that control the car take the desired steering angle δ and a throttle input ranging from 0 to 1 derived from the desired longitudinal force F.

**Results**

The controllers were tuned to meet several performance requirements for each controller in the simulation track. Criteria for a successful race were
- lap time
- maximum deviation from reference trajectory
- average deviation from reference trajectory

The best simulation run used an LQR controller with EKF SLAM to complete the track in less than 180 seconds and had a minimum deviation less than 5 meters from the trajectory; the results are also shown in the summary plot below.

<!--
<img src='/images/MCT_project/buggy_pid_results.jpg' alt="pid results" class="center">
<p style="text-align:center"> <i>Simulation plots for tuned PID controller</i></p>


<img src='/images/MCT_project/buggy_statefeed_results.jpg' alt="state feed results" class="center">
<p style="text-align:center"> <i>Simulation plots for tuned state feedback controller</i></p>


<img src='/images/MCT_project/buggy_lqr_results.jpg' alt="lqr results" class="center">
<p style="text-align:center"> <i>Simulation plots for tuned LQR controller</i></p>


<img src='/images/MCT_project/buggy_mpc_results.jpg' alt="mpc results" class="center">
<p style="text-align:center"> <i>Simulation plots for tuned MPC controller</i></p>
-->

<img src='/images/MCT_project/buggy_ekfslam_results.jpg' alt="ekf slam results" class="center">
<p style="text-align:center"> <i>Simulation plots for tuned EKF SLAM</i></p>


**References**

24-677 Project Manuals

Rajamani Rajesh. Vehicle Dynamics and Control. Springer Science & Business Media, 2011.

Kong Jason, et al. “Kinematic and dynamic vehicle models for autonomous driving
control design.” Intelligent Vehicles Symposium, 2015.

cmubuggy.org, https://cmubuggy.org/reference/File:Course_hill1.png

“PID Controller- Manual Tuning.” Wikipedia, Wikimedia Foundation, August 30th, 2020. https://en.wikipedia.org/wiki/PID_controller#Manual_tuning
