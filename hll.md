HLL
===

Here is a list of features for the TUNES High Level Language (HLL).

Some features appear in several categories, because they fulfill several aspects of the design.

Note that, to recall the notions from Richard Gabriel's
[The Structure of a Programming Language Revolution](https://www.dreamsongs.com/Files/Incommensurability.pdf),
TUNES is firmly in the Programming System paradigm, rather than the Programming Language paradigm:
the system is live, keeps running, and you interact with it and modify its code while it's running;
it is not a dead thing that is restarted every time you modify the code, each time losing all data.
Thus, the HLL is meant as a standardized, initial and universal interface to the live system,
that exposes the features of the system;
it is not meant as just yet another language with which to generate dead programs.


Purity and Effects
------------------

  * EASY: There is a higher-order pure functional core based on the lambda calculus.
    You can also express all kinds of side-effects, including assignment and
    first-class continuations, from which you can implement non-determinism, etc.

  * MEDIUM: You can switch the view on existing code from pure to impure, so you can
    reify effectful code as pure code in monadic style in a suitable explicit effects monad;
    and you can apply monadic code to a monad and achieve the effect.

  * HARD: You can edit existing source code in either style and have the system
    transform the source while preserving types, preserving comments, etc.


Homoiconicity
-------------

  * EASY: Start with Lisp syntax.
    Implement syntax-case hygienic macros.

  * MEDIUM: PLT-style language extensibility.
    Staged evaluation.

  * HARD: Notion of first-class computing system.
    Reify not just source but running state.


Negative Expressiveness
-----------------------

The HLL shall possess the ability to express *restrictions* on future behavior.

  * EASY: Express intent as to validity domain, to allow for reasoning / transformation;
    typing that constrains inputs and environment, outputs and effects.
    Algebraic data (and function) types, with effects.

  * MEDIUM: Safely manipulate resources: Linear logic; not just for efficiency, also for security.
    Dependent types; modular proof strategies.

  * HARD: FULL abstraction: "Blind quantifiers", that prevent introspection at the base level;
    abstractions that do not leak; virtual machines without a backdoor.


Concurrency
-----------

  * EASY: Threads, shared or per-thread memory, atomic ops, message passing, transactions, etc.

  * MEDIUM: Data structures are immutable by default.
    Rely on ownership for efficient distributed data exchange (Linear Logic).
    Proper system equality based on mutable intension / immutable extension
    (see [hbaker paper](http://www.pipeline.com/~hbaker1/ObjectIdentity.html)).

  * HARD: Management: interrupt + PCLSRing, de-/re-compilation, migration, save&restore, etc.


Access to lower-levels of abstraction
-------------------------------------

  * EASY: Low-level bit-banging. Byte arrays, bitblt.
    Strings are not byte arrays but abstract character sequences; cheap random access not required;
    underneath strings can be compressed, can be UTF-8 or any encoding, etc.

  * MEDIUM: Standardize FFI to C, Java, or whatever the underlying system languages are,
    independently from implementation.

  * HARD: Have a continuum of virtual machines from high-level to low-level (UNCOL, LLVM and below)
    allowing both portable abstraction AND hardware specialization (guarded by features, etc.)


Virtualization
--------------

  * EASY: Run code in a VM and intercept its "system calls" to implement them or filter them.

  * MEDIUM: Define arbitrary first-class languages on top of the existing Lisp,
    that you can virtualize and automatically have source-level debugging, etc.

  * HARD: make persistence, garbage collection, distributed transactions, etc., below Lisp,
    implementable via reflection without leaving the language yet providing full abstraction.


Modularity
----------

Modularity is about division of labor as much as about splitting code in brain-sized chunks.

  * EASY: Interactive environment yet application delivery. Incremental programming.

  * MEDIUM: PLT style modules. Modularity across meta-levels.

  * HARD: Implicit communication that scales. The expression problem across modules and extensions.
    More cooperation with less coordination.


Persistence
-----------

  * EASY: An orthogonally persistent object database. Transactional code and schema updates.
    System-wide versioning and easy forking (in a virtualized instance).
    Code updates are transactional and may upgrade stack frames where necessary.
    No filesystem: search the object graph for structure, get set of access paths.

  * MEDIUM: Everything orthogonally persistent at every level by default, depending on user focus.
    (Only save Model and maybe Controller of MVC, not View; use Convergent Concurrency)
    Infinite undo. Omnipresent omniscient debugging. Declarative domain specification.
    Planet-wide backups by default. Incremental migration. Automated schema upgrade.
    Autoextracting state for regression tests.

  * HARD: Representation infrastructure upgrade, extensible representations,
    debugging representation bugs from a cross-compiler
    that does not share the same representation.
    Proving representation correct so it doesn't have to be debugged.


Interface
---------

  * EASY: Reactive functional programming, MVC. Generate interface from data type. Composing Lenses.

  * MEDIUM: Bidirectional programming. Interface managers as first-class meta-level objects.
    Reasoning about interfaces: automatically check that
    the user is never stuck and can always reach the entire system, that
    there is enough area and contrast to see each clickable feature, etc.

  * HARD: Infer programs from interfaces,
    choose data structure representation from usage context,
    learn programs by example, etc.
    Preserving privacy as you learn to adapt to the user.
    Total recall, in a searchable way, at a low-level when needs be; forever instant replay.


Reflection
----------

  * EASY: Source code is available for programmers, but also for metaprograms.
    Metaprogramming with macros, not ugly code generators or annotation processors.
    PLT-style hygiene and modularity.

  * MEDIUM: Debugging from the meta-system. Separate meta-levels, yet navigate easily between them.
    Keep embedded system small, debug info in large IDE (identify state by fast crypto digest).

  * HARD: The end-user is in full control (but the device will reset between users).
    (ε (x) (P x)) Skolemization witness, controlled via dynamic binding of strategies
    and scope control. Types across multiple reflection levels.
