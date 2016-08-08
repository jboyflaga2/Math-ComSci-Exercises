# How to run the stand-alone executables I provided

In the README of the root directory of this repository I said this:

> I will also put here the finished executable of each assignment (with some kind of a signature to prove that I made them) and it's accompanying resources so that I have proof that I really finished the assignments.

If you want to be able to run the executable, for "Week 2 - Generating Mazes" for example, just follow these steps:

_(I compiled these projects using Windows so you can be able to run these on Windows only.)_

1. Extract the zip file "`\Assignments\FilesForStandAlone-Windows.zip`"

2. Extract the zip file "`\Assignments\Week2\maze-generator-executable.zip`"

3. Copy the file(s) (`.exe` and other files) inside the extracted `maze-generator-executable.zip` into the extracted  `FilesForStandAlone-Windows.zip`

The resulting set of files should be like in the image below:

![](sample-stand-alone-files.png?raw=true)

# Some hints and some difficulties I encountered while solving the assignments

## Week 1

I decided not to do the assignment for Week 1 because I already did something like this before when I solved ["Game of Life" or CS 106B last Spring 2011](http://jeremiahflaga.blogspot.com/2011/08/solution-for-game-of-life-stanfords.html).

## Week 2
### Word Ladders

(July 25, 2016)

![](Week2/word-ladder-by-jboy-flaga.png?raw=true)

#### Hints: 

Just follow the pseudo-code on page 3 of the assignment handout.

As stated in the handout, I used a `Queue<Vector<string> >`, or to make it more clear, I wrote:

``` C++
typedef Vector<string> WordLadder;
...
Queue<WordLadder> queueOfWordLadders;
```

#### Difficulties: 

No difficulties encountered.

### Generating Mazes

(August 8, 2016)

![](Week2/maze-generator-by-jboy-flaga.png?raw=true)

#### Hints:

For list of chambers I used this:
``` C++
typedef Set<cell> Chamber;
...
Vector<Chamber> chambers;
```

(There are hints in the handout that we can use `Vector` and `Set`.)

... and, in the pseudocode, after we remove the wall, we have to update the list of chambers.


#### Difficulties:

1. The use of randomInteger from the "random.h" library - take note that the parameters (low, high) are INCLUSIVE. I experienced runtime error because of index out of bounds.

2. Another difficulty I encountered is in updating the list of chambers after removing the wall. After removing the wall, I needed to remove the two chambers that **was** separated by the wall. And because I was using a `<Vector>` to contain the list of `Chambers`, when I tried to remove the first chamber, the indices of the `<Vector>` already changed. When I tried to remove the second chamber, the one removed _by the code I have written_ is not the one I intended to remove. The reason is because the indices already changed.


------------------------------

# How I was able to create a stand-alone .exe for the assignments

### 1. Go to C:\Qt\Qt5.7.0\5.7\mingw53_32\mkspecs\win32-g++\qmake.conf

### 2. Look for QMAKE_LFLAGS and put a "-static"
I got this from https://www.youtube.com/watch?v=chMNUzpN4pw
```
QMAKE_LFLAGS            = -static
```

### 3. Build project then copy the .exe from the build directory

### 4. There are demo projects that come with the assignments. What I did is just change the .exe from that demo to my own .exe file.

For example, for the "word-ladder" project:

a. go to \Assignments\Week 2\<strong>assign-2-adts</strong>\word-ladder\build-word-ladder-Desktop_Qt_5_7_0_MinGW_32bit-Debug\debug

b. copy "word-ladder.exe"

c. paste it into \Assignments\Week 2\<strong>assign-2-adts-demos</strong>\windows-demos\word-ladder



