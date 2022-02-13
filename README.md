#Statistics

## Distributions

- Standard Deviation
    
    Is a measure of how spread out numbers are
    
    ```python
    # Standard Deviation
    sd1 = st.stdev(d1)
    print('Standard Deviation : ',sd1)
    ```
    
    - Discrete
        
        Certain values
        
    - Continuous
        
        Values within a range
        
- Normal Distribution
    
    A function that represents the distribution of many random variables as a symmetrical bell-shaped graph
    
    # $f(x) = \frac{1}{\sigma\sqrt{2\pi}} 
      \exp\left( -\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^{\!2}\,\right)$
    
    ![empirical_rule_graph2.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/60905d88-c4e9-4891-83d1-f02e5871cff8/empirical_rule_graph2.png)
    
- Skewness
    
    A measure of asymmetry/distortion of symmetric distribution
    
    ![pearson-mode-skewness.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d152ee1f-b60b-48f2-934b-98a2fd371589/pearson-mode-skewness.jpg)
    
    ```python
    from scipy.stats import skew
    # Skewness
    skewness1 = skew(d1)
    print('Skewness : ',skewness1)
    ```
    
- Mean, Median, Mode
    
    [main-qimg-29a4925034e075f16e1c743a4b3dda8b-lq.jfif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0d707434-395e-48b4-9ff0-a1f9bd981231/main-qimg-29a4925034e075f16e1c743a4b3dda8b-lq.jfif)
    
    ```python
    # Mean
    mean1 = np.mean(d1)
    print('Mean : ',mean1)
    # Mode
    mode1= st.mode(d1)
    print('Mode : ',mode1,mode2)
    # Median
    median1 = np.median(d1)
    print('Median : ',median1)
    ```
    
- Cantor’s Diagonal Argument
    
    Clever technique to show that the integers and reals cannot be put into a one-to-one correspondence (some infinite sets are actually 'bigger' than the set of positive integers)
    
    [68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f776174747061642d6d656469612d736572766963652f53746f7279496d6167652f6c69525654346f506139726a33673d3d2d3332323739343737372e3134376465393734653762333.jfif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9e24fb9d-48c9-4a6d-8084-943231537ad2/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f776174747061642d6d656469612d736572766963652f53746f7279496d6167652f6c69525654346f506139726a33673d3d2d3332323739343737372e3134376465393734653762333.jfif)
    

## Central limit theorem

- Population and samples
    
    ![sample-size-definition.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d3af2565-de52-4007-8138-6026c5ef2940/sample-size-definition.png)
    
- Sampling Distribution
    
    A probability distribution of a statistic obtained from a larger number of samples drawn from a specific population
    
    ![unnamed-chunk-63-1.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8084d86a-544f-4fc3-8212-ad6e0491fe9e/unnamed-chunk-63-1.png)
    
- Central Limit Theorem
    
    **More times you roll the die**, the more likely the shape of the distribution of the **means** tends to look like a **normal distribution graph**
    
    ![500px-Dice_sum_central_limit_theorem.svg_-250x300.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4ae8008c-6263-461d-9dfb-05b081170248/500px-Dice_sum_central_limit_theorem.svg_-250x300.png)
    
- Z-Score
    
    Measures the distance between a data point and the ***mean***
     using standard deviations
    
    # $Z = \frac{x - \mu}{\sigma}$
    
    # $Z = \frac{value - mean}{standard deviation}$
    

## Hypothesis Testing

- Hypothesis testing is a statistical method used in making statistical decisions using experimental data
    - Hypothesis is based on:
        - Normalization
            
            '''$x_{normalized}= \frac{x - x_{min}}{x_{max} - x_{min}}$
            '''
        - Standard normalization
            
            # $x_{new} = \frac{x - \mu}{\sigma}$
            
    - Important parameter of hypothesis testing:
        
        **H0:** Null hypothesis (no significant difference between specified populations)
        
        **H1:** Alternative hypothesis (an *alternative* to the null)
        
    - Level of significance:
        
        Refers to the degree of significance in which we accept or reject the null-hypothesis
        
        Level of significance reflects your risk tolerance and confidence level. For example, if you run an A/B testing experiment with a significance level of 95%, this means that if you determine a winner, **you can be 95% confident that the observed results are real and not an error caused by randomness**
        
        Level of significance is usually taken as 5%, (also called alpha) which means your output should be 95% confident to give similar kind of result in each sample
        
        ```python
        from scipy.stats import norm
        norm(mean1, sd1)
        y1 = 0.95
        x1 = norm(mean1, sd1).ppf(y1)
        z1 = norm(mean1, sd1).pdf(x1)
        
        plt.figure(figsize=(12,6))
        ax = plt.gca()
        x = np.linspace(mean1-3*sd1, mean1 + 3*sd1, 100)
        plt.plot(x, norm.pdf(x, mean1, sd1))
        plt.axvline(x1, color='red')
        plt.axhline(z1, color='red')
        plt.title("Normal Distribution N(1774.5, 314.84)")
        print("We have 95% of probability that r <= {}".format(round(x1,3)))
        ```
        
    - Types of errors:
        - **I error:** reject null-hypothesis, but hypothesis was true
        - **II error:** accept null-hypothesis, but hypothesis is false
    - Types of tests:
        - **One tailed test:** the region of rejection is on only **one**
         side of the sampling distribution
        - **Two-tailed test:** the critical area of a distribution is **two**-**sided**
        
        ![1_Fwmazvo993cH6q79bpfeIw.jpeg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2a5aec76-4523-496e-a179-69b9b760b605/1_Fwmazvo993cH6q79bpfeIw.jpeg)
        
    - P-value:
        
        The probability of finding the observed results when the null hypothesis (H0) is **true**
        
        If your P-value is less than the chosen significance level (5%) then you reject the null hypothesis i.e. accept alternative hypothesis (example with coins) 
        
        ```python
        from scipy.stats import norm
        norm(mean1, sd1)
        x1 = 2300
        y1 = norm(mean1, sd1).cdf(x1)
        z1 = norm(mean1, sd1).pdf(x1)
        
        plt.figure(figsize=(12,6))
        ax = plt.gca()
        x = np.linspace(mean1-3*sd1, mean1 + 3*sd1, 100)
        plt.plot(x, norm.pdf(x, mean1, sd1))
        plt.axvline(x1, color='red')
        plt.axhline(z1, color='red')
        plt.title("Normal Distribution N(1774.5, 314.84)")
        print("Probability to have more than {} rating is {}%".format(x1, round(100*y1,2)))
        ```
        
    - Degree of freedom:
        
        $DF = N - P$       (N=sample size, P=Number of parameters/relationships)
        
        ```python
        # Degrees of freedom
        dof = len(d1) + len(d2) - 2
        ```
        
    - Hypothesis testing types:
        - **T-Test** (Student T-Test)
            
            A statistical test that is used to compare the means of two groups
            
            - One sample T-Test
                
                Determines whether the sample mean is statistically different from a known or hypothesized population mean
                
                ```python
                # One sample T-test
                dt['White Rating'].describe()
                ttest, pval = stats.ttest_1samp(dt['White Rating'], 180)
                print("P-values: ",pval)
                
                if pval<0.05:
                    print("reject null hypothesis")
                else:
                    print("accept null hypothesis")
                ```
                
            - Two-sampled T-Test
                
                Compares the means of two independent groups in order to determine whether there is statistical evidence that the associated population means are significantly different
                
                ```python
                # Two sampled T-test
                dt[['White Rating','Black Rating']].describe()
                ttest,pval = stats.ttest_ind(dt['White Rating'],dt['Black Rating'])
                print("P-values: ",pval)
                
                if pval<0.05:
                    print("reject null hypothesis")
                else:
                    print("accept null hypothesis")
                ```
                
            - Paired sampled T-Test
                
                Tests for a significant difference between 2 related variables
                
                ```python
                # Paired sampled T-test
                dt[['White Rating','Black Rating']].describe()
                ttest,pval = stats.ttest_rel(dt['White Rating'],dt['Black Rating'])
                print("P-values: ",pval)
                
                if pval<0.05:
                    print("reject null hypothesis")
                else:
                    print("accept null hypothesis")
                ```
                
            
            **H0:** mean difference between two sample is 0
            
            **H1:** mean difference between two sample is not 0
            
        - **Z-Test**
            
            A statistical test used to determine whether two population means are different when the variances are known and the sample size is large
            
            - Conditions for Z-Test
                - Sample size > 30 (otherwise, use T-test)
                - Independent data points
                - Normally distributed data (for s>30 does not matter)
                - Randomly selected
                - Equal sample sizes
            - One sample Z-Test
                
                Test whether a population parameter is significantly different from some hypothesized value
                
                ```python
                # One sample Z-Test
                print('Test statistic:      ','P-value: ')
                ztest(d1, value=2300)
                ```
                
            - Two-sample Z-Test
                
                Compare the means of two samples to see if it is feasible that they come from the same population
                
                ```python
                # Two sampled Z-Test 
                print('Test statistic:      ','P-value: ')
                ztest(d1,d2,value=0)
                ```
                
            
            **H0:** mean of two group is 0
            
            **H1:** mean of two group is not 0
            
        - **ANOVA Test**
        - **Chi-Square Test**

## Pareto Principle

80% of effects come from 20% of causes (20% → 80%)

- Reference:
    
    [https://towardsdatascience.com/hypothesis-testing-in-machine-learning-using-python-a0dc89e169ce](https://towardsdatascience.com/hypothesis-testing-in-machine-learning-using-python-a0dc89e169ce)
    
    [Walker, H. W.  Degrees of Freedom.  Journal of Educational Psychology.  31(4) (1940) 253-269](http://courses.ncssm.edu/math/Stat_Inst/PDFS/DFWalker.pdf)
    
    [Pandy, S., and Bright, C. L., Social Work Research Vol 32, number 2, June 2008](http://www.montefiore.ulg.ac.be/~kvansteen/MATH0008-2/ac20122013/Class11Dec/Supplementary%20info_AppendixD_DegreesOfFreedom.pdf)
    
    .[https://www.simplypsychology.org/z-score.html](https://www.simplypsychology.org/z-score.html)
