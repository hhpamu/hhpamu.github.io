---
title: "Control Stabilization for Bi-Quadcopter Payload Delivery System"
excerpt: "24-774 course project, Carnegie Mellon University"
collection: portfolio
---
<!--


This is a final project for <a href="https://courses.illinois.edu/schedule/2022/spring/ME/470">ME 470: Senior Design Project</a>.


In this project, the design challenge required students to build a 3D Printer enclosure that would enable the Grainger <a href="https://www.library.illinois.edu/enx/idea-lab/">Innovation, Discovery, Design, and Data (IDEA)</a> Lab to process longer, larger, and more complex print times that may take multiple days. This would provide them with additional capabilities to print more types of 3D models for their supported Senior Design, Capstone, and other research and learning projects. At the time of proposal, the IDEA lab personnel were limited by print times as there were concerns with safety by running machines for long periods of time without supervision. By providing the the following functionality, it would provide them with the ability to process more complex and larger models:
* Fire sensor that would trigger a fire extinguisher or other fire suppression system in the enclosure
* Webcam that would be networked so to remotely monitor the printers
* Compartment to house 3D printer filament to better control humidity exposure as humidity caused a filament brittleness
* Thermometer and humidity sensor to monitor temperature and humidity inside the enclosure
* Dehumidifier inside to again, better control humidity
* Ports for air ventilation, including mounted system fans to expel hot air
* Accommodate different sized 3D Printers including the Original Prusa i3 MK3S+, Lulzbot Taz 5, Lulzbot Taz Pro, Lulzbot Taz Pro XT, and Elegoo Mars and Elegoo Saturn 3D Printers
* Maintain optimum conditions
  * Temperature: 62 to 68 degrees Fahrenheit
  * Humidity: 0-15%
 

My team consisted of <a href="https://www.linkedin.com/in/lucas-hari/">Lucas Hari</a>, <a href="https://www.linkedin.com/in/ryansjacobs/">Ryan Jacobs</a>, <a href="https://www.linkedin.com/in/naman-jain-34a2b317a/">Naman Jain</a>, <a href="https://www.linkedin.com/in/alpkara1999/">Alp Kara</a> and Myself.


Here is the poster we presented at the trade show (open image in a new tab better resolution)


<img src='/images/ME 470 3D-Printer Enclosure Poster.jpg' alt="2022_ME170_Trade_Show_poster" class="center">


Our final presentation is available to view <a href="https://drive.google.com/file/d/1CiiN_F4HlnuYSA_M9JqTKd2Pi15-rHMN/view?usp=sharing">here</a>


Our final report is available to view <a href="https://drive.google.com/file/d/1fEH2LtMO-KjH0yI0g04wTUAGdjU6A4sB/view?usp=sharing">here</a>


-->


The Multi-feature Enclosure for 3D Printing Equipment, as part of the <a href="https://courses.illinois.edu/schedule/2022/spring/ME/470">Mechanical Engineering Senior Design Project</a>, advances 3D printing capabilities within academic and research environments. This project, undertaken for the <a href="https://www.library.illinois.edu/enx/idea-lab/">Innovation, Discovery, Design, and Data (IDEA)</a> Lab, aimed to address the limitations faced by the lab in processing long-duration, intricate 3D printing tasks. The IDEA Lab has six different 3D printer models. These 3D printers are used by undergraduates, postgraduates, and faculty members for a wide variety of senior design projects, capstones, and research projects. Typical prints can be large in volume (11 x 11 x 27 in.), have complex geometry, and take several days to print. As a result, 3D printers are run for long periods of time without supervision. Currently, IDEA Lab does not control temperature and humidity for 3D printing. The 3D printer filament is hygroscopic, meaning the filament absorbs moisture from the air during prolonged exposure. The expansion due to humidity alters the print resolution, and thus decreases print quality, and also raises the likelihood of a print failure due to a clogged nozzle. The IDEA Lab needed to limit the duration, complexity, and size of prints to reduce the possibility of failing or causing a fire. By designing an enclosure equipped with safety and efficiency-enhancing features such as a fire sensor, remote monitoring webcam, humidity-controlled filament storage, and optimized temperature and humidity conditions, the project sought to safely extend the operational time of printers. This innovation not only facilitates the lab's ability to undertake more complex and larger-scale 3D printing projects but also contributes to the broader educational and research goals by enabling the production of diverse and intricate 3D models. 


