<h1>Model Card: Adaptive Surrogate-Based BBO Strategy</h1>

<hr>

<h2>1. Overview</h2>

<p><strong>Name:</strong> Adaptive Multi-Surrogate Black-Box Optimisation Strategy</p>
<p><strong>Type:</strong> Surrogate-based black-box optimisation framework</p>
<p><strong>Version:</strong> Final Capstone Submission (Week 10)</p>

<p>
This model describes a flexible <strong>Black-Box Optimisation (BBO)</strong> strategy developed for the 
<strong>Imperial College London Machine Learning Capstone Project</strong>.
Rather than relying on a single fixed model, the approach uses an 
<strong>adaptive framework</strong> that selects different surrogate models and acquisition strategies 
depending on:
</p>

<ul>
<li>Dimensionality of the optimisation problem</li>
<li>Observed noise levels</li>
<li>Function smoothness and behaviour</li>
</ul>

<p>
Across the ten optimisation rounds, the strategy evolved from 
<strong>broad exploration</strong> to <strong>targeted exploitation</strong>, 
with method switching introduced whenever optimisation progress plateaued.
</p>

<hr>

<h2>2. Intended Use</h2>

<h3>Suitable Tasks</h3>

<p>This optimisation strategy is appropriate for:</p>

<ul>
<li>Maximising expensive black-box functions under small evaluation budgets (~10–20 queries)</li>
<li>Low- to moderate-dimensional problems (2D–8D)</li>
<li>Continuous input domains bounded within <code>[0,1]<sup>d</sup></code></li>
<li>Problems where the objective is expected to be relatively smooth</li>
<li>Educational demonstrations of exploration versus exploitation trade-offs</li>
</ul>

<h3>Use Cases to Avoid</h3>

<p>This strategy is not suitable for:</p>

<ul>
<li>High-dimensional problems (d ≫ 8) without further adaptation</li>
<li>Highly discontinuous or extremely non-smooth objective functions</li>
<li>Unbounded optimisation problems</li>
<li>Large-budget optimisation settings</li>
<li>Production environments without additional robustness validation</li>
</ul>

<hr>

<h2>3. Strategy Across the Ten Rounds</h2>

<h3>High-Level Evolution</h3>

<h4>Rounds 1–3: Exploration Phase</h4>

<ul>
<li>Broad sampling of the search space</li>
<li>Construction of initial surrogate models</li>
<li>Understanding function smoothness, sparsity, and noise characteristics</li>
</ul>

<h4>Rounds 4–6: Transition Phase</h4>

<ul>
<li>Increased exploitation of promising regions</li>
<li>Reduced exploration parameters (e.g., β in UCB)</li>
<li>Introduction of progress validation checks</li>
<li>Noise-aware modelling for stochastic functions</li>
<li>Gradient-based optimisation for higher-dimensional problems</li>
</ul>

<h4>Rounds 7–10: Refinement Phase</h4>

<ul>
<li>Focused search near best-known solutions</li>
<li>Switched from UCB to Expected Improvement (EI) when progress stagnated</li>
<li>Increased local optimisation restarts</li>
<li>Fine-tuning of neural network surrogate models</li>
</ul>

<hr>

<h3>Techniques Used by Function Type</h3>

<table>
  <thead>
    <tr>
      <th>Function Type</th>
      <th>Technique</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Classification</td>
      <td>Support Vector Machines</td>
      <td>A supervised learning model used for classification tasks</td>
    </tr>
    <tr>
      <td>Regression</td>
      <td>Linear Regression</td>
      <td>Models relationships between dependent and independent variables</td>
    </tr>
    <tr>
      <td>Clustering</td>
      <td>K-Means Clustering</td>
      <td>Partitions observations into nearest-mean clusters</td>
    </tr>
    <tr>
      <td>Dimensionality Reduction</td>
      <td>Principal Component Analysis</td>
      <td>Emphasises variation and reveals strong patterns in data</td>
    </tr>
  </tbody>
</table>

<hr>

<h3>Decision-Making Logic</h3>

<p>The strategy selects the next query point by:</p>

<ul>
<li>Fitting a surrogate model to observed data</li>
<li>Applying an acquisition function (UCB or EI) or gradient optimisation</li>
<li>Evaluating progress against the incumbent best solution</li>
<li>Adjusting exploration intensity when improvement stalls</li>
</ul>

