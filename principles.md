Principles
==========

Behind a good design are guiding principles.
These principles are not features, though they inform the choice of features.


Founding Principles
-------------------

### Genericity

All the next features must be included in their fullest genericity.
No arbitrary restriction should be added to the syntax or semantics of the language.
In particular, the ability to use a feature must be actually independent
of the ability to use another one whenever they are theoretically orthogonal.

We need genericity to obtain maximal software reuse and compression.

Genericity is the expression of computing freedom; it naturally gives birth dually
to Uniformity and Orthogonality, to Abstraction and Reflection,
to Hardware Independence and Hardware Access.


### Precision

The HLL should enable programmers to specify precisely what they want, without having to either underspecify or overspecify it.

Note: This is not about floating point arithmetic precision, though a corollary in a very particular case.

Uniformity

There is a unified way to manipulate computer abstractions. All computer abstractions are made equal in the same whole system, whether give them the name object, function, term, pattern, or whatever.

Code chunks, functions, classes, symbols, attributes, are equally objects, which makes higher-order and reflective expression much more straightforward.

Ultimately, uniformity's advantage is to allow for the simplest possible semantics for the system's parts.

Consistency and Orthogonality

Consistency

On modifying an aspect of an object, all the other aspects must be updated accordingly, least either the object or the modification must be invalidated.

Orthogonality

Independent aspects of an object can be dealt with independently.

A Duality

These are dual requirements that basically mean that one can express precisely what one wants: one can express it all of what one wants at the same time (consistency), but is not forced to express more than it at that time (orthogonality).

Basic Principles

Dynamism

A computing system is to evolve, to learn and to adapt, to interact with the human world, not to sit there and stay the same. Hence a deepest feature of its interaction language must be dynamism; that is, new objects of any kind (we saw already that somehow there was a generic kind) may appear or become obsolete at any time.

Higher-Order

You may abstract any subterm in any term of any order, to obtain a function of a higher order. Variables, integers, types, or functions parameters, function return values can independently be of any kind and any type, including variables, integers, types, functions.

We need higher-order expressiveness to achieve maximal power, because if we don't, other systems will have to be built on top of ours nonetheless, and our system will be yet another sucker system.

Purity

Pure code (with no side effect), and read-only data, should be recommended and favored. Also, The language semantics must not depend in any way on the peculiarities of today's computers (e.g., size of binary words or characters), which does not mean it cannot interface to it, which it should do very easily.

Purity is to be encouraged, because it leads to much cleaner semantics and much more efficient implementations when it comes to distribution, object sharing, and parallel optimization.

Lazy evaluation

Evaluation can be done only as needed; it should be possible to leave this as an assumed evaluation context.

Lazy evaluation is needed, because only it allows so much things that strict evaluation forbids, and simplifies many a program's structure; for the usual argument: if you don't implement it, people will reimplement it on top of the system, and you'll lose any advantage from having an integrated system.

Extensibility

Modularity

Objects come in replaceable, upgradable modules. Modules are identified uniquely across the computing world, and come with their specification.

Modules and new semantics may be created and added dynamically to the system. Objects may be automatically relinked to upgrades or extensions, or translated into a new universe of values.

Actually, extensibility is just the (important) combination of modularity, dynamism, and being-higher-order: modules of any abstraction order may be upgraded dynamically.

Modularity is necessary for safe object sharing and fine grain software competition.

Quotienting

It is often found in theoretical textbooks in maths or CS that "it does not matter which (terms) are primitive and which are derived", which is a particular case of the principle according to which objects are to be considered "up to isomorphism". However, there currently exist no programming system that implements this principle.

The Tunes HLL must enable programmers to specify what they want without specifying more, so they can express exactly what they need, and let it be optimized later, according to the needs that will arise of a representation suited to something else than the original coding.

Among the basic constructs of the language, there must be some way to quotient a structure by any given equivalence relation on that structure, and keep whatever operations on this structure with which the equivalence relation is compatible.

