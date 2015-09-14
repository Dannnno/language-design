**Question**

Pick three quotes from the readings about language design. Good candidates 
are:

   + Something you agreed with / resonates with your own experience
   + Something you disagree with
   + Something that is interesting, a new idea or perspective you'd like to remember
   + Something you didn't understand

For each quote, describe what it was about the quote that led you pick it.

**Response**

> In a way, a language design of the old school is a pattern for programs. But now we
> need to “go meta.” We should now think of a language design as a pattern for language
> designs, a tool for making more tools of the same kind.  
> ... 
>  
> My point is that a good programmer in these times does not just write programs.
> A good programmer builds a working vocabulary. In other words, a good programmer
> does language design, though not from scratch, but by building on the frame of a base
> language. [Steele, 1998]

What I really like about this section is that it really addresses what it means to design a language, and how that should affect how we write code.  Very frequently when I talk to people about programming languages, or being interested in software development, most people simply assume that a programming language is voodoo and that software development is just lines and lines of that voodoo.  And while there are voodoo languages, and some people develop software like that, they're both doing it wrong.  

In today's era of quickly shifting standards and models, where every year some hot new language or approach to design comes out, we need to be more flexible with how we use languages, and how and why we design new ones.  When we think of language design as a tool for making more tools, we greatly enhance our ability to use existing tools in new ways, because they were designed to be used in new ways.  This is what it really means, to me, to build a working vocabulary.  Like the author mentioned in the text, every language has some set of primitives, and in order to extend that language you must define things in terms of those primitives.  As you build your working vocabulary you're naturally extending the language, and developing new programs.

As a side note, even though this class focuses on language design, you can also look at this quote from the other direction. That is, when you are just doing standard coding, you are still not free to ignore the problems that language design has. Ultimately, your code will be used by other people, and will be adapted and grown into doing things it was not originally intended to do. The code you write implicitly defines a mode of thought and a way to interface human ideas with the computer. In the same way that scientists still have to learn to write well and communicate their ideas, code has to be usable and extensible. So, studying language design may well also be useful when just "coding".

