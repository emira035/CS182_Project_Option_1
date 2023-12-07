# CS182 Project Option 1 JQF

The following repository implements changes to the files **Noguidance.java** and **Coverage.java** files. A tutorials folder was added to the repo to seperate the PUT file.

## How to run this implementation

###  Step 1 Download and install JQF

We downloaded JQF from the provided link [JQF Repo Link ](https://github.com/rohanpadhye/JQF)

In the installation folder on the terminal we executed the following command

**mvn package**

JQF should now be built. This command must be called every time changes are made to the JQF source.

###  Step 2 Fuzz the Program under Test ###

Using PUT provided us, we moved the file to the **tutorial** folder and executed the following command in the folder directly.

**javac -cp .:$(../scripts/classpath.sh) SimpleTest.java**

this command compiles the PUT file which will be used to be fuzzed.

Next we were asked to Run **Jqf-Random** on PUT for 10 Iterations

Directly in the tutorials folder we executed the following command to accomplish this.

**../bin/jqf-random -c .:$(../scripts/classpath.sh) SimpleTest testSimpleTest 10**

we received the following output as a result.

![image](https://github.com/emira035/CS182_Project_Option_1/assets/72326644/6c0ffc0f-6bac-4a00-9da6-acaa5a199e3a)







