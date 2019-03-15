# Knowledge Representation and Reasoning

## Project Description - Computer Science (CS) Academic Advisor
We built an Academic Advisor for CS Majors at Northwestern University using knowledge representation and reasoning. All knowledge representation and reasoning are stored in [Cyc-style](https://en.wikipedia.org/wiki/Cyc) microtheories.

### Highlights
- Usage of [Companion Cognitive Systems](http://www.qrg.northwestern.edu/ideas/companions-idea.htm), a [DARPA IPTO](https://en.wikipedia.org/wiki/Information_Processing_Techniques_Office) funded project
- Analogical Matching (via the Structure-Mapping Engine) for similar courses
- Multiple ways to recommend courses

### Directory Structure:
     .
     ├── .gitignore             # contains file types not to be synced with GitHub
     ├── Presentation.pptx      # project presentation                               
     ├── README.md                               
     ├── The FIRE Manual.pdf    # manual of the FIRE reasoning engine of Companion Cognitive Systems
     ├── analogy.krf            # file that contains analogy examples
     ├── analogy_scaled.krf     # file that contains analogy examples that are scaled significantly
     └── main.krf               # main file that contains defined ontology, facts, and rules

### Environment Setup
To get setup please do the following:
- run Companion
- upload all `.krf` flatfiles to Companion
- run queries (details shown below)

### Team Members:
- Nico Tyjeski [@ntyjeski49](https://github.com/ntyjeski49)
- Harper Pack [@harperpack](https://github.com/harperpack)
- Keith Pallo [@KeithPallo](https://github.com/KeithPallo)
- Albert Guo [@Albert-Z-Guo](https://github.com/Albert-Z-Guo)

------------------------------------------------------------------------------

## Overview of Motivation
We sought to create an automated version of an academic CS advisor. The difficulties students face in trying to understand their academic options and plan their futures motivated us to develop a solution that obviated these challenges.

Currently, there are several different resources that exist for students to plan out their courses. These include published course manuals, assigned academic advisors, peer course reviews, and several other systems. However, it is tedious and time-consuming for students to extract and reconcile information from a multitude of disparate sources.

![Image_1](/images/readme_image_1.png)

In order to ameliorate this situation, we wanted to allow students to access a single, all-encompassing system to support them in their academic planning pursuits, thus freeing them from having to reckon with a multitude of different resources.

![Image_2](/images/readme_image_2.png)

Through Companions we have created a system that allows us to ask and receive answers to questions that we, as CS students ourselves, have faced. These range from simply checking whether two classes are the same, to reasoning whether two classes are similar based on multiple criteria. In this particular project, we have intentionally limited the scope of our queries to focus on planning one quarter ahead - although virtually all of our core representation and reasoning could easily be extended.  


Note: In our repo we have also included `Presentation.pptx` which further details the background and goals of our project.

------------------------------------------------------------------------------

## Project Structure
Our project is structured into 3 main files - `main.krf`, `analogy.krf` and `analogy_scaled.krf`. Below we have documented the main functionality provided from each of these files. These files add new knowledge and representation to the Companions base, so after uploading the `.krf` files queries can be automatically run. Example queries are shown below along with scenarios in which students may use them.

After setting up the environment as described above, we recommend testing our system by running the example queries. However, you are free to add knowledge as laid out in the files and test custom queries as well!

**Please note that queries for `main.krf` and `analogy.krf` should be run within the `CSAcademicAdvisorMt` context; queries for `analogy_scaled.krf` should be run within the `AnalogyScaledMt` context**

### File 1 - main.krf

**Representation:** In this file we make use of, and expand upon, the information held in Companions about Northwestern University's CS department and it's courses. This includes departments, professors, research groups, years, quarters, courses, and when courses meet. We also define a series of collections for overall research areas, like AI and Systems, along with all the classes that fall under those areas.

**Reasoning:** Within this file we present several different forms of reasoning. All are horn clauses, and some build upon each other for more complex reasoning. At a high level, we will be reasoning whether or not classes are appropriate/feasible for a CS student in a given term, whether or not the weekly lecture schedule of classes overlap, and what classes would be a good fit given different facets of a student's interests.

- **Scenario 1** <br />
I really liked learning about ArtificialIntelligence programming. What could I take to expand upon that knowledge? <br/>
Example Query: <br />
`(goodClassGivenTopic ArtificialIntelligenceProgramming-Fall2018 (WinterQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))) ?newCourse)`

- **Scenario 2** <br />
I really liked Willie’s teaching style. What could I take next quarter with him? <br/>
Example Query: <br />
`(goodClassGivenProfCourse IntroductiontoArtificialIntelligence-Fall2018 (WinterQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))) ?newCourse)`

- **Scenario 3** <br/>
I know that I want to take Data Science and Machine Learning. Can I take them both schedule-wise? <br/>
Example Query: <br />
`(notOverlap DataScienceSeminar-Fall2018 MachineLearning-Fall2018)`

- **Scenario 4** <br/>
What are the possible courses I can take that would not overlap with the other 3 course that I have in mind? <br/>
Example Query: <br />
`(notOverlapTwo ?course DataScienceSeminar-Fall2018 MachineLearning-Fall2018 ProgrammingLanguages-Fall2018 (FallQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))))`

- **Scenario 5** <br/>
I really liked the Intro to AI course material and the teaching style of Machine Learning. What are two other courses I might like? <br/>
Example Query: <br />
`(quarterSuggestionOne ?course1 ?course2 IntroductiontoArtificialIntelligence-Fall2018 MachineLearning-Fall2018 (WinterQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))))`

- **Scenario 6** <br/>
I really liked the Intro to AI course material and the teaching style of Machine Learning. What are two relevant courses along with a third that is logistically feasible? <br/>
Example Query: <br />
`(quarterSuggestionTwo ?course1 ?course2 ?course3 IntroductiontoArtificialIntelligence-Fall2018 MachineLearning-Fall2018 (WinterQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))))`

- **Scenario 7** <br/>
I really liked The Design of Technological Tools for Thinking and Learning. What are some courses that might be taught by professors who have a similar background? <br />
Example Query: <br />
`(similarResearchGroup TheDesignofTechnologicalToolsforThinkingandLearning-Winter2018 ?newCourse (SpringQuarterFn (AcademicYearFn NorthwesternUniversity (YearFn 2018))))`

### File 2: analogy.krf
This file contains a simple example that represents the core advanced reasoning that Analogical Matching (via the Structure-Mapping Engine).

**Representation:** <br />
Here we describe 4 similar courses in microtheories as cases and add them all in a case library. We also defined predicates `probabilityRelated` and `mathHeavy` to denote courses are probability-related and math-heavy.

**Reasoning:** <br />
We used `reminding` predicate to find courses that are similar to a course that is both probability-related and math-heavy.

- **Scenario 1** <br />
What are some similar courses to ProbabilisticGraphicalModels-Winter2018? <br />
Example Query: <br />
`(reminding ProbabilisticGraphicalModels-Winter2018DescriptionMt (CaseLibrarySansFn similarCourses ProbabilisticGraphicalModels-Winter2018DescriptionMt) (TheSet) ?similarCourse ?match)`

### File 3: analogy_scaled.krf
This file contains a much more complicated example that is self-contained with much more complicated ontology defined than the ontology in `main.krf`.

**Representation:** <br />
We ontologized 16 new predicates in this file, including `differentContentApproach`, `moreDifficultThan`, etc.  These predicates help to describe the classes in this file primarily in terms of the relationships between them.

**Reasoning:** <br />
Here we describe 6 courses in microtheories as cases and add them all in a case library. As noted above, each of the 6 courses are described using a variety of predicates.  We again use the `reminding` predicate to obtain courses similar to a specified course, and trust FIRE's structure-mapping engine to determine the dimensions of similarity and evaluate courses in that vein.

- **Scenario 1** <br />
What are some similar courses to KRR-Winter2018DescriptionMt? <br />
Example Query: <br />
`(reminding KRR-Winter2018DescriptionMt CourseDescriptionsCaseLibrary
 (TheSet) ?case ?match)`

------------------------------------------------------------------------------

**Special Thanks:** <br />
We would like to thank our class instructors: Irina Rabkina and Willie Wilson for their patience and help!
