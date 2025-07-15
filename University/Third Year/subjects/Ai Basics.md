مادة مبادئ الذكاء الصنعي  سنة 3 فصل تاني



| lec1 | [[#Introduction to Artificial intelligence .]]    |
| ---- | ------------------------------------------------- |
| lec2 | [[#INTELLIGENT AGENTS]]                           |
| lec3 | [[#Artificial Intelligence Methods of Inference]] |
| lec4 | [[#Knowledge Representation]]                     |
| lec5 |                                                   |
| lec6 |                                                   |

---
`lec 1`
# Introduction to Artificial intelligence .

what is AI ?
AI is a subfield of **Computer Science**. In regular computer science, we write programs to solve logical or computational problems. But in **AI**, we go one level deeper:

> **AI = making computers solve problems that usually require human intelligence.**

### ~={orange}Turing Test  by alan turing =~
the turing test is an test where the human interacts with a computer and a person without knowing which is which , if the human can't tell who's the machine and who's the human the machine passes the test 

what are the abilities required for an machine to passes turing test 
- naturual language processing 
- Automated Reasoning 
- learning 
- Knowledge and storing info
- Vision ( for Total Turing test)
- Robotics ( for Total Turing test)


### ~={orange}Cognitive Science العلم الذهني =~
This is the study of how humans think and how we can **simulate that thought process**.

- **Cognitive architectures** model human behavior in tasks.
- We observe humans: how long they take, what mistakes they make, etc.    
- Then build systems that match those behaviors.
  
**Problem?**  
Human thinking is complex and not always observable. It’s hard to build a detailed model from only external behavior.
### ~={orange}Logical approuch الخيار المنطقي =~
This is about programming computers to think **logically**, based on facts and rules.

>Example:  
"All humans are mortal. Socrates is human. → Therefore, Socrates is mortal."

Rational = Conclusions are provable from inputs and prior knowledge

** but the Problems**
- Real-world knowledge is often informal or vague.
- Proving things logically can be too slow or complex.
  
### ~={orange}Acting Rationally التصرف بعقلانية =~
This is the **most modern and practical** view.
and they can give their rescources.

> A **rational agent** is a system that does the best it can, with the resources it has, to achieve its goals.

It doesn’t just “think logically” — it **acts to achieve goals**, even if it has limited information or time.

Depending on the available **resources** (time, memory, data), agents may:

- Act without thinking (like reflexes)
- Do fast, approximate reasoning
- Or think deeply and logically

This is what most modern AI systems are based on!

### ~={orange} Major Areas of Study in AI=~

1. Reasoning & Problem Solving (Planning, scheduling, assistants, optimization).
2. Natural Language Processing (Understanding and generating human language).
3. Vision (Understanding images and scenes).
4. Robotics (Physical movement, manipulation, and mapping environments).

#### ~={cyan}What are we at now ?=~ 

- **SKICAT** : classifies space teloscope images better than humans 
		
- **DEEP BLUE** : Beat world **chess champion** Garry Kasparov.
		
- **Pesguse & Jupiter** :  **Voce-Controlled** sys for travel and Weather 
		
- **HipNav** : AI-assisted surgery.
		 
- **NavLab** : A self-driving car that drove across the USA 98%
		
- **Google News** : Automatically gathers and organizes global news.
		
- **Ds1** : NASA SpaceCraft that did an autonomous flyby an astroid.
		
- **proVeb** : solves puzzles.

| Easy For Human      | Hard For AI<br>              |
| ------------------- | ---------------------------- |
| speech and language | Playing chess                |
| Recognize faces     | - Scheduling flights         |
| Creating art/Music  | Sorting huge amounts of mail |
| Common Sence        | Solving logical puzzles      |

---
`lec 2`

# INTELLIGENT AGENTS

agents and enviroment 
PEAS
Enviroment Type
Agent Types 
  - Simple Reflex agent
   - states 
  -  modal based agent 
   - utility based agent 
   - goal based agent

---
What is an Agent ? 
 an agent is anything that perceiveing his enviroment  using sensors and acts upon it 
 العميل هو اي شي بيتفاعل وبيتعامل مع البيئة تبعه بيستخدم الحساسات وامور اخرى ليعالج ويتصرف بناء على ذلك 
 there as Human Agent 
 and the Robotic agent 

#### ~={orange}Agents and Enviroments =~
- The **architecture** is the hardware (robot body, computer).
    
- The **agent program** is the software (what tells it how to behave).
    
- The **agent function** maps all past percepts : ادراك → best action.  
    Noted as: `f: P* → A`

---
### ~={orange}RATIONAL AGENTS=~
dose the best possible thing 
Rational just means **maximizing the expected outcome**, even with uncertainty.

> what is rationality ??
 rational is diffrent from omniscience(العلم بكل شيئ)
coz agent might not have all the  relavent information 

Rational != Perfect but its maximaizing expected outcome

---
### ~={orange}Autonomy In Agents =~
the agent is dependent on its own experience rather the knowledge of designer 

- A **non-autonomous** agent acts only on pre-programmed rules.
- A **fully autonomous** agent learns everything itself (not practical).
- 
>Like a baby learning to crawl, then walk. Autonomy grows with experience.

---
## ~={red}PEAS=~
Performance Measure , Enviroment , Actutors(المحركات) , Sensors 

**P** = Performance measure (what defines success)  
**E** = Environment (what world it lives in)  
**A** = Actuators (how it acts)  
**S** = Sensors (how it sees)

>Must first specify the setting for intelligent agent design for each agent 
>for example automated taxi 

p : distance , time , money
E: streets , Hallways 
A:  brakes , horn , signals , accelerator 
S : Camera , GPS

.... and other examples 

---
### ~={orange}Enviroment Types =~

- Fully observable != partially observable
- Deterministic(محددة) != stochastic(عشوائية)
- Episodic(عرضي ) !=  Sequential( مرحلي)
- Static != dynamic 
- Discrete != continuous 
- single agent != multiAgent 
شرح زيادة 

| Type                     | Meaning                            | Examples                         |
| ------------------------ | ---------------------------------- | -------------------------------- |
| **Fully Observable**     | Agent sees entire environment      | Part-picking robot               |
| **Partially Observable** | Agent sees only part of it         | Taxi driver                      |
| **Deterministic**        | Next state is predictable          | Crossword puzzle                 |
| **Stochastic**           | Involves randomness                | Backgammon                       |
| **Episodic**             | Actions are independent            | Image analysis                   |
| **Sequential**           | Actions depend on previous ones    | Taxi driving                     |
| **Static**               | Doesn’t change on its own          | Crossword                        |
| **Dynamic**              | Changes over time                  | Driving in traffic               |
| **Discrete**             | Limited number of actions/percepts | Chess                            |
| **Continuous**           | Infinite actions/percepts          | Real-world driving               |
| **Single Agent**         | One decision-maker                 | Crossword                        |
| **Multi-agent**          | Multiple decision-makers           | Taxi with passengers, other cars |
|                          |                                    |                                  |

> Backgammon ( لعبة الطاولة ) , 

|Task|Observability|Determinism|Environment|Episodic?|Percepts/Actions|Agent Type|
|---|---|---|---|---|---|---|
|**Crosswords**|**Fully observable**|**Deterministic**|**Static**|**Sequential**|**Discrete**|**Single**|
|**Backgammon**|**Partially observable**|**Stochastic**|**Static**|**Sequential**|**Discrete**|**Single**|
|**Taxi Driver**|**Partially observable**|**Stochastic**|**Dynamic**|**Sequential**|**Continuous**|**Multi**|
|**Part-Picking Robot**|**Fully observable**|**Deterministic**|**Dynamic**|**Episodic**|**Continuous**|**Single**|
|**Image Analysis**|**Partially observable**|**Stochastic**|**Semi-static**|**Episodic**|**Continuous**|**Single**|


![[Pasted image 20250712183614.png]]

## ~={pink}Types Of Agents=~ 

there are Four Types of Agents in order of increasing generality 

###### 1. ~={purple}~={red}[[#Simple Reflex Agent]]  =~=~{simple|cyan} 
###### 2. ~={yellow}[[#Model Based Relfex Agents]]=~ {reflex|8|yellow}
###### 3.~={orange} [[#~={blue}Goal-Based Agent=~]]=~ {goal|5|blue}
###### 4. ~={green}[[#~={red}Utility-Based Agent=~]]=~ {Utility|2|Red|}

 > All these can be turned into learning agents

---

### 1.~={cyan}Simple Reflex Agent=~ {simple}

##### its basiclly based on current percept , **==No Memory==**

might face proplems like infinte loops , and it cant Plan 

>Example: If dirt is seen → Suck

other examples : `fly buzzing on light` , `Thermostat` ,`chess openings` and some moves (like my chess game application)

---
## ~={pink}States :=~

what is an State ? the internal state can contain information about external enviroment 
the state depend on history of percept and action taken

 => If each internal state includes all information relevant to information making, the **state space** is ==Markovian==

 if State include the 
- ~={yellow}Percepts(ادراك)=~ + ~={orange}Action Lead to it=~ (the State) => thats an ~={cyan}Perfect Recall.=~

> **~={purple}Perect Information=~** = ~={cyan}Perfect Recall=~ + Full Observability +  Deterministic Actions.

---
### 2.~={yellow}Model Based Relfex Agents =~{reflex}

#### Agent with an State
- Uses a **model** (knowledge of how the world works).
- Has **internal state** (remembers things) **and Can Updated it**  

> Example : Knows that turning wheel affects direction.

![[Pasted image 20250713113741.png]]

---
### 3.~={blue}Goal-Based Agent=~{goal}

#### has an state, and enviroment , ***But its has an Goal*** 
-  uses knowledge about a goal to guide its actions.
- sees **goals** to decide between actions.

> Example: Sees red light → knows car is stopping → should brake

![[Pasted image 20250713114208.png]]


---
###  4.~={red}Utility-Based Agent=~{Utility}

#### its with an state, knows the enviroment, has an Goal , still not enough.

-  Adds **preferences** to goals: Not just get to goal, but get there **better**
- Has a **utility function**: Measures success, happiness, safety, etc.

>Example: Taxi driver chooses a safe and fast route

>متل الحكي يلي حكيتو انا بالسمنار goal based بهمه يوصل من نقطة a لنقطة b بدون اي نقاط تانية او شروط تانية 
 اما ال utility based ما بهمه بس كيف يوصل للgoal تاعته بل بهمه انو يوصل باحسن طريقة , اقل مسافة اعلى سرعة اقل زمن .....الخ


![[Pasted image 20250713115449.png]]
 
---
## ~={orange}Learning Agents =~

Performance element is what was previousely 

- Perfomance element : input sensor + output sensor 
- Learning element : modifies performance element 
- it has an proplem generator , that **tries to solve** the proplems + **Suggest** exploring new actions 
- Critic : how is the agent doing.


![[Pasted image 20250713121105.png]]

---
an complete example of how its working 

Taxi driver Makes quick left turn across 3 lanes
• Critics observe shocking language by passenger and other drivers and informs bad action 
• Learning element tries to modify performance elements for future 
• Problem generator suggests experiment out something called Brakes on different Road conditions 
<=> Exploration vs. Exploitation 
=> Learning experience can be costly in the short run 
=> shocking language from other drivers 
=> Less tip 
=>Fewer passengers

---

## The big picture of the simple **Model-Based** agent 

![[Pasted image 20250713122332.png]]


---
`lec 3 `


# Artificial Intelligence Methods of Inference

## Trees and Graphs 
---
you can see all info related to **Trees** Here [[Trees]]
you can see all info related to **Graphs** Here [[Graphs]]

### so what we need an Trees in AI?

trees are useful in something called **~={pink}Decisions Making Trees=~**.

- trees and lattices are useful for classifying Objects into hierarchical thing idk 
- also an Great representation of Knowledge .

## ~={blue}Binary Decision Trees=~.

- Every Question must take us down one level in the Tree
- all Leaves will be Answers 
- all internal nodes are Questions 
- There will be a maximum of 2 N answers for N questions. (coz its binary bruh)
- Decision trees can be translated into production rules.

![[Pasted image 20250714172728.png]]


## ~={blue}And-OR Trees and Goals=~ .

- AND-OR trees also use backward chaining.
- AND-OR-NOT lattices use logic gates to describe problems.

>• 1990s, PROLOG was used for commercial applications in business and industry. 
>• PROLOG uses backward chaining to divide problems into smaller problems and then solves them.


---
# ~={green}Types of Logic =~

## ~={red} Deduction=~ ( الاستنتاج )

Starting from an general rules (~={yellow}Premisies=~) to reach an specofoc certin conclusion 

 >**Example**  Socrates Mortallity 
>humans are mortal , socretes is human => socrates is mortal 

**general -> specific** 

---
## ~={blue} Induction=~ ( الاستقراء )

oppesite of the deduction its starting from an Observation or example and going into an general conclusion ( not all times its gonna guaranteed to be true)

>we seen 100 white swans => we assume that all swans are white (unless one day we see an black one)

**specifci -> general** 

---
## ~={yellow}Intuition=~( الحدس)

giving an rule without reasoning or proven theory

---
## ~={orange}Heuristics=~ ( الاستدلال الارشادي)
this is based on experiences and past shi 

---
## Generate and Test(التجربة والاختبار)
trying different things until something work 

---
## ~={purple}Analogy=~ (الاستعارة/القياس)
based on something similar to another things
**Finding similiarites between shis** 

---

# Syllogisms(القياسات المنطقية)vs. Rules

- Syllogism 
– All basketball players are tall. 
– Jason is a basketball player. 
– Jason is tall.

- Rules
  IF
	All basketball players are tall and Jason is a basketball player 
THEN 
	Jason is tall.

---
![[Pasted image 20250714175050.png]]

---
# Direct Reasoning 
## ~={red}[[Modus Ponens]]=~
It’s a basic rule of reasoning that helps us figure out something **must be true** based on a **logical if-then statement**.

if p then q  (p -> q).

---

## Truth Table Modus Ponens

|P|Q|P→QP \rightarrow Q|(P→Q)∧P(P \rightarrow Q) \land P|[(P→Q)∧P]→Q[(P \rightarrow Q) \land P] \rightarrow Q|
|---|---|---|---|---|
|T|T|T|T|T|
|T|F|F|F|T|
|F|T|T|F|T|
|F|F|T|F|T|

---

##  Rules of Inference

![[Pasted image 20250714192957.png]]

![[Pasted image 20250714193006.png]] 

---

## Shallow and Casual Reasoning 

idk what the nga prof meant with this so im adding the whole thing 
![[Pasted image 20250714194024.png]]

---

## Chaining 

Chain – a group of multiple inferences that connect a problem with its solution


|                     ~={blue}Forward chaining=~                      |                             ~={red}Backward chaining=~                             |
|:-------------------------------------------------------------------:|:----------------------------------------------------------------------------------:|
| A chain that is searched / traversed from a problem to its solution | A chain traversed from a hypothesis back to the facts that support the hypothesis. |


### ~={yellow}Some Characteristics of Forward and Backward Chaining=~



|   ~={blue}Forward chaining=~    |              ~={red}Backward chaining=~              |
| :-----------------------------: | :--------------------------------------------------: |
|        Planing, Control         |                      Diagnosis                       |
|             Future              |                         Past                         |
|          Data Drivien           |                     Goal Driven                      |
| works forward to find solutions | works backwards to find facts support the hypothesis |
|          Breadth-first          |                 Depth-First search                   |
|                                 |                                                      |
|                                 |                                                      |
|                                 |                                                      |


---
`lec 4`


# Knowledge Representation

what is knowledge 

