# Modules

## Identity and dependencies

§ A [module depency] can be [satisfied] by another, [compatible module].

For a module dependency to be substitutable, the dependency cannot be on a
specific version of a specific module. Instead a dependency must only be
expressed indirectly on the expectations a compatible module must fullfill.

It might be instructive to study the history leading up to an artefact such as
http://www.slf4j.org/ a project serving only as an indirection to support
various logging libraries to coexist. Also see, dependency injection, as
implemented in IoC

It might not be necessary for a module identity to imply a stream of versions
directly but for reason of hotswapping it might be interesting to expose
module loading as a stream of instances.


## Types, laws, tests and contracts

Hindley–Milner can deduce the most general type of an expression.

In a similar vein the exact semantic requirements of a module should be
deduced. Not only from it's structural type, but also by any algebreaic
properties declared about it, and tests provided to test those properties.

This is a key "innovation" of this system, tests and laws are intrinsically
linked to the formalization of modules, just as much as types are.

A contract could either be explicitly declared, or implicitly derived from an
existing module.


## Information shielding

Information hiding is the principle in which a module author picks a most
specific type to expose the module as, thus protecting the module from too
strict expactations from dependees, preserving some freedom in how the module
might change in future versions without breaking other modules.

The principle of information shielding is instead that responsibility if
module authors are to shield their own module from changes in their
dependencies, by finding the most general type satisfying the needs of the
module, and be free to expose their own most specific type for when it could
be useful.

The most specific type of a module could for example be useful for dispatching
on providing a suitable strategy for an algorithm the module is involved in.
In environments of information shielding it is tempting to use reflection for
determining the exact module implementation at run time. However, in many
cases, the exact dispatching involved could, and should, be determined
statically at design time.


## Module versioning

Modules as such are versioned

Modules are versioned automatically, at all stages, in such a way that all
dependencies, and all transformation stages can be tracked. The source module
is versioned in such a way that services or expecations cannot change witout
changing its version.

While the version identifier as such might be expressed as a hash, to
implement versioning as a merkele tree of versions. It should be possible
automatically, and deterministicly, derive a semantic version
(http://semver.org/).

The exact verion of a module is intrinsic to the programming system, and not a
feature of an external tool such as git, in such a manner that an exect
verion, and lineage, of a module can be provided to the running process.
Without gymnasitcs of build tool scripting.


