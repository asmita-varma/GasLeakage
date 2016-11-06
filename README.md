<h1>GAS LEAKAGE DETECTION<h1>

<h2>Abstract</h2>

The importance of safety for public and private structures has been growing drastically, but still these structures are not as efficient when it comes to these features. The existing traditional methods employed are either expensive for installation or not smart enough. In the era of Internet of Things(IoT), interconnected smart devices change this scenario by  connecting a plethora of devices together and to the internet. This project aims at detecting any Gas Leakage in laboratory and raise the usual sound and light alarm but along with it the IoT oriented Gas Leakage Detection System also notifies the person in charge with the help of a call over phone and an e-mail. Also, the sensor data is continuously updated on cloud in order to keep a track of all the readings and perform analytics on it to make predictions of any upcoming harmful situations. 

<h2>Objective</h2>

Different types of gases are used for various purposes in our surrounding. It is very important to keep a check on the concentration levels of the gases in our surrounding as some of the gases, when exceed the safe concentration level, are flammable under the room temperature and humidity condition. A gas detection system checks for the concentration levels and alerts people about the leakage and try to prevent any kind of mishap. This project is about a gas leakage detection system that does not only alerts people by alarm but also sends an email to the concerned and give them a call so that even if they are not present in the room at the moment, they are made aware of the situation so that they could act immediately. In addition to this, this system also records the reading of the sensor and uploads it to the cloud so that the readings could be analysed and help prevent any mishap by making predictions based on the data. 

<h2>Components Required</h2>

1. Arduino UNO (ATMEGA328)
2. Ethernet Shield (W5100)-2
3. GSM Module (SIM900A)
4. *Gas Sensor- MQ2
5. Piezo Buzzer
6. Ethernet Cable-2
7. Breadboard
8. Jumper wires- male to female and male to male


*Note: The sensor value only reflects the approximated trend of gas concentration in a permissible error range, it DOES NOT represent the exact gas concentration. The detection of certain components in the air usually requires a more precise and costly instrument, which cannot be done with a single gas sensor. If your project is aimed at obtaining the gas concentration at a very precise level, then we do not recommend this gas sensor.


<h2>Software and Libraries required</h2>

<ul type="disk">
<li>Software- Latest version of Arduino IDE</li>
<li>Create an account on ThingSpeak, create a channel and add a field in the channel to which all the data will be uploaded. This will also provide a Write API Key which will be used in the code for uploading sensor values to cloud.</li>
(ThingSpeak is an IoT platform that enables you to collect, store, analyze, visualize, and act on data from sensors or actuators, such as Arduino®, Raspberry Pi™, BeagleBone Black, and other hardware.) 
<li>A Temboo account and a Gmail account is necessarily required for this project.</li>
(Temboo is a site that spins around IoT. They also support sending mail by their library that is already implemented inside Arduino IDE by default.)
<li>Header files</li>
1. Temboo.h (This is present by default in the Arduino IDE.)<br>
2. TembooAccount.h (A file needs to be made which includes information regarding our account on Temboo as well as Gmail. The content is auto generated along with the code in temboo.)
</ul>


<h2>Circuit Diagram</h2>

<img src = "gasDet.png">



<h2>Stepwise Procedure</h2>
<ol>
<li>Create a ThingSpeak, Gmail and Temboo Account.</li>
<li>Create a Channel on ThingSpeak and add required field. Under the API Keys section a Write API Key is specified. It should be noted as it is required in the code of uploading values to ThingSpeak.</li>
<li>Two arduino UNO board and Ethernet Shield have been used in this project.</li>
<li>First shield is stacked over the arduino and connected with the sensor. This set up is used for uploading values to cloud.</li>
<li>Second shield is stacked over the second arduino and connected with GSM Module and sensor. This set up will be used for sending email and making a call.</li>
<li>This link is the <a href="https://docs.google.com/document/d/1vNuvJTlB42lO_MS-T16ujX6l26VtwW5XcqShtU7TNuE/edit?usp=sharing">Procedure</a> for email sending part.</li>
<li>After the above Procedure is completed, we can  go ahead for making the connections. </li>
<li><a href="https://docs.google.com/document/d/1dOiJYuyDyumG8RJXtqYNS0hyhyjRN6rBwwnIX3epk-A/edit?usp=sharing">Make Connections</a>. This link provides the steps for making the connections.</li>
</ol>

<h2>Code</h2>

<ul type="disk">
<li> <a href="https://github.com/asmita-varma/GasLeakage/blob/master/Gas_Leakage_Detection/Header%20File">Header File</a></li>
<li> <a href="https://github.com/asmita-varma/GasLeakage/blob/master/Gas_Leakage_Detection/Alert%20User%20-%20alarm,call,%20e-mail">Alert User - alarm,call, e-mail</a></li>
<li> <a href="https://github.com/asmita-varma/GasLeakage/blob/master/Gas_Leakage_Detection/Cloud%20Updation">Cloud Updation</a></li>

<h2>Snapshots of Project</h2>
