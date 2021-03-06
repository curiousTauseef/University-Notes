STAT231
=======

Statistics.

    Cyntha Struthers
    Section 001
    Email: castruth@gmail.com
    Mondays/Wednesdays/Fridays 1:30pm-2:20pm in STP 105

This is the second time I'm taking this course. The first time around, I received an injury about a month in that made going to this class no longer feasible. This set of notes therefore contains the Spring 2016 version of the course, combined with the Winter 2017 version of the course. Over time, these will be merged together.

# 4/1/17

Course notes are available on LEARN - don't buy the paper copy unless you really want to.

There are i-clicker questions, worth 5% overall. Lowest 25% of clicker answers are not included in grade calculation. There are also 5 assignments, each worth 1%, that teach the use of R. Some tutorials include tests, and there are two midterms (each worth 15%). Final exam worth 50%.

In STAT230, we were given information about the population, and wanted to figure things out about individual samples. In STAT231, we will be learning about the opposite - given information about a sample of the population, what can we figure out about the population?

An **empirical study** is a study in which we learn by observation or experimentation. Empirical studies involve uncertainty by nature - if we run the same experiment multiple times, we are very likely to get results that aren't totally identical. Using the probability tools we learned about in STAT230, we can model this uncertainty and use it to learn more from the study results.

A **population** is a collection of units, like all students taking STAT231, or all the cars on a particular road. A **process** is a system by which units are produced, like a car insurance claim system (it produces car insurance claims as units).

Both of these are collections of units, but processes generally emit units over time, while populations are generally all already there at a certain point in time. For example, a population might be "current STAT231 students", while a process might be "past, present, and future STAT231 students".

;wip: merge this with the 2/5/16 content

# 6/1/17

Read chapter 1 and do the end of chapter problems to review STAT230. Assignment 1 due next Monday, concerns the setup and use of R.

A **variate** is a characteristic of units in a population/process, usually represented as $x$, $y$, or $z$. They can be:

* Continuous - real numbers or intervals of real numbers. For example, height, weight, or component lifetime.
* Discrete - integers or intervals of integers. For example, number of vehicular accidents on a highway, number of i-clicker questions in class.
* Categorical - elements of a set. For example, hair color or dog breed.
* Ordinal - elements of an ordered sequence. For example, a person's health (poor, satisfactory, good, excellent), or survey responses (strongly agree, agree, neutral, disagree, strongly disagree).
* Complex - other types of values. For example, images or written responses.

Knowing the type of a variate helps us choose a good probability model for the data.

An **attribute** of a population/process is a function of a variate that is defined for every unit in the population (not every unit in a study or survey). For example, if we have all students in a class (the population), and each individual student (the unit in the population) has a grade (variate on every unit), then an attribute might be the class average or proportion of students who passed the class (a function of the grade variate). Common attributes are mean/median/mode/variance/proportion.

Empirical studies are either **observational** or **experimental**. Observational empirical studies are those in which information is collected about the population/process without attempting to change any variates of units in the population. When we do change variates, it is an experimental empirical study. Generally, in an experimental empirical study, researchers will do something to one subset of the population, and leave the rest as a control group. Note that even in an observational empirical study, researchers can change variates outside of the context of the study - for example, researchers might ask the entire population to complete a survey, which changes variates like "how fed up is this participant with surveys?", yet this is still an observational study, since the survey is external to the study itself.

**Sample surveys** are observational empirical studied in which we select a representative sample of units from population and determine relevant variates for those units.

Numerical and graphical summaries are used to make sense of large datasets, where we would otherwise not be able to by looking at the numbers directly.

Some numerical summaries include measures of location (sample mean, median, mode), variability/dispersion (sample variance, sample standard deviation, range, interquartile range), and shape (sample skewness, sample kurtosis).

A dataset is a set $y = \set{y_1, \ldots, y_n}$. If $y_i \in \mb{R}$, sample mean is $\overline y = \frac 1 n \sum_{y_i \in y} y_i$, sample median is $\hat{y} = \frac{y_{\left(\floor{\frac n 2}\right)}}{y_{\left(\ceil{\frac n 2}\right)}}$, and sample mode doesn't usually have a widely accepted notation.

The median of a dataset is not unique - a dataset with an even number of elements can have two medians, though usually we just average them to get a single summary value.

The mode is sometimes considered to be multiple values as well when there are several values that are most common, though in this course we consider the mode to not exist when there's no single most common value. Also, the most commonly occurring group/class in grouped data is known as the **sample modal group/class**.

An **order statistic** is just a sorted version of a dataset. It's denoted $\set{y_{(1)}, \ldots, y_{(n)}}$.

# 9/1/17

There's actually a shortcut to get to STP from MC - go left instead of straight and cut through St. Jerome.

Tutorial test next wednesday. One question might be, "a study was conducted in October 2016 on people recovering from heart disease at a particular clinic, where they were asked to complete a questionnaire - what is the process or population?". Any reasonable answer will work: "population of people who attended the clinic in October 2016". Also look into questions like "how does the mean/median/variance change if we do something to the dataset, like add 5 to eah sample?".

A bimodal distribution is one that has what appears to have multiple "humps" on its histogram. A unimodal distribution is one that looks like a single "hump" - a bell-curve-like shape.    

Common numerical summaries we care about are:

* The centre of the data, or **central tendency**:
    * The **sample mean/arithmetic mean**: for a variable $y$, the sample mean is denoted $\overline y = \frac 1 n \sum_{i = 0}^n y_i$.
        * The nice thing about this is that the sum of the deviations from the mean is always 0, so $\sum (y_i - \overline y) = 0$.
        * Under an affine transformation $y_i = ax_i + b$, $\overline y = a \overline x + b$ - the mean can simply be transformed as well.
    * The **geometric mean** is better for logarithmically distributed data: for a variable $y$, the geometric mean is denoted $\overline y = \left(\prod_{i = 0}^n y_i\right)^{\frac 1 n}$.
    * The **harmonic mean** is rarely useful, and is the reciprocal of the arithmetic mean of the reciprocals of a variable.
    * The average is usually the one value that, if applied in the problem's situation, is equivalent to applying all the original values.
    * The **median** is the middle-most observation, or the sample mean of the middlemost observations if there are multiple. Essentially, we arrange the dataset in ascending order, and then pick the middle one.
        * The advantage of medians is that they are less sensitive to outliers than summaries like the sample mean.
        * The concept of the median can be extended to **quartiles** and **percentiles**, and generalized into **quartiles**. While the median is the value such that 50% of the dataset is at or below it, the quartiles and percentiles are a different fraction. Percentiles are represented with $q(p)$ where $0 \le p \le 1$.
        * The first quartile is a value for which 25% of the data is equal or below that value ($q(0.25)$), while the second quartile is 50% ($q(0.5)$), the third 75% ($q(0.75)), and the fourth 100% ($q(1)$).
        * The first percentile is a value for which 1% of the data is equal or below that value, while the second percentile is 2%, the third 3%, and so on.
        * To find the $0 \le p \le 1$ percentile, we take the $p(n + 1)$th value, or average the nearest 2 values if $p(n + 1)$ is not an integer.
    * The **mode** is the observation or observations that occur most often (a dataset can have more than 1 mode). This is often more useful for categorical data, or discrete numerical data with only a few possibilities.
    * The mean, median, and mode aren't always a good measure of centrality. We can combine this with other types of summaries to get a more accurate picture. For example, histograms are a great way to see the entire distribution of the data.
