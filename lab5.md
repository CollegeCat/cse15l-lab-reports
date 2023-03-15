# Lab 5 Report

For this last lab, I will choose the topic of the task we did for lab 4 report, and week 7 lab.

In the competition we had to follow these steps:

1. Setup Delete any existing forks of the repository you have on your account
2. Setup Fork the repository
3. The real deal Start the timer!
4. Log into ieng6
5. Clone your fork of the repository from your Github account
6. Run the tests, demonstrating that they fail
7. Edit the code file to fix the failing test
8. Run the tests, demonstrating that they now succeed
9. Commit and push the resulting change to your Github account (you can pick any commit message!)

Inside of the week 7 lab, we are provided some tips on how to speed up the process to complete these steps. 
Like learning some shortcuts on the keyboard, copying and pasting, etc. But we can also save oursleves a lot more time if we were to say,
write a bashscript that does a lot of the work for us.

Writing a script that looks similar to this (assuming we do the first 2 steps of the set up before executing) :

```
set -x

ssh cs15lwi23axr@ieng6.ucsd.edu

rm -rf lab7
git clone git@github.com:CollegeCat/lab7.git
cd lab7/

javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
```
In this example, we will of course assume that the address of the repository will be named the same every time, and that the tests will compile.
Since we are writing a script that is very specific to the competition, we do not need to check for outputs on most lines (unlike the grader).

`set -x` *is an important component, since this will make the script output everything that is currently executing, almost as if we were running the tests ourselves.*

After we get the output, we can see what tests failed from the output, and manually fix them. (Sadly my knowledge is not enough to make an sh file that runs nano and fixes the bugs).

Then we might run a second executable that checks the output, commits and pushes.

```
set -x
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
git commit -m "Updadted"
git push
```

And this way, we are able to complete the tournament task with 2 executable scripts. As I am sure there are probably more efficient ways to run this, such as running and doing everything on a single executbale, I will just say this is still more efficient than typing everything yourself.

