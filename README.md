# Experimentation-of-dynamic-decision-graph
Question of focus: Can a neural network learn an input-dependent computational graph by dynamically composing small reusable modules, while simultaneously learning when to stop computing? What if a neural network wasn't a fixed graph, but a collection of small functions from which it constructs a different computational graph for each input?

Steps:

Implement with repeated dynamic routing and softmax first to check feasibility of idea
Implement two more networks to be trained side-by-side, one with mostly Euclidean mappings and some hyperbolic and one with mostly hyperbolic and some Euclidean, then map out routing to identify when which were used
Add expert embeddings and attention routing
Add adaptive halting (learned halting rule) (two outputs, one which is transformed representation the other is usefulness)
Implement (or try to) local FF objectives
FF objectives + "goodness" value as stoppage rule instead of adaptive halting for comparison (or something that is close to progress not necessarily goodness) (central problem is preventing gamification of this local objective while actually correlating with usefulness)
Expected results (based on theory): 
- Deeper models generally would have similar representations across each layer due to there typically being a prevailing pattern (Nguyen et. al, 2020), thus each layer augments with additional 
- To my understanding, wider models with a greater hidden state will be able to capture more feature representations, so are more effective when many factors are involved 
- I'm going to go out on a limb and guess that by reverse-bottlenecking width for depth > 2 experts would be more effective at catching edge cases, and would also be more prone to overfitting while bottlenecking will make it better at reinforcing a more specific pattern (would like to compare a representation of their loss functions too) (I guess this counts as a hypothesis) (Will math things out later when I'm smarter)
    - This reminds me of how random forest randomizes feature inputs to prevent similar trees - I can probably similarly apply this if my experts converge to the same/similar representations
    - I wonder how transfer learning will work with this kind of architecture, since my current hypothesis on how transfer learning works is that the predominant pattern as specified earlier overlaps in the similar task, thus making it easier to transfer to that task because most of the heavy lifting's already done (same idea for distilled learning I think)
- Since I keep seeing online how irl data is nonlinear, I think hyperbolic models will be selected first to capture features as it will be easier to express it as such, and then once transformed will favour linear for learning representations before decoding


Works Cited:
    Nguyen, Thao, Maithra Raghu, and Simon Kornblith. "Do wide and deep networks learn the same things? uncovering how neural network representations vary with width and depth." arXiv preprint arXiv:2010.15327 (2020).