# Introduction to Systems Design - Requirements Analysis

These notes are taken almost verbatim from Paul Baumgarten's page [here](https://pbaumgarten.com/ib-compsci/unit-1/). Some material and ideas have been added using the resources at [IB Compsci Hub](https://ib.compscihub.net/)

## System development life cycle

At university level for a Computer Science course, the design cycle for software is known as the SDLC: System development life cycle (some books substitute "system" with "software").

![SDLC](./media/05/sdlc.png)

The major sections of the SDLC are:

* Requirements analysis
* Design
* Implementation
* Testing
* Evolution

We will examine each section for what needs to occur. ON this page, we will be focusing on Requirements Analysis.

---

## SDLC Phase 1: Requirements analysis

Aim of phase 1: Figure out what the project needs to accomplish.

There are typically 4 elements to this:

* Project scoping
* Stakeholder consultation
* Project research
* Requirements planning

---

### Project scoping

> Find out exactly what it is you have to do

A **scope document** allows all parties to agree in writing as to what *is* and *is not* included within the project. It effectively becomes the contract, and establishes common expectations for client and creator.

* Happy customer = good word of mouth.
* Disgruntled customer (feels ripped off or that you didn't deliver on what was promised) = bad for business.
* Burnt out producer (feeling taken advantage of, frustrated at changing requirements) = Not healthy!

Scoping should be SMART

* **S**pecific
* **M**easurable
* **A**greed upon
* **R**ealistic
* **Time** bound

Ensure your scopes identify time, financial and resource constraints!

It is inevitable that a project scope will change over time. Make sure that your scope doesn't get more vague over time - if it changes, it should change in a way that makes it more clear and specific!

### Stakeholder consultation

#### Identifying stakeholders

* Who is relevant? Employers, employees, customers…?
* Who will use the system?
* Who will depend on the system (even if they don't use it directly)?
* Who will provide information the system depends on? (even if they don't enter it directly)
* Who is paying for the system? (why?)

#### Getting information from the stakeholders

Possible strategies for obtaining requirements from stakeholders

* Surveys
  * Advantages: Easy to get a lot of data
  * Disadvantages: Many won't answer, data may be superficial
* Interviews
  * Advantages: More detailed data, here individual perspectives
  * Disadvantages: Not as many voices, questions may not be clear, responses may not be honest
* Direct observations
  * Advantages: Can directly see problems or issues as they occur
  * Disadvantages: People may not work as normal under observation. Not all possible problems or concerns will always occur and may only occur rarely.
* Document collection (about the current system)
  * Advantage: Allows one to understand the system in place
  * Disadvantage: May not make requirements clear alone, can be confusing

Failure to involve all relevant stakeholders may lead to software that is not suitable for its intended use! (The manager doesn't necessarily always know what the clerical staff do!)

Effective collaboration and communication between all parties: client, developer, end users.

Consultation should occur continually throughout the lifecycle to identify problems early.

Be aware of privacy issues – being able to get honest, frank information from a stakeholder without fear of retribution (eg: a staff member who might have valuable insight into how some part of the system doesn't work the way management thinks it does) – create an environment where you can extract those valuable nuggets

### Project research

* Examine the **current system** that yours will replace – strengths, weaknesses, idiosyncrasies.
* Examine **competing products** – strengths, weaknesses, idiosyncrasies.
* Examine **your capabilities** – what are you capable of producing? if you need additional expertise, what can you afford to recruit?
* Examine the **literature** (journals, online forums) – how are other people addressing the problem?

---

### Requirements planning

Your requirements are generally split into functional and non-functional requirements.

* Functional: What will the program actually do? For example:
  * Store hours worked per employee per day
  * Store hourly rates for employees by category of employment
  * Store daily timesheets for up to 5 years history
  * Calculate income tax obligiations per employee at the end of each month
    
* Non-functional: Doesn't affect what the program will actually do, but will impact on creating it anyway. For example:
  * The system shall run on Android / iOS / the web.
  * The system shall be compatible with Microsoft SQL / Google Firebase
  * The system shall share data with (insert other existing product here)
  * The system shall be operational in 3 months
  * The system shall store it's data within Switzerland (due to privacy laws)


### Exercise

Split off into pairs - one taking the role of customer, one taking the role of developer. Customer comes up with an app/software project they want the developer to "design". Developer must ask questions to ascertain:
 * A scope document: Explicitly list "in scope" and "out of scope" items
 * Identify stakeholders
 * Requirement specification: Functional and non-functional items

Reverse roles when ready.

Save these project outlines as we will continue to use them.


## Your IA

You will go through these steps with your client as part of the first step of your IA. 

## Check your Understanding

1.  Imagine you are working for a governnment designing a system to accept emergency signals from cell phones and forward them to the appropriate emergency responders. 
    1.  Who are the stakeholders for this system?

    2.  What are some strategies you might use to gather requirement information from these various stakeholders?

    3.  If some of the stakeholders are in conflict about their desires, which stakeholders do you think should be prioritized in this system?

    4.  What are some functional requirements of such a system?

    5.  what are some possible non-functional requirements of such a system?


2.  Mr. Griswold worked for a textbook company a few years ago; he worked on writing a statistics textbook and accompanying web applications to support the learning in the textbook. After discussion, it was decided to make most of the web apps available for anybody to use - they can be found at [http://stats.cpm.org](http://stats.cpm.org).

    1.  Who were some of the stakeholders for this system (the system being the book + apps)?

    2.  When Mr. Griswold joined the team, he was given three requirements for his textbook writing:

        1.  He was required to write it in Microsoft Word
        2.  The problems needed to be written in a way where students could engage in problem-solving and discussion in the process of learning the material
        3.  The font had to be Times New Roman.
   
        Which of these were *functional* requirements and which were *non-functional* requirements?

    3.  Partway through the project, Mr. Griswold was asked to work on a website where students and teachers using the textbook could click a button and generate sample problems and tests automatically. The program was already partially completed, and Mr. Griswold was making it more attractive and adding features. Here were some of the requirements laid on in his scope statement:
   
        1.  The project will have a simple user-interface that allows students to generate single problems or entire assignments, based either on a single chapter or cumulative up to a specific chapter.
        2.  It will be possible to export assignments in Word or PDF formats.
        3.  The code will be written in Dart and HTML and based on already-existing code.
        4.  The names used in the problem generator word problems will come from a wide variety of cultures and will be both male and female.

        Which of these were *functional* and which were *non-functional* requirements?

    4. What are some steps Mr. Griswold and his team might have gone through in the initial research stage before writing the book?