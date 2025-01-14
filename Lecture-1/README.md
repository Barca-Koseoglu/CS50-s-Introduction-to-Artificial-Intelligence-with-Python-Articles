# Lecture 1: Knowledge

## Knowledge
A lot of intelligence is based on knowledge, especially for human intelligence. People *know* information, and using that information, they're able to draw conclusions and reason about the information in order to figure out how to do something or figure out another piece of information.

With AI, we want to take knowledge and find a way to reason with and act upon it.

**Knowldge-based agents**: agents that reason by operating on internal representations of knowledge.

## What do we mean by reasoning based on knowldge?

Take a look at these three sentences:

*If it didn't rain, Harry visited Hagrid today.*

*Harry visited Hagrid or Dumbledore today, but not both.*

*Harry visited Dumbledore today.*

These are all pieces of informations; facts that we know. We humans can try to reason about this; since Harry visited Dumbledore today, he **didn't visit Hagrid today**. Using this new piece of information we infered from the given information, we can also say that **it rained today**, because if it didn't, Harry would've visited Hagrid, but we **know** Harry didn't visit Hagrid.

This brings the question: how can we make our AI **logical**? How can we make it reason like we can?

One thing to note is that humans normally reason with logic using language. AI, on the other hand, can't actually understand language, so it relies on more formal ways to reason with logic:

**Sentence**: an assertion about the world in a knowldege representation language; it states a fact that AI can understand in its own language.

**Propositional logic**: Logic based on statements about the world. **propositional symbols** are symbols- most likely letters- that represent a fact about the world. For example, *P* might represent the fact that it rained today.

**Logcial connectives**: symbols that help us connect propositional symbols together to reason more facts that might exist. 

### Types of logical connectives:

**NOT (!)**

<img width="150" alt="notpic" src="https://github.com/user-attachments/assets/da468bbf-af6f-446e-9527-b3a3c9d2e8b3">

This is called a truth table, which demonstrates what NOT means when we attach it to a sentences. If P is false, NOT make it true, so P = False, !P == True. If P is True, then !P is False. It essentially makes the sentence the opposite of what it is, kind of like English.

**AND (^)**

<img width="212" alt="andtable" src="https://github.com/user-attachments/assets/ea7fffc3-af35-4981-a8a7-fd3e7546a0f4">

AND **combines** two different sentences together. In the diagram, P and Q are two different sentences. P^Q is True if and only if both P and Q are True. If either one or both are False, then P^Q is False.

**OR (v)**

<img width="207" alt="ortable" src="https://github.com/user-attachments/assets/5b1207a6-0e52-4e21-b93a-2823554db923">

OR also combines two sentences together, written P v Q. If at least one of the sentences are True, then P v Q will be True. If both are False, it will return False.

**Implication (->)**

<img width="371" alt="impgraph" src="https://github.com/user-attachments/assets/de7b4c98-520c-4aa4-b822-aef28a8b2bdd" />

Implication is when P IMPLIES Q. That means P makes a statment about Q. So if P is True, whatever Q is will be the answer. Let's say if it is raining, I will be indoors. This is P -> Q. Where P is True and Q is True. If Q is False, that means that if it's raining, I will be someplace other than indoors, which makes the statement False. Now, if P is False, then it doesnt affect Q at all. P makes no claim at all. If "if it is raining, I will remain indoors" is said, and it isn't raining, then the statment isn't making any claim, so whatever Q is, whether it's staying indoors or outdoors, will be True.

**Biconditional (<->)**

<img width="196" alt="bicon" src="https://github.com/user-attachments/assets/21c78eaa-cc62-43d0-a028-41f9520676c7" />

A Biconditional says "if and only if." So you could say I will be indoors, if and only if it's raining. It demonstrates what will happen if it isn't raining. in this case you won't be indoors no matter what. If I am indoors, it's also reasonable to include that it's also raining. They both imply each other, that's why it's only true if both of them are the same.

These five are going to form the core of propositional logical, the language we use in order to describe ideas and reason abou those ideas.

## Additional terms

**model**: assignment of a truth value to every propositional symbol, creating a "possible world". So if we have P and Q, where P claims it's raining and Q claims it's Tuesday, then the model could show a possible world where P is True and Q is False by assigning them the values (P=True, Q=False). If there are N vairables, the number of possible worlds is 2^n, because each variable can be 2 things, True or False.

**knowledge Base**: A set of sentences known by a knowledge-based agent. We give our AI agent information about the world, like what's True and False.

**Entailment**: α ⊨ β. In every model in which sentence α is True, sentence β is also True. "Alpha entails Beta". This means in every model, in every possible world, this stands. This helps us draw conclusions. So if alpha is something like "I know that it's Tuesday in January", then a reasonable beta could be "I know for sure that it's january". The first sentence *entails* the second statement. It's this idea of entailment that we want. We'd like our AI to infer and draw out conclusions from sentences we give it.

### Inference example

P: it is a Tuesday.

Q: it is raining.

R: Harry will go for a run.

KB (knowledge base): (P ^ !Q) -> R (if it is Tuesday AND it is NOT raining, then that IMPLIES that Harry will go for a run.). P (P is True, it is Tuesday). !Q (Q means it's raining, so in order for !Q to be True, then it can not be raining).

Using these, we can draw inferences. P ^ !Q is only True is both P and !Q are True. We know that both of those statements are True from the knowldge base, so since the left part is all True, that IMPlIES the right part is also True. So we can infer that R is True, and we can add it into our knowldge base. This is the beginning of an **Inference Algorithm**. The question we want to ask, with a given query Alpha, is does KB entail alpha? KB ⊨ α? This is equivalent to saying "given the information in KB, can we conclude that Alpha is True?"

## How do we create these algorithms, though?

Turns our there are many different algorithms. One of the simplest algorithms is called **model checking**.
