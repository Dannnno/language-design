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

> If your standard is natural language, division/fraction notation isn't particularly intuitive.
> But to someone who knows the notation, ab / b is very intuitive, and it's immediately obvious that
> you can cancel the bs. So the goal of an intuitive programming syntax shouldn't be to emulate
> natural language, necessarily, but to provide intuitive hooks and syntax for the types of things
> that programmers do a lot. 
> [Comment by "Peter" ([Source](https://www.fastcodesign.com/1665735/why-arent-computer-programming-languages-designed-better#comment-bc08f700-3c06-11e1-921b-9794fc737ae8))] [Pavlus, 2012]

I feel that this comment on the Pavlus article really gets to the heart of the matter - that knowing the notation is part of any (technical) job, and once you can grok it, it becomes second nature.  So while natural language may make it easier to read and write code at first, when it comes down to it the most important thing is making sure that someone who uses it often (i.e. professionals and very passionate amateurs) can do what they need to do clearly and easily.

> **Example code should be exemplary.**  
> If an API is used widely, its examples will be the archetypes 
> for thousands of programs. Any mistakes will come back to haunt 
> you a thousand fold. [Bloch, 2006]

This is perhaps my favorite quote of the entire reading.  Having spent this past summer working with a horrible API (most modules were not documented, and only 23% of the examples worked (we checked)) I appreciate and understand this the most.  Your API is how to get developers to use your project.  If you make a large barrier to entry in the form of missing or bad documentation and examples, they will look elsewhere for their solutions. 


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

It wouldn't have made sense for the designer of the sound lab to make it able to work with whole scores - but it should have been designed so that someone else could make it do that if they wanted to.  In the same way that it doesn't make sense for the language designer to define 20 numeric types, the designer should have 1000 sound transforms - but it should have been doable for those users who do need that functionality.

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
 

In what way is an API a language? 

**Response**

- You have an input interpreted as a series of instructions, generating an output
- An API has the same problems as a language. It can be easy to grow, or not. It can be surprising,
it can require documentation.
- It's supposed to be a way for a human to get a computer to do a very specific task.
- You don't have as many choices of syntax or power
- It's usually difficult to modify

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


- Article: Programming should have a lower barrier to entry, and should attempt to be more human
- I agree that the problem stated is a problem.
- But the article is implicitly saying that humanizing is definitely the solution to that problem
- We need to be open minded, and not reject the problem because we don't like that solution
- Maybe weird things (graphical languages, ???) are the solutions.
Shouldn't stop thinking about this problem.

- Evidence-based design: An interesting idea!
- Beware of "New Coke": Be careful of what you're testing.
If you test based on new users, you're implicitly designing a lanugage that is suitable
for new users, but not necessarily anything else. That is not the only measure of a good language.


---

**Question**

How do implementation choices (e.g., as an interpreter/compiler or as an
internal DSL) affect the user experience? Can or should we always hide our
implementation choices from users?

**Response**

The best (and possibly only) reason to let the user know what the implementation details are is if it affects (especially restricts) the things the user is able to do, and the things the user **must** do in order to make their program run.  For example, in the choice between an interpreter and a compiler, there is a difference in what you're able to do at runtime, as well as the existence of a (potentially executable) generated file.  Additionally, performing things such as static analysis is generally easier when everything happens at compile time versus runtime.  

In general, we should hide as much as possible - details about the internal parser or AST are almost certainly irrelevant to the end user, and would only confuse the user.  "**Keep APIs free of implementations details.**	 They confuse users and inhibit the flexibility to evolve." [Bloch, 2006].  In general, any implementation choice that affects how it is run, written, or edited, should be revealed to the user to the extent they need it for their workflow.

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

- We're often told that we will read code more than we write it, so is this just
saying AppleScript goes too far down that road?

- No matter how natural you try to get it, it's still going to have to be unambiguous.

- There are lots of ways to express the idea of repetition, but it's probably best for
maintainability's sake that there's only one real way to do it.

- For a DSL, since you're trying to aim it at someone who's a domain expert,
you want it to be more readable. Just don't go too far.
- You probably want to reflect what the experts do. So, if they use math and not
natural language, math is actually going to be the more understandable choice.

last paper: "DSL syntax can be close to the notations used by domain experts".

Arguably, write-ability can be suplemented by IDEs, although that basically doesn't exist much yet.
As long as it doesn't impair workflow, readabliity should be prioritized over write-ability,
up until the point that write-ability becomes difficult.

Never rely on the fact that your language is the only way to accomplish something

Readability isn't just reading by novices, but also includes higher-level abstractions
like design patterns, idioms, etc. Readability requires that the right way be the only or one of
obvious ways to do it.

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