> If your standard is natural language, division/fraction notation isn't particularly intuitive.
> But to someone who knows the notation, ab / b is very intuitive, and it's immediately obvious that
> you can cancel the bs. So the goal of an intuitive programming syntax shouldn't be to emulate
> natural language, necessarily, but to provide intuitive hooks and syntax for the types of things
> that programmers do a lot. 
> [Comment by "Peter" ([Source](https://www.fastcodesign.com/1665735/why-arent-computer-programming-languages-designed-better#comment-bc08f700-3c06-11e1-921b-9794fc737ae8))] [Pavlus, 2012]

I feel that this comment on the Pavlus article really gets to the heart of the matter - that knowing the notation is part of any (technical) job, and once you can grok it, it becomes second nature.  So while natural language may make it easier to read and write code at first, when it comes down to it the most important thing is making sure that someone who uses it often (i.e. professionals and very passionate amateurs) can do what they need to do clearly and easily.

The other point is that often, natural language is *not* actually suitable for certain purposes. Many notations are much *easier* than natural language. Usability is indeed a good aspiration, but the answer isn't so simple as "natural language". In fact, there probably isn't just one good answer. Hence why we are in a class called domain-specific languages!

> **Example code should be exemplary.**  
> If an API is used widely, its examples will be the archetypes 
> for thousands of programs. Any mistakes will come back to haunt 
> you a thousand fold. [Bloch, 2006]

This is perhaps my favorite quote of the entire reading.  Having spent this past summer working with a horrible API (most modules were not documented, and only 23% of the examples worked (we checked)) I appreciate and understand this the most.  Your API is how to get developers to use your project.  If you make a large barrier to entry in the form of missing or bad documentation and examples, they will look elsewhere for their solutions. 

Meanwhile, bad examples are also indicative of other problems. To make a good language, you should have a good idea of how it should be used. Furthermore, it should be useful in the sense that "the way it should be used" should be *good*. If you find yourself writing poor examples, that may mean that the easiest thing to do in your framework is write bad code, and that you may not have put enough time into considering how you intend your work to be used.

---

**Question**

How do the themes of _Growing a Language_ relate to the lab we did this week?

**Response**

In the sound lab there was the issue that each sound could only have a single transformation applied to it (and an unavoidable side effect of playing the sound and writing to a file).  This made it very hard to extend the library - multiple transformations couldn't be done by cleanly calling multiple methods sequentially, but instead by writing a new function that explicitly performed all of those transformations (or even worse, daisy-chaining using the fact that the output file name was "out.wav").  This violated [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) as well as ease of expansion and use.  

If it had been designed in the style that _Growing a Language_ recommended, however, it would be easy to make the change mentioned above (chaining sound transformations) as well as extending the module to perform new, unplanned-for things such as playing or transforming an entire musical score.  The way the language (module) is planned from the get-go has a huge impact on the way users can and will use your module, or if they will at all.

> Parts of the language must be designed to help the task of growth. A good set of types,
ways for a user to define new types, to add new words and new rules to the language, to
define and use all sorts of patterns—all these are needed. The designer should not, for
example, define twenty kinds of number types in the language. But there will be users
who, all told, beg for twenty kinds of numbers. The language should have a way for the
user to define number types that work well with each other, and with plus signs and other
such signs, and with the many ways of pushing bits in and out of the computer.  [Steele, 1998]

It wouldn't have made sense for the designer of the sound lab to make it able to work with whole scores - but it should have been designed so that someone else could make it do that if they wanted to.  In the same way that it doesn't make sense for the language designer to define 20 numeric types, the designer shouldn't have 1000 sound transforms - but it should have been doable for those users who do need that functionality.

---

**Question**

How would you know a well-designed language? What are the symptoms? How would
you know a poorly designed language? What are the symptoms?

**Response**

There isn't really a definitive set of rules for determining what is (or is not) a "well-designed" language.  In general you can have an idea about how well-designed a language is by how easy it is for you to use it, how many other people use it (proportional to how long it has been around/known), and if it meets some other criteria.  For example, as Steele pointed out in his article, "the sole way to win is to plan for growth" [Steele 1998]. Thus a well-designed language needs to plan for growth, both by the developers and by users.  It should also be relatively straightforward to use - the more you have to check the documentation for a single task, the more likely it is that it was poorly designed.  "Documentation matters." [Bloch 2006].  By the same token, it should follow the principle of least surprise - "Every method should
do the least surprising thing it could, given its name. If a method
doesn’t do what users think it will, bugs will result." [Bloch 2006]

Additionally it should be designed to take as much of the load off of the user as possible - for example, if a large amount of boiler plate code is required to do a certain task, that boiler plate should be pulled into the language itself and only require the minimum amount of input from the user.  "Don’t make the client do anything the library could do" [Bloch 2006]. This leads into the additional point of productivity - users should be able to use the language without fighting it, and be able to complete their tasks in a productive manner.

Additionally, in the case of a DSL, it should be usable by domain experts who have little to no knowledge of programming.  Likewise, it should be difficult to misuse (and ideally easy to use for what it is designed as well).  "What is easy to do?  What is hard to do?  What is impossible?" [Prof Ben, 2015].

---
 
**Question**
 
In what way is an API a language? 

**Response**

An API is a way to communicate a series of instructions to a computer. It defines a set of concepts and abstractions about objects and manipulations, to make it easier to use and understand by humans. It defines exactly what is easy to do, what is possible to do, and what cannot or shouldn't be done. It is often difficult for the users to directly modify an API. However, it still needs to be able to be used flexibly and extensibly, in situations and for purposes that were not foreseen when it was developed. Things that can be problematic for a language can also be problematic for an API, from the need of documentation to violating the principle of least surprise. The main difference is that in an API, your choices of syntax and power are more limited than the general case. However, as it tends more and more towards a true internal DSL, that boundary can also become blurrier.

It might be possible to give technical definitions that would let you distinguish APIs and full-blown languages. But, if you were to take Python's duck-typing approach and ask, "Does it look like a language? Does it act like a language?", the answer is yes.

---

**Question**

The comments on the Pavlus article seem to set up a conflict between
professional programmers and everyone else. What is the essence of this
conflict? Do you sympathize more with the substance of the article's arguments
or with the substance of the majority of the commenters' arguments? Do you
sympathize more with the tenor of the article or the tenor of the majority of
the commenters?

**Response**

There are two interesting, and not necessarily conflicting, points of view in this article (and its comments).  On the one hand, there are the programmers, many of whom would assert that it is OK for there to be some kind of overhead: 

> Our languages may be esoteric and the tools hard to master, but show me any other technical profession where tools are straightforward to learn and mastery comes easily. [Comment by "Strengthiness" ([Source](https://www.fastcodesign.com/1665735/why-arent-computer-programming-languages-designed-better#comment-93e75ca0-9b5b-11e4-a3e4-4930d33952b2))] [Pavlus, 2012].  

There are even those who think that it is good for there to be this overhead:

> The issue with writing software is not being able to program; it's being able to program \*well\*.

> There are a number of languages out there which have been specifically designed to be easier to write for novice programmers.  
> ...  
>  
> I guess most companies have got somewhere ... [a] program that they rely on for some task but which is woefully inadequate, or worse, a security minefield, because it was written by someone who didn't really understand the technical issues. [Comment by "Simon" ([Source](https://www.fastcodesign.com/1665735/why-arent-computer-programming-languages-designed-better#comment-95ed5400-5bc1-11e1-921b-9794fc737ae8)) [Pavlus, 2012].  

 
They raise a good point - programmers handle a lot of really important, really sensitive things that should certainly be done as well as possible.  Furthermore, the purpose of the tool is to design it to be usable by the programmers once they have learned their craft - something designed for novices may end up being used exclusively by novices. 

However, perhaps the most important point that programmers make is that there is much, much more to software development than just the lines of code.

> The key to understandable code (apart from being well structured..and formed..) is appropriate commenting.

> Oh and hopefully some unit tests, or TDD, and some autodoc....and maybe reSharper...oh and using common design patterns...oh and.

> Wait a second, this programming thing isn't just about the actual code! [Comment by "Drew Brigham" ([Source](https://www.fastcodesign.com/1665735/why-arent-computer-programming-languages-designed-better#comment-1da48980-66bd-11e1-921b-9794fc737ae8))] [Pavlus, 2012].

While an easier language to learn may help to some extent, there are many other  important (and often harder) concepts that are necessary. 

On the other hand, it is maybe irresponsible to dismiss the complaints of those who are less technically fluent. We don't want to make the mistake of conflating the problem with the flawed suggested solution, thereby discarding both.

The "repeat" code example given in the article is an excellent microcosm of this point. Several commenters correctly point out that "repeat" is actually a horrible solution. You almost never want to loop some number of times, that's just incidental. The actual concept being expressed is that you want to do something for each element of some collection. The standard for-loop notation is much more flexible and (eventually) understandable than the "repeat" notation. However, although "repeat" is a bad idea, revisiting for-loops is not. If Guido van Rossum had not paid attention to this kind of complaint, we would never have gotten Python.

A lot of advances we've made past older languages that are now ridiculed for being obtuse came from listening. We should accept that these are real problems, with non-obvious and tradeoff-y solutions, but that solving them would be a *good* thing. The real point that should be made to people who bring up complaints like these isn't that they're foolish and don't know what they're talking about. It's that despite first appearances, these issues are extremely difficult to solve well, but we are indeed going to try.

---

**Question**

How do implementation choices (e.g., as an interpreter/compiler or as an
internal DSL) affect the user experience? Can or should we always hide our
implementation choices from users?

**Response**

The best (and possibly only) reason to let the user know what the implementation details are is if it affects (especially restricts) the things the user is able to do, and the things the user **must** do in order to make their program run.  For example, in the choice between an interpreter and a compiler, there is a difference in what you're able to do at runtime, as well as the existence of a (potentially executable) generated file.  Additionally, performing things such as static analysis is generally easier when everything happens at compile time versus runtime.  

In general, we should hide as much as possible - details about the internal parser or AST are almost certainly irrelevant to the end user, and would only confuse the user.  "**Keep APIs free of implementations details.**	 They confuse users and inhibit the flexibility to evolve." [Bloch, 2006].  In general, any implementation choice that affects how it is run, written, or edited, should be revealed to the user to the extent they need it for their workflow.

However, there is a case that could be described as exposing implementation details. Sometimes we are tempted to hide implementation so much that we lose extensibility, and lock users into one workflow. For example, the CS5 sound lab tried to hide file operations except for reading in from an initial file. As a result, every function automatically wrote to a file and then played the result, because there was no easy way for the user to do those actions. Another related question is how much to allow interoperability between an internal DSL and the host language. Sometimes it is convenient to provide optional hooks into what could be considered implementation details.

Therefore, implementation details should be hidden until the point that they limit extensibility. Those details that are exposed should be entirely optional, available to the advanced user who wants to extend functionality, but hidden from the novice.

---

**Question**

The Pavlus article mentions the researchers' comments that people preferred
"natural-language replacements for some of the more abstruse syntax". In other 
words, people found it easier to work with code that looks more like a human language (e.g.,
English). Consider the following quote by William R. Cook, one of the creators
of JavaScript:


> The experiment in designing a language that resembled natural languages (English
> and Japanese) was not successful. It was assumed that scripts should be
> presented in “natural language” so that average people could read and write
> them. … In the end the syntactic variations and flexibility did more to confuse
> programmers than to help them out. It is not clear whether it is easier for
> novice users to work with a scripting language that resembles natural language,
> with all its special cases and idiosyncrasies. The main problem is that
> AppleScript only appears to be a natural language: in fact, it is an artificial
> language, like any other programming language. … even small changes to the
> script may introduce subtle syntactic errors that baffle users. It is easy to
> read AppleScript, but quite hard to write it.
[[Cook 2007, page 1-20]](https://dl.acm.org/citation.cfm?doid=1238844.1238845)

Are these two experiences of natural languages at odds with one another? Would
you choose to include natural language in the design of a DSL? If so, how might
you do so? If not, why not?

**Response**

The quote that we already cited above is very relevant:

> If your standard is natural language, division/fraction notation isn't particularly intuitive.
> But to someone who knows the notation, ab / b is very intuitive, and it's immediately obvious that
> you can cancel the bs. So the goal of an intuitive programming syntax shouldn't be to emulate
> natural language, necessarily, but to provide intuitive hooks and syntax for the types of things
> that programmers do a lot. 
> [Comment by "Peter" ([Source](https://www.fastcodesign.com/1665735/why-arent-computer-programming-languages-designed-better#comment-bc08f700-3c06-11e1-921b-9794fc737ae8))] [Pavlus, 2012]

There are (at least) two main considerations for syntax. The first is how well it fits the task at hand, *in a vacuum*. That is, how good it is considering only the language and the task, and not what users are already used to or know. The other is how easy it will be for real users to adopt. Considering this, the analogy with mathematics is apt. After all, mathematicians do *not* use natural language. They use mathematical notation, because
it is simply better for the task. However, when new ideas come along, to begin with, the ideas are explained using natural language and older notation. The optimal descriptions for learning concepts are not the same as the optimal descriptions for using them.

This mirrors the tradeoffs in language design pretty well. Ultimately, notation specially crafted for the task really is better, and not just for efficiency's sake. The price is the learning curve. There is also the risk of a syntax not becoming widely adopted and therefore not being suitable for discussing ideas with other people. The idea of extensible languages is somewhat of a solution to this. New concepts are first described in terms of primitives people already understand, but the universal language is flexible enough to allow new and more specialized notation to be added in beyond that point. This is how mathematics itself handles the problem.

The priority should probably be on how well the language design fits the actual task, on how good it is for people to use rather than to learn. Within that realm, you should optimize for familiarity. This means that, where suitable domain-specific notation and concepts exist, they should be used. This includes natural language, so if there is a natural language way to write something that doesn't really have any drawbacks, it should be preferred. Thus, for example, you should prefer Haskell's "if .. then .. else .." to Java's ".. ? .. : ..".

There are two final interesting ideas that might also be useful. First, as mentioned before, extensible languages naturally have a way to solve this problem to some extent, as useful new notation will simply appear as it becomes useful. Given that, it may be best to not only aim for *extensibility*, but also *reducibility*. If a language appears like it could have been an extension of some simpler language, then it may be easier to learn. Additionally, they will still be useful to people who only know a subset of the language.

Second, one last extremely hypothetical thought. Even in extensible languages, there is still the question of when to use the less convenient but more primitive description, and when to use the specialized notation. Looking up mathematical ideas on Wikipedia is awful because of how much terminology gets used. For someone who already understands the terminology, it's the best way to write it. But, if a more primitive description could be given without making it too much larger, then arguably that's the better explanation. IDEs may, in the future, provide some solution to this problem. As long as the mapping between primitive and specialized notation is one-to-one enough, it might be possible for two people to view and write the exact same code, but in different modes better suited to their understanding.

---

**Question**

Briefly describe how you split up the work for this assignment.

**Response**

Read independently
Made an outline together
Then worked on different sections and came back together

Dan
- Growing
- Quotes
- Well-designed
- Implementation
- comments #1

Matt
- Growing
- Quotes
- API
- Natural language
- comments #2

---
