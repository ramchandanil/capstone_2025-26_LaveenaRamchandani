<h1>Black-Box Optimisation Capstone Project</h1>

<p>
This notebook presents the results of a <strong>13-week Black-Box Optimisation (BBO)</strong> process.
The objective was to iteratively optimise unknown functions using a feedback-driven approach. See solution attached HTML version
</p>

<p>The optimisation process involved:</p>

<ul>
<li>Submitting input parameters to the black-box system</li>
<li>Observing resulting output scores</li>
<li>Refining optimisation strategies over time</li>
</ul>

<p>The notebook demonstrates several key analytical and optimisation concepts:</p>

<ul>
<li>Structured data collection and analysis</li>
<li>Tracking optimisation performance across iterations</li>
<li>Tracking optimisation performance across iterations</li>
<li> Understanding the outputs based on cummulative chart</li>

</ul>

<hr>

<h2>Data Collection</h2>

<p>The dataset consists of the following components:</p>

<ul>
<li><strong>Input parameter vectors</strong> submitted during each weekly iteration based on learning of that specific week</li>
<li><strong>Corresponding output scores</strong> returned by the black-box system</li>
</ul>

<p>
The input parameters are included primarily for <strong>transparency and reproducibility</strong>, 
while the output scores are used as the primary metric for evaluating optimisation performance.
</p>



<p>
This table contains all input vectors submitted to the black-box system during the 
<strong>13-week optimisation process</strong>.
</p>

<p>The input records are provided to support:</p>

<ul>
<li>Reproducibility of the optimisation experiment</li>
<li>Transparency of the optimisation strategy</li>
<li>Documentation of parameter exploration over time</li>
</ul>

<p>
Although the primary analysis focuses on output values, these inputs provide 
<strong>full traceability of the optimisation decisions</strong> made during each iteration.
</p>

<hr>

<h2>Cumulative Optimisation Progress</h2>

<p>
To better understand how optimisation performance evolved over time, cumulative output scores 
are calculated across all functions. This approach highlights how incremental improvements 
contribute to overall optimisation success throughout the 13-week process.
</p>

<pre><code class="language-python">
import pandas as pd
import matplotlib.pyplot as plt

# Create cumulative version of outputs
cumulative_outputs = outputs.copy()

# Apply cumulative sum to all function columns (skip Week column)
for col in outputs.columns[1:]:
    cumulative_outputs[col] = outputs[col].cumsum()

# Plot cumulative outputs
plt.figure(figsize=(10,6))

for col in cumulative_outputs.columns[1:]:
    plt.plot(cumulative_outputs["Week"], cumulative_outputs[col], label=col)

plt.title("Cumulative Optimisation Progress Across Functions")
plt.xlabel("Week")
plt.ylabel("Cumulative Output")
plt.legend()
plt.grid(True)

plt.show()
</code></pre>

<hr>

<h2>Interpretation</h2>

<p>
The cumulative optimisation curves illustrate how performance improvements accumulate over 
the course of the optimisation process. Periods of rapid growth indicate successful discovery 
of high-performing regions in the search space, while flatter regions represent refinement 
and incremental improvement.
</p>

<p>
This behaviour reflects a common pattern observed in real-world optimisation systems:
</p>

<ul>
<li><strong>Early phase:</strong> exploration with limited immediate gains</li>
<li><strong>Middle phase:</strong> discovery of promising optimisation regions</li>
<li><strong>Late phase:</strong> refinement and incremental improvements</li>
</ul>

<p>
Such trajectories are typical in iterative optimisation workflows where a small number of 
iterations contribute disproportionately to overall performance gains.
</p>
