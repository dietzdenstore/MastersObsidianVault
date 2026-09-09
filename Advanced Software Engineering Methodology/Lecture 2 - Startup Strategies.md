# **Lean Software Development**
## Why Lean?
- Project often feel slow or wasteful
- Teams deliver features no one uses
- Late testing leads to expensive bugs
- Local optimizations don’t help the whole system
## Where Lean Came From
![[Pasted image 20260908082035.png]]
## Illustrative Case:
![[Pasted image 20260908082549.png]]

## The Three Ideas Behind Lean
![[Pasted image 20260908082958.png]]

## ShopNow Example:
![[Pasted image 20260908083157.png]]![[Pasted image 20260908083204.png]]![[Pasted image 20260908084336.png]]
![[Pasted image 20260908084606.png]]

# **What you (Students) should be able to do**
1. Map
	Locate queues, handoffs and bottlenecks in a software value stream
2. Diagnose
	Connect delivery problems to the seven Lean principles.
3. Improve
	Choose a small intervention that reduces delay or failure demand.
4. Measure
	Use flow and quality measures to judge whether the system improved.
# **Seven principles of Lean Software Development**
### 1. Eliminate waste
Waste is anything that doesn't add value to a product. As in lean manufacturing, value is determined not in the mind of the developer, but in the mind of the customer. This isn't just about the value of the product, either, it factors in the temporal dimension. Anything that gets in the way of rapidly satisfying a customer need is waste.

**Waste** = anything that doesn’t either add **customer value**
- Many of these wastes have their roots
	- **partially done work** – e.g., unfinished features, code waiting in branch
	- **unused features** – e.g., building things customers don’t use
	- **delays** – e.g., dependencies, waiting for approvals, slow reviews
	- **defects** – e.g., bugs, poor quality
- Goal – **focus effort on activities that create value**
- Less waste → faster delivery, lower costs, and higher quality
#### Example - Waste hunt: ShopNow Release 18
![[Pasted image 20260908094717.png]]
![[Pasted image 20260908095250.png]]

#### Case Study: E-commerce Platform
- Scenario:
	- Thousands of products overstocked because of bad demand prediction
	- Manual double-checking of orders in warehouse slows flow.
	- Multiple product descriptions entered in different systems (redundancy).
- What types of waste are visible here?


### 2. Amplify learning
This is one of the key areas where lean software development deviates from lean manufacturing. The Poppendiecks contrast development as "an exercise in discovery" with manufacturing as "an exercise in reducing variation." Since discovery depends on creativity, knowledge, and experimentation, lean software development is supposed to produce multiple iterations of an idea as part of a learning process. 

### 3. Decide as late as possible
This is how the lean approach manages the uncertainty inherent in any process as complex as software development. Given that there are many levels of uncertainty inherent in any software development project (e.g. lack of clarity from customers, unknown progress of competitors, untested capabilities of hardware, etc.), it makes sense to avoid committing to one development course until absolutely necessary. This avoids doing work based on potentially faulty assumptions that may have to be redone once more certain knowledge comes to light. 

### 4. Deliver as fast as possible
Traditional software development often emphasizes the need to avoid making any mistakes. This makes sense given the fact that a lot of early software was used for applications where mistakes could be dangerous and/or incredibly expensive, such as space missions. As software became more widespread, speed became more valuable for many reasons. 

Speedy development minimized the time between when customers delivered specifications and when they received their software, reducing the risk that the software would be obsolete by the time it was delivered. In addition, speedy delivery allows for more of what the Poppendiecks described as "discovery cycles": "Design, implement, feedback, improve."

### 5. Empower the team
Successful software development depends on managing numerous details precisely and correctly. Since no one knows the details of the software like the developers, they should be trusted with making many of the important decisions about how to proceed. Not only that but having decisions made by a central authority slows the process—and creates waste—because of time spent sending inquiries and waiting for replies. 

### 6. Build integrity in
Often rephrased as "build quality in," the original conception of lean software development saw integrity as a kind of intuitive design that perfectly mirrors a user's desires. Integrity is also supposed to make the software adaptable, extensible, and maintainable. 

### 7. See the whole  
Often rephrased as "optimize the whole," or "improve continuously," the impetus to see the whole comes from the potential for numerous defects that can come from breaking a large project into smaller pieces or having multiple organizations working on a project together but separately. By fostering healthy competition between groups, management can achieve outstanding productivity between the different teams.

![[Pasted image 20260908090638.png]]
#### **End-to-end process** (Food app example)
- **Student is hungry & opens the app**
- **Browsing** – looking through options and choosing an order → _(1 & 2 together take about 5 mins)_
- **Ordering** – selecting a pick and paying → **1 min**
- **Kitchen receives the order** → **1 min**
- **Prepares the order** → **15–30 mins**
- **Notify the student** (order's ready) → **1 min**
- **Student picks up & eats it** → **1 min(s)**
- **Feedback** (no time listed)

#### **See the whole (E-commerce platform example)**
- You are a part of a software engineering and operations team building a large-scale e-commerce platform. Customers expect:
	- **Fast, smooth experience** (search, browse, checkout)
	- **Trustworthy service** (e.g., secure payment, reliable delivery)
	- **Continuous improvement** (e.g., new feature, better recommendations)

- Value stream:
	- customer search – select products to cart – checkout & payment
	- -warehouse picking/packing – shipping – delivery – post services & customer satisfaction

- Scenario:
	- The UX team optimizes checkout speed: page load time drops from 4 seconds → 1 second
	- Payment team adds new providers (Visa, PayPal, Apple Pay)
	- Warehouse buys faster scanners
	- These are local wins
		- customer still complains: “it takes too long to get my package”
##### **Mapping the value stream**
- Checkout - 1 min
- Payment - 2 min
- Order processing - 1 hour
- Warehouse -1 day
- Shipping 2-4 days

What is the bottleneck here?
Clearly, shipping & warehousing dominate the flow.
###### **Focus on the bottleneck!!!**
- If warehouse & shipping takes 3-4 days, optimizing checkout speed from 4 sec to 1 sec is meaningless.
- Invest in **faster and last-mile delivery** instead

#### Measure End-to-end Customer value
- As a customer, do you care about
	- faster checkout or getting package quickly, reliably, and correctly?
- Where would you invest more if you want happier customers?



<span style="color:rgb(255, 0, 0)"><b>NEED TO FILL OUT THE REMAINING, AS THE LECTURE DIDNT COVER ALL</b></span> 