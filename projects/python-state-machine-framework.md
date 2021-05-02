---
layout: project
title: python-state-machine-framework
category: project
tags: python state-machines qp qm qpcpp
---

### Summary

One of the later courses of the Computer Science curriculum at USF is `Automata Theory and Formal Languages`. I really enjoyed this class, one of the reasons being that I already had a year of experience using hierarchical state machines at my internship. I mention [Quantum Leaps QP](https://www.state-machine.com/products/qp/){:target="_blank" rel="noopener noreferrer"} in a couple of other places on my site and if you can't tell, I am a big fan. I got to use it for about 4 years when I worked at [Nypro(now Jabil Healthcare Engineering & Technology)](https://www.jabil.com/industries/healthcare.html){:target="_blank" rel="noopener noreferrer"}. We had a project assigned to use where we were to work in groups to make a presentation about formal languages, automata theory, or both. At my suggestion, my partner and I decided to develop a minimal state machine framework in Python.

Being pretty minimal, there are three classes:

- ActiveObject
- Event
- EventScheduler

A program consists of one `EventScheduler`, multiple persistent `ActiveObjects`, and an arbitrary number of transient `Events`. `ActiveObjects` can communicate in two way, by directly posting an `Event` to another `ActiveObject's` event queue or by publishing an `Event` to the `EventScheduler`. Published `Events` are only received by `ActiveObjects` who have previously subscribed to a specific event name.

`ActiveObjects` do not immediately react to `Event` that are posted to them. The `EventScheduler` has a combination priority/round-robin scheduling algorithm that it uses to invoke `ActiveObjects` to act on `Events` in their queues.

### Designer

While we did not make a GUI application like QM that let you design your state machines completely in a GUI. But, we did make an XML schema that let you express the state machine without writing code. The only code necessary was to write methods in Python that would be invoked by name through the procedural state machine handler.

```xml
<states>
  <off>
      <entry>
          off
      </entry>
      <transitions>
          <ON_SIG>
              idle
          </ON_SIG>
      </transitions>
      <exit>
          on
      </exit>
  </off>
  <idle>
      <entry>
      </entry>
      <transitions>
          <INSERT_SIG>
              playing
          </INSERT_SIG>
          <PLAY_SIG>
              playing
          </PLAY_SIG>
          <OFF_SIG>
              off
          </OFF_SIG>
      </transitions>
      <exit>
      </exit>
  </idle>
  ...
</states>
```

_`player.ao` - `idle`, `playing`, and `off` refer to states that will be transitioned to if that message is received in that state. `off` and `on` refer to methods that will be defined on the Player class in Python. Notice the repetition in the use of `off`, that is because they are contextually different things that the framework is aware of._
