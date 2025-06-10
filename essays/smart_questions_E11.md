---
layout: essay
type: essay
title: "E11: Reflect on smart questions"
date: 2025-06-10
published: true
labels:
  - Questions
  - Answers
  - StackOverflow
---

<img width="300px" class="rounded float-start pe-4" src="../img/askquestions.jpg">

# Smart Questions, Smarter Engineers: Why the Way You Ask Matters

There’s a certain electricity in the air when a question slices through the haze and lands, sharp and clear, on a forum like Stack Overflow. Some questions are like a beacon—engineered with precision, humming with context, and practically begging for a high-voltage answer. Others, well, they flicker and sputter, lost in the static. Eric S. Raymond’s legendary treatise, “How To Ask Questions The Smart Way,” isn’t just a manifesto for getting answers—it’s a blueprint for how real engineers think, communicate, and solve problems. Let’s crack open two Stack Overflow threads, one a model of Raymond’s precepts, the other a cautionary tale, and see what happens when you ask the smart way—and when you don’t.

---

## The “Smart” Question

**Thread:** [Why is processing a sorted array faster than processing an unsorted array?](https://stackoverflow.com/questions/11227809/why-is-processing-a-sorted-array-faster-than-processing-an-unsorted-array)

Here’s the question:

```
Why is processing a sorted array faster than processing an unsorted array?
#include <algorithm>
#include <ctime>
#include <iostream>

int main()
{
    // Generate data
    const unsigned arraySize = 32768;
    int data[arraySize];

    for (unsigned c = 0; c < arraySize; ++c)
        data[c] = std::rand() % 256;

    // !!! With this, the next loop runs faster.
    std::sort(data, data + arraySize);

    // Test
    clock_t start = clock();
    long long sum = 0;
    for (unsigned i = 0; i < 100000; ++i)
    {
        for (unsigned c = 0; c < arraySize; ++c)
        {   // Primary loop.
            if (data[c] >= 128)
                sum += data[c];
        }
    }

    double elapsedTime = static_cast<double>(clock()-start) / CLOCKS_PER_SEC;

    std::cout << elapsedTime << '\n';
    std::cout << "sum = " << sum << '\n';
}

Without std::sort(data, data + arraySize);, the code runs in 11.54 seconds.
With the sorted data, the code runs in 1.93 seconds.
(Sorting itself takes more time than this one pass over the array, so it's not actually worth doing if we needed to calculate this for an unknown array.)

Initially, I thought this might be just a language or compiler anomaly, so I tried Java:
import java.util.Arrays;
import java.util.Random;

public class Main
{
    public static void main(String[] args)
    {
        // Generate data
        int arraySize = 32768;
        int data[] = new int[arraySize];

        Random rnd = new Random(0);
        for (int c = 0; c < arraySize; ++c)
            data[c] = rnd.nextInt() % 256;

        // !!! With this, the next loop runs faster
        Arrays.sort(data);

        // Test
        long start = System.nanoTime();
        long sum = 0;
        for (int i = 0; i < 100000; ++i)
        {
            for (int c = 0; c < arraySize; ++c)
            {   // Primary loop.
                if (data[c] >= 128)
                    sum += data[c];
            }
        }

        System.out.println((System.nanoTime() - start) / 1000000000.0);
        System.out.println("sum = " + sum);
    }
}
With a similar but less extreme result.

My first thought was that sorting brings the data into the cache, but that's silly because the array was just generated.

What is going on?
Why is processing a sorted array faster than processing an unsorted array?
The code is summing up some independent terms, so the order should not matter.
```


What’s happening here?  
A developer, GManNickG, supplies a full, minimal, and reproducible code sample in both C++ and Java. The question is laser-focused, the results are measured, the initial hypotheses are stated and then questioned. The user even details the steps already taken—running the code in two languages, providing timing data, and expressing confusion at the unexpected result. The tone? Neutral, curious, and open to correction. No trace of “plz help urgent.” Just honest curiosity and technical rigor.

---

## The “Not So Smart” Question

**Thread:** [How do I set text background colour with the PDF::API2 Perl module?](https://stackoverflow.com/questions/42157312/how-do-i-set-text-background-colour-with-the-pdfapi2-perl-module)

Here’s the question:
```
How do I set text Background colour with the PDF::API2 Perl module?


I want to use text background or highlight colour using PDF::API2. How I can do this?

```

What’s missing?  
No code. No error messages. No evidence of research or attempts. No context about what’s been tried or what’s not working. The question is a single sentence, floating in a vacuum. The reader is left to guess at the specifics—what version of PDF::API2? What have you tried? What does “background color” mean (highlighting text, filling a box, something else)? There’s no sign of effort, and no hook for engagement.

---

## Why Smart Questions Matter

Smart software engineers don’t just sling code—they debug, hypothesize, and communicate with clarity. The “smart” question is an extension of that mindset. When you ask the smart way, you’re not just fishing for a solution; you’re showing respect for the time and expertise of others. You’re framing your problem so it’s answerable, reproducible, and interesting. You’re inviting a conversation, not a guessing game.

Raymond’s precepts aren’t just etiquette—they’re engineering.  
- **Do your homework:** Show what you’ve tried, what you suspect, and where you’re stuck.
- **Be specific:** Give enough code, data, and context so others can see what you see.
- **State your expectations:** What did you expect to happen? What actually happened?
- **Be concise but thorough:** Don’t bury the question in noise, but don’t starve it of detail.
- **Be polite and open:** You’re asking for help, not demanding a fix.

---

## How the Threads Stack Up

### The “Smart” Question:  
- **Fulfills Raymond’s precepts:**  
  - Full code sample, timing data, and cross-language testing.
  - Clear statement of the problem and hypotheses.
  - Concrete, focused questions.
  - Polite, professional tone.
- **Community response:**  
  - The answers are as sharp as the question.  
    - Mysticial’s top answer breaks down branch prediction, using both analogy and technical detail.  
    - Others add benchmarks, code optimizations, and even assembly-level analysis.  
    - The discussion is rich, nuanced, and educational—branch prediction, compiler optimizations, cache effects, and more, all unpacked with diagrams, code, and real data.
  - The original poster and other users engage, ask follow-ups, and clarify points. The thread becomes a living document, referenced by thousands.

### The “Not So Smart” Question:  
- **Falls short of Raymond’s precepts:**  
  - No code, no context, no evidence of research.
  - Vague, underspecified request.
  - No engagement or follow-up.
- **Community response:**  
  - Sparse, tentative answers.  
    - Users guess at what the asker might want—do you mean highlight? Draw a rectangle?  
    - Suggestions are generic, sometimes just links to documentation.  
    - No real discussion, no depth, no “aha!” moments.
  - The thread fades into obscurity, unlikely to help anyone else.

---

## Insights: What I Learned

The difference is night and day. The “smart” question doesn’t just get a better answer—it creates a feedback loop of learning and engagement. The asker gets a deep, nuanced explanation. The answerers get to flex their expertise and contribute meaningfully. The whole community benefits, because the thread becomes a resource, not just a transaction.

The “not so smart” question? It’s a dead end. No one learns, no one’s inspired, and the next person with the same problem is left stranded.

But here’s the kicker: asking smart questions isn’t just about forum etiquette. It’s about thinking like an engineer. It’s about breaking down problems, testing hypotheses, and communicating clearly. It’s about being the kind of developer who doesn’t just solve problems, but helps others solve them too.

So next time you’re stuck, remember:  
Don’t just ask for a fish. Show your work, ask a real question, and you might just spark a conversation that lights up the whole room.

---

**Smart question thread:**  
[Why is processing a sorted array faster than processing an unsorted array?](https://stackoverflow.com/questions/11227809/why-is-processing-a-sorted-array-faster-than-processing-an-unsorted-array)

**Not so smart question thread:**  
[How do I set text background colour with the PDF::API2 Perl module?](https://stackoverflow.com/questions/42157312/how-do-i-set-text-background-colour-with-the-pdfapi2-perl-module)

---

*Ask smart. Code smarter. The difference is everything.*