<img src='/images/ME470_project/ME 470 3D-Printer Enclosure Poster.jpg' alt="2022_ME170_Trade_Show_poster" class="center">
<p style="text-align:center"> <i>The poster we presented at the trade show (open image in a new tab better resolution)</i></p>


The project began with identifying common issues in 3D printing such as print failures due to temperature fluctuations, poor humidity control, typical ranges of temperature and humidity for optimal printing and failure. Fires caused by 3D printers are often undocumented, making it difficult to quantify, but many incident reports found online indicated that unsupervised prints increase the risk of a fire. More commonly, 3D prints can fail while unattended, resulting in wasted time and printer material. Initial research along with a comprehensive literature review found that these problems are addressed by DIY enthusiasts by using an enclosure on their 3D printer, filament or both. The enclosure also needed to be capable of accommodating multiple 3D printer models, with a particular focus on the largest, the Lulzbot TAZ Pro XT. This information guided the design process of our enclosure. 


<img src='/images/ME470_project/Screenshot 2023-12-06 183644.png' alt="hardware" class="center">
<p style="text-align:center"> <i>Hardware used</i></p>


Once ideation was complete, the team proceeded to design a cost-effective frame by leveraging T-slot aluminum extrusions that allow for an array of modular attachment options. The walls were constructed from clear acrylic panels allowing the user to view the 3D printer easily. A Peltier electrothermal intake fan supplies cool air into the enclosure while an exhaust fan pushes hot air out of the enclosure. These fans toggle on and off when the detected temperature from the temperature sensor surpasses the upper bound of the ideal temperature range for 3D printing. Silica gel sits inside the enclosure to remove moisture from the air, and a dry box houses the filament spool for further humidity control. A webcam live streams video through OctoPrint on the Raspberry PI 4 to the end user’s mobile device for remote viewing. OctoPrint also allows users to start/stop/cancel prints and see real-time temperature and humidity data from their mobile device. The spaghetti detective AI-based print failure detection was also added to warn the user by a text message or email. Finally a fire suppression system was included using the commercially available Blazecut system. 


<img src='/images/ME470_project/Screenshot 2023-12-06 183518.png' alt="Final build" class="center">
<p style="text-align:center"> <i>The final prototype</i></p>


The project's effectiveness was evaluated based on its ability to maintain optimal printing conditions within a specified temperature (62-68°F) and humidity (0-15%) range, as well as on its modularity and ease of assembly. The evaluation also considered the successful integration of temperature and smoke sensors, the webcam, and a user-friendly interface for remote monitoring. The team successfully built one cost-effective enclosure to house the IDEA Lab’s new Taz Pro XT printer. The Taz Pro XT is the largest 3D printer model in the IDEA Lab, making the enclosure viable for all six 3D printer models in the IDEA Lab. Furthermore, this enclosure design meets all the design criteria proposed by the sponsor, and additional enclosures can be built for all IDEA Lab printers cost-effectively at $1677.85 per enclosure. Replicability is ensured with thorough instructions for building the frame, and for using the control systems. Upon testing, The cooling system reduced the steady-state enclosure temperature by more than 4°F for the floor and ceiling temperatures and did not have a significant effect on humidity as expected.



Our final presentation is available to view <a href="https://drive.google.com/file/d/1CiiN_F4HlnuYSA_M9JqTKd2Pi15-rHMN/view?usp=sharing">here</a>


Our final report is available to view <a href="https://drive.google.com/file/d/1fEH2LtMO-KjH0yI0g04wTUAGdjU6A4sB/view?usp=sharing">here</a>


The team consisted of <a href="https://www.linkedin.com/in/lucas-hari/">Lucas Hari</a> working on controls, <a href="https://www.linkedin.com/in/ryansjacobs/">Ryan Jacobs</a> involved in temperature and humidity monitoring, <a href="https://www.linkedin.com/in/naman-jain-34a2b317a/">Naman Jain</a> on fire suppression, <a href="https://www.linkedin.com/in/alpkara1999/">Alp Kara</a> and Myself working on structures and integration.
