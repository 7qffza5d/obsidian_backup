### Links: [[Formal Language]]

### Tags: #satisfactory 

# Context-Free Grammar

Context-free grammar is a [[Formal Grammar|grammar]] that describes a [[Context-Free Language|context-free language]]. As context-free languages describe describes languages wider than [[Regular Language|regular languages]], it has looser rules. A context-free grammar is a grammar in which every rule must:
- Have a left hand side that is a single nonterminal.
- Have a right hand side.
The second requirement is the part that is looser than regular grammars, whose right-hand side must be $\varepsilon$ or a single terminal or a single terminal followed by a single nonterminal. To see a CFG in action, let's look at an infamous example of a context-free language.
$$\text{A}^\text{n}\text{B}^\text{n} = \{\text{a}^n\text{b}^n | n \ge 0\}$$
This language can be described with a CFG as:
$$G = \{\{\text{a}, \text{b}, S\}, \{\text{a},\text{b}\}, R, S\}$$
where the rules are:
$$R = \{S \to \varepsilon, S \to \text{a}S\text{b}\}$$
A proof that a grammar correctly corresponds to a language can be done with a [[Loop Invariant|loop invariant]], which would be given here if I ever bother.
### Related Concepts