<p><strong>Strength:</strong> Highly flexible and adaptive.</p>
<p><strong>Limitation:</strong> Performance depends heavily on surrogate model accuracy.</p>

<hr>

<h2>4. Performance</h2>

<h3>Evaluation Setup</h3>

<ul>
<li>Eight black-box functions evaluated</li>
<li>One submission per function per week</li>
<li>Primary objective: maximise output value</li>
</ul>

<h3>Metrics Used</h3>

<p><strong>Primary metric:</strong> Maximum observed function value</p>

<p><strong>Secondary metrics:</strong></p>

<ul>
<li>Week-on-week improvement</li>
<li>Distance to incumbent best</li>
<li>Acquisition value diagnostics</li>
</ul>

<p>
No formal train/test split was used; evaluation occurred through live weekly submissions.
</p>

<h3>Overall Results</h3>

<ul>
<li>Strong performance on smooth low-dimensional functions using GP-based Bayesian Optimisation</li>
<li>Improved stability on noisy functions using noise-aware surrogate modelling</li>
<li>Neural network surrogates showed diminishing returns in 6D–8D settings due to limited data</li>
<li>Performance improved over rounds, with plateauing near estimated optima</li>
</ul>

<hr>

<h2>5. Assumptions and Limitations</h2>

<h3>Core Assumptions</h3>

<ul>
<li>The objective function is reasonably smooth</li>
<li>The global optimum lies within <code>[0,1]<sup>d</sup></code></li>
<li>Surrogate models generalise effectively from limited observations</li>
<li>Noise is moderate and can be modelled</li>
</ul>

<h3>Limitations</h3>

<ul>
<li>Small sample sizes (~10–17 points per function)</li>
<li>Risk of surrogate overfitting</li>
<li>Computational constraints limited neural network size and GP restarts</li>
<li>Weekly submission delays restricted rapid exploration</li>
<li>Neural networks extrapolate poorly in sparse regions</li>
<li>GP scalability decreases with dimensionality</li>
</ul>

<h3>Failure Modes</h3>

<ul>
<li>Convergence to local optima</li>
<li>Surrogate mis-specification (e.g., incorrect kernel assumptions)</li>
<li>Locking onto noisy spikes</li>
<li>Exploration parameter misconfiguration</li>
</ul>

<hr>

<h2>6. Ethical Considerations</h2>

<h3>Transparency &amp; Reproducibility</h3>

<p>Transparency supports:</p>

<ul>
<li>Clear documentation of assumptions</li>
<li>Reproducibility of weekly decisions</li>
<li>Understanding why specific points were selected</li>
<li>Adaptability to new optimisation domains</li>
</ul>

<p>The repository structure ensures that:</p>

<ul>
<li>The optimisation pipeline can be re-run</li>
<li>Model choices remain inspectable</li>
<li>Hyperparameters and acquisition logic are traceable</li>
</ul>

<h3>Real-World Adaptation</h3>

<p>
Explicit documentation of intended use, assumptions, limitations, and failure modes 
reduces misuse when adapting this strategy to real-world domains such as:
</p>

<ul>
<li>Hyperparameter tuning</li>
<li>Engineering optimisation</li>
<li>Drug discovery</li>
</ul>

<hr>

<h2>7. Reflection on Clarity and Completeness</h2>

<p>This model card clearly explains:</p>

<ul>
<li>What the optimisation framework is</li>
<li>How the strategy operates</li>
<li>When it should be applied</li>
<li>Its risks and limitations</li>
</ul>

<p>
Adding excessive technical detail (for example full hyperparameter tables or derivations) 
would reduce clarity without significantly improving practical usefulness.
The current structure balances:
</p>

<ul>
<li>Transparency</li>
<li>Technical depth</li>
<li>Readability</li>
</ul>

<hr>

<h3>Summary of Strengths and Weaknesses</h3>

<h4>Strengths</h4>

<ul>
<li>Adaptive method switching</li>
<li>Explicit handling of noise</li>
<li>Strong performance in low-dimensional smooth settings</li>
<li>Balanced exploration and exploitation</li>
</ul>

<h4>Weaknesses</h4>

<ul>
<li>Limited scalability</li>
<li>Sensitive to surrogate model quality</li>
<li>Higher overfitting risk in small-data settings</li>
<li>Neural network performance constrained by compute limits</li>
</ul>
