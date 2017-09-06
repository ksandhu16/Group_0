# Group 0
* Marcel Jar
* Barb Czegel

## Project Overview

### Client information
For this project, I will be acting as my own client. It might not be the same for your specific case.

I am a full time faculty member of Seneca's School of Information and Communications Technology.  Over the course of the past four years, I have taught more than ten different courses, including multiple courses in Project management. I have a B.Sc. in Electrical Engineering, as well as M.Sc. and Ph.D. degrees in Telecommunications.

I have programmed in a large number of languages in  my career, including C/C++, MATLAB/Simulink, Python, HTML/CSS/JavaScript, VHDL, Bash, Visual Basic, Assembly, and even Pascal (I am that old!), not to mention other languages that I have used in smaller projects. As a programmer, I believe that there is always a proper tool for a given problem.

### Business Statements
As a professor at Seneca, I have to work with our current Course Management System: Blackboard. This system has been adopted by a large number of prestigious universities and colleges across North America, such as Cornell University, University of Toronto, and even overseas institutions such as the University of Manchester. Nevertheless, the system's design has a number of flaws that makes some tasks much harder than necessary. Just as an example, it is impossible to export multiple assignments from one course section into another. Any faculty teaching multiple sections of the same course has to export assignments from one section into another one by one.

In order to make my own life easier in the long term, I have decided to create web applications to replace most of the functionality provided by Blackboard. My first task, which is what is being covered in this project, is to create a tool to allow members of a particular group to schedule meetings with their instructor. This schedulling tool should follow a set of rules that are discussed in the key system requirements shown below.


### Key System Requirements
In what follows, we present a list of important requirements that the system must have in order to solve the business problem:

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
This project consists of a web application to allow students to pick time slots for their meetings with the instructor. As such, it requires a **front-end** for the students to access and perform the necessary actions, as well as a **back-end** for the information to be saved and later used to create dynamic pages. Also, it requires the whole application to be **hosted** and made available to the students. 

In this technical overview, we will discuss the technologies used in each one of these three areas: **front-end**, **back-end**, and **hosting**.

### Front-end
This web application makes use of **Bootstrap 4**, a popular *HTML*, *CSS*, and *Javascript* framework. This framework is used for the following reasons:
- It contains components, such as navbars, cards, panels, dropdowns, tabs, etc. These components make it easier to create professional looking websites.
- It posesses a number of CSS classes to make forms, buttons, and other elements to have a very polished look.
- It implements a very responsive layout tools based on **Flexbox**, which allows the application to be properly visualized in virtually any resolution. 

Note that we have chosen **Bootstrap 4**, which is still in Alpha, as opposed to  **Bootstrap 3**, which already has a stable release. This was due to the fact that the responsive layout tools have been dramatically changed from **Bootstrap 3** to **Bootstrap 4**. So, as this website has just been created, I decided not to use a framework that would soon be replaced, and probably would require major changes in the code in a few years. 

This web application also uses **JQuery**, an ubiquitous *JavaScript* library. This library was used in this project for three reasons:
- It is required by Bootstrap
- It provides the developer with a number of tools to select particular elements and respond to a number of events
- It allows users to easily send **Ajax** requests to the server. This allow modals to be used to send requests to the server and use the server response to change the current page. This is done, for example, when the user logs in.

### Back-end
This web application was written using **Django**, a Python web framework that greatly eases the creation of web applications powered by databases. **Django** is a full-stack framework that employes a model-template-view, **MTV**, pattern. In what follows, we explain what each component of the pattern does with regards to this project:

- Templates are written in *HTML* with a few Django tags to allow dynamically created content to be rendered. Templates are extensively used in this project. First, they are used to create a base page that gets extended for particular views. This avoids the need to repeate the same lines of code for elements that are common to multiple views, such as the *navbar* at the top. Second, they are used with tags such as **if-elif-else**, **for**, and **in**, to create dynamically generated  pages, using information in **JSON** format coming from views as explained below.
- Views are implemented in this proejct as Python functions that are called when a particular URL is entered, or when an **AJAX** request is performed. They return a call to render a template with a set of data in **JSON** format.
- Models in Django are implemented as Python classes that fully describe tables in the database, as well as methods to interact with the data. They can be translated by the framework into SQL code that will in turn perform CRUD operations into the database. In this project, we make extensive use of models in order to avoid the need to write down SQL code.

The chosen database engine was **SQLite** for the following reasons:
- The application does only store a few Megabytes of data, and is not expected to have a high concurrency. High-volume of data and high-concurrency are the two factors that normally prevent the use of **SQLite**. 
- All data is storedin a single file that can be downloaded, or uploaded. This will allow me to easily work off-line in the subway or on planes.
- It is the default database for Django. Hence, there is no need to change any settings. :)

### Hosting
The web application is stored in a **Linux Ubuntu 14.04** web server hosted at **Digital Ocean**. It uses **Apache 2** as the server application, **Python 3** (with **Django**) as the server-side scripting language, and **SQLite** as its database engine.

**Digital Ocean** was chosen because they provide an easy and inexpensive method to create *VMs* which can be accessed and controlled via *SSH*. Also, the company has a reputation for reliability (i.e., their servers are seldom offline), and they provide a great number of detailed tutorials about how to set up servers using different configurations with their VMs. 

## System Components

### Account Management
Used to create, edit, and delete user accounts. Only faculty personnel is allowed to access it. This component is also used to check if a user has provided the right credentials for authentication purposes.

### Meeting Time Picking Tool
Used to allow students to pick a meeting time, as well as to allow the instructor to keep track of which groups are meeting at each allocated meeting time.


## Use Cases

### User Login
**Pre-requisites**: The user has an account in the system and is currently online. 
**Actor**: Student. 
**Use Case Successful Post-conditions**: The user is authenticated by the system. 

1. The student clicks on **Login**.
2. The system brings up a modal for the user to enter his/her credentials.
3. The user enters his/her credentials and clicks on the **Login** button inside the modal.
   * The user can cancel this operation by clicking on the **cancel** button inside the modal, or by clicking anywhere outside the modal.
4. The system checks the rpovided credentials against the database and authenticates the user if there is a match.
   * The system sends an error message in case authentication fails. The user can the enter his/her credentials again.
5. After succesfully autenthicating a user, the **Login** button changes to **Settings**, which provides options such as **change password** and **logout**. 

### User Choosing a Meeting Time
**Pre-requisites**: The user has already discussed the meeting times with his colleagues and is currently online.s
**Actor**: Student.
**Use Case Successful Post-conditions**: A meeting time is allocated to the student's group and all group members get a notification by email.

1. The student clicks on a specific meeting time, from a pool of meeting times displayed on the meetings tab.
2. If the meeting time has not been taken by other groups, the system will bring up a modal asking for the student's confirmation.
   * If the meeting has been taken, the system will bring up an error modal letting the user know that he/she needs to pick a different time.
3. If the student is logged in, the system will change the meeting status from available to taken and email all group members. 
   * If the student is not logged in, the system will let the user know that he/she needs to log in to pick a meeting time (see previous use case).
