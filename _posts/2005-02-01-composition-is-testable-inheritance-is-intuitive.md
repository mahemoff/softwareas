---
id: 52
title: Composition Is Testable, Inheritance Is Intuitive?
date: 2005-02-01T23:51:17+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=50
permalink: /composition-is-testable-inheritance-is-intuitive/
categories:
  - SoftwareDev
---
Ivan Moore [illustrates how to replace inheritance with composition](http://ivan.truemesh.com/). He explains why the solution is testable, but I would argue there is a flipside: the resulting design is less intuitive. A compromise must be made between testability and intuitiveness, which suggests a technology deficiency.

Ivan's Emphasiser example is a textbook case of two competing architectural styles. The *inheritance* style encapsulates word emphasis in a template method; whereas the *composition* style encapsulates word emphasis in a separate class. Even before mock objects, design authorities such as [the Gang of Four (GoF)](http://mahemoff.com/paper/software/learningGoFPatterns/) urged developers to consider delegation instead of inheritance. In many cases, inheritance is abused, and delegation is a more logical relationship.

However, in this example, inheritance is not abused at all. It is reasonable to have subclasses varying on word emphasis. Admittedly, the composition model is more flexible: if you wanted to emphasise sentences and numbers as well, then composition would let you have any combination of emphasis strategies. But, for the design as is, inheritance offers a unit of "close classes".

In single-inheritance languages, an inheritance hierarchy makes a convenient "module"; the superclass and its descendants are partitioned off. When the "isa" relationship really is present, it's worthwhile making use of it to produce such a module, and that's the case for the inheritance structure. The composition example contains twice as many such modules (Emphasiser and WordEmphasiser).  In this case, a further refactoring would help: incorporate the GoF *Composite* pattern: rename Emphasiser to "DocumentEmphasiser" and create a new Emphasiser interface which both DocumentEmphasiser and WordEmphasiser implement. Now we're back to one inheritance hierarchy, and one which expresses the DocumentEmphasiser-WordEmphasiser relationship more explicitly. Even so, this is still more complicated than a simple inheritance hierarchy.

And for all that, the composition architecture is the one I'd likely use in this case. Testability, as the blog entry says, is the key. Many developers think that designs shouldn't be influenced by testability. Utter nonsense! Programs are not oil paintings ... they are there to solve a problem, not to be admired for their elegance. Hopefully, elegant solutions will also solve problems, but in some cases a trade-off must be made. One of the use cases for software is testing it, so this use case must be considered in evaluating design choices.

In this case, composition is a bit less elegant, but a lot more testable, than composition. So it's the optimal choice in most real-world situations. (Though I'd consider taking it further with *Composite*.)

So here's the point: do we have to make the trade-off between testability and intuitiveness? All this shows there is an opportunity to create superior testing and language facilities. In an ideal environment, there will be no trade-off to make; the best design will be sufficiently testable.