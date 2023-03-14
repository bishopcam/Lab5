# Lab Report 5 - Revisiting Researching Commands 
## Cameron Bishop
---
### My chosen command, find, for locating files within a directory

In my research I once again used the mainly the basic linux manual page https://man7.org/linux/man-pages/man1/find.1.html. It has all of the options listed and is generally the simplest explanation for the modifications.

As defined on https://www.geeksforgeeks.org/find-command-in-linux-with-examples/ The find command in UNIX is a command line utility for walking a file hierarchy. It can be used to find files and directories and perform subsequent operations on them. 

---

### -readable
The first command that I thought would be really nice is the -readable option, so it can list a more expansive list of all of the files the user can currently access and are readable by current permissions.

<code>find -readable</code>  
  
Executing this in a bash terminal results in this:
```
  .
  ./.git
  ./.git/config
  ./.git/description
  ./.git/FETCH_HEAD
  ./.git/HEAD
  ./.git/hooks
  ./.git/hooks/applypatch-msg.sample
  ./.git/hooks/commit-msg.sample
  ./.git/hooks/fsmonitor-watchman.sample
  ./.git/hooks/post-update.sample
  ./.git/hooks/pre-applypatch.sample
  ./.git/hooks/pre-commit.sample
  ./.git/hooks/pre-merge-commit.sample
  ./.git/hooks/pre-push.sample
  ./.git/hooks/pre-rebase.sample
  ./.git/hooks/pre-receive.sample
  ./.git/hooks/prepare-commit-msg.sample
  ./.git/hooks/push-to-checkout.sample
  ./.git/hooks/update.sample
  ./.git/index
  ./.git/info
  ./.git/info/exclude
  ./.git/logs
  ./.git/logs/HEAD
  ./.git/logs/refs
  ./.git/logs/refs/heads
  ./.git/logs/refs/heads/main
  ./.git/logs/refs/remotes
  ./.git/logs/refs/remotes/origin
  ./.git/logs/refs/remotes/origin/HEAD
  ./.git/logs/refs/remotes/upstream
  ./.git/logs/refs/remotes/upstream/HEAD
  ./.git/logs/refs/remotes/upstream/main
  ./.git/objects
  ./.git/objects/info
  ./.git/objects/pack
  ./.git/objects/pack/pack-a98a6300614eec431298fd6769ceb9c56831aea0.idx
  ./.git/objects/pack/pack-a98a6300614eec431298fd6769ceb9c56831aea0.pack
  ./.git/packed-refs
  ./.git/refs
  ./.git/refs/heads
  ./.git/refs/heads/main
  ./.git/refs/remotes
  ./.git/refs/remotes/origin
  ./.git/refs/remotes/origin/HEAD
  ./.git/refs/remotes/upstream
  ./.git/refs/remotes/upstream/HEAD
  ./.git/refs/remotes/upstream/main
  ./.git/refs/tags
  ./all-java.sh
  ./quiz-layout
  ./quiz-layout/classes
  ./quiz-layout/classes/biomed
  ./quiz-layout/classes/biomed/genes1.txt
  ./quiz-layout/classes/biomed/genes2.txt
  ./quiz-layout/classes/biomed/genes3.txt
  ./quiz-layout/classes/biomed/paper-about-genetics.pdf
  ./quiz-layout/classes/cse
  ./quiz-layout/classes/cse/ExampleClass.java
  ./quiz-layout/classes/cse/generics.txt
  ./quiz-layout/classes/cse/interfaces.txt
  ./quiz-layout/classes/cse/linked-list.txt
  ./quiz-layout/classes/history
  ./quiz-layout/classes/history/history-of-computing.pdf
  ./quiz-layout/classes/history/liskov.txt
  ./quiz-layout/classes/history/lovelace.txt
  ./quiz-layout/classes/history/turing.txt
  ./quiz-layout/general-notes
  ./quiz-layout/general-notes/course-plan-w23.txt
  ./quiz-layout/general-notes/todos.txt
  ./Read.java
  ./some-files
  ./some-files/a.txt
  ./some-files/even-more-files
  ./some-files/even-more-files/a.txt
  ./some-files/even-more-files/d.java
  ./some-files/more-files
  ./some-files/more-files/b.txt
  ./some-files/more-files/c.java
```
This is a pretty expansive list, even with a lot of .git files that are not obviously readable but still found. 

