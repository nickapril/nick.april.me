---
layout: post
title:  "Rails Web Application"
date:   2017-05-30 00:00:00
img: TA-main.png
description: This Ruby on Rails Web application was built last spring to help improve student learning in large university classes. TA OnDemand standardizes teaching assistant office hour scheduling and provides a space for virtually hosted office hours. This application will encourage interaction among teaching assistants and students and therefore improve the quality of student learning.
---

TA OnDemand consists of three main features:
1. Dynamic scheduler 
2. Appointments
3. Live chat

### Dynamic Scheduler
The scheduler feature runs on JavaScript.

### Instant Messaging
The Live Chat feature uses Action Cable to seamlessly integrate WebSockets with the rest of our Rails application. It provides a JavaScript framework for developers and allows easy access to our models written with Active Record. 

We built the Live Chat feature so it can withstand multiple channels from a single user, allowing someone to hold many private conversations at once.
