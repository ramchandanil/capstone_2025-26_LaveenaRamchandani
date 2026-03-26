<h1>Datasheet: BBO Capstone Project Dataset</h1>

<p>
This datasheet documents the dataset used for the <strong>Black-Box Optimisation (BBO) Capstone Project</strong>, 
following the framework introduced in <strong>Mini-Lesson 21.1</strong> and supported by weekly experimental reflections.
The dataset was created for <strong>educational optimisation research</strong> and strategy evaluation rather than general machine learning benchmarking.
</p>

<hr>

<h2>1. Motivation</h2>

<h3>Why was this dataset created?</h3>

<p>
The dataset was developed to support a course-based <strong>black-box optimisation challenge</strong> focused on learning efficient query strategies under strict evaluation constraints.
The primary objective was to maximise unknown black-box objective functions using a limited number of evaluations.
</p>

<p>The dataset supports the following goals:</p>

<ul>
<li><strong>Optimisation research</strong> — identifying input configurations that maximise unknown objective outputs</li>
<li><strong>Strategy evaluation</strong> — comparing exploration versus exploitation trade-offs</li>
<li><strong>Surrogate modelling</strong> — testing model-based approximations of unknown functions</li>
<li><strong>Educational reflection</strong> — supporting weekly decision analysis and documenting optimisation behaviour</li>
</ul>

<p>
The dataset is not intended for general machine learning model training, but rather for 
<strong>optimisation strategy learning and interpretability analysis</strong>.
</p>

<hr>

<h2>2. Composition</h2>

<h3>What does the dataset contain?</h3>

<p>
The dataset consists of <strong>query–response pairs</strong> collected across multiple black-box functions.
</p>

<h3>Inputs</h3>

<ul>
<li>Continuous feature vectors bounded within a normalised search space (typically <code>[0,1]^d</code>)</li>
<li>Dimensionality varies by function depending on the optimisation problem</li>
</ul>

<h3>Outputs</h3>

<ul>
<li>Single scalar objective values</li>
<li>Higher values correspond to improved optimisation performance</li>
</ul>

<h3>Dataset Structure</h3>

<p>The dataset is organised into:</p>

<ul>
<li>Initial sampling data</li>
<li>Weekly optimisation queries</li>
<li>Corresponding function outputs</li>
</ul>

<pre><code>
data/
 ├── initial_data/
 ├── week1/
 ├── week2/
 └── weekN/
</code></pre>

<p>Each weekly folder contains:</p>

<ul>
<li>Inputs queried during that week</li>
<li>Observed outputs from black-box evaluation</li>
</ul>

<h3>Size and Format</h3>

<p>
The dataset size increases over time as new evaluations are added.
</p>

<ul>
<li>Initial dataset: approximately 10–20 samples per function</li>
<li>Weekly additions: approximately 1 sample per function per week</li>
<li>Total size depends on overall project duration</li>
</ul>

<p>Formats include:</p>

<ul>
<li><code>.npy</code> NumPy arrays</li>
<li>Text files containing Python-evaluable lists</li>
</ul>

<h3>Gaps and Caveats</h3>

<ul>
<li><strong>Spatial gaps:</strong> query locations are non-uniform because sampling is optimisation-driven</li>
<li><strong>Temporal gaps:</strong> only a small number of evaluations were allowed each week</li>
<li><strong>Noise:</strong> some functions may exhibit stochastic output behaviour, introducing variability</li>
</ul>

<hr>

<h2>3. Collection Process</h2>

<h3>How were queries generated?</h3>

<p>
Queries were generated using <strong>surrogate-based optimisation strategies</strong>.
Strategy selection varied depending on observed function behaviour and weekly optimisation performance.
</p>

<h3>Examples of strategy choices</h3>

<h4>Exploration Phase (Weeks 1–3)</h4>

<ul>
<li>Random sampling</li>
<li>Uncertainty-driven exploration</li>
</ul>

<p><strong>Purpose:</strong> Build initial surrogate approximations.</p>

<h4>Balanced Optimisation Phase (Weeks 4–6)</h4>

<ul>
<li>Bayesian optimisation methods</li>
<li>Acquisition functions such as:
    <ul>
        <li>Upper Confidence Bound (UCB)</li>
        <li>Expected Improvement (EI)</li>
    </ul>
</li>
</ul>

<p><strong>Purpose:</strong> Improve objective values while preserving uncertainty coverage.</p>

<h4>Refinement Phase (Weeks 7–10)</h4>

<ul>
<li>Exploitative optimisation around promising regions</li>
<li>Local search refinement</li>
</ul>

<p><strong>Purpose:</strong> Fine-tune solutions near estimated optima.</p>

<h3>Time Frame</h3>

<ul>
<li>Approximately 10–14 weeks of experimentation</li>
<li>Approximately 1 query per function per week under evaluation constraints</li>
</ul>

<hr>

<h2>4. Preprocessing and Uses</h2>

<h3>Transformations Applied</h3>

<h4>Input Scaling</h4>

<p>
Inputs were already normalised to the search bounds <code>[0,1]</code>.
</p>

<h4>Output Normalisation</h4>

<p>Some analysis pipelines used:</p>

<ul>
<li>Mean-variance normalisation</li>
<li>Standardisation prior to surrogate training</li>
</ul>

<p>
Predictions were transformed back to original output scales when required.
</p>

<h3>Intended Uses</h3>

<ul>
<li>Reproducing black-box optimisation pipelines</li>
<li>Studying acquisition strategy effectiveness</li>
<li>Evaluating surrogate modelling decisions</li>
<li>Supporting academic reflection on optimisation behaviour</li>
</ul>

<h3>Inappropriate Uses</h3>

<ul>
<li>❌ General machine learning benchmarking</li>
<li>❌ Deployment-level predictive modelling</li>
<li>❌ Inferring true underlying function forms</li>
<li>❌ Training large-scale deep learning systems</li>
</ul>

<p><strong>Reasons:</strong></p>

<ul>
<li>Dataset size is limited</li>
<li>Sampling is strategy-biased</li>
<li>Data is non-IID and optimisation-driven</li>
</ul>

<hr>

<h2>5. Distribution and Maintenance</h2>

<h3>Where is the dataset available?</h3>

<pre><code>
data/
 ├── initial_data/
 ├── week1/
 ├── week2/
 └── weekN/
</code></pre>

<p>Files include:</p>

<ul>
<li><code>initial_inputs.npy</code></li>
<li><code>initial_outputs.npy</code></li>
<li>Weekly <code>inputs.txt</code> and <code>outputs.txt</code></li>
</ul>

<h3>Terms of Use</h3>

<p>
This dataset forms part of an academic capstone project and should be used only for 
<strong>educational and research reflection purposes</strong>.
</p>

<p>
Users should follow institutional academic integrity guidelines.
</p>

<h3>Maintenance</h3>

<p>
The dataset is maintained by the project author.
Updates are performed weekly by appending new query results and updating documentation logs.
</p>

<hr>

<h2>⭐ Reflection Notes</h2>

<p>
This project demonstrates the importance of balancing <strong>exploration</strong> and <strong>exploitation</strong> 
in black-box optimisation.
</p>

<p>
Early-stage exploration supported the construction of robust surrogate models, while later-stage exploitation 
improved objective performance.
</p>

<p>Key limitations include:</p>

<ul>
<li>Sampling bias</li>
<li>Limited evaluation budget</li>
<li>Sensitivity to noisy outputs</li>
</ul>

<p>Future work could explore:</p>

<ul>
<li>Adaptive acquisition scheduling</li>
<li>Multi-surrogate ensemble strategies</li>
</ul>
