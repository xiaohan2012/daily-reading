# active learning prediction error monotonicity check

we show if the prediction error on $`q`$ is monotonically decreasing if the estimator is unbiased. 

consider a query node $`q`$, 

at time point $`t_1`$, denote:

- $`P_{t_1}(y_q=1 )=p_1`$, therefore $`P_{t_1}(y_q=0)=1-p_1`$
- prediction error corresponding to $`y_q=1`$ is $`a_1`$, for the other case, it's $`b_1`$


at time point $`t_2 > t_1`$, denote:

- $`P_{t_2}(y_q=1)=p_2`$, therefore $`P_{t_2}(y_q=0)=1-p_2`$
- prediction error corresponding to $`y_q=1`$ is $`a_2`$, for the other case, it's $`b_2`$



then the score for $`q`$:

- at $`t_1`$ is $`p_1 a_1 + (1-p_1)b_1`$
- at $`t_2`$ is $`p_2 a_2 + (1-p_2)b_2`$



it should be true that:

$`a_1 > a_2`$ and $`b_1 > b_2`$ (as we add more examples, the prediction error should decrease)

then 

$`p_1 a_1 + (1-p_1)b_1 - p_2 a_2 + (1-p_2)b_2 > p_1 a_1 + (1-p_1)b_1 - p_2 a_1 + (1-p_2)b_1 = (p_1 - p_2)(a_1 - b_1)`$

now consider the following two cases:

if $`y_q=1`$, then $`p_1>0.5`$ (if we assume the estimator is unbiased)
and $`p_2 > p_1`$ because the belief is reinforced. 

meanwhile, $`a_1 < b_1`$ because in $`a_1`$ conditions on the correct output of $`t_q`$, thus smaller error. 

therefore, $`(p_1 - p_2)(a_1 - b_1) > 0`$

therefore prediction error on $`q`$ decreases as $`t`$

the case for $`y_q=0`$ can be proved almost the same. 