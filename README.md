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


### Step 3 Modification of JQF to print out trace events

For this step we modified the following files **Noguidance.java** and **Coverage.java**

**Noguidance.java** has a function named ‘generatecallback’ that passes the TraceEvent to another class called **Coverage.java** through a class function called ‘handleEvent’.

‘handleEvent’ applies a visitor pattern to handle the corresponding TraceEvent type, which can be [callEvent,ReturnEvent,BranchEvent,etc]. When the visitor is applied to the TraceEvent, it will execute the corresponding  visitor function, which in this case is ‘visitBranchEvent’. 

We modified ‘visitBranchEvent’ to output the event Id and Branch arm for the BranchEvent.

We then Built JQF again.

**mvn package**

We then reran the following command

**../bin/jqf-random -c .:$(../scripts/classpath.sh) SimpleTest testSimpleTest 10**

Here is the output that we have for the following changes

![image](https://github.com/emira035/CS182_Project_Option_1/assets/72326644/5aa5168b-6782-40ef-b7f0-89f1ca726392)

### Step 4 Change test inputs as needed and print out the coverages

For this step we were asked to modify the source so that JQF generates the value '200' for each iteration. 

**Noguidance.java** class has a function called getInput() that returns an inputstream.This function returns a inputstream that makes regular calls random.nextInt(256) to retrieve inputs.

We modified it to create new input stream that has its read implementation to just return the value 200.

We then Built JQF again.

**mvn package**

We then reran the following command

**../bin/jqf-random -c .:$(../scripts/classpath.sh) SimpleTest testSimpleTest 10**

Here is the output that we have for the following changes

![image](https://github.com/emira035/CS182_Project_Option_1/assets/72326644/e492679b-79f0-402e-b41c-690665068c59)


For the next part of this step we were also asked to output the thread-name and event-info for all trace events.

We modified the file **Coverage.java** for this part.

in coverage.java we modified the HandleEvent function to output the current thread and the toString() value of the TraceEvent.

We then Built JQF again.

**mvn package**

We then reran the following command

**../bin/jqf-random -c .:$(../scripts/classpath.sh) SimpleTest testSimpleTest 10**

Here is the output that we have for the following changes

![image](https://github.com/emira035/CS182_Project_Option_1/assets/72326644/4782487e-8fea-49a0-8711-f8956fbf4867)








