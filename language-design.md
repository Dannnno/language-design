_Fill in each this file with your responses, placing each response after its
corresponding question._

---

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
>
> ...
>
> My point is that a good programmer in these times does not just write programs.
> A good programmer builds a working vocabulary. In other words, a good programmer
> does language design, though not from scratch, but by building on the frame of a base
> language. [Steele, 1998]

> If your standard is natural language, division/fraction notation isn't particularly intuitive.
> But to someone who knows the notation, ab / b is very intuitive, and it's immediately obvious that
> you can cancel the bs. So the goal of an intuitive programming syntax shouldn't be to emulate
> natural language, necessarily, but to provide intuitive hooks and syntax for the types of things
> that programmers do a lot. 
> (https://www.fastcodesign.com/1665735/why-arent-computer-programming-languages-designed-better#comment-bc08f700-3c06-11e1-921b-9794fc737ae8)[Comment by "Peter."] [Pavlus, 2012]

> Example code should be exemplary.
> If an API is used widely, its 
> examples will be the archetypes 
> for thousands of programs. Any 
> mistakes will come back to haunt you a thousand fold. [Bloch, 2006]

---

**Question**

How do the themes of _Growing a Language_ relate to the lab we did this week?

**Response**

Growth and stuff
    - Original design, methods could not possibly be used in some new way
    - New design, it has to be easy to add new modifications, and create them from others
    - The new design should be able to be extended towards stuff like playing from a score,
    even though we didn't actually implement that.
Quote, perhaps "Parts ..."

---

**Question**

How would you know a well-designed language? What are the symptoms? How would
you know a poorly designed language? What are the symptoms?

**Response**

*Look at Bloch*

- Room to grow, growable by users
- How often you have to consult documentation
- For a DSL, if it can be used by people with expertise in just the domain (and not for example programming)
- Productivity?
- Amount of boilerplate?
"Don't make the client do anything the library could do." 

- Principle of least surprise!
- Difficult to misuse, rather than just easy to use. Ask, "What should it be impossible to do?" ~ Prof Ben

Possible outside quote: You want things to be simple, but that's not the same as them being easy.

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

- Programmers: It's OK (perhaps good) for there to be some kind of overhead.
- As far as "perhaps good": A low barrier to entry is just begging for having novices
write code, which means that the abstract ideas will also be worse. Leads to lots of bad code
and a worse final product.
- Better suited to what programmers actually do, once they learn it
- More productive (?) and easier to use, once you get used to it
- Rarely actually the hard part of programming
- (Although it can force a certain way of thinking, a la Sapir-Warf)
- "Our languages may be esoteric ... show me any other technical profession ..."

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

Does the implementation restrict, in things the user can or has to do?

Multi-step processes?

Final product: i.e., speed, static analysis

Hide as much as possible. For example, parsing, or internal AST.
But they will still have to know about implementation choices that change how it is
written, edited, and run. (Such as compiled vs. interpreted, or internal vs external)



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
