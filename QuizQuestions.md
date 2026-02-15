# quizquestions.md
## Part 4: Quiz Questions (Causality) — 15 MCQs with Answers and Explanations

### Question 1: Confounding
A researcher compares outcomes between treated and untreated groups and finds a large difference. Why might this difference fail to be causal?

A) The outcome is measured after treatment  
B) The treated group is larger than the control group  
C) A pre-treatment variable affects both treatment assignment and the outcome  
D) The outcome is continuous rather than binary  

**Correct Answer: C**

**Explanation:**  
C is correct: if a pre-treatment covariate influences both treatment and outcome, it creates a backdoor path (confounding), so the naive difference mixes causal effect with selection bias.  
- A is incorrect: outcomes are typically measured after treatment in causal studies.  
- B is incorrect: sample size imbalance does not inherently create bias.  
- D is incorrect: outcome type does not determine causality validity.

---

### Question 2: Backdoor Criterion (Adjustment Set)
In a DAG \(X \rightarrow T\), \(X \rightarrow Y\), \(T \rightarrow Y\), which adjustment identifies the total effect of \(T\) on \(Y\)?

A) Adjust for \(X\)  
B) Adjust for \(Y\)  
C) Adjust for a mediator \(M\) where \(T \rightarrow M \rightarrow Y\)  
D) Adjust for a collider \(C\) where \(T \rightarrow C \leftarrow Y\)  

**Correct Answer: A**

**Explanation:**  
A is correct: adjusting for the common cause \(X\) blocks the backdoor path \(T \leftarrow X \rightarrow Y\).  
- B is incorrect: conditioning on outcomes is not a backdoor strategy and can be harmful.  
- C is incorrect: adjusting for a mediator blocks part of the total effect.  
- D is incorrect: conditioning on a collider opens spurious associations.

---

### Question 3: Unconfoundedness (Selection on Observables)
What does unconfoundedness mean for identifying the ATE using observed covariates \(X\)?

A) \(T\) is randomized  
B) \((Y(1), Y(0)) \perp T \mid X\)  
C) \(Y \perp X\)  
D) \(T \perp X\)  

**Correct Answer: B**

**Explanation:**  
B is correct: after conditioning on \(X\), treatment assignment is as good as random with respect to potential outcomes.  
- A is incorrect: unconfoundedness is an assumption used when treatment is not randomized.  
- C is incorrect: outcomes can depend on covariates.  
- D is incorrect: treatment can depend on \(X\); that is exactly why we adjust.

---

### Question 4: Positivity / Overlap
Which statement best describes the positivity assumption?

A) Every unit has the same treatment effect  
B) For any covariate pattern \(X\), both treatment and control are possible: \(0 < P(T=1 \mid X) < 1\)  
C) The outcome model must be linear  
D) Confounders must be normally distributed  

**Correct Answer: B**

**Explanation:**  
B is correct: positivity ensures we have comparable treated and control units across covariate strata.  
- A is incorrect: constant effects are not required.  
- C is incorrect: positivity is not about model form.  
- D is incorrect: positivity is not a distributional assumption.

---

### Question 5: What Weak Overlap Implies
If treated units have propensity scores mostly near 1 and controls mostly near 0, what is the main concern?

A) Outcome measurement error  
B) Lack of overlap may make estimates unstable and reliant on extrapolation  
C) Treatment becomes a mediator  
D) SUTVA is automatically violated  

**Correct Answer: B**

**Explanation:**  
B is correct: weak overlap strains positivity, makes IPW weights extreme, and forces methods to extrapolate beyond observed comparisons.  
- A is incorrect: overlap is distinct from measurement error.  
- C is incorrect: treatment is not a mediator.  
- D is incorrect: SUTVA is about interference and treatment definition, not overlap.

---

### Question 6: Extreme IPW Weights
Which observations tend to get very large inverse probability weights?

A) Treated units with \(e(X)\) near 0 and control units with \(e(X)\) near 1  
B) Treated units with \(e(X)\) near 1 and control units with \(e(X)\) near 0  
C) Units with \(e(X)\) near 0.5  
D) Units with high outcomes  

**Correct Answer: A**

**Explanation:**  
A is correct: for treated, weights scale like \(1/e(X)\); for controls, like \(1/(1-e(X))\).  
- B is incorrect: these cases usually lead to smaller weights.  
- C is incorrect: \(e(X)\approx 0.5\) produces moderate weights.  
- D is incorrect: weights depend on treatment probabilities, not outcomes.

---

### Question 7: Stabilized IPW
Why use stabilized IPW weights?

A) To avoid checking overlap  
B) To reduce variance and improve finite-sample behavior while targeting the same estimand under assumptions  
C) To guarantee the causal effect is positive  
D) To remove the need for covariates \(X\)  

**Correct Answer: B**

**Explanation:**  
B is correct: stabilization often reduces the influence of extreme weights, improving variance properties (but does not “fix” lack of overlap).  
- A is incorrect: overlap diagnostics remain essential.  
- C is incorrect: weighting does not guarantee effect direction.  
- D is incorrect: IPW relies on \(X\) via \(e(X)\).

---

### Question 8: Trimming
What is the primary tradeoff of trimming units with extreme propensity scores?

A) It increases sample size but reduces bias  
B) It improves comparability (internal validity) but changes the target population (external validity)  
C) It eliminates unmeasured confounding  
D) It makes treatment randomized  

**Correct Answer: B**

**Explanation:**  
B is correct: trimming restricts inference to common support, which can stabilize estimation but changes the estimand toward an overlap-supported subpopulation.  
- A is incorrect: trimming reduces sample size.  
- C is incorrect: trimming does not fix unobserved confounders.  
- D is incorrect: trimming does not create randomization.

---

### Question 9: Matching and Calipers
What does a caliper do in propensity score matching?

A) Forces the logistic regression to converge  
B) Prevents matches that are too far apart in propensity score  
C) Ensures every treated unit is matched  
D) Makes post-treatment adjustment safe  

**Correct Answer: B**

**Explanation:**  
B is correct: calipers set a maximum allowable distance to avoid poor matches.  
- A is incorrect: convergence is handled by modeling choices.  
- C is incorrect: calipers may drop treated units without close matches.  
- D is incorrect: post-treatment adjustment remains risky regardless of matching.

---

### Question 10: Matching With Replacement
If controls can be reused across multiple treated units, what is true?

A) This is matching with replacement; it can reduce bias but may increase variance  
B) This is matching without replacement; it always reduces variance  
C) It guarantees perfect balance  
D) It is identical to IPW  

**Correct Answer: A**

**Explanation:**  
A is correct: replacement can improve match quality when overlap is limited, but repeated use of a few controls can inflate variance.  
- B is incorrect: without replacement requires removing selected controls.  
- C is incorrect: balance can improve but is not guaranteed to be perfect.  
- D is incorrect: matching and IPW are different estimators.

---

### Question 11: Standardized Mean Difference (SMD)
What does SMD measure?

A) Statistical significance of the causal effect  
B) Covariate balance between treated and control groups, scaled by pooled variability  
C) Overlap of outcomes between groups  
D) The variance of propensity scores  

**Correct Answer: B**

**Explanation:**  
B is correct: SMD quantifies covariate imbalance in standardized units and is commonly used before/after matching or weighting.  
- A is incorrect: balance is not the same as effect significance.  
- C is incorrect: SMD is about covariates, not outcomes.  
- D is incorrect: SMD is not a PS variance metric.

---

### Question 12: Balance vs Causality
If all observed covariates have \(|\text{SMD}|<0.1\) after adjustment, what can we conclude?

A) The estimate is definitely unbiased  
B) Observed covariate balance is good, but unmeasured confounding could still bias results  
C) Positivity is satisfied automatically  
D) The effect must be statistically significant  

**Correct Answer: B**

**Explanation:**  
B is correct: good balance on observed \(X\) is encouraging but does not prove unconfoundedness (unmeasured confounding may remain).  
- A is incorrect: balance is necessary but not sufficient for unbiasedness.  
- C is incorrect: overlap must still be checked.  
- D is incorrect: significance depends on variance and sample size.

---

### Question 13: Post-Treatment Bias
Which variable is generally unsafe to adjust for when estimating the *total* effect of \(T\) on \(Y\)?

A) A baseline demographic variable  
B) A pre-treatment outcome measure  
C) A mediator measured after treatment  
D) A pre-treatment risk factor  

**Correct Answer: C**

**Explanation:**  
C is correct: controlling for mediators blocks part of the total effect; post-treatment variables can also act as colliders and induce bias.  
- A, B, and D are pre-treatment and are valid candidates for adjustment (if not colliders).

---

### Question 14: Outcome Regression Under Weak Overlap
Why can outcome regression be risky when overlap is weak?

A) Linear regression cannot be used for causal inference  
B) It may extrapolate counterfactuals outside regions supported by the data, relying on functional-form assumptions  
C) It forces weights to be extreme  
D) It violates SUTVA  

**Correct Answer: B**

**Explanation:**  
B is correct: poor overlap means the model may predict outcomes for treated units using regions where similar controls barely exist (and vice versa), increasing sensitivity to misspecification.  
- A is incorrect: regression can be used under assumptions.  
- C is incorrect: extreme weights are not a regression mechanism.  
- D is incorrect: SUTVA is unrelated to overlap/regression extrapolation.

---

### Question 15: Identification vs Estimation
What is the difference between identifying an estimand and estimating it?

A) Identification produces a numeric ATE; estimation draws the DAG  
B) Identification uses causal assumptions/graph rules to express the effect; estimation computes a numeric value using data and a statistical method  
C) Identification checks model convergence; estimation checks overlap  
D) They are the same step with different names  

**Correct Answer: B**

**Explanation:**  
B is correct: identification answers “what must be adjusted for (in principle) to interpret causally,” while estimation answers “what is the numeric effect using this method on this data.”  
- A is incorrect: reversed.  
- C is incorrect: those are diagnostics, not the core distinction.  
- D is incorrect: they are different stages.

