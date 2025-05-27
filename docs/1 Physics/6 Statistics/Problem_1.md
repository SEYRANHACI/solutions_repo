### Task 1: Simulating Population Distributions

In this first part of the Central Limit Theorem (CLT) exploration, we begin by creating large datasets to represent different types of population distributions:

* **Uniform Distribution**: Values are equally likely within a range (0 to 10).
* **Exponential Distribution**: Skewed right; models wait times or lifetimes (scale = 2).
* **Binomial Distribution**: Discrete distribution representing the number of successes in 10 trials with probability 0.5.

The histograms above visualize the shape of each distribution. These populations will be used in the next task to sample and observe how the sample means behave according to the CLT.

Let me know if you're ready to proceed to **Task 2: Sampling and Visualization**.


### **Task 2: Sampling and Visualization**

We now investigate how sample size affects the distribution of sample means for different population types (Uniform, Exponential, Binomial). For each case:

* We take random samples of sizes 5, 10, 30, and 50.
* We compute the mean of each sample.
* We repeat this process 1000 times to build a **sampling distribution**.
* Then we **plot histograms** to visualize how these sample means begin to resemble a **normal distribution** as the sample size increases.

#### 🔍 Observations:

* For small sample sizes (e.g., 5), the sampling distribution reflects the skewness of the original population.
* As the sample size increases, all sampling distributions begin to take on a **bell-shaped curve**, aligning with the **Central Limit Theorem**.
* The convergence to normality occurs faster for symmetric distributions (like Uniform or Binomial) compared to skewed ones (like Exponential).

Let me know when you’re ready for **Task 3: Parameter Exploration**.