To be more specific with the -readable option, we can give it a path to find the readable files in like this <code>find quiz-layout/ -readable</code> This prints only the readable files in quiz-layout, and its inner directories, but not beyond.
```
  quiz-layout/
  quiz-layout/classes
  quiz-layout/classes/biomed
  quiz-layout/classes/biomed/genes1.txt
  quiz-layout/classes/biomed/genes2.txt
  quiz-layout/classes/biomed/genes3.txt
  quiz-layout/classes/biomed/paper-about-genetics.pdf
  quiz-layout/classes/cse
  quiz-layout/classes/cse/ExampleClass.java
  quiz-layout/classes/cse/generics.txt
  quiz-layout/classes/cse/interfaces.txt
  quiz-layout/classes/cse/linked-list.txt
  quiz-layout/classes/history
  quiz-layout/classes/history/history-of-computing.pdf
  quiz-layout/classes/history/liskov.txt
  quiz-layout/classes/history/lovelace.txt
  quiz-layout/classes/history/turing.txt
  quiz-layout/general-notes
  quiz-layout/general-notes/course-plan-w23.txt
  quiz-layout/general-notes/todos.txt

```
The differences between these file lists highlights the usefulness of this command where you can easily craft a list of readable files within directories, and easily know their full paths so you can then read them with another command like less. 
  
---
### -size
The second option for find is the -size test, which allows a user to get all of the files that are above or below a certain size using certain given paramaters, as listed, with + as greater than the given size, and - as less than               `b'    for 512-byte blocks (this is the default if no
                     suffix is used)
                     
              `c'    for bytes

              `w'    for two-byte words

              `k'    for kibibytes (KiB, units of 1024 bytes)

              `M'    for mebibytes (MiB, units of 1024 * 1024 = 1048576
                     bytes)

              `G'    for gibibytes (GiB, units of 1024 * 1024 * 1024 =
                     1073741824 bytes)
                     
then with a number to determine if its larger or smaller than that given size

To use this command you would type something similar to this:  

<code>find \some-files -size +1c</code>  
  
Executing this in a bash terminal results in this:
```
  some-files/a.txt
  some-files/even-more-files/a.txt
  some-files/even-more-files/d.java
  some-files/more-files/b.txt
  some-files/more-files/c.java
     
```
This displays all of the files larger than 1 byte in some-files, where then the directories are not listed by find because they are smaller.

Another example, using the command <code>find \some-files -size -1c</code> the command only finds the smaller files than one byte, the directories.
```
  some-files
  some-files/even-more-files
  some-files/more-files

```
---
### -fprint (file)
The third option for the find command is more of a supporting command for the other commands, where it puts the result of the find command into a file as given, or creates it if it is not there

To use this command, I want to get all of the files that start with course- and then add them to a file called coursePlans, where the path to these course files can be stored. 

<code>find -name course-* -fprint coursePlans.txt</code>    

Note: There is no console output neccesarily, but a new file coursePlans.txt is created with the following written on line one
```
./quiz-layout/general-notes/course-plan-w23.txt

```
Once again, there will not be output for using -fprint, but instead a file will be created with the findings of the command, here by using a start pattern, all of the .java files in the java structure and their paths inside of the JavaFiles.txt file

<code>find -name '*.java' -fprint javaFiles.txt</code>    

```
  ./quiz-layout/classes/cse/ExampleClass.java
  ./Read.java
  ./some-files/even-more-files/d.java
  ./some-files/more-files/c.java

```
---

### -exec {} ; 
The Last option for the find command I want to show is the exec command which allows the user to execute a command on every file that is found by the find query. Here I have it so that it just uses cat to read out the info of each file in the some-files folder. 

<code>find some-files/ -type f -exec cat {} \;</code>  
  
Executing this in a bash terminal results in this:

```
  hello
  nested file
       junit
  test
  hi
  psvm\n

```
To use this in another way we can do something like this to delete all of the files in the some-files folder, without deleting the directories, because we are only searching for type f files, and then running the remove command on each one. 

<code>find some-files/ -type f -exec rm -rf {} \;</code>

```
  prior to deletion some files listed with ls -R would look about like this
  ./some-files:
  a.txt even-more-files/  more-files/ 

  ./some-files/even-more-files:
  a.txt d.java
  ./some-files/more-files:
  b.txt c.java

  when using ls -R to list all of the files recursively from the directories, because the directories are now empty the directory some files looks like this
  ./some-files:
  even-more-files/  more-files/

  ./some-files/even-more-files:

  ./some-files/more-files:

```
As you can see, the combination of find and the command rm, you can remove all of the files that fulfill a certain find search criteria.
