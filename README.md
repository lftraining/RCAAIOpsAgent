# ILT-course-template
This is a template to get authors started with the necessary structure for creating courses with LaTeX
1. First: Rename COURSENUMBER.tex to whatever your course number is .tex, eg LFS307.tex
2. Second: edit COURSENUMBER.tex to use your course number and version
3. Third: Run make release-full
4. Fourth: Look around
5. Fifth: Run make clean
6. Sixth: Look around

COURSENUMBER.tex is where the course architecture is declared. It is where you choose which chapter comes first and which follow. Chapters go in CHAPS. Each chapter goes in a chapter directory titled COURSENUMBER_CHAPTERTITLE:
COURSENUMBER_chapterRed/
COURSENUMBER_chapterBlue/
etc.
Each chapter directory has an index.tex that declares the chapter architecture in sections.
chapter1/index.tex
Put your sections in the associated chapter directory and list them in the index.tex file in the order you wish for them to appear.

Labs are written in a labs.tex file under the chapter directory they belong to:
chapterRed/labs.tex

SOLUTIONS are not answers. They are the assets (e.g. yaml files, c programs, etc.) that you want the student to have access to in order to complete the labs.
These assets go in a labs directory inside the associated chapter directory:
chapterRed/labs
chapterBlue/labs

When the course is built these assets will be put in the SOLUTIONS directory and zipped automatically.

# [PutCourseNumberHere]
Put Course Title Here

You can set this course up by running the following commands:
```
  git clone git@github.com:lftraining/PutCourseNumberHere.git
  cd PutCourseNumberHere
  git submodule update --init --recursive
  ./common/UTILS/cmtool download 
```
## Building the course

## Building the course
To build this course you should install Docker and run the following:
```
docker pull eeganlf/tex-build:v1.0
```
Once the image is downloaded, be sure you are inside this repository, and run:
```
docker run -it --rm -v $(pwd):/$(basename $(pwd)) --workdir /$(basename $(pwd)) eeganlf/tex-build:v1.0 /bin/bash
```

To ensure course builds completeley, run the following inside the course directory:
```
make release-full
```
then:
```
make clean
```
For a quick test you can run:
```
make release
```
then:
```
make clean
```


In order to build ElearningCourseNumberHere the Elearning variant
```
cd ..
ln -s [PutCourseNumberHere] [ElearningCourseNumberHere]
cd [ElearningCourseNumberHere]
docker run -it --rm -v $(pwd):/$(basename $(pwd)) --workdir /$(basename $(pwd)) eeganlf/tex-build:v1.0 /bin/bash
```
Then:
```
make release-elearning
```

