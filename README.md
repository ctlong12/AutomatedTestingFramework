
<p align="center">
  <img width="300" height="300"               src="https://github.com/ctlong12/AutomatedTestingFramework/blob/master/README_IMAGES/moodle-logo.png" border="0" alt="MVC">
</p>

# Moodle Automated Testing Framework!

Welcome to the **Moodle** Automated Testing framework! Moodle is a free and open-source learning management system (LMS) written in PHP and distributed under the GNU General Public License. Moodle is used for blended learning, distance education, flipped classroom and other e-learning projects in schools, universities, workplaces and other sectors.

# The Goal

The testing framework runs on Ubuntu (Linux/Unix). The testing framework will be invoked by a single script fcalled **“./scripts/runAllTests.sh”** and will access a folder containing test case specifications. Each of these files will conform to a test case specification template. Each test case specification file thus contains the meta-data that the framework needs to setup and execute the test case and collect the results of the method being tested.

## Getting Started

- To run the framework simple clone the project to your machine.
```
    git clone https://github.com/csci-362-01-2019/Home-School-Drop-Outs.git
```

- Navigate to the scripts directory located in the TestAutomation directory.
```
    cd ../pathToProject/TestAutomation/scripts
```
- Run the testing framework with the following command.
```
    bash ./runAllTests.sh
```
# The Framework

At the framework’s highest level, it can be broken down into six steps. Start the script, Run all test cases, store expected outputs, compare to the output, write to JSON, display web page. At any step during the process, if what the script is looking for is not there, skip the test case. 
<br />
<br />

<a target="_blank"><img width="950" height="175" src="https://raw.githubusercontent.com/ctlong12/AutomatedTestingFramework/master/README_IMAGES/Overview_General.png" border="0" alt="High Level Overview"></a>

<br />

## Framework Overview

First, the runAllTests.sh bash script is ran. Once the script begins running, it looks for test cases in the test case folder. Once the file is found, it is parsed and broken up into an array of values, this is why the format of the test case is important. The expected output (specified in the test case) is written into an oracle file to test for correctness later on. Once all values are parsed and the script determines that it is a valid test case, it then determines whether or not the method to test is valid. If it is a valid test, the script then runs the method with the input from the test case and checks the output with the oracle to test whether or not the output matches the oracle. The values from the array are then stored in a JSON formatted file and then the script restarts until it iterates through the entire test case folder. Once completed, the JSON file is parsed and sent into an HTML document to output all results into a table.

<br />

<a target="_blank"><img width="950" height="700" src="https://raw.githubusercontent.com/ctlong12/AutomatedTestingFramework/master/README_IMAGES/Test%20Cases%403x.png" align = "right" border="0" alt="High Level Overview"></a>

<br />
<br />

< br />

## Adding New Methods

To provide users with a more flexible and interactive experience, the framework has been modified not only to accept new test cases, but also new moodle methods. The architecture which runs all the test cases remains the same. What does change is the process before running all the tests. Before running all of our tests, our bash scripts checks the client “executables” directory to see if any new methods or test cases have been added by a user. If new methods were added, we cycle through them and attempt to construct a new method. To construct a new method, we first look through the component (given to us by the method case) to find the name of the method we wish to extract. From there, we grab the entire line where the method is location and all lines following up until the functions end.

<br />

<a target="_blank"><img width="950" height="600" src="https://raw.githubusercontent.com/ctlong12/AutomatedTestingFramework/master/README_IMAGES/MethodTesting.png" border="0" alt="Method Overview"></a>

<br />

## Dynamic Driver Overview

If the method is constructed correctly then we need to update the driver to account for the new method. The framework has a flexible driver than can be expanded upon to account for any new methods the testing framework gets. We are able to add new methods into our testing framework due to the implementation of a expandable/flexible driver. What this means is that if a new method is added then the driver will be updated to account for the new method that it received. The process of adding new methods to the driver starts with the creation of the require statement. This require statement is the same name of the method we are testing, it is added using a “sed” command directly after the last require statement in the file. The function that follows is a simple php method that calls executes the method. The input accepts an array of arguments which makes this flexible enough to account for a functions with any given amount of parameters. Once the require statement is added, the updated version of the “driver.php” file is stored in the “TestCasesExecutables” directory. From there we have a new updated driver that has accounted for any new methods that have been added.

<br />

<p align="center">
  <img width="750" height="500" src="https://raw.githubusercontent.com/ctlong12/AutomatedTestingFramework/master/README_IMAGES/Driver)_Update.png" border="0" alt="Dynamic Driver"></a>
</p>

<br />



## Client Side Using Laravel 



To diplsay the results of our test cases, we will be using a PHP Web Application Framework called Laravel. Laravel is a free, open-source PHP web framework, created by Taylor Otwell. The goal of Laravel is to aid the development of web applications following the model view controller (MVC) architectural pattern. Some of the features of Laravel are a modular packaging system with a dedicated dependency manager, and different ways for accessing relational databases. 

Utilizing the power behind this framework also gives us the opportunity to implement a more robust client side to the already robust testing framework. User authentication, and the ability to create test cases and methods directly from the client side are two of the main features implemented through the Laravel framework.

### The Model View Controller Architecture 



The Model View Controller (usually known as MVC) is a software design pattern commonly used for developing user interfaces which divides the related program logic into three interconnected elements.​ The model represents the data, and does nothing else. The model doesn’t depend on the controller or the view. The view displays the model data, and sends user actions (e.g. button clicks) to the controller.

<br />
<p align="center">
  <img width="700" height="600"               src="https://raw.githubusercontent.com/ctlong12/AutomatedTestingFramework/master/README_IMAGES/MVC.png" border="0" alt="MVC">
</p>
<br />

