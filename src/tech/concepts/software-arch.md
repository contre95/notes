# Software Architecture

A random recopilation of Software Architecture principles and ideas I've found
online.


## Hyrum's Law

[read more..](https://www.hyrumslaw.com/#)

Hyrum's law states the following:

```
With a sufficient number of users of an API,
it does not matter what you promise in the contract:
all observable behaviors of your system
will be depended on by somebody.
```

It talks about how "implicit interfaces", not in the sense implicit implemented
interfaces, like in Go, but rather dependency contracts that are implicitly
estrablished on large scale systems.

