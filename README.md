# Group 0

Group members:
* Marcel Jar

## Project Overview

### Client information
For this project, I will be acting as my own client. 

I am a full time faculty member of Seneca's School of Information and Communications Technology.  Over the course of the past four years, I have taught more than ten different courses, including multiple courses in Project management. I have a B.Sc. in Electrical Engineering, as well as M.Sc. and Ph.D. degrees in Telecommunications.

I have programmed in a large number of languages in  my career, including C/C++, MATLAB/Simulink, Python, HTML/CSS/JavaScript, VHDL, Bash, Visual Basic, Assembly, and even Pascal (I am that old!), not to mention other languages that I have used in smaller projects. As a programmer, I believe that there is always a proper tool for a given problem.

### Business Statements
As a professor at Seneca, I have to work with our current Course Management System: Blackboard. This system has been adopted by a large number of prestigious universities and colleges across North America, such as Cornell University, University of Toronto, and even overseas institutions such as the University of Manchester. Nevertheless, the system's design has a number of flaws that makes some tasks much harder than necessary. Just as an example, it is impossible to export multiple assignments from one course section into another. Any faculty teaching multiple sections of the same course has to export assignments from one section into another one by one.

In order to make my own life easier in the long term, I have decided to create web applications to replace most of the functionality provided by Blackboard. My first task, which is what is being covered in this project, is to create a tool to allow members of a particular group to schedule meetings with their instructor. This schedulling tool should follow a set of rules that are discussed in the key system requirements shown below.


### Key System Requirements
In what follows, we present a list of important requirements that the system must have in order to solve the bussiness problem:

#### General Requirements
* It must be available online 24/7 and be accessible by any registerd BTR490 student, independent of their current location.
* It must be accesssible and usable on any modern browser, whether in a regular computer, or in a smartphone/tablet. I.e., it should adapt to different screen sizes.

#### Security Requirements
* It should deal with user's information in a safely manner. For instance, passwords should be stored in a hashed format.
* It must ensure that only students that have been registered by the professor are able to sign in into the website in order to schedule their appointments.
* It should mantain user's sign in authentication, even if they switch to other views.
* Under any hypothesis it can allow users to bypass authentication by using, for example, tricks such as entering complete URLs.

#### Logical Requirements 
* It should prevent users from schedulling meetings if:
  * the user hasn't signed in
  * the chosen meeting has already been picked by other group
  * the group to whom the user belongs to has already scheduled a meeting time

#### Communication Requirements
* In case an action cannot be performed, the system should let the user know the reason why. For example, if a user enters the wrong credentials, the system should let him/her know that a wrong username or password has been provided.
* In case a meeting is scheduled, the system should email all group members, as well as the instructor, letting them know when the meeting will take place.


## Technical Overview

## Use Cases
