# Knowledge Representation and Reasoning

## Project Description - CS Academic Advisor
In this project our group built an Academic Advisor for Computer Science Majors at Northwestern University using knowledge representation and reasoning. All knowledge representation and reasoning are stored in [Cyc-style](https://en.wikipedia.org/wiki/Cyc) microtheories.

### Highlights
- Usage of [Companion Cognitive Systems](http://www.qrg.northwestern.edu/ideas/companions-idea.htm), a [DARPA IPTO](https://en.wikipedia.org/wiki/Information_Processing_Techniques_Office) funded project
- Analogical Matching (via the Structure-Mapping Engine) for similar courses
- Multiple ways to recommend courses

### Team Members:
- Nico Tyjeski
- Harper Pack
- Keith Pallo
- Albert Guo

### Environment Setup
To get setup please do the following:
- run Companion
- upload all `.krf` flatfiles to Companion
- run queries (explanation show below)

### Directory Structure:
     .
     ├── .gitignore             # contains file types not to be synced with GitHub
     ├── Presentation.pptx      # project presentation                               
     ├── README.md                               
     ├── The FIRE Manual.pdf    # manual of the FIRE reasoning engine of Companion Cognitive Systems
     ├── analogy.krf            # file that contains analogy examples
     ├── analogy_scaled.krf     # file that contains analogy examples that scaled significantly
     └── main.krf               # main file that contains defined ontology, facts, and rules

------------------------------------------------------------------------------


# Overview of Motivation
In this project, our group aimed to create an interactive version of an academic CS advisor. The motivation for this project came from some of the difficulties that arise when any Northwestern Computer Science Student is trying to plan out their future course schedule.


Currently, there are several different resources that exist for students to plan out their courses. These include published course manuals, assigned academic advisors, peer course reviews (in our case CTECs) and several other systems. However, these methods often fall short as this usually results in a time consuming cycle where students move from resource to recource - partically getting information as shown here.

![Image_1](/images/readme_image_1.png)

In order to allerivate this challenge we wish to change the model from the student having to access and manage individual resources to the student being able to interface with one holistic system as seen here.

![Image_2](/images/readme_image_2.png)

Overall, using companions we believe that we have created a system that allows CS students to ask the CS Advisor questions we personally have had. These range from simply checking if two classes are the same, two reasoning if two classes are similar based on multiple criteria. In this particular project, we have limited the scope of our queries to focus on planning one quarter ahead - although virtually all of our core representation and reasoning could easily be extended.  


Note: In our repo we have also included a presentation called < > which further details the background of our project, and the goals for the system that we have created.

------------------------------------------------------------------------------



Our project is structured into XXXX main files - main.krf and analogy.krf. Below we have documented the main functionality provided from each of these files. Overall, these files add new knowledge and representation to the companions base, so after uploading the `.krf` files queries can be automatically run. Example queries are shown below along with scenarios in which students may use them.
=======


After setting up the environment as described above, we recommend testing our system by running the example queries. However, you are free to add knowledge as laid out in the files and test custom queries as well!



## File 1 - main.krf


Representation: In this file we utilize representation by ....

Reasoning: Within this file we present several different forms of reasoning, but all of them revolve around the utilization of horn clauses ....


#### Scenario 1 --- goodClassGivenTopic <br />
I really liked learning about KRR. What could I take to expand upon that knowledge? <br/>
Example Query: `(goodClassGivenTopic ArtificialIntelligenceProgramming-Fall2018 (WinterQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))) ?newCourse)`

#### Scenario 2  --- goodClassGivenProfCourse  <br />
I really liked Willie’s teaching style. What could I take next quarter with him? <br/>
Example Query: `(goodClassGivenProfCourse IntroductiontoArtificialIntelligence-Fall2018 (WinterQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))) ?newCourse)`

#### Scenario 3  ---  notOverlap <br/>
I know what I want to take Data Sciene and Machine Learning. Can I take them both schedule-wise? <br/>
Example Query: `(notOverlap DataScienceSeminar-Fall2018 MachineLearning-Fall2018)`

#### Scenario 4 --- notOverlapTwo <br/>
I want to what are the possible courses I can take without overlapping with the other 3 course that I have in mind. <br/>
Example Query: `(notOverlapTwo ?course DataScienceSeminar-Fall2018 MachineLearning-Fall2018 ProgrammingLanguages-Fall2018 (FallQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))))`

#### Scenario 5 --- quarterSuggestionOne <br/>
I really liked the Intro to AI course material and the teaching style of Machine Learning. What are two other courses I might like? <br/>
Example Query: `(quarterSuggestionOne ?course1 ?course2 IntroductiontoArtificialIntelligence-Fall2018 MachineLearning-Fall2018 (WinterQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))))`

#### Scenario 6 ---- quarterSuggestionTwo <br/>
I really liked the Intro to AI course material and the teaching style of Machine Learning. What are my options, and what is a third class I can take? <br/>
Example Query: `(quarterSuggestionTwo ?course1 ?course2 ?course3 IntroductiontoArtificialIntelligence-Fall2018 MachineLearning-Fall2018 (WinterQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))))`

<br/>

## File 2 - analogy.krf

This file represents the core advanced reasoning that our system enables - which is analogy.

Representation: ....


Reasoning: ....

<br/>

### File 3 - analogy_scaled.krf

Representation: ....

Reasoning: ....

<br/>

### File 4 - <Harpers File> 

Representation: ....

Reasoning: ....

<br/>

------------------------------------------------------------------------------

Special Thanks: We would like to thank our class professors
