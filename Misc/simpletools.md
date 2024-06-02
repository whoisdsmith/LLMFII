---
aliases:
  - simpleTools
tags:
  - "#python"
  - "#software-development"
  - "#developer-tools"
  - "#cli"
  - "#example-code"

  - "#simple-tools"
  - "#python-scripts"
  - "#tool-usage"
---
# simpleTools
This Repository is intended to create and maintain simple Tools that anyone can use without having to code. The tools can be as simple as extracting few keywords from text, but with lot of options and customizations. \
Invoking the tools should be as simple as Double Clicking the Python files. Any extra requirements will be mentioned explicitly in the python files itself or an Usage example will be provided. 

### simpleLogFilter.py
Select Input Location, 
Select Output Location,
Enter Output Filename if required,
Enter Keyword(s) (comma separated), 
Check the suggestions option to get more keyword options. 
Click on Submit and then click on Open Output File Location Button to go to the output location.


![image](https://user-images.githubusercontent.com/46163555/154674017-ec517875-6015-426c-8ef7-85006e21a45a.png)

### Python Modules Installation
pip install PySimpleGUI


### simpleUMLGenerator
![image](https://user-images.githubusercontent.com/27662483/155001410-b3ab267e-4cbb-4712-abf4-3314df8fcde4.png)

### Pre-requisites
pip install PysimpleGUI \
pip install pylint \
Install GraphViz software from : https://graphviz.org/download/ \
You need to install Graphviz with the option "Add Graphviz to the System PATH for all users". \
If the python module does not contain <__ init __ .py>, add an empty <__ init __ .py> file in the module.

### simplePy2Exe
This tool generates exe from a python file. It uses pyinstaller internally to generate the executable.

<img width="387" alt="py2exe" src="https://user-images.githubusercontent.com/27662483/155382524-2d5a131d-3916-481a-931e-91581da10f28.PNG">

### Pre-requisites
python3 -m pip install PysimpleGUI \
python3 -m pip install pyinstaller 

### simpleFileUtility
This tool helps in splitting a single big file into smaller chunks or merge multipe chunks of files into a single file. The testing is done only
on csv files. Support for other file types will be added later.

<img width="373" alt="SimpleFileUtility" src="https://user-images.githubusercontent.com/27662483/157937722-7f372cb4-dc34-4437-817a-4affa6fb2f2b.PNG">

### Pre-requisites
python3 -m pip install PysimpleGUI \
python3 -m pip install pandas 

### simpleParamiko
This tool helps in executing Linux commands remotely from Windows machine using Paramiko. The user can send multiple linux command at once and get the command output in the Output text box in the Windows machine itself.
<img width="723" alt="simpleParamiko" src="https://user-images.githubusercontent.com/27662483/163843899-4a7e7c68-7e8a-44fe-b686-5289be2e0460.PNG">
### Pre-requisites
python3 -m pip install paramiko
