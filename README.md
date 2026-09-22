# Experimentation-of-dynamic-decision-graph
Question of focus: Can a neural network learn an input-dependent computational graph by dynamically composing small reusable modules, while simultaneously learning when to stop computing? What if a neural network wasn't a fixed graph, but a collection of small functions from which it constructs a different computational graph for each input?

Steps: 
1. Implement with repeated dynamic routing and softmax first to check feasibility
2. Add expert embeddings and attention routing
3. Add adaptive halting (so the learned halting rule thing) (two outputs, one which is transformed representation the other is usefulness)
4. Local FF objectives
5. FF objectives + goodness as stoppage rule (or something that is close to progress not necessarily goodness) (central problem is preventing gamification of this local objective while actually correlating with usefulness)
