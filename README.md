# Moodle Automated Testing Framework!

Welcome to the **Moodle** Automated Testing framework! Moodle is a free and open-source learning management system (LMS) written in PHP and distributed under the GNU General Public License. Moodle is used for blended learning, distance education, flipped classroom and other e-learning projects in schools, universities, workplaces and other sectors.

# The Goal

The testing framework runs on Ubuntu (Linux/Unix). The testing framework will be invoked by a single script fcalled **“./scripts/runAllTests.sh”** and will access a folder containing test case specifications. Each of these files will conform to a test case specification template. Each test case specification file thus contains the meta-data that the framework needs to setup and execute the test case and collect the results of the method being tested.

## Getting Started

- To run the framework simple clone the project to your machine.

    > git clone https://github.com/csci-362-01-2019/Home-School-Drop-Outs.git


- Navigate to the scripts directory located in the TestAutomation directory.
    > cd ../pathToProject/TestAutomation/scripts

- Run the testing framework with the following command.
    > bash ./runAllTests.sh

# The Framework

At the framework’s highest level, it can be broken down into six steps. Start the script, Run all test cases, store expected outputs, compare to the output, write to JSON, display web page. At any step during the process, if what the script is looking for is not there, skip the test case. 
<br />

<a target="_blank"><img width="300" height="300" src="https://raw.githubusercontent.com/ctlong12/AutomatedTestingFramework/master/README_IMAGES/HighLevel.png" border="0" alt="High Level Overview"></a>

<br />

First, the runAllTests.sh bash script is ran. Once the script begins running, it looks for test cases in the test case folder. Once the file is found, it is parsed and broken up into an array of values, this is why the format of the test case is important. The expected output (specified in the test case) is written into an oracle file to test for correctness later on. Once all values are parsed and the script determines that it is a valid test case, it then determines whether or not the method to test is valid. If it is a valid test, the script then runs the method with the input from the test case and checks the output with the oracle to test whether or not the output matches the oracle. The values from the array are then stored in a JSON formatted file and then the script restarts until it iterates through the entire test case folder. Once completed, the JSON file is parsed and sent into an HTML document to output all results into a table.
