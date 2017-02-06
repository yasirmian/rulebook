# RuleBook
**A Simple Rules Abstraction for Java8+**

-----------------

### Why Another Rules Abstraction?
Rules engines like Drools are more than many projects need. The format of the rules is also very specialized. And how rules are evaulated is not entirely straightforward. Other rules engines add a bunch of annotations or specialized requirements that can be foreign to many Java developers. That's why RuleBook is a dead simple, 100% Java rules abstraction without the mountain of special annotations required by other [simple?] rules abstractions. It also executes rules in the order in which they are specified (ALWAYS!). 

RuleBook rules are built in the way that Java developers think: Java code. And they are executed in the way that programmers expect: In order. Tired of classes filled with if/then/else? Need a nice abstraction that allows rules to be easily specified in way that decouples rules from eachother? Want to write rules the same way that you write the rest of your code [in Java]? RuleBook just might be the rules abstraction you've been waiting for.

### How Does RuleBook Work?
RuleBook is based on the Chain of Responsibility pattern. Each rule specified in a RuleBook is chained together in the order in which it is specified. As one rule completes, the next rule is evaluated. Any rule can break the chain by returning RuleState.BREAK from the 'then' Function in the rule.

State in Rules is handled through Facts. A Fact is literally just data that is named and supplied to a Rule or RuleBook _(note: facts added to a RuleBook are applied to all rules in the RuleBook)_. Facts can be both read and written to. So, in that way, facts can be used to evaluate state at the completion of a RuleBook execution and they can also be used to pass data into a Rule or RuleBook.