Reflection

The language can talk about itself, manipulate code at any level: source code, intermediate representations or processor executable format, so that extensibility is at all computing levels.

It means the language provides (direct or indirect) uniform access to the internal representation of objects, of which source code should merely be an external representation.

It allows easy meta-programming in the language: the compiler is its own preprocessor; the language is its own macro-command language.

Reflection is a generalization of higher-order expressiveness: not only the universe is layered by abstractions, but it has standard embeddings into itself.

Security

Objects come with their full specification, so that system security is never endangered.

Specification can be multi-level (i.e., conditions for the object not to crash the system, conditions for it to work properly), may come with proofs assuming different assumptions (according to the level of trust you give to each module's providers), and may involve any kind of strong typing, from first-order typing to full computational logic. Code with side-effects will have pre/post conditions, or will be considered as iteration of pure code. Temporal logic may even be involved for time-aware proofs.

Security is a must, because it's better to have no computer than a computer you cannot trust, especially when computer information is used in any critical work that may involve human lives or lots of money. (Extrapolate on the rationale for totally generic security with examples, using whole-system metaphors.)

Extensibility without Security is not worth a penny (see C, Elisp, et al.). (Explain these examples and some generic reason that extends beyond all of them to rationalize this.)

Parallelizability

Modules are executed in parallel, and scheduled by the system (with directives from the programmer). Parallelized partial-lazy evaluation leads to future values as in Ellie.

Being able to easily parallelize a program is needed because parallel computers have important performance advantages over sequential ones, and a distributed system is inherently parallel.

Interactivity

By means of reflexivity and dynamism, the language allows direct, interactive development of programs, without an inefficient edit-compile-debug cycle. It also allows any kind of direct interaction between the system and its human user, so that it replaces a shell (and its associated scripting languages). This is a feature of the language, because it means its semantics allow efficient semi-compilation and interpretation. This is also a feature of the standard library and environment. The rest follows from dynamism, self-extensibility, and reflexivity.

Interactivity is needed, because otherwise other languages will have to be written and learned, limiting the commonality of this language.

Low-level awareness

Scalability

When you don't need features like higher-order programming, you can tell the system (if it doesn't find it by itself), so that it may scale down its power, and take advantage of the peculiarities of the restriction of the system to implement objects more efficiently, with less resources.

E.g., if a program explicitly handles virtual memory (using BLOCK statements as in Forth), it doesn't need a MMU processor; if it explicitly handles memory allocation/deallocation, it needn't run in an implicit garbage collecting environment; if it only uses 16 bit integers, it needn't use 32 bit integers on hardware where 16 bit is cheaper and as (or more) efficient; etc.

We need scalability for efficiency, and adaptability to mobile computers and obsolete hardware.

Hardware consciousness

The actual resources (size of memory, of words in the arithmetic or floating point unit, CPU cycles, etc) of computers will always be finite, whereas the field of computing possibilities is infinite; thus the programmer must be able to control resource use of his program, and to handle overflows that will eventually occur. The HLL must thus be aware of side-effects, because they are intrinsically inevitable.

Hardware consciousness is required because time and space resources are a major concern for humans, who cannot wait and pay indefinitely to waste new resources.

Integration

The language must allow easy access to external objects from other systems, written using any semantics or syntax. All these objects (including languages), whether low-level or high-level, should be embeddable into the HLL.

Integration is needed to allow soft and efficient upgrading of existing systems toward the Tunes project, and communication with the world external to the Tunes system.

Partial evaluation

Evaluation can be done as early as information and resources allow. Function calls, message passing et al. can be dynamically compiled or inlined.

E.g., when an object '1+1+x' is seen, it's automatically evaluated as '2+x'. When a generic function is called with specific but incomplete parameters, it may get specialized and optimized accordingly.

It's a little more precise than "eager evaluation" since it also applies to non-terminal objects (actually, all objects are equal, so the concept of terminal object isn't clear in Tunes as it is in lower-order, non-reflective systems).

The compiler/interpreter might then be as simple as just a trivial (parametrizable) front end and then partial evaluation done on parsed objects.

Partial evaluation is needed because it involves such performance improvements. The programmer must be aware of it to help the system manage it better when he knows while the system doesn't (which will always eventually happen).

Persistence

Object automatically persist together with the system. There is no need to explicitly convert objects to and from unsafe persistent binary or ascii files. This is a language feature, as it greatly affects the language's standard library and programming habits.

Persistence is needed, because not granting it is wasting at least 30% of users' time, ignoring overheads for parsing or complex error recovery. Include the citation for the software development study that produced this statistic.

Garbage Collection

This feature is the complement of persistence: objects are automatically destroyed when no more needed.

Garbage collection is needed because no persistent higher-order expressiveness is possible without it: either space resources will explode, or low-level memory management will have to be done manually by the users.

Note that Scalability above means that GC should be implemented directly in the user program when both possible and simpler overall.

Nice Human Interface

Syntax is purely for human convenience. Lisp hasn't become a dominant force because it forgot that simple statement. Other languages focus on the convenience, but offer no nice semantics; they're worse, but better.

Automatic rewrite

Conceptually, the semantics are everything; the syntax is only sugar for the human user. Thus the language system should automatically rewrite programs according to user-defined criteria.

Particularly, the human user completely controls the level of redundancy the language will provide or require when he reads or writes programs.

Automatic rewrite is needed because different users have different understanding of computing at different moment and in different context, and the computer shall adapt the syntax to the user's concerns, not the converse.

Self-extensible Language

The syntax must be able to evolve according to the context, new syntaxes may be dynamically defined. This must be done in conjunction with the semantic aspect of things, with corresponding extensible grammars.

Particularly, any language can be added in a module as a sublanguage of the HLL.

Self-extensible language is needed to dynamically allow all kind of objects to be equally well-interfaced between humans and computers.

Implicitness

The human should never have to say more than they need. They should be constantly able to control which information to explicitly give to the system, and which to have the system find out by itself, and how the system will try to find out.

The human user completely controls the level of redundancy the language will provide or require when he reads or writes programs. They may ask the system to replace any implicit object by the explicit object it found.

Implicitness is needed because computers are as good as people at tracking redundancies, and any person's work saved is worth much more than computer work spent.

Non-Requirements

Uniqueness

The designer of Eiffel, Bertrand Meyer, says that a language should provide "Uniqueness". "The Principle of Uniqueness," Meyer says, "is easily expressed: the language should provide one good way to express every operation of interest; it should avoid providing two."

If this is meant syntactically, then it can only lead to absurd limitations of the language: a Turing-equivalent language can only have undecidably many equivalent ways to do the same things anyway.

The Perl motto seems righter: "There's more than one way to do it." Indeed, people should be allowed to do things in the way they like best and manage fastest, so they can adapt their programs to their needs, and not the other way around.

Of course, Perl is also wrong in a different manner, in that it can't unify those ways.

By limiting the ways people can talk, you don't add information, only noise through redundancy. Meyer himself said later that software should help people do good, not forbid them from behaving badly, and there he was right.

To add information would be not to forbid people from communicating simpler, more adapted syntax, but to allow them to communicate more complex, adapted meaning. That is, to allow implicit higher-order unification of different views on the "same" objects.

This can be achieved trivially through semantics-based reflection: once an isomorphism between two objects is found, it can be optimized and absorbed by the system, so that the two objects will actually appear the "same" to users, without any performance degradation, even though they were different in their original context (in which they might still be consistently available!).

Compatibility

The language doesn't need to be compatible with any previous standard, though we'll try to stick to existing traditions whenever we don't have any explicit argument against it.

Leveraging and reuse of older code will be achieved through meta-programming and semi-automatic translation of code from older, dirtier languages to our newer, clean HLL.

