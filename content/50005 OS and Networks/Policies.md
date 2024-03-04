# Security Policies
---
**Security policy** is a statement of what is and what is not allowed
- Requirements to a system, or refinements of more abstract properties
**Security Mechanism** is a method, tool or procedure for enforcing a security policy
- 3 classes: Prevention, Detection, Recovery

 Types of **Access Control**
	 - Discretionary or Mandatory Access control
	 - Discretionary means sys admin can modify another person's access control, while Mandatory means no one can change another's access control

Confidentiality policy:
- Prevents unauthorized disclosure of information
- I have a function $c$ that filters all the inputs to give me the set of inputs $A$ that can be revealed

Protection Mechanisms
- A function that will return $p(i_{1},...,i_{n})$ if the set of inputs are valid, and Error Message if the set is not.
- It is only secure if:
	- Protection mechanism m returns values consistent with the stated confidentiality policy c
	- Consistent means that the inputs that you block out are because they will result in outputs that would impart confidential information
	- There exists $m'$ such that $m(i_{1},...,i_{n}) = m'(c(i_{1},...,i_{n}))$

Key ideas:
- **Policies** describe what is allowed
- **Mechanisms** control how policies are enforced
- **Trust** underlies everything


## Confidentiality Policy Model
One implementation is **Bell-LaPadula**
- For **reading**, Information flows up, not down 
	- i.e. "Read up disallowed", "read down" allowed
	- Simple Security Condition (Step 2)
		- Subject s can read object o iff L(s) dom L(o) and s has permission to read o.
- For **writing**, the information flow is reversed
	- i.e. "Writes up" allowed, "writes down" disallowed
	- Although can write stuff that have higher classification, cannot read the stuff that were written before hand, can only write to it
	- Star ($*$) property 
		- Subject s can write object o iff L(s) ≤ (dom) L(o) and s has permission to write o.
- Besides classifications, security levels include **categories** (i.e. imagine security levels to be **vertical** in nature, while categories are **horizontal** in nature)
	

Definitions:
- **dominate** (dom) idea is if A dom B, then B is a subset of the rights afforded by A
- Security levels are arranged in linear ordering.
	- ✓Top Secret:highest
	- ✓Secret
	- ✓Confidential
	- ✓Unclassified: lowest
- Subjects (s) have security clearance L(s).
- Objects (o) have security classification L(o).

## Integrity model
Definitions:
- **Integrity** labels are associated with subjects and with objects in our system. The label should reflect the trustworthiness of the subject or reliability of the info in the object.
	- NOTE: Nothing to do with confidentiality!
		- Example: For example, a physics professor might have integrity label: (Expert: {Physics})  meaning that she has a very high degree of credibility in her area of **Physics**.  But there’s no particular reason to trust her opinion on a matter of **politics** or **animal husbandry**.
- A system consists of a **set S of subjects**, a **set O of objects**, and a set **I of integrity levels**
- The relation ≤ ⊆I ×I holds when the second integrity level dominates the first.
	- Some possible operations:
		- min: I ×I → I gives the lesser of two integrity levels (with respect to≤).
		- i:S ∪O →I returns the integrity level of an object or asubject.
		- r⊆S ×O defines the ability of a subject to read an object.
		- w⊆S ×O defines the ability of a subject to write to anobject.
		- x⊆S ×S defines the ability of a subject to invoke (execute) another subject.

Ken Biba (1977) proposed three different integrity access control policies:
1. The Low Water Mark Integrity Policy  
2. The Ring Policy  
3. Strict Integrity

Policies:
- Under the ring and low watermark model, anyone can read anything

**Low watermark policy**
What is it? 
1. s ∊S can write to o ∊O if and only if i(o) ≤i(s).
	- Means: Subject can only write to less trust worthy object
2. If s ∊S reads o ∊O, then i ́(s) = min(i(s),i(o)),where i ́(s) is the subject's integrity level after the read.
	- Means: If Subject absorb information from O, then the new integrity level of subject is the lower of the two (Subject and Object)
	- idea of lowering integrity levels when it is being read -- this is a characteristic of a low watermark policy
3. s1 ∊S can execute $s_2$ ∊S if and only if i(s2) ≤i(s1)
	- I.e. Kernel can execute user program instructions and kernel instructions, but user program cannot execute kernel instructions

**Problems**
- However, low watermark policy will cause Indirect modification problem
	- Because subject levels lowered when subject reads from low-integrity object.
- Solution: keep subject levels static (**Ring** policy)  
	- Anyone can read anything 
	- Puts trust in user/system that it is fully patched etc
	- But this is very naive

A solution is the third integrity policy: **Strict Integrity (a.k.a) Biba's Model**
1. s ∊S can reado ∊O if and only if i(s) ≤ i(o). 
	- i.e. “no reads down”
2. s ∊S can writeto o ∊O if and only if i(o) ≤ i(s). 
	- i.e. “no writes up”
3. s1 ∊S can execute $s_2$ ∊S if and only if i(s2) ≤i(s1).

## Lipner Model
In order to meet the **five commercial requirements**:
1. Users will not write their own programs, but will use existing production programs and databases.
2. Programmers will develop and test programs on a nonproduction system; if they need access to actual data, they will be given production data via a special process, but will use it on their development system
3. A special process must be followed to install a program from the development system onto the production system.
4. The special process in requirement 3 must be controlled and audited
5. The managers and auditors must have access to both the system state and the system logs that are generated.

Combine both the Bell-LaPadula and the Biba models
1. Bell-LaPadula component first (control reading)
2. Add in Biba component (control writing)

**Why do we need to add in Biba component?**
1. Just using Bell-LaPadula is too inflexible -- sometimes higher up need to update lower level integrity code but cannot due to no write down rule  
2. Solution: have two different levels to control the reading and writing respectively
	1. Check integrity level if you can write
	2. Check security level if you can read
#foc