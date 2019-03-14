# Knowledge Representation and Reasoning

## Project Description
Academic Advisor for Computer Science Majors at Northwestern University

## Team Members:
- Nico Tyjeski
- Harper Pack
- Keith Pallo
- Albert Guo

## Getting Started
### Environment Setup
- a working Companion

### Directory Structure:
     .
     ├── .gitignore             # contains file types not to be synced with GitHub
     ├── README.md                               
     ├── analogy.krf            # file that contains analogy examples
     └── main.krf               # main file that contains defined ontology, facts, and rules

### Overview of Use Cases
Scenario 1
I really liked learning about KRR. What could I take to expand upon that knowledge? <br />
`(goodClassGivenTopic ArtificialIntelligenceProgramming-Fall2018 (WinterQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))) ?newCourse)`

Scenario 2
I really liked Willie’s teaching style. What could I take next quarter with him? <br />
`(goodClassGivenProfCourse IntroductiontoArtificialIntelligence-Fall2018 (WinterQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))) ?newCourse)`

Scenario 3
I know what I want to take Data Sciene and Machine Learning. Can I take them both schedule-wise? <br />
`(notOverlap DataScienceSeminar-Fall2018 MachineLearning-Fall2018)`

Scenario 4
I want to what are the possible courses I can take without overlapping with the other 3 course that I have in mind. <br />
`(notOverlapTwo ?course DataScienceSeminar-Fall2018 MachineLearning-Fall2018 ProgrammingLanguages-Fall2018 (FallQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))))`

Scenario 5
I really liked the Intro to AI course material and the teaching style of Machine Learning. What are two other courses I might like? <br />
`(quarterSuggestionOne ?course1 ?course2 IntroductiontoArtificialIntelligence-Fall2018 MachineLearning-Fall2018 (WinterQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))))`

Scenario 6
I really liked the Intro to AI course material and the teaching style of Machine Learning. What are my options, and what is a third class I can take? <br />
`(quarterSuggestionTwo ?course1 ?course2 ?course3 IntroductiontoArtificialIntelligence-Fall2018 MachineLearning-Fall2018 (WinterQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))))`
