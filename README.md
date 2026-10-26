Experimentation-of-dynamic-decision-graph
Question of focus: Can a neural network learn an input-dependent computational graph by dynamically composing small reusable modules, while simultaneously learning when to stop computing? What if a neural network wasn't a fixed graph, but a collection of small functions from which it constructs a different computational graph for each input?

Steps:

Implement with repeated dynamic routing and softmax first to check feasibility of idea
Implement two more networks to be trained side-by-side, one with mostly Euclidean mappings and some hyperbolic and one with mostly hyperbolic and some Euclidean, then map out routing to identify when which were used
Add expert embeddings and attention routing
Add adaptive halting (learned halting rule) (two outputs, one which is transformed representation the other is usefulness)
Implement (or try to) local FF objectives
FF objectives + "goodness" value as stoppage rule instead of adaptive halting for comparison (or something that is close to progress not necessarily goodness) (central problem is preventing gamification of this local objective while actually correlating with usefulness)
Expected results (based on theory): WIP