* The volatility, or **dispersion** - how far the values are spread out:
    * The **range of a dataset** is two numbers - the minimum value of the dataset, and the maximum value. This can also be thought of as the zeroth and fourth quartile values. We also often subtract the smaller from the larger to get a single-number range.
    * The **interquartile range** (IQR) is the range of the middle 50% of the dataset - the first quartile value and third quartile value ($q(0.75) - q(0.25)$). It's more robust than the range because it excludes extreme values and outliers.
    * The **sample variance** is defined as $s^2 = \frac{1}{n - 1} \sum_{i = 0}^n \left(y_i - \overline y\right)^2$. Note that the variance is $s^2$, not $s$. Also, the variance of a whole dataset/population $x = \set{x_1, \ldots, x_n}$.
        * This is almost, but not quite, the average of the squared deviation from the mean.
        * Basically, this measures how much the data is spread out from the mean.
        * There's a good reason to divide by $n - 1$ rather than $n$, but we'll cover that later on.
        * Under an affine transformation $y_i = ax_i + b$, $s_y^2 = a^2 s_x^2$ - the squared factor applies to the variance, but not the variance.
        * Another useful formula for the sample variance is $s^2 = \frac 1 {n - 1} \left(\sum y_i^2 - n(\overline y)^2\right)$.
        * Note that the units for the variance is always the square of the units for the samples themselves.
        * Variance is also known as $\mu_2$, the second central moment, $E[(Y - \mu)^2]$.
    * The **standard deviation** is the positive square root of the sample variance, denoted $s$.
        * Why do we square the deviations rather than just adding them up like $\sum_{i = 0}^n (y_i - \overline y)$? The negative deviations and positive deviations would cancel each other out; squaring the values ensures that the standard deviation accumulates to a non-negative value. This also ensures that variance is always symmetric - points above and below the mean both contribute the same amount to the variance.
        * Why do we square the deviations rather than adding their absolute values like $\sum_{i = 0}^n \abs{y_i - \overline y}$? While the absolute value function would still represent variance (the given formula is called the **mean absolute deviation**), it's harder to work with since it's not differentiable. Also, the squared deviation is affected by outliers quadratically while the absolute deviation is only affected linearly, so taking its square root later would give unintuitive results.
        * Under an affine transformation $y_i = ax_i + b$, $s_y = a s_x$ - the factor applies to the standard deviation, but not the intercept (this trivially follows from the formula for the sample variance).
        * If the dataset is unimodal and roughly symmetric, then about 68% of the data will be within 1 standard deviation of the mean, and around 95% of the data will be within 2 standard deviations. This is because the dataset would look somewhat like the normal distribution, which has probability values that give us those numbers. This doesn't work so well for things like bimodal distributions, but is a very common summary in the real world.
    * The **mean absolute deviation** is defined as $\frac{1}{n - 1} \sum_{i = 0}^n \abs{y_i - \overline y}$. This is what we get if we use the absolute value function rather than squaring in the formula for variance. It's relatively rarely used.
* How fat the tails are, or **kurtosis** - the frequency of extreme obserations.
* How symmetric the data is about some point or axis, or **symmetry**.

# 11/1/17

### Symmetry

We also often care about **sample skewness** - how non-symmetric the data is. This measures how different the dataset looks when comparing the side of the mean, mirrored over to the right side. Left-skewing/negative-skewing datasets have distributions that seem to "lean to the right" (they have a long left tail), while right-skewing/positive-skewing distributions seem to "lean to the left" (they have a long right tail).

One way to estimate skewness is to compare the mean and median, measuring $\text{mean} - \text{median}$. If the mean is less than the median, then we'd say the dataset might be left skewed (more of the weight is on the left), if they were equal, we say the dataset is probably symmetric (weight is about the same above and below the mean), and if the mean was greater than the median, then we say the dataset might be right-skewed (more of the weight is on the right side).

The real measure of skewness is $\frac{\frac 1 n \sum \left(y_i - \overline y\right)^3}{\left(\frac 1 n \sum \left(y_i - \overline y\right)^2\right)^{\frac 3 2}}$. We won't be expected to memorize this for the course. The numerator is the the mean cubed error, and the denominator somewhat resembles the population variance. The use of cubing in the numerator preserves the sign of the error, while the denominator has the $\frac 3 2$ exponent in order to scale the numerator to a reasonable range.

A long right tail in a dataset distribution means a positive skewness. A long left tail means a negative skewness. A symmetric distribution has a skewness close to 0. A skewness between -1 and 1 is generally considered "close to 0" for Guassian data.

For example, if a person is diagnosed with a disease that has a mean time of death about 8 months after diagnoses, and survives for several months after diagnosis, then they should hope that the distribution of deaths is more right-skewed, so that most of the probability of death is already behind them.

Skewness is defined as $\frac{\mu_3}{\sigma^3}$, where $\mu_3$ is the third central moment, $E[(Y - \mu)^3]$, and $\sigma$ is the standard deviation.

### Spikiness

**Sample kurtosis** is the measure of how frequent extreme observations are with respect to the normal distribution - how "s". Basically, it checks if the tails of the dataset's distribution are fatter (more extreme observations) or thinner (less extreme observations) than a normal distribution. It can also be said to measure how peaky/pointy the distribution's curve is - too much stuff in the middle means big values greater than 3, too little stuff in the middle means small values less than 3.

Kurtosis is defined as $K = \frac{\frac 1 n \sum \left(y_i - \overline y\right)^4}{\left(\frac 1 n \sum \left(y_i - \overline y\right)^2 \right)^2}$. Note that $K$ must be non-negative. A normal distribution has $K = 3$. If $K > 3$, then the tails of the dataset's distribution are fatter than a normal distribution (there are more extreme observations), and if $K < 3$, then the tails of the dataset's distribution are thinner than a normal distribution (there are fewer extreme observations).

Kurtosis of 0 means the data is all the same - there's no error. The uniform distribution has a kurtosis close to 1.8, because it has no outliers - all of the values are within a couple standard deviations. Values between 2 and 4 are generally considered "close to 3" for Guassian data.

Kurtosis is especially useful in finance, where accurate assessment of risks and expected returns are important. It basically tells us how normal-like our data is - if the kurtosis is very close to 3, we can often assume that the dataset is normally distributed, which is extremely useful for doing statistics with.

Kurtosis is defined as $\frac{\mu_4}{\sigma^4}$, where $\mu_4$ is the fourth central moment, $E[(Y - \mu)^4]$, and $\sigma$ is the standard deviation.

So, to tell if a Guassian model is suitable for a given dataset, we can check if the mean/median are roughly the same, the skewness is close to 0, the kurtosis is close to 3, and about 95% of samples are within 2 standard deviations.

The five-number summary of any dataset is a tuple containing the min, first quartile, median, third quartile, and the max. They're useful for summarizing location and spread, but they can't represent things like bimodal distributions.

Graphical summaries
-------------------

A frequency histogram has rectangles where the height is the number of observations in that bucket. Note that the bucket sizes might not be the same. A **relative frequency** histogram is a frequency histogram where the rectangle heights are scaled based on the bucket width and the total number of observations - $\text{rectangle height} = \frac{\text{number of observations in bucket}}{\text{total number of observations} \times (\text{upper bound of bucket} - \text{lower bound of bucket})}$.

Relative frequency histograms are useful because we can superimpose a probability density function on top of them, since the Y axes match. The sum of the rectangle areas also sum up to 1.

Potential test question: which bucket of a relative frequency histogram does the median fall into? Each percentile of a histogram lies within the first bucket whose value, when added to all previous bucket values, is greater than that percentile. For example, to find the median's bucket, we add bucket heights from left to right until we reach or exceed 0.5.

Empirical CDFs are to CDFs as relative frequency histograms are to PDFs - they're a way to let us graphically compare CDFs to the actual shape of the data. An empirical CDF is a step function that jumps up by $\frac 1 n$ (where $n$ is the number of observations) for each observation, where the X axis is observation values and the Y axis is the cumulative probability. Each percentile can be found in the empirical CDF by taking the X axis value correponding to that percentage of the Y axis. The CDF technically allows us to reproduce the entire dataset, given that it's drawn with enough resolution. The distribution and skewness of the data can be found by looking at the spacing between steps on the X axis - closer spacing on the left side compared to the right side implies the data tends to be positively skewed.

