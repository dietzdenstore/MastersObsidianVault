First part of lecture, he was talking about ensuring human authors and not making LLM's perform tasks for you, since it hinders learning.
# What is an Argument?

## Discussion
### My own thoughts
- "Hjemmel"
A precondition / logic for something else to be logical. In relation to Software Architecture, it would be something that backed up your claim.
### Thoughts from the class:
- Logic / precondition
- Statement + reason
- Evidence
- ~~Opinion~~
- Leads to discussion
- ~~Negotiation~~
- Traceability (In regards to software architecture)

## Definition from the slides
- *... "to give an argument" means to offer a set of reason or evidence in support of a conclusion*
- *An argument is not simply a statement of certain views, and it is not simply a dispute*
- *Arguments are efforts to support certain views with reasons*
- *It is not a mistake to have strong views. The mistake is to have nothing else*
## General rules
- What are you trying to prove?
- What are the premises
- Unfold your ideas in a natural order
- Start from the reliable premises. If your premises are weak your conclusion is weak
- Be concrete and concise
- Build on substance
- Use consistent terms
#### Example:
*You should participate in group work. It enhances your learning. It's also fun because you are together with friends. Remember all the times you have enjoyed the good company of your fellow students*
## Argument Types
- How do you or structure an argument?
- Several ways of arguing
	- By example
	- By analogy
	- By authority

# Recap - Software Architecture

## Definition
*The **software architecture** of a system is the set of structures needed to reason about the system. These structures comprise software elements, relations among them, and properties of both.*

<span style="color:rgb(255, 0, 0)">(Insert definition implications from slides)</span> 

## Early Prediction of system qualities

<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 

Design is a "wicked" problem: there are rarely right/wrong answers, but rather, there are better/worse approaches, each with their own set of contextual tradeoffs

## Types of architectural views

<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 

## Types of Diagrams
<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 

## Quality Attributes
<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 

### Maintainability etc.

### Quality Attribute Scenarios
<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 

Good idea to read both from left to right AND from right to left
### Quality Attribute Tactics
<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 
#### Tactics-Based Questionnaire
<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 

## Architectural Patterns

<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 

- Problem-solution pairs that occur in a given context and are affected by it
	- Context-problem-solution triplet
- Design and Architectural Patterns
- Architectural styles
	- components, connectors, and issues related to control and data flow
- It is usually not clear when a pattern is "big" enough to be considered architectural

## Architectural Significant Requirement (ASRs)
- A requirement that will have a profound effect on the architecture - that is, the architecture might well be dramatically different in the absence of such a requirement
- Business Model
- Business Scenario
- Quality Attribute Workshop
- Utility tree

<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 

# Case Example
<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 

# Attribute Driven Design (ADD)
<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 

# The process of software architecture
![[Cervantes (2024a) - Designing Software Architectures A Practical Approach, 2nd Edition.pdf]]

# Complexity
## Class discussion
- What is a complex system?
	- More components leads to more complexity
	- Understanding architecture
	- Large set of functionality
	- Non-linear 
	- Difficult to understand
	- Many constraints
	- Difficult to implement
	- Unclear Tools
	- Unpredictable
	- Emerge as complex

- How is software architecture related to complex systems?
	- Design
	- Method
	- Abstraction
## Definition
- Cambridge Dictionary
	- "*The state of having many parts and being difficult to understand or find an answer to"*
- The DevOps Handbook
	- *"Defies any single person's ability to see the system as a whole and understand how all the pieces fit together"*


# Industry 4.0 and Challenges
![[Pasted image 20260909143733.png]]

- Increasing connectivity
- 30-50% reduction of total machine downtime
- Due to increasing connectivity
	- Security Threats
	- Scalability
	- Software infrastructure
- A way to address the software infrastructure challenge
	- Middleware
			<span style="color:rgb(255, 0, 0)">(Insert middleware architecture from slides)</span> 


## Flexible Production System
Traditional production system vs Industry 4.0 production system
<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 
### Industry 4.0 example
<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 
#### Production Sequence (Diagram)
<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 
- Is a deterministic system
## Flexible Production Processes
<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 
## Asset Interoperability Challenge
<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 


![[Pasted image 20260909145140.png]]

1. **Technical (Foundational):** 
	Establishes the basic physical and communication links so that hardware or software can send and receive raw data packets
2. **Syntactic (Structural):** 
	Defines the strict grammar, syntax, and data formats (like XML or JSON structures) for how messages are packaged and organized.
3. **Semantic:** 
	Ensures both systems interpret the exact same meaning from the exchanged data using shared vocabularies, coding systems, and data dictionaries.
4. **Pragmatic:** 
	Adds context, intent, and behavioral patterns to the data exchange so receivers understand _why_ the information was sent or how to act on it.
5. **Dynamic:**
	Manages real-time changes, updates, and continuous state synchronization between active, evolving systems or digital models
6. **Organizational:** 
	Aligns workflow processes, legal policies, governance, and business goals across different entities or departments for seamless collaboration.

## Reconfigureability challenge
<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 

### Reconfiguration Template Analysis
<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 

### Design and Tactics
<span style="color:rgb(255, 0, 0)">(Insert from slides)</span> 
