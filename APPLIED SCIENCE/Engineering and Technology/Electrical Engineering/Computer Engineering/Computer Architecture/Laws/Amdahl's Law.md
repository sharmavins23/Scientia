In [[Computer Architecture]], Amdahl's Law provides a formula for theoretical speedup in latency of execution of a task. The following is a formula:

$$
	S_{\text{latency}}(s) = \frac{1}{(1-f) + \frac{f}{s}}
$$

In the above equation, $s$ is the speedup of the part of the task benefitting from improved resources. Usually, $s$ is set to 50. $f$ refers to the fractional proportion of execution benefitting from improved resources.