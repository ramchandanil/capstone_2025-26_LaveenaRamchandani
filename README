# capstone_2025-26_LaveenaRamchandani
This is a repository for my Capstone project as per the Imperial Buinsess college course of Professional Certificate in Machine Learning and Artificial Intelligence

**Section 1: project overview**
The BBO capstone project focuses on optimising an unknown black-box system by iteratively selecting input queries and observing outputs. Its goal is to balance exploration and exploitation to identify high-performing regions efficiently. This reflects real-world machine learning problems such as hyperparameter tuning and model optimisation where internal model details are unavailable. The project supports my career by developing practical optimisation, experimentation, and documentation skills aligned with machine learning competitions and applied data science roles.
**
Section 2: Input & Output** 
How has your query strategy changed?
My strategy shifted from broad exploration to more structured, model-informed queries using smooth sigmoid-based functions. I now rely more on observed outcomes and heuristics than random sampling.

How do you balance exploration vs exploitation?
I prioritise exploitation around promising regions while still exploring through intermediate values to avoid premature convergence.

How would SVMs change your approach?
A soft-margin SVM could separate high- and low-performing regions while handling noise. A kernel SVM would help model non-linear black-box behaviour.

What limitations appear as data grows?
There is a risk of overfitting to known regions, and some dimensions may prove irrelevant without feature analysis or cross-validation.

How does this black-box setup help you think like a data scientist?
It reinforces decision-making under uncertainty, iterative learning, and using models as guides rather than ground truth.

**Section 2: inputs and outputs**
The model receives a fixed-length numerical query vector as input. Each query consists of multiple dimensions (ranging from 2D up to 8D), where each dimension represents a continuous parameter value. All input values are constrained to be non-negative and lie within the range 
[0,1]
[0,1]. Queries are formatted as hyphen-separated decimal values with six decimal places.

Example input (3D):
0.529960-0.389360-0.789410

The model returns a single scalar response value representing the black-box outcome. This output acts as a performance signal used to evaluate the quality of the input query. The response is used comparatively across iterations to guide future query selection but does not expose any internal model details.

Example output:
0.7421 (performance score)

This input–output structure supports black-box optimisation by enabling iterative refinement of queries based solely on observed performance.
**Section 3: challenge objectives**
Objective: Maximise each of the 8 functions.
The challenge explicitly states the goal is to find the global maximum for each function.

**Constraints and Limitations**
Limited observations (queries):
Each function starts with 10 initial input-output pairs.
Each week, you can make 1 new query per function.
Challenge lasts 13 weeks, so total observations per function will be:
10 initial + 13 weekly queries = 23 points per function.

**Unknown function structure:**
No assumptions can be made about the shape, smoothness, or correlations in the function beforehand.
This is a true black-box optimization problem.

**Sequential querying:**
You receive feedback after submitting each weekly input, so your strategy must adapt over time based on observed results.

**Limited data-driven inference:
**
With only 23 points per function, you must rely on data analysis, correlation detection, and machine learning models that can handle small data efficiently.
Other Considerations
You cannot assume linearity, monotonicity, or other functional forms.
Computational approaches like Gaussian Processes, Bayesian Optimization, or Decision Trees with hyperparameter tuning may be suitable due to the small dataset.
Proper tracking and documentation on GitHub is expected (code, data sheets, model cards, and presentations).

**Section 4: technical approach**
Used a combination of exploration and exploitation to guide queries while modeling the unknown functions. Focused on learning from initial 10 points and selecting inputs likely to improve understanding and approach the maximum.

**ML Methods**:
Gaussian Process (GP): Provided predictions and uncertainty estimates for balancing exploration and exploitation.
SVM Regression: Captured non-linear relationships without assuming a function structure.

**Exploration vs. Exploitation:
**
Exploration: Queried uncertain regions to expand knowledge.
Exploitation: Targeted points predicted to have high outputs.
Balance: Used GP uncertainty and predictions (Expected Improvement) to guide selection.

**Query Highlights:**
Week 1: Focused on exploration to reduce uncertainty.
Week 2: Mixed exploration and exploitation to refine models.
Week 3: Emphasized exploitation using GP and SVM predictions.

**Unique Points:**
Adaptive updates with each new observation.
Combined multiple ML models for robustness.
Optimized for small data scenarios with careful point selection.

**Next Steps:**
Explore Bayesian Optimization formally.
Use ensemble models to improve predictions.
