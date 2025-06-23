---
layout: essay
type: essay
title: "Smart Questions, Good Answers"
# All dates must be YYYY-MM-DD format!
date: 2015-09-08
published: true
labels:
  - Questions
  - Answers
  - StackOverflow
---

<img width="300px" class="rounded float-start pe-4" src="../img/smart-questions/rtfm.png">

# The Real Significance of Coding Standards

Coding standards are quite often misconceived. These are often looked at by outsiders or even by some beginners as impositions that are arbitrary-who is to care about tab or space, break placement, comma placement after brackets? It is really straightforward to regard them as mere appearances. But really, good coding standards have more to offer than having a say on how the code looks—they affect how the code runs, how teams work together, and how developers learn. They are, in fact, both mental constraints and long-term investments that yield dividends.

The most basic way of looking at it is: they keep you from creating junk. But the more correct version is: they help you to cultivate the habit of rational thinking before you write any piece of code.


## ESLint: Is it an Error Detector or Learning Engine?

ESLint, which is a code linter for JavaScript (and TypeScript, etc.) and, by the way, it is certainly a tool for coding standards to be enforced in real-time. First of all, ESLint is perceived as something regressive—especially in VSCode, where the red and yellow wavy lines, in essence, say that everything is broken even if your program technically runs.

But, it is this very perception of “strictness” that conceals the key value of the tool. ESLint highlights the problems at an early stage: scope errors, unused variables, bad promise handling, undeclared globals, shadowed variables, etc. These are not visual irritations. These are signs of structural weaknesses. These are code smells you would have missed, had the program experienced a quiet failure during production.

After you've resolved those issues, the result isn't just a code that has a nice appearance but it has a more robust logic.

Are the Warnings Annoying? Yes, Definitely. But They Are Also of Utmost Importance.
The majority of students, myself included, have an irritating beginning. Warnings that are, for example, "Unexpected console.log" or "prefer-const" seem rather unimportant at the beginning. What difference does it make that a variable is declared as let instead of const if the value does not change?
 
It is important because ESLint is trying to convey a message: the idea of your code should match its structure. A const declares a variable which a referencing cannot change. A let is a variable which can change. Picking the wrong one as a synonym is a kind of deception-not to the machine, but to the next human who reads your code. Or to yourself when you are coming back to it three months later and forget what you were thinking about.

Accordingly, ESLint transforms into a thing that brings a person to contemplate. Every time you get a lint error it gives you a question: Are you really sure this is what you mean?

## Are the Warnings Annoying? Absolutely. But Also Necessary.

The majority of students, myself included, have an irritating beginning. Warnings that are, for example, "Unexpected console.log" or "prefer-const" seem rather unimportant at the beginning. What difference does it make that a variable is declared as let instead of const if the value does not change?
 
It is important because ESLint is trying to convey a message: the idea of your code should match its structure. A const declares a variable which a referencing cannot change. A let is a variable which can change. Picking the wrong one as a synonym is a kind of deception-not to the machine, but to the next human who reads your code. Or to yourself when you are coming back to it three months later and forget what you were thinking about.

Accordingly, ESLint transforms into a thing that brings a person to contemplate. Every time you get a lint error it gives you a question: Are you really sure this is what you mean?

## Standards Aren’t Just About You

In the case of team projects, the necessity of coding standards comes out even more evidently. Without them, every developer is writing in his/her own personal dialect of the language. The codebase consequently becomes a mosaic. It is no longer reliable. You are wasting your time figuring out the intention instead of reading the logic.

That standard gone wrong is usually relative, though its consistency is automatically maintained and, thus, no cognitive overhead is encountered. The shift from syntax to substance comes as a gift. Thousands of files over time, time zones, developers with differeting degrees of expertise, all are unified under ESLint which enforces the same code across the board.

Think about it as a common speech that everyone in the repo knows. Or a vocabulary that is controlled in a disorganized system.
## Why Linting Also Teaches the Language

There is a crucial side effect: if you are in the process of learning JavaScript, it will be much quicker if you use ESLint.

Instead of just memorizing rules or syntax from a handbook, you get to know better the things you disobey and get corrected-instantly. ESLint discusses those expressions that are not safe or are unclear. It discourages bad scoping, provides warnings about callback misuse, and shows the way to the best practices (this sometimes is even outside of the language specification; it depends on the config used).

It's uncomfortable, definitely-but it is educational. The jelly-bean phrase makes it difficult to understand. As a result, you are not only avoiding mistakes but also writing better code because you comprehend the reasoning behind why it’s better.

## Final Analysis: Standards Improve Quality More Than Any Other Tool

If someone came to me and said that I could only use one engineering technique to enhance the average code quality of a team or a project, I would surely suggest the use of coding standards. It is neither version control nor testing that I mean. It is purely standards with strict enforcement.

Why? Because, coding standards not only deal with bugs but they also influence habits in the longer run. They alter, in fact, the way a person behaves. They push the way of reading the code and keeping it easily readable. They also prevent the readability issues and problems in maintainability and accountability for the developer. Be it ESLint or other linters used to impose them, the scaling is better than most human processes. Followed by a correct standard, you will be able to build everything else.

You are not doing it just for show. You are building habits.

## One Week with ESLint: Thoughts So Far
My experience of living with ESLint for a week in VSCode has turned me into a fan of this program. I am forced to agree that getting rid of all the errors is a Herculean task-it's torturous. But it is indeed not a waste of time! In fact, the time spent struggling with ESLint can be more appropriately called learning. You learn to explain your intentions clearly, reorganize thoughts as required, and clean the workspace of debris you were previously unaware of. It doesn’t feel as if you are really learning in a school-like environment but rather it is akin to debugging your brain.

Riddled with errors. But it is effective.

That’s the entire thrust of the matter.