Empirical CDFs are often used in research papers to summarize a dataset, since most datasets are too large to include in the paper.

A **box-and-whiskers plot** is a useful way to show the five number summary that also highlights outliers. It's a 1D plot that looks something like this:

      o   <- each outlier is plotted as a point, while non-outliers are only summarized by the box and whiskers
    
    ----- <- top whisker represents maximum value that isn't an outlier
      |
    ----- <- top of box represents third quartile
    |   |
    |---| <- line in the box represents median
    |   |
    ----- <- bottom of box represents first quartile
      |
    ----- <- bottom whisker represents minimum value that isn't an outlier
    
          <- there might not be any outliers in the dataset

An **outlier** is an observation $x_i$ such that $x_i > Q_3 + 1.5 IQR$ or $x_i < Q_1 - 1.5 IQR$, where $Q_1, Q_3$ are the first and third quartiles, and $IQR$ is the interquartile range $Q_3 - Q_1$. The reason we use 1.5 is because it is convention, and fits the normal distribution relatively well. In other words, an outlier is any point that doesn't fall into the range $[2.5Q_1 - 1.5Q_3, 2.5Q_3 - 1.5Q_1)]$. When we're drawing a box plot, we figure out the quartiles, figure out the ranges in which observations are outliers, and then find the max/min observations that aren't outliers.

Box plots visually show the shape of the data. A box with whiskers that are different lengths is skewed to one side, while the height of the box shows the dispersion.

Box plots tell us the approximate variance, the quartiles, the outliers, and the skewness.

# 13/1/17

**Order statistics** are the sorted observation values.

Consider a dataset containing mortality percentages from cancer types for female humans in Ontario, including lung cancer, stomach cancer, and other. Clearly, the population is human females in Ontario, and the dataset is categorical since the types of cancer are discrete and not ordered.

What kind of graphical summary should we use? News sites might use a pie chart, while a better option might be a bar graph (a bar graph looks a lot like a histogram, but we space out the bars to show that each bar is a different thing).

Graphs should always have appropriate axis bounds, have clearly labelled axes and titles with units, and should only be used when really appropriate.

All of the above summaries are for univariate data. However, bivariate datasets (datasets of the form $\set{\tup{x_1, y_1}, \ldots, \tup{x_n, y_n}}$) are also common. We often graphically summarize these datasets with a scatter plot, which is very useful for showing relationships between the two variates.

The **sample correlation** is a measure of association between two numerical variables. It's defined as $r_{xy} = \frac{\sum \left(x_i - \overline x\right)\left(y_i - \overline y\right)}{\sqrt{\sum \left(x_i - \overline x\right)^2} \sqrt{\sum \left(y_i - \overline y\right)^2}}$. Basically, it's a simplified version of $r_{xy} = \frac{S_{xy}}{\sqrt{S_x S_y}}$, where $S_{x_1 \ldots, x_n}$ is the covariance and $S_x$ is the variance. Note that $-1 \le r_{xy} \le 1$ - values close to 1 means that there's a linear positive correlation, and values close to 0 means that there's almost no correlation. Specifically, sample correlation measures **linear association**.

The sample correlation value is generally not very intuitive to guess - it's easy to find datasets that intuitively have no correlation, that have a large sample correlation. We usually wantto see a scatter plot or something to help verify our results.

An explanatory variate is a variate that's used to explain or determine the distribution in a study. A response variate is a variate that changes in response to the explanatory variate. In other words, the explanatory variate is sort of like the cause, and the response variate is sort of like the effect. For example, if we have a study that asks if clicker grades determine the final STAT231 grade, an explanatory variate might be clicker grades, while the response variate might be the final STAT231 grade. Likewise, if we have a study that asks if final grades explain clicker marks, the final grade would be the explainatory variate, and the clicker grade would be the response variate.

# 16/1/17

Start reading chapter 2. Look up information about tutorial test 1 on Odyssey and on LEARN. Seats are assigned.

Scatter plots work for numeric datasets, like discrete or continuous ones. However, we can't use them for categorical datasets, like the dataset consisting of pairs containing whether a particular student is from Canada, and which university program they're in. For these bivariate categorical datasets, we have different summaries. One of them is a table.

Another way is the relative risk. Suppose we have a dataset $D = \set{\tup{x_1, y_1}, \ldots, \tup{x_n, y_n}}$ with two variables. **Relative risk** a way of summarizing bivariate categorical data - a measurement of how two variables affect each other. Basically, relative risk is $\frac{P(A \mid B)}{P(A \mid \neg B)}$ - the probability of $A$ occurring given that $B$ occurrs over the probability of $A$ occurring given that $B$ does not occur. For independent variables, relative risk is 1. The farther the relative risk is from 1, the more strongly it implies that the variables are associated.

For example, suppose we have categorical variables, $x = \set{\text{smoker}, \text{non-smoker}}$ and $y = \set{\text{lung cancer}, \text{no lung cancer}}$. How do we determine the relationship between these variables, given a dataset of samples?

Statistical Problems
--------------------

We have been doing descriptive statistics so far - describing statistical phenomena that we can see with numerical and graphical techniques to show features of interest (e.g., data mining, data analysis).

Now we will focus on statistical inference - predicting statistical phenomena that we can't see, and generalizing conclusions from studies to the whole process/population (i.e., machine learning). It's a form of inductive reasoning.

The types of problems we'll look at in this course are:

