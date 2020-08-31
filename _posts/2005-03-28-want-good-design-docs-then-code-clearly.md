---
id: 79
title: Want Good Design Docs? Then Code Clearly!
date: 2005-03-28T11:26:45+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=79
permalink: /want-good-design-docs-then-code-clearly/
categories:
  - SoftwareDev
---
Martin Fowler makes some good points about <a href="http://martinfowler.com/bliki/CodeAsDocumentation.html">Code As Documentation</a>. It fits in with Scott Ambler's [Agile Documentation text](http://www.agilemodeling.com/essays/agileDocumentation.htm) text.

In line with those, here's my summary on documentation and agile development:

> **Documents are often necessary. But for any aspect of design, prefer expressing it in code over expressing it in a document. **

Doing so obviously benefits the code base:

> Self-documenting code means the code base is easier understood. This delivers value by making the code more robust and maintainable.

And - less obviously - yields great benefits for the documentation itself:

> Self-documenting code means the documentation focuses on high-level matters that count. It will usually be based on industry-standard patterns that are easily conveyed in a design document, and the design document will be able to point them out and discuss how and why they have been used in the particular project context. The code will support internal reuse, so there Will be less components to document. And components will work in the same way - even when those patterns are not industry standard, they will only need to be described once.

> In contrast, poor code requires detailing the minutiae of all the idiosyncratic decisions that were made. These were often made by different developers, and differ for arbitrary reasons.

> When something is intrinsically clear, it requires little or no documentation. Doors don't require instruction manuals; safety-critical chemical plants do. Where you have any choice, make your code as intuitive as the former, and this will minimise your documentation needs. The complexity of any programming problem is fixed, but it is the developer who determines how much extra complexity the code adds.