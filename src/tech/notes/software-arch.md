# Software Architecture

A random recopilation of Software Architecture principles and ideas I've found
online.


## Conways's Law
[read more..](https://en.wikipedia.org/wiki/Conway%27s_law)

```
Any organization that designs a system (defined broadly) will produce
a design whose structure is a copy of the organization's 
communication structure.
— Melvin E. Conway
```

The law is based on the reasoning that in order for a software module to function, multiple authors must communicate frequently with each other. Therefore, the software interface structure of a system will reflect the social boundaries of the organizations that produced it, across which communication is more difficult. Conway's law was intended as a valid sociological observation, although sometimes it's used in a humorous context.
other. Therefore, the software interface structure of a system will 
reflect the social boundaries of the organizations that produced it, 
across which communication is more difficult. Conway's law was intended 
as a valid sociological observation, although sometimes it's used in a 
humorous context.


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

