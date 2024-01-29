The Medical Test Paradox is a popular math problem and [[Veridical Paradox|veridical paradox]] applying [[Bayes' Theorem|Bayes' theorem]]. The problem is stated as follows:

> Suppose 1% of a sample of 1000 women (so, 10 women) have breast cancer. In the group of breast cancer patients, 9 are true positives, and 1 is a false negative. In the group of healthy individuals, 89 are false positives, and 901 are true negatives. How accurate is the test?

Applying statistical notation, we state that women who *actually* have cancer is $H$ and women who do not is $H'$. Women who test positive are $P$ and women who do not are $P'$. As such:

$$
\begin{align}
P(H\vert P) &\approx \frac{9}{9+89} \\
&= 9.184\%
\end{align}
$$

This value is denoted as the PPV, or Positive Predictive Value, for a medical test. However, looking at the test, we can compute its *accuracy*, usually broken down into [[Medical Test Sensitivity|sensitivity]] and [[Medical Test Specificity|specificity]]. Test sensitivity for our example is $90\%$. Test specificity for our example is $91.010\%$.

The paradox arises from the fact that the test is roughly $90\%$ accurate. However, if a woman *gets* a positive result, there is only a $9.184\%$ chance that she *actually* has breast cancer.