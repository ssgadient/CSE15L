# Week 9 - Grade Server
## Code of grade.sh: 

```
rm -rf student-submission
echo "Cloning student submission..."
git clone $1 student-submission 2> /dev/null
echo "Done!"
error=0
javac -target 1.8 -cp ".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar" ListExamples.java TestListExamples.java
CP="..:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar"
cd student-submission

ls -a > fileList.txt
if [ $(grep -c "ListExamples.java" fileList.txt) -eq 0 ]
then
    echo "\"ListExamples.java\" was not found!"
    exit 1
fi

echo "Compiling..."
javac -cp $CP *.java

if [ $? -ne 0 ]
then
    echo "Compiler error!"
    exit 1
fi

echo "Done!"
echo "Running tests..."
cp ListExamples.class ..
java -cp $CP org.junit.runner.JUnitCore TestListExamples > error.txt
cp ../ListExamples.class .
if [ $(grep -c "testFilter" error.txt) -ne 0 ]
then
    let "error+=1"
    echo "[FAILED 0/1] testFilter"
else
    echo "[PASSED 1/1] testFilter"
fi

if [ $(grep -c "testMerge" error.txt) -ne 0 ]
then
    let "error+=1"
    echo "[FAILED 0/1] testMerge"
else
    echo "[PASSED 1/1] testMerge"
fi

if [ $error -eq 2 ]
then
    echo "Score: 0/2"
    echo "See error.txt file in student-submission for details"
fi

if [ $error -eq 1 ]
then
    echo "Score: 1/2"
    echo "See error.txt file in student-submission for details"
fi

if [ $error -eq 0 ]
then
    echo "Score: 2/2"
    echo "All tests passed!"
fi
```

## Student submissions:  

![Image](https://ssgadient.github.io/CSE15L/lab-8/GradeCorrected.PNG)  
![Image](https://ssgadient.github.io/CSE15L/lab-8/GradeSignature.PNG)  
![Image](https://ssgadient.github.io/CSE15L/lab-8/GradeFilename.PNG)  

## Tracing the list-methods-filename repository:  

`rm -rf student-submission` removes any previous student submission folders and returns an error code of 0. There is no standard output or error for this command. 

`echo "Cloning student submission..."` prints out that string to the terminal. This command has an error code of 0, and its standard output is "Cloning student submission...". It does not have a standard ouput. 

`git clone $1 student-submission 2> /dev/null` pulls the student-submission from github and has an error code of 0. Funnily enough, the string it produces "Cloning from https://..." is actually classified as standard error while not having a standard output, as shown by the need for the `2>` operator. 

`echo "Done!"` is another command with error code 0, stdout of "Done!" and no stderr. 

`javac -target 1.8 -cp ".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar" ListExamples.java TestListExamples.java
CP="..:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar"` has an exit code of 0. Note that this is where the wheat implementation (ie the instructor version) and the tester files are compiled. Essentially, I chose to recompile these files every student submission because I end up moving the ListExamples.class file out of the student submission folder into the main testing folder. There is no standard output or error. 

`cd student-submission` has an exit code of 0 and is no standard output or error. 

`ls -a > fileList.txt` has a standard output consisting of all the filenames in student-submission. However, it has an exit code of 0 and no standard error. 

The `if [ $(grep -c "ListExamples.java" fileList.txt) -eq 0 ]` condition is met because we can't find the ListExamples.java file in the student-submission folder. 

The echo `"echo\"ListExamples.java\" was not found!"` command runs fine with an exit code of 0, the usual standard output, and no standard error. `exit 1` however has an exit code of 1, but has no standard output or error. At this point, the file stops running, as it has been forced to exit. 