---
layout: page
title: About
permalink: /about/
---

<div>
    <ul class="contact-list">
        <li>
            {% if site.author %}
              {{ site.author | escape }}
            {% else %}
              {{ site.title | escape }}
            {% endif %}
        </li>
        {% if site.email %}
        <li><a href="mailto:{{ site.email }}">{{ site.email }}</a></li>
        {% endif %}
    </ul>
</div>

<div>
    {% include social.html %}
</div>

Software engineer. Passion for low-level technologies and embedded hardware design.


## Open Source Contributions

### [RIOT-OS](http://www.github.com/RIOT-OS/RIOT) - 2017

* A real-time multi-threading operating system that supports devices for the Internet of Things (IoT)
* Using an Atmel’s Wi-Fi module (ATWINC1500), developed the first Wi-Fi driver for the Operating System, connecting it to the IPv6/6LoWPAN networking stack. This pull request is currently under reviews being done by the RIOT developer community


## Projects

### [WolfieMouse](http://www.github.com/kbumsik/WolfieMouse) - Spring 2016 and Spring 2017

* Maze-solving robot for IEEE Region 1 Micro-mouse Competition. The mouse runs on STM32F445 microcontroller and FreeRTOS.
* Designed a mouse-sized robot that solves a 16x16 size maze by implementing Flood Fill algorithm using a customized C++ STL Deque algorithm library and robotics algorithm such as Sensor Fusion and PID motor control. 
* Designed a PCB board using KiCad (an open-source alternative to Altium), with an ARM Cortex-M4F Microcontroller (STM32F446), 2 DC motor drivers, 4 custom-designed infrared range finders.

### WolfieNet-IoT - Spring 2017

* Created a web application that allows users to control Arduino and Raspberry Pi wirelessly via an Amazon Web Service (AWS) cloud server, using protocols for the Internet of Things such as MQTT and Zigbee.
* Presented at Hack@CEWIT Major League Hackathon and won the Best Use of Amazon Web Service Prize.
* Designed architecture for the full-stack web application integrating SQLite database, extensive RESTful web API based on Python Flask web framework, and ReactJS client-side view. 


## Work

### Samsung SDS America, Software Engineer Intern - Summer 2016

* CR2 (Conference Room Reservation System) development team.
* Was responsible for developing C# .NET MVC back-end web program, including designing new database tables and Microsoft Transact-SQL transactions that can handle 500 user requests from 200 active users while preventing request conflicts.

### Republic of Korea Army, First Staff Sgt., 1117 Engineer Division - Feb. 2010 to Dec. 2011

* Developed Soldier Training Reporting System using PHP, MySQL, and JavaScript. The system provides web dashboards for training officers, replacing a Microsoft Excel-based management of the division, making it easier to keep track of around 400 soldiers’ training progress.
* Served as a network administrator in the division. Maintained Cisco L3 routers and an Ericsson telephone exchange system of the division. Obtained Korea National Certificate of Intermediate Network Administrator during the service

## Academic Research

### Localization on Robot Network and Wireless Sensor Nodes

* Developed a robot localization system using MUltiple SIgnal Classification (MUSIC) algorithm to locate multiple robots and wireless sensor nodes based on multiple Wireless Signal Strength Indicator from wireless stations. The system detects location of robots with more than 90% of accuracy.
* Implemented a wireless signal noise reduction algorithm using digital signal filters such as Kalman Filter. These filters contribute to improving accuracy from 60% to 90% by suppressing Gaussian noise and Rayleigh fading noise. 
* Designed a swarming algorithm for multiple robots using a divide and conquer strategy. A Matlab simulation tool is designed to test the algorithm easily.