* Estimation problems (what proportion of Ontario residents aged 14-20 smoke? what's the distribution of survival times for HIV patients?)
* Hypothesis testing problems (is it true that a particular cancer treatment works? does so-and-so reduce criminal activity?)
* Prediction problems (what will the value of this stock be at a particular time? how much will a patient's blood pressure drop if they take this drug?)

We use our numerical and graphical summaries to choose a statistical models (mathematical models incorporating probability) to fit the data. For example, we can use statistical models to fit the exchange rate between CAD and Euro, or when earthquakes/natural disasters are likely to happen. Statistical models can even be used to simulate experiments using computers.

A **random variable** is a variable that represents a variate of a randomly selected unit of a population/process.

Statistical models are chosen based on background knowledge about populations (for example, we might have traffic accident data, which can be a Poisson process due to the way the process works), past experience (human height data is usually normally distributed), mathematical convenience (using easy-to-understand and easy-to-use models where possible, like Guassian), and datasets that the models will be tested against (for example, we might be testing against normally distributed data).

In STAT230 we covered a lot of different families of statistical models, like:

* $Y \tilde \mathrm{Binomial}(n, \theta)$ for sequences of $n$ independent success/fail trials each with $\theta$ probability of success, where $Y$ is the number of successes.
* $Y \tilde \mathrm{Poisson}(\theta)$ for random occurences of an event over time averaging $\theta$ per unit time, where $Y$ is the number of event occurences.
* $Y \tilde \mathrm{Exponential}(\theta)$ for random occurences of an event over time averaging $\theta$ per unit time, where $Y$ is the time between event occurences.
* $Y \tilde \mathrm{Guassian}(\theta), \theta = \tup{\mu, \sigma}$ for a wide variety of measures occurring in nature or when many statistical models are summed together, where $Y$ is the value of the quantity.

The PDF of a random variable is $f(y; \theta)$ where $y \in \mathrm(range)(Y)$ - we want to show that the model is dependent on the value of the statistical model family's parameters.

# 18/1/17

Tutorial test 1 was today. Start working on chapter 2 end of chapter problems.

The tutorial test had a few questions about parameter estimation - estimating the parameters for a statistical model based on a sample of a population/process, and quantoify how good those estimates are.

For example, we can estimate $\mu$ in a normal distribution as the sample mean, or $\sigma^2$ as the sample variance. We could also use the sample proportion to estimate $p$ in a Binomial distribution. We figured this out intuitively, but there are formal ways to estimate parameters too. In this course, we'll look at the Method of Maximum Likelihood (MLE), the most often used method. Another common one is the Bayesian Estimation Method.

A **point estimate** of a parameter $\theta$ is an estimate $\hat \theta$ that is the result of a function (called a point estimator) of observed data $y_1, \ldots, y_n$. For example, the sample mean $\overline y$ is a point estimate for the parameter $\mu$ in a Guassian distribution.

Suppose we have a coin that has probability $\theta$ of being heads. How do we estimate $\theta$? Intiutively, to get the **best guess/estimate** we can from the available data, we could use a Binomial model, flip the coin a lot of times, and take the sample proportion to estimate the model's $p$ parameter. We could also keep flipping the coin until we got some number of failures, and use a negative binomial model.

The best guess is not the same thing as a good/reasonable guess - a good/reasonable guess is just one that makes the result we got relatively probable. A bad guess would make the result we got unlikely, like guessing that our coin was fair if we only got 1/100 heads (it's highly improbably that the coin has 50% heads if we observe that).

The best guess of a parameter is the one that is most likely to give us the results we did - the **maximum likelihood estimate** $\hat \theta$ (note that this is the same as the point estimate). For example, if we flip a coin 100 times and get 45 heads, assuming a binomial model, the value of parameter $p$ that is most likely to give us this result is 0.4.

In other words, if we graph $P(Y = 45)$ where $Y ~ \mathrm{Binomial}(n, p)$ over all possible $p$, the graph has a peak at $p = 0.4$. Any procedure that finds the parameter that gives us the maximum likelihood estimate is called a **Method of Maximum Likelihood**. Basically, we decide how plausible each value of $\theta$ is by looking at how probably it makes our observations.

Note that $Y$ is a random variable representing the potential data used to estimate $\theta$, while $y$ is the actual, observed data. Also, the set of possible values of $\theta$ is often called $\Omega$, the parameter space.

Maximum Likelihood Estimates
----------------------------

The **likelihood function** for $\theta$ in a statistical model is defined as $L(\theta; y) = P(Y = y; \theta) = P(Y = y; \theta)$ (the probability of observing data $y$ as a function of $\theta$), sometimes shortened as $L(\theta)$. The **maximum likelihood estimate** is the value of $\theta$ that maximizes the likelihood function. Usually, we do this by differentiating the likelihood function with respect to $\theta$, then setting that derivative to 0 and solving for $\theta$ to find the critical points, then checking to see if they're the global maximum.

### Discrete distributions

For example, the likelihood function for $\theta$ in a binomial model is $L(\theta; y) = P(Y = y; \theta) = {n \choose y} \theta^y (1 - \theta)^{n - y}$ - we just substituted $y$ in place of $k$.

The value of the likelihood function doesn't actually matter, only how large it is relative to other values of the likelihood function. That means we can drop constant factors and terms in the likelihood function, since the maximum would still occur at the same $\theta$ value. For example, we can just as well use $L(\theta; y) = \theta^y (1 - \theta)^{n - y}$.

# 20/1/17

The likelihood function is the probability of observing the data $y$ as a function of the unknown constant $\theta$, scaled by an arbitrary positive constant $k$.

The **relative likelihood function** is defined as $R(\theta; y) = \frac{L(\theta; y)}{L(\hat \theta)}$ - the likelihood function rescaled to be between 0 and 1. This makes comparing likelohood functions easier.

The binomial relative likelihood function is $\frac{\theta^y (1 - \theta)^{n - y}}{\hat \theta (1 - \hat \theta)^{n - y}}$ where $\hat \theta = \frac y n$.

What is the Y axis of the relative likelihood function? It's the **likelihood** of the X axis, not the probability of anything. Likewise, $\theta$ isn't a probability either, just an unknown constant. For example, a value of $\theta$ that makes $R(\theta) = 0.6$ means that $\theta$ is 0.6 times as likely as the maximum likelihood estimate.

A likelihood is different from a probability - **likelihoods are the frequency of certain hypotheses out of all hypotheses, while probabilities are the frequency of certain results out of all results**. Hypotheses are statements like "the unknown parameter $\theta$ is 0.3", and results are something like "we observed "

The **log likelihood function** is just the log of the likelihood function, $l(\theta) = \ln L(\theta)$. Clearly, it has its maximum at the same point, even though the shape is different.

We like the log likelihood function because it's often easier to differentiate, which makes it easier to find the maximum likelihood estimate. Since likelihood functions are often products of lots of factors, using the product rule over and over again quickly gets messy. The log likelihood function can often be written as multiple terms using the $\ln a + \ln b = \ln(ab)$ identity, after which we can differentiate individual terms really easily using the sum rule.

For example, the log likelihood function is $l(\theta; y) = \ln \left(\theta^y (1 - \theta)^{n - y}\right) = y \ln \theta + (n - y) \ln (1 - \theta)$. Differentiating this is a piece of cake, and we get $\frac{\dee}{\dee \theta} l(\theta) = \frac y \theta - \frac{n - y}{1 - \theta} = \frac{y - \theta n}{\theta(1 - \theta)}$. Solving $\frac{y - \theta n}{\theta(1 - \theta)} = 0$, we get $\theta = \frac y n$, as expected.

Suppose we have two independent data sets $y, z$ for two independent random variables $Y, Z$ that share a parameter $\theta$. Clearly, $P(Y = y, Z = z; \theta) = P(Y = y; Z = z; \theta)$, so the combined likelihood is $L(\theta; y) L(\theta; z)$.

# 23/1/17

Suppose $y_1, \ldots, y_n$ is the number of events that occurred at day 1 to $n$, respectively, and a Poisson distribution is appropriate for this dataset. What's the likelihood function for the Poisson distribution $Y \tilde \mathrm{Poisson}(\theta)$, where $\theta$ is the average rate of events?

Intuitively, we know that the average rate of accidents is $\overline y$. Why is this?

Here, the likelihood function is $L(\theta; y_1, \ldots, y_n)P(\text{observing the data } y_1, \ldots, y_n; \theta)$ - the probability of observing the events we did for any given average event rate.

Let $Y_i$ be the number of events recorded on day $i$. Then $L(\theta; y_1, \ldots, y_n) = P(Y_1 = y_1, \ldots, Y_n = y_n; \theta)$. Since each event occurring is independent (one of the assumptions necessary to use the Poisson distribution), $P(Y_1 = y_1, \ldots, Y_n = y_n; \theta) = P(Y_1 = y_1; \theta) \ldots P(Y_n = y_n; \theta) = \prod_{i = 1}^n \frac{\theta^{y_i} e^{-\theta}}{y_i!} = \frac{1}{\prod_{i = 1}^n y_i!} \theta^{\sum_{i = 1}^n y_i} e^{-n\theta}$.

To simplify the equation, we can use the fact that $n\overline y = \sum_{i = 1}^n y_i$. Then, dropping the constant factors and substituting $n \overline y$ in, we get $L(\theta; y_1, \ldots, y_n) = \theta^{n \overline y} e^{-n\theta}$. So, the log likelihood function is $l(\theta; y_1, \ldots, y_n) = n \overline y \log \theta - n \theta$.

Differentiating, $l'(\theta) = \frac{n \overline y}{\theta} - n$, so if $l'(\theta) = 0$, $\theta = \overline y$.

So $\hat \theta = \overline y$ - the sample mean. Also, the relative likelihood function is $\frac{\theta^{n \overline y} e^{-n \theta}}{{\hat \theta}^{n \overline y} e^{-n \hat \theta}}$.

Recommended problem: course notes, example 2.2.4 (page 57-58)

Suppose we have a randomly selected sample $y = \tup{y_1, \ldots, y_n}$ from a random variable $Y = \tup{Y_1, \ldots, Y_n}$. Since each $Y_i$ is independent of the others, $L(\theta; y) = P(Y_1 = y_1, \ldots, Y_n = y_n) = P(Y_1 = y_1) \cdots P(Y_n = y_n)$.

### Continuous distributions

For discrete distributions so far we had $L(\theta; y) = P(Y = y; \theta)$. However, this isn't suitable for continuous random variables, since $P(Y = y; \theta)$ is always 0 (what's the probability that a dart hits a particular exact point?).

How do we construct a likelihood function? The basic idea is that whenever we're taking an observation in real life, we're actually rounding it to some number of decimal places. As a result, we can treat those observations as if they fall into lots of tiny intervals.

Basically, we can replace $P(Y = y)$ with the probability density function (PDF) $f(y; \theta)$. So, $L(\theta; y) = \prod_{i = 1}^n f(y_i; \theta)$.

What's the likelihood function for an exponential distribution $Y \tilde \mathrm{Exponential}(\theta)$ for a dataset $y_1, \ldots, y_n$, where $\theta$ is the mean rate of events? Note that the PDF is $f(y; \theta) = \frac 1 {\theta} e^{-\frac y \theta}$.

Clearly, $L(\theta; y) = \frac{e^{-\frac 1 \theta \sum_{i = 0}^n y_i}}{\theta} = \frac{e^{-\frac{n \overline y}{\theta}}}{\theta}$. Dropping the constant factors, we get $e^{-n} e^{-\frac{n\overline y}{\theta}}$. So $\hat \theta = \overline y$, the sample mean again.

What's the likelihood function for a Gaussian distribution $Y \tilde \mathrm{Guassian}(\mu, \sigma^2)$ for a dataset $y_1, \ldots, y_n$, where $\mu, \sigma^2$ are the mean and variance? Here, we have two parameters for our likelihood function, so we'll need to use multivariate calculus to maximize it.

Details are in the course notes, but $\hat\mu = \overline y$ (the sample mean), and $\sigma^2 = \frac 1 n \sum_{i = 1}^n (y_i - \overline y)^2$ (sort of like the sample variance, but with $n$ rather than $n - 1$ for the denominator).

Also, if we know one of the parameters, we can simply use a partial differential for the likelihood function to maximize the likelihood of the unknown parameter.

# 25/1/17

Midterm next tuesday. Midterm covers everything up to Monday's lecture. Do the practice problems at the end of chapter 2.

The **invariance property** says that if $\hat \theta$ is the MLE of $\theta$, then $g(\hat \theta)$ is the MLE of $g(\theta)$. In other words, to find the maximum likelihood of a function, we just need to find the maximum likelihood of its parameter.

For example, the variance of the binomial distribution is $\sigma^2 = n\theta(1 - \theta)$. Therefore, the MLE of the variance is $n \hat \theta(1 - \hat \theta)$

Aside, if $Y_1, \ldots, Y_n$ are independent random variables with $E[Y_i] = \mu$ and $\mathrm{Var}(Y_i) = \sigma^2$. Then $E[\overline Y] = \my$ and $\mathrm{Var}(\overline Y) = \frac{\sigma^2}{n}$.

When we solve statistical problems, we usually start by fitting a model to the data. After we fit a model, however, we should always check that the model actually represents the distribution well. Some ways we can do this are: superimposing a PDF onto the relative frequency histogram and visually checking similarity, superimposing an empirical CDF on the theoretical CDF and visually checking similarity, checking the QQ-plot for straight lines, and comparing observed frequencies with expected frequencies predicted by the model.

The last one might warrant some explanation. One way to check model fit is to compare how often we see some samples to how often the model says we should see them. For example, for a Poisson model we would first fit it to the dataset using the sample mean as $\theta$. Then, we can calculate the theoretical frequency for an interval $nP(y_1 \le Y \le y_2)$ predicted by the Poisson model, and then compare them with the actual number of times we observe values between $y_1$ and $y_2$. We usually choose around 10-15 intervals for $y_1$ and $y_2$ such that each one contains at least one sample.

---

My previous STAT231 notes follow:

---

# 2/5/16

There are 3 tutorial tests, 2 midterms, and a final exam.

The Challenger space shuttle disaster occurred due to a failed O-ring. However, the right data analysis could have presented this tragedy - there was already enough data available to find this problem, but it wasn't looked at in the right way. Statistics can help prevent this sort of error.

Kansas weather reports, in a study, were found to be accurate about 85% of the time in predicting rain. However, if they just said "it's not going to rain", they would be right 90% of the time. Likewise, ESPN pundits were found to correctly predict the results of games about 48% of the time. Statistics can help us evaluate which analysts and predictors are believable.

Statistics also allows us to evaluate relationships between two things. For example, does smoking cause lung cancer, or does lung cancer cause smoking? Are they related at all?

Statistical data
----------------

There are two main types of data:

* **Numeric data**, like a grade or a width. Numerical data can be:
    * **Discrete** - an element of a countably large set. For example, the number of pennies in a set of coins.
    * **Continuous** - a measure, like height or weight.
* **Categorical data** (area of study, name, etc.). Categorical data can be:
    * **Binary** - falling into two categories.
    * **Ordinal** - there are categories, but there is an underlying order to the data. For example, colors are categorical data, but they have an underlying order on the EM spectrum.

A **transformation** is a function over a variable. A **linear transformation** is one of the form $y = mx + b$. A linear transformation is also known as an **affine transformation**.

A **coding** is a transformation that converts categorical data to numerical data. For example, colors can be assigned numbers, like 0 for red, 1 for orange, and so on.

Summaries
---------

We often want to extract important information about a data set to find its properties. When we do so, we extract **data summaries**. We can do this **numerically** (like finding the mean, stddev, median, etc.) or **graphically** (like making a scatter plot). Numerical summaries tell us about certain fundamental properties of data sets, while graphical summaries tell us the shape of the data.

Suppose we have $100 in a bank account, with 4% interest the first year, 8% the second, and 12% the third. What is the average interest rate?

> Although it would seem at first glance to be 8%, the arithmetic mean doesn't represent the actual average here.
> The average interest rate is the single rate such that, after those 3 years, we would have the same interest gains as we did with this bank account.  
> Let's denote this rate as $x$. Then according to the interest formula, $100(1 + x)^3 = 100 \cdot 1.04 \cdot 1.08 \cdot 1.12$.  
> So $(1 + x)^3 = 1.257984$ and $x = 0.0795059$, or about 0.795%.  
> As it turns out, this is basically the same thing as the geometric mean of the interest rates. In this case, we use the geometric mean since the interest is defined in terms of an enponential function of $n$.  

A car drives from A to B at 40 km/h, and immediately drives back at 60 km/h. What is the average speed of the car?

> Although it would seem at first glance to be 50 km/h, this is not the case, since the car takes less time driving back since it's going faster.  
> Let's denote the distance between A and B as $x$, in km. Then the trip from A to B took $\frac{x}{40}$ hours, and the trip back took $\frac{x}{60}$ hours.  
> Since the total time taken is $\frac{x}{40} + \frac{x}{60}$, the average speed is $\frac{40\frac{x}{40} + 60\frac{x}{60}}{\frac{x}{40} + \frac{x}{60}} = \frac{2}{\frac{1}{40} + \frac{1}{60}}$, or 48 km/h.  
> As it turns out, this is the same thing as the harmonic mean of the speeds.  

# 4/5/16

When we talk about distributions, we oftne picture them as bumps or hills - a high area in the middle, and low areas on the sides. In this picture, the **tails** of a distribution are the low areas on the sides. The concept of tails doesn't really generalize that well, so we'll avoid it for actual formal explanations.

### Centrality

To find a percentile $\beta$, we sort the observations from low to high, and then take the value at the 1-indexed position $\beta(n + 1)$ (or the sample mean of the two values closest to the 1-indexed position $\beta(n + 1)$).

The average/central tendency isn't always the only thing we care about. Suppose you flip a coin $n$ times before a heads appears. If you are paid $2^n$ dollars for doing so, at what price would you pay to play this game?

> Note that a head comes up on the first trial with 1/2 probability, paying out 2 dollars, on the second trial with 1/4 probability, paying out 4 dollars, and so on.  
> So the expected value is $\sum_{i = 1}^\infty i \frac 1 i = \infty$ - the expected value is infinity!  
> However, most people wouldn't even pay 40 dollars to play - it seems like risk/variability is also an important factor in deciding whether to play. This is called St. Peter's Paradox.  

Suppose we have a dataset $x = \set{x_1, \ldots, x_n}$. Suppose we know one observation with value $k$ is unreliable, and we want to discard it from $x$. Can we find the new mean and variance?

> Let $y = \set{y_1, \ldots, y_{n - 1}}$ be the dataset with the unreliable observation removed.  
> Clearly, $\sum y_i = \sum x_i - k$, since we removed only that one element, and since $\sum x_i = n \overline x$, $\sum y_i = \sum x_i - k$.  
> So the sample mean is $\overline y = \frac{\sum x_i - k}{n - 1}$.  
> To find the variance, we can use the alternate form of the variance formula, so $s_y^2 = \frac 1 {(n - 1) - 1} \left(\sum y_i^2 - (n - 1)(\overline y)^2\right)$.  
> Since $\sum y_i = \sum x_i - k$, $\sum y_i^2 = \sum x_i^2 - k^2$.  
> Since we already know $\overline y$, $s_y^2 = \frac{1}{n - 2} \left(\sum x_i^2 - k^2\right) - \frac{\left(\sum x_i - k\right)^2}{n - 1}$.  
> This same technique can be used to calculate the mean and variance of a dataset after adding or removing any number of items to it, without looking at the existing elements of the dataset.  

When you have a dataset with sample mean $\overline x$ and remove an item with value $\overline x$, the mean stays the same, while the variance increases or stays the same.

The batting champion of a baseball season is the player with the highest batting average (probability of hitting the ball in each attempt, times 1000). However, although there have been 13 people with a batting average above 400 before 1941, there have been none after that year. Why does this happen?

In every sport, players have gotten better, absolutely speaking, over time - it doesn't seem like batters are actually getting worse. However, better pitchers, fielders, and managers can make a batter's job a lot harder.

We can actually test this by looking at the batting average for individual average batters over their careers. As it turns out, the average batter's batting average stays about the same over their career. However, the variance in the average player's ball hitting rate shrinks over their careers. Since the average is lower than 400, the shrinking variances mean that the tails in the batting average distribution shrink as well (causing fewer 400+ batting averages). When we become more consistent at hitting the ball at the average rate, that means there are fewer low-performers, but also fewer high-performers.

# 9/5/16

### Association

Suppose we have a dataset $D = \set{\tup{x_1, y_1}, \ldots, \tup{x_n, y_n}}$ with two variables. How do we measure how much these two variables are associated (how is one variable affected by the other)?

For example, suppose we have categorical variables, $x = \set{\text{smoker}, \text{non-smoker}}$ and $y = \set{\text{lung cancer}, \text{no lung cancer}}$. How do we determine the relationship between these variables, given a dataset of samples?

**Relative risk** is a measure of association between two categorical variables. Basically, relative risk is $\frac{P(A \mid B)}{P(A \mid \neg B)}$ - the probability of $A$ occurring given that $B$ occurrs over the probability of $A$ occurring given that $B$ does not occur. For independent variables, relative risk is 1. The farther the relative risk is from 1, the more strongly it implies that the variables are associated.

For two categorical Boolean variables, relative risk is $\frac{\frac{\abs{x \wedge y}}{\abs{x}}}{\frac{\abs{\neg x \wedge y}}{\abs{\neg x}}}$. Expanded into a more useful form, it becomes $\frac{\frac{\abs{x \wedge y}}{\abs{x \wedge y} + \abs{x \wedge \neg y}}}{\frac{\abs{\neg x \wedge y}}{\abs{\neg x \wedge y} + \abs{\neg x \wedge \neg y}}}$.

The sign of $r_{xy}$ (specifically, the sign of the numerator) tells us the direction of the association (positive means variables tend to increase each other, while negative means one tends to increase when the other decreases, and vice versa), and the magnitude of $r$ tells us the strength of the association (0 meaning no association). The denominator ensures that $-1 \le r_{x, y} \le 1$ for any dataset.

For non-linear relationships, the sample correlation coefficient doesn't work so well. For example, for two variables $x, y$ associated by $y = x^2$, the sample correlation coefficient is 0, even though we defined them to be associated by a particular function. A general measure of association for any function (not just linear ones) wouldn't really be meaningful since it's always possible to construct a function to fit a finite dataset. Therefore, all measures of association must be against a particularly chosen class of functions.

For a perfect linear relationship between variables $x, y$, like $y = ax + b$, $r_{xy} = 1$ if $b > 0$, and $r_{xy} = -1$ if $b < 0$. If $b = 0$, then $r_{xy} = 0$.

Since we're assuming our dataset is a sample of the population rather than the population itself, we can only find evidence of associations rather than actual associations themselves. Even if the evidence is very strong, it doesn't say for sure that the association is there. Basically, correlation doesn't imply causation.

# 11/5/16

The reason we have summaries is to figure out the shape of a dataset, and see if we can identify it as following a certain distribution. obtaining the distribution allows us to make predictions about future observations and other useful statistical things.

The **five number summary** of a dataset is a common set of summaries: minimum, first quartile, median, third quartile, and, maximum. Basically, it gives 5 equally spaced points on the histogram.

Since $\sum (x_i - \overline x)(y_i - \overline y) = \sum x_i y_i - n \overline x \overline y$ and $\sum (x_i - \overline x)$, we can write the formula for the correlation coefficient more simply as $\frac{\sum x_i y_i - n \overline x \overline y}{s_x s_y}$.

### Graphical Summaries

One of the most commonly used graphical summaries is the histogram. This is generally used when we have data that can be grouped/binned (organized into disjoint, ordered sets). By "histogram", most people actually mean a **frequency histogram** - a bar plot where the X axis is the bins, and the Y axis is the frequency of observations in each bin.

In contrast, statisticians usually mean **density histograms** when talking about histograms. This is the same thing, except the Y axis is the density of the bin.

The bins in a density histogram don't all have to all have the same range - one can encompass 30 elements, while another might encompass 10. On the plot, the bars don't all have to have the same width. The height of each bar is chosen such that the area of the bar (width of the bin times the height) is equal to the relative frequency of observations that fall into its corresponding bin. The relative frequency is simply $\frac{\text{number of observations in the bin}}{\text{total number of observations}}$.

Note that the total area underneath the density histogram is always 1. Since the total area under a probability density function is also 1, the density histogram is very useful for comparing data with known probability density functions, which we do very often when trying to figure out if a dataset follows a certain distribution. We can't use the usual frequency histogram for this because the total area of the bars doesn't add up to 1.

The **empirical cumulative distribution function** (empirical CDF) for discrete numerical data is a plot where the X axis is the range of possible observation values, and the Y axis is the number of observations that are less than or equal to that value. So for a dataset $x = \set{x_1, \ldots, x_n}$, and $F(x_i) = \abs{\set{v \in x \middle| v \le x_i}}$, the empirical CDF is a plot of $(x_i, F(x_i))$.

The advantage of the empirical CDF is that the percentile values are directly shown on the plot - to find the $n$th percentile, we find the X axis value such that the Y axis is $n$ percent of the maximum Y axis value. For example, to find the median, we would find the Y axis . Also, the mode is the bar that has the largest increase in height compared to the bar on its left.

The Q-Q plot is used for checking if a dataset resembles a normal distribution. This is a plot of the $\alpha$th quantile of the dataset and the $\alpha$th quantile of the Z distribution $N(0, 1)$ (normal distribution with mean 0 and variance 0), for all $\alpha$.

So the median of the dataset is plotted at the X axis value that is the median of the Z distribution, the 95th percentile of the dataset is plotted at the X axis value that is the 95th percentile of the Z distribution, and so on. Basically, this is a plot of $(p \text{th percentile of the Z distribution}, p \text{th percentile of the dataset})$ for all $0 \le p \le 100$. The X axis goes on infinitely in both directions.

If the Q-Q plot resembles a straight line, the dataset resembles a normal distribution. For example, for a normally distributed dataset, it would always be the case that the $p$th percentile of the dataset be a linear function of the $p$th percentile of the Z distribution, so all $(p \text{th percentile of the Z distribution}, p \text{th percentile of the dataset})$ would lie along the same line. For a uniform dataset, we would have a sigmoid-like shape, because the uniform distribution has no tails. For an exponential distribution, we would have a quadratic-looking upward curve, because the exponential distribution has a long right tail.

A **scatter plot** plots two variables against each other, where the X axis is one variable and the Y axis is the other, and points are plotted for each observation. The scatter plot is great for finding patterns in the data, like correlations, grouping, and so on.

# 16/5/16

Quiz about numerical and graphical summaries, I'm writing in DC1351 on Thursday at 3:30PM, for just under 1 hour.

Statistical Analysis
--------------------

A common statistical problem is "Given a population of observations, some of the characteristics of which are unknown, and a sample taken from that population, what can we say about the population by looking just at the sample?".

The PPDAC approach is a sort of template for solving this type of problem: problem, plan, daa, analysis, and conclusion. It's specific to statistics at Waterloo.

* The **problem** can be descriptive (what properties of the population are we interested in?), causative (does X cause Y? how are they related?), and predictive (what will be the result of doing X?).
    * We should also identify and explicitly state the population of interest. A **unit** is a member of the target population, and a **variate** is a characteristic of a unit. An **attribute** is a function over the variates of a collection of units.
    * For example, for finding the presidential approval rating, the target population is the voting population, a unit is any particular voter, a variate is whether they approve of the president, and the proportion of approvals is the attribute.
* The **plan** can be experimental (variables are chosen and controlled when making observations) or observational (variables can't be controlled when making observations).
    * We first choose a study population from which we draw the sample.
    * For the presidental approval rating example, we might choose the subset of voters that have a phone (so we can call them to ask whether they approve).
    * For a new drug being tested, the study population might be a collection of mice, while the target population is all humans - the study population doesn't have to be a subset of the target population.
* The **analysis** involves setting up a statistical model.
    * That means we assume (after obtaining sufficient evidence to back it up) that the data follows some known distribution, possibly with unknown parameters.
    * For the presidental approval rating example, since we can probably assume that the voters are independently making decisions, and that approval is a binary result, we can probably use a binomial distribution.
    * A **bias** is a systematic error in the data. Bias is often caused by measurement error, or selection bias (for example, people only ask for exam remarks if they got less than they feel they deserved, so marking errors might be systematically higher than the true value).
    * When distribution parameters are unknown, we often use Greek letters like $\mu, \sigma, \pi$. When we have sample parameters, which we do know, we often use English letters like $\overline y, s^2, p$, or Greek letters with hats, like $\hat, \mu, \hat \sigma, \hat pi$.
    * The **study error** is the difference between the target population mean and the study population mean for the attribute under study: $\mu_1 - \mu_2$.
    * The **sampling error** is the difference between the sample mean and the study population mean for the attribute under study: $\overline y - \mu_2$.
    * When we're picking a sample, we really want it to represent the population - the properties of the population should be likely to be similar to the properties of the population, to reduce the sampling error as much as possible. We do this by doing **random sampling**. Correctly doing random sampling is critical in avoiding biases, but often depends on characteristics of the problem.
* The **conclusion** is a statement that should be understandable by non-experts.

### Estimation

The **method of maximum likelihood** is finding th most likely value of an unknown parameter of a statistical model, based on a sample. For example:

> We have a coin that either has a 25% chance of getting heads, or a 75% chance of getting heads.  
> Suppose that we flipped the coin 100 times and got 30 heads. Obviously, we would say that it's most likely that the coin has a 25% chance of getting heads.  
> Mentally, it seemed like we asked "what is the probability of 30 heads occuring, if it were the case that the coin had a 25% chance of getting heads?" and "what would that probability be if it were the case that the coin had a 75% chance of getting heads instead?", and then chose the option that maximizes the probability of the event occuring.  

Essentially, the method of maximum likelihood is picking the parameter that makes our observed sample properties most likely.

Formally, given a discrete distribution $Y$ with probability function $f$ and unknown parameter $\theta$, then the **likelihood function** is defined as $L(\theta; y_1, \ldots, y_n) = P(Y_1 = y_1, \ldots, Y_n = y_n) \text{ for the given value of } \theta$.

We then find the value of $\theta$ that maximizes the likelihood function. This value is the **maximum likelihood estimate** (MLE), denoted $\hat \theta$.

Suppose we have a variable $X \tilde \mathrm{Poisson}(\mu)$. What is the MLE of $\mu$?

> Clearly, the probability of each sample observation is $\frac{e^{-\mu} \mu^r}{r!}$ where $r$ is the value of the observation, by the definition of the Poisson distribution.  
> Therefore, $P(Y_1 = y_1, \ldots, Y_n = y_n) = \frac{e^{-\mu} \mu^{x_1}}{x_1!} \cdots \frac{e^{-\mu} \mu^{x_n}}{x_n!}$ (we can just multiply the probabilities together because all of the observations are independent, which we know is the case since we're using the Poisson distribution).  
> We can find the value of $\mu$ that maximizes the likelihood function by taking the logarithm of the whole thing, then finding where the derivative of that is 0. This is a pretty common way to find the max.  
> This value of $\mu$ is the maximum likelihood estimate.  

# 18/5/16

The midterm covers everything up to next week.

Most statistical inference problems start with parameter estimation. We generally start with a guess, and then try to refine it using samples.

A sample $y$ can be thought of as a a set of outcomes of a random variable $Y$, rather than just a set of numbers. This random variable is the **statistical model**.

To review, lowercase Greek letters like $\mu, \theta$ are unknown parameters, lowercase Latin letters like $x, y$ are known/sample parameters, and uppercase Latin letters like $X, Y$ are random variables. These letters correspond: $y_i$ is a single outcome drawn from the random variable $Y_i$.

Likewise, $\overline y$, the sample mean can be thought of as a single outcome of a random variable $\overline Y$. As a result, with multiple samples, we can get a whole distribution of different $\overline y$ values. The unknown population mean is $\mu$, while $\overline Y$ is the random variable with the distribution of all the different $\overline y$ values.

These random variables, like $\overline Y, S^2, \overtilde \pi$ are **estimators**. These sample values, like $\overline y, s^2, \hat \pi$ are **estimates**.

Estimate the approval rating of the president:

> The approval rating is $\pi$, a population parameter that we don't know. Suppose we interview 10 people and get $\set{A, A, D, D, D, D, A, D, D, D}$, where $A$ means approval and $D$ means disapproval.  
> We want to find $\hat \pi$, the MLE of $\pi$. Clearly, $L(\pi; y_1, \ldots, y_n) = \pi \pi (1 - \pi) (1 - \pi) (1 - \pi) (1 - \pi) \pi (1 - \pi) (1 - \pi) (1 - \pi)$, because the probability of each person approving is just $\pi$.  
> So $L(\pi; y_1, \ldots, y_n) = \pi^3 (1 - \pi)^7$, and the log likelihood function is $l(\pi) = \ln(\pi^3 (1 - \pi)^7) = 3 \ln \pi + 7 \ln(1 - \pi)$.  
> Clearly, the value of $\pi$ that maximizes $l(\pi)$ is $\frac{3}{10}$ (by taking the derivative of the log likelihood function). Therefore, the MLE for the approval rating is $\frac{3}{10}$.  

Estimate the average website hits per hour, given a sample of visits over $n$ hours $\set{y_1, \ldots, y_n}$:

> Assume that the data is from a Poisson distribution. Then we want to figure out the distribution parameter $\mu$.  
> Construct the likelihood function $L(\mu; y_1, \ldots, y_n) = \frac{e^{-\mu} \mu^{y_1}}{y_1!} \cdot \ldots \cdot \frac{e^{-\mu} \mu^{y_n}}{y_n!}$.  
> So $L(\mu; y_1, \ldots, y_n) = \frac{e^{-n\mu} \mu^{\sum y_i}}{y_1! \ldots y_n!}$.  
> So the log likelihood function is $l(\mu) = -n \mu + \sum (y_i \ln \mu) - \ln(y_1! \ldots y_n!)$.  
> Differentiating the log likelihood function with respect to $\mu$, we get $-n + \sum \frac{y_i}{\mu}$.  
> By setting the derivative to 0 and solving for $\mu$, we find the maximum value of the log likelihood function at $\hat \mu = \frac 1 n \sum y_i = \overline y$.  
> So if we have a Poisson distribution, the best guess for the parameter $\mu$ is $\overline y$.  

Estimate the probability that a Canadian contestant wins Jeopardy, given a sample of shows Canadian contestants appeared in $\set{y_1, \ldots, y_n}$:

> Clearly, if a contestant appears in $n$ shows, then they won $n$ in a row and lost in the $n + 1$th show.  
> We assume that shows are independent. Therefore, we have a geometric distribution, $Y \tilde \mathrm{Geo}(\pi)$.  
> Recall that for a geometric distribution, $P(Y = y) = \pi^{y - 1}(1 - \pi)$.  
> So $L(\pi; y_1, \ldots, y_n) = \pi^{y_1 - 1}(1 - \pi) \ldots \pi^{y_n - 1}(1 - \pi) = \pi^{\sum y_i - n} (1 - \pi)^n$.  
> So $l(\pi) = (\sum y_i - n) \ln x + n \ln (1 - x)$. Using the usual methods, we find the value of $\pi$ that maximizes $l(\pi)$ to get the MLE of $\pi$.  

Estimate the proportion of left handers in this university:

> Strategy 1: Suppose we got our data by asking people from the population until we got a 10 left handers, and we needed to ask 100 before before there were 10.  
> Strategy 2: Suppose we got our data by asking 100 people from the population, and 10 of them turned out to be left handers.  
> Let $\pi$ be the proportion of left handers. In strategy 1, we have a negative binomial distribution.  
> So in strategy 1, we asked 99 people and got either left or right handed, and the 100th person answered left handed. So the likelihood function is $L(\pi) = {99 \choose 9} \pi^9 (1 - \pi)^{90} \times \pi$.  
> So in strategy 2, we asked all 100 people, and got either left or right handed. So the likelihood function is $L(\pi) = {100 \choose 10} \pi^{10} (1 - \pi)^{90}$.  
> As it turns out, both strategies give the same MLE for $\pi$, $\frac{1}{10}$.  

Note that when we're maximising value of a parameter by taking the derivative, setting it to 0, and solving for the parameter, we have to make sure that the solution is actually the global maximum, not a local maximum or even a minimum. When there are multiple solutions, we must check each of them to find the one that results in the largest likelihood value.

Note that in this course, there will only ever be one solution to the derivative being equal to 0, so we won't have to worry about it.

When we have lots of independent observations, the likelihood function will look like $P(Y_1 = y_1) \cdot \ldots \cdot P(Y_n = y_n)$. So if $n$ is large, we're multiplying a lot of numbers between 0 and 1, which means that the actual likelihood is going to be very small. To deal with this, we sometimes use the **relative likelihood function** $R(\theta) = \frac{L(\theta)}{L(\hat \theta)}$, which always has a maximum of 1 at $\hat \theta$.

Note that this only works for discrete distributions. For continuous ones, we have other tools.

# 25/5/16

;wip: missed due to interviews

# 30/5/16

While the likelihood interval results in a likelihood interval, the sampling distribution gives us a confidence interval.

The theory of estimation deals with problems of the form "estimate an unknown population attribute $\theta$ given a sample drawn from the population, $\set{y_1, \ldots, y_n}$ to get the estimate, $\hat \theta(y_1, \ldots, y_n)$". So far, we've looked at the maximum likelihood estimation technique for solving these for discrete distributions.

Another one is the **method of least squares**, where we find the value of $\theta$ that minimises some squared error function we define - minimizing $\sum E(y_i, \theta)^2$. If $\theta$ is $\mu$ in a normal distribution, then this works out to just be the sample mean, since the error is $y_i - \mu$ and we're minizing \sum (y_i - \mu)^2$. This is not the best method, but it's very popular becuase it's so simple.

So far, when we're estimating we've been trying to get a single value as the estimate. However, it's often more useful to get an interval estimate instead - to find an interval $[A, B]$ such that $\theta$ has at least a given probability of being within this interval. This type of interval problem often shows up as determining margins of error.

One way to obtain an interval estimate is via a relative likelihood function. Unlike the MLE method, where we find the most likely value, we're finding all values of a relative likelihood that exceed a certain probability threshold.

Basically, a $p$-percent likelihood interval for an unknown parameter $\theta$ is $\set{\theta \middle| R(\theta) \ge p}$, where $R(\theta) = \frac{L(\theta)}{L(\hat \theta)}$ is the relative likelihood function and $\hat \theta$ is the MLE. The lowest and highest values in the resulting set is then the likelihood interval. The likelihood interval itself, though, is a set of all values of $\theta$ that satisfy the criteria.

All $p$-percent likelihood intervals are subsets of $q$-percent intervals if $q \le p$ - smaller percentage likelihood intervals are subsets of higher percentage likelihood itnervals. The MLE belongs to all likelihood intervals. The higher the value of $p$, the higher the probability that the true value doesn't fall into the interval. Likelihood intervals are not easy to interpret and don't have an intuitive meaning, so we generally want to use something else.

The **method of sampling distributions** is a better way to estimate intervals. An $n$-percent confidence interval means that we're $n$ percent sure that the value falls withint this interval, which is a lot more intuitive. Given a sample $\set{y_1, \ldots, y_n}$ and a confidence threshold $p$:

1. Identify the pivotal distribution, from the model.
2. Find the endpoints of the pivotal distribution that exceed the confidence threshold $p$.
3. Rearrange the endpoints to construct a coverage interval.
4. Estimate the coverage interval using the sample to get a confidence interval.

;wip: for a normal dist the coverage interval is $(\overline Y - Z^* \frac{\sigma}{\sqrt{n}}, \overline Y + Z^* \frac{\sigma}{\sqrt{n}})$, and the confidence interval is $(\overline y - Z^* \frac{\sigma}{\sqrt{n}}, \overline y + Z^* \frac{\sigma}{\sqrt{n}})$

The confidence interval tells us the probability that the true value falls within a certain range. However, we can also use them to say "the true value must be at most $A$ from our estimate" by choosing our sample size $n$ such that $A = \frac{Z^* \sigma}{\sqrt{n}}$.

The problem with confidence intervals is if we don't know $\sigma$ or if the population isn't normal.

From the central limit theorem, if $n$ is large, and $Y_1, \ldots, Y_n$ are arbitrary distributions with mean $\mu$ and variance $\sigma^2$, then $\overline Y \tilde N(\mu, \frac{\sigma^2}{n})$.

# 1/6/16

;wip: missed first half due to interviews

Continuing with multiple examples of choosing sample sizes such that we have a certain margin of error - making the confidence interval at least a certain size. Interestingly, to get a margin of error of 3% in any population, all we need to do is ask around 1000 people, regardless of how large the population is.

# 5/6/16

I dropped this course due to my injuries, as it became infeasible to continue going to classes.