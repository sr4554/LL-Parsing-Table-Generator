# LL-Parsing-Table-Generator

The LL Parsing Table Generator is a software project that automates the creation of LL parsing tables for a given context-free grammar.It takes a grammar as input, including its production rules, terminals, and non-terminals, and applies a set of algorithms to construct the parsing table.
The generated LL parsing table facilitates the parsing process by guiding a parser to make decisions on which production rule to apply at each step, based on the current input symbol and the top of the parser's stack.For example,

Take a grammar,like this 
    E -> T E'
    E' -> + T E' | €
    T -> F T'
    T' -> * F T' | €
    F -> ( E ) | id
    
    [€ is empty terminal]
    
Use space ' ' as seperator in production Seperate productions with pipe '|' or with different arrow-productions Any string on the left side of -> is a nonterminal Any non-nonterminal on the rightside of -> is a terminal
 The parsing table will be:
 
 PARSING TABLE
 --------------
 ╒═════════════╤══════════╤═══════════╤═══════════╤══════════╤════════╤════════╤═════════╤════════════╕
│ NON -       │ id       │ +         │ *         │ (        │ )      │ $      │ FIRST   │ FOLLOW     │
│ TERMINALS   │          │           │           │          │        │        │         │            │
╞═════════════╪══════════╪═══════════╪═══════════╪══════════╪════════╪════════╪═════════╪════════════╡
│ E           │ E  → TE' │           │           │ E  → TE' │        │        │ (  id   │ $  )       │
├─────────────┼──────────┼───────────┼───────────┼──────────┼────────┼────────┼─────────┼────────────┤
│ E'          │          │ E' → +TE' │           │          │ E' → ε │ E' → ε │ ε  +    │ $  )       │
├─────────────┼──────────┼───────────┼───────────┼──────────┼────────┼────────┼─────────┼────────────┤
│ T           │ T  → FT' │           │           │ T  → FT' │        │        │ (  id   │ $  )  +    │
├─────────────┼──────────┼───────────┼───────────┼──────────┼────────┼────────┼─────────┼────────────┤
│ T'          │          │ T' → ε    │ T' → *FT' │          │ T' → ε │ T' → ε │ ε  *    │ $  )  +    │
├─────────────┼──────────┼───────────┼───────────┼──────────┼────────┼────────┼─────────┼────────────┤
│ F           │ F  → id  │           │           │ F  → (E) │        │        │ (  id   │ +  $  )  * │
╘═════════════╧══════════╧═══════════╧═══════════╧══════════╧════════╧════════╧═════════╧════════════╛

Successfully created a parsing table.
