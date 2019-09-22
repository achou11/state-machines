# State Machines

## What is it?

> There are many variants in definitions of finite state machines, depending on
  whether one views them as language acceptors/generators (automata), or machines that react with their environment and produce output (eg. Mealy and
  Moore machines, I/O automata), or logical models (Kripke structures) etc.
> [...] In practice, several extensions are useful to enhance the expressive power and
to describe more complex systems more efficiently

*Source: [Hierarchical State Machines](https://link.springer.com/content/pdf/10.1007/3-540-44929-9_24.pdf), Mihalis Yannakakis, Bell Laboratories, 2000*

A basic finite state machine features states, transitions and accept external inputs. Basic FSMs can be extended by adding outputs, memory, hierarchy, concurrency and communication. A machine with outputs will produce an output for each external input it receives. A machine with memory will hold track of a set of internal variables, which it can update on receiving external inputs. A machine with hierarchy contains sub-machines and can delegate the processing of external inputs to those sub-machines. A machine featuring concurrency and communication may contain a set of machines, which concurrently process external inputs and communicate together. Extensions add expressivity to the machine at the cost of higher complexity.

According to the extensions added to the basic state machine formalism, the following terminology is commonly used:
 
| Extension | Terminology | Features |
|:---|:---|:---|
| - | basic finite state machine ([FSM](https://en.wikipedia.org/wiki/Finite-state_machine)) | states, transitions |
| output| basic finite state transducer ([FST](https://en.wikipedia.org/wiki/Finite-state_transducer)) | states, transitions, output functions |
| output depending only on state| [Moore machine](https://en.wikipedia.org/wiki/Moore_machine) | states, transitions, output functions |
| output depending on state and input | [Mealy machine](https://en.wikipedia.org/wiki/Mealy_machine) | states, transitions, output functions |
| memory | extended finite state machine ([EFSM](https://en.wikipedia.org/wiki/Extended_finite-state_machine)) | states, transitions, set of variables, guards, memory update functions |
| memory + output| extended finite state transducer (EFST) | states, transitions, set of variables, guards, memory update functions, output functions  |
| hierarchy | hierarchical finite state machine (HFSM or HSM) | tree of states, transitions |
| hierarchy + memory| extended hierarchical finite state machine (EHFSM or EHSM) | tree of states, transitions, set of variables, guards, memory update functions  |
| hierarchy + memory + outputs| extended hierarchical finite state transducer (EHFST or EHST)| tree of states, transitions, set of variables, guards, memory update functions, output functions |
| concurrency| communicating finite state machines ([CFSM](https://en.wikipedia.org/wiki/Communicating_finite-state_machine)) | set of state machines, communication protocol, concurrency semantics |
| concurrency (broadcast communication) + hierarchy | [statecharts](http://www.inf.ed.ac.uk/teaching/courses/seoc/2005_2006/resources/statecharts.pdf)  | set of hierarchical state machines, history pseudo states, broadcast communication protocol, concurrency semantics tightly integrated to the FSM semantics|
| concurrency + hierarchy | communicating hierarchical finite state machines ([CHFSM or HCFSM](https://en.wikipedia.org/wiki/Communicating_finite-state_machine#Communicating_Hierarchical_State_Machine)) | set of hierarchical state machines, communication protocol, concurrency semantics |


## What is it used for?
> Finite state machines constitute one of the most fundamental modeling mechanisms in Computer Science. They have been widely used to model systems in a wide variety of areas, including sequential circuits, event-driven software, communication protocols and many others.

*Source: [Hierarchical State Machines](https://link.springer.com/content/pdf/10.1007/3-540-44929-9_24.pdf), Mihalis Yannakakis, Bell Laboratories, 2000*

Extensions to the basic state machine formalism can be chosen based on the characteristics and complexity of the system or computation to model:
- regular languages can be described with basic FSMs. Cf. [regexp simulator](http://ivanzuzak.info/noam/webapps/fsm_simulator/)
- [morphological analysis](https://en.wikipedia.org/wiki/Morphology_(linguistics)) can be [performed by state transducers](https://www.cs.ubc.ca/~carenini/TEACHING/CPSC503-10/applications-of-finite-state.pdf)
- CFSMs can be used to model [some classes of distributed systems](https://pdfs.semanticscholar.org/b218/d40091ac73be4cf8861991c2dda10008bb8f.pdf)
- extended hierarchical finite state transducers, or their statecharts extension, can be used to [model user interface behaviour](https://medium.com/dailyjs/user-interfaces-you-can-trust-with-state-machines-49de7fa138a6), or [game agent behaviour](http://www.gameaipro.com/GameAIPro/GameAIPro_Chapter04_Behavior_Selection_Algorithms.pdf)

## Reading

- General
  - [From the Choo docs](https://choo.io/docs/state-machines/)
  - [The Rise Of The State Machines](https://www.smashingmagazine.com/2018/01/rise-state-machines/)
  - [State Machines: What Are They?](https://kyleshevlin.com/what-are-state-machines)
  - [How I Learned to Stop Worrying and ❤️ the State Machine](http://raganwald.com/2018/02/23/forde.html)

- User interface modeling
  - Horrocks, Ian. Constructing the User Interface with Statecharts. Boston, MA: Addison-Wesley, 1999
  - [User Interfaces You Can Trust with State Machines](https://medium.com/dailyjs/user-interfaces-you-can-trust-with-state-machines-49de7fa138a6)
  - [State Machines in React](https://gedd.ski/post/state-machines-in-react/)
  - [State Machines: Our First XState Machine](https://kyleshevlin.com/our-first-xstate-machine)

- Model-based testing
  - [Model-Based Testing in React with State Machines](https://css-tricks.com/model-based-testing-in-react-with-state-machines/)

- Gaming
  - [Behavior Selection Algorithms - Game AI Pro](http://www.gameaipro.com/GameAIPro/GameAIPro_Chapter04_Behavior_Selection_Algorithms.pdf)

- Distributed systems
  - [Persistent connections with gen_statem in Elixir](https://andrealeopardi.com/posts/connection-managers-with-gen_statem)

## Projects

- JavaScript
  - [XState](https://github.com/davidkpiano/xstate)
  - [Kingly](https://brucou.github.io/documentation)
  - [Stent](https://github.com/krasimir/stent)
  - [jssm](https://github.com/StoneCypher/jssm)
  - [Rosmaro](https://rosmaro.js.org/)
  - [Javascript State Machine](https://github.com/jakesgordon/javascript-state-machine)

- Python
  - [Sismic](https://sismic.readthedocs.io)

- Erlang/Elixir
  - [Erlang/OTP gen_statem](http://erlang.org/doc/man/gen_statem.html)

- Other
  - [[Boost].SML](https://boost-experimental.github.io/sml)
  - Pretty sure there's a finite state machine implementation in every known programming language...

## Examples

- User interface modeling
  - [Getting from Redux to a state machine](https://krasimirtsonev.com/blog/article/getting-from-redux-to-state-machine-with-stent)
  - [Password meter](https://brucou.github.io/documentation/v1/tutorials/password-meter-ui-implementation.html#Vanilla-js)
  - [Keypad](https://brucou.github.io/documentation/v1/examples/keypad.html)
  - [two-player chess game](https://brucou.github.io/documentation/v1/tutorials/chess-game-ultimate.html)
  - [Svelte Suspense](https://brucou.github.io/documentation/v1/examples/svelte%20suspense.html)
  - [Wizard form](https://brucou.github.io/documentation/v1/examples/wizard-form.html)
  - [contextual user flows](https://github.com/hashicorp/vault)
  - [screen saver](https://medium.com/@carloslfu/modeling-a-screensaver-with-a-statechart-a-real-use-case-f57301682570) 
  - [miscellaneous (no code samples)](https://xstate.js.org/docs/about/showcase.html)
