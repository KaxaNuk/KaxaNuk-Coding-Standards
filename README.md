KaxaNuk Official Coding Standards
=================================

***Official coding standards that all KaxaNuk projects must adhere to***

The purpose of these documents is to align our internal coding and system architecture practices in order to make our code as **maintainable** as possible. We define maintainable code as code that presents the following qualities:

1. Readability
2. Modifiability
3. Verifiability

We define each of these below.

## 1. Readability

Code must be reasonably easy to read and understand by someone who:

* knows all the basics of the programming language being used, but is not a high-level expert, and
* doesn't understand all the intricacies of our code-base and platforms.

As such, we:

* Avoid "clever" constructs and one-liners that save us multiple lines in exchange for making the code harder to understand.
* Avoid the use of global variables inside any modules and functions we declare.
* Encapsulate any self-contained logical code block into its own separate function, even if it will be called only once in the codebase.
* Document with a top-level comment every single function we declare, specifying _what it does_, _what restrictions and purpose each parameter has_, and _what are the possible formats of the output_.


## 2. Modifiability

It must be as easy as possible to make basic edits to the code, as well as to find and understand the basic edits made by anyone in a given commit.

As such, we:

* Avoid [magic numbers/magic constants](https://en.wikipedia.org/wiki/Magic_number_(programming)), instead (preferably) declaring them in configuration files, or (less preferably) declaring them in a configuration structure at the top of the module.


## 3. Verifiability

It must be easy to ensure that the code does what we intend it to do, and that any bugs that were previously fixed are not re-introduced in subsequent edits.

As such, we:

* Type-hint every function we declare.
* Write automated unit tests for every module function we declare. 


## How these are enforced

This document is the *why*, and it changes rarely. Its enforceable form lives in
[`KaxaNuk/KaxaNuk-Agent-Skills`](https://github.com/KaxaNuk/KaxaNuk-Agent-Skills), in the `common`
package: `python-pep8` and `python-bloom-code` state the rules an AI assistant applies while it
writes Python, and the `bloom-code-lint` skill ships a checker that reports every mechanical
violation with a remediation hint. That package is versioned; when a rule here changes, the change
lands there too.

Install them into a repository with:

```bash
apm install KaxaNuk/KaxaNuk-Agent-Skills/common --target claude
```

With the KaxaNuk Researcher, nothing is installed per repository: `apm install -g
KaxaNuk/KaxaNuk-Researcher` brings `common`, with every other KaxaNuk package, once for your user, so
every folder you open — every strategy included — has the rules.
