# Introduction to Statistics in Python

## Summary Statistics

### Mean and median

In this chapter, you'll be working with the [2018 Food Carbon Footprint
Index](https://www.nu3.de/blogs/nutrition/food-carbon-footprint-index-2018)
from nu3. The `food_consumption` dataset contains information about the
kilograms of food consumed per person per year in each country in each
food category (`consumption`) as well as information about the carbon
footprint of that food category (`co2_emissions`) measured in kilograms
of carbon dioxide, or CO<sub>2</sub>, per person per year in each
country.

In this exercise, you'll compute measures of center to compare food
consumption in the US and Belgium using your `pandas` and `numpy`
skills.

`pandas` is imported as `pd` for you and `food_consumption` is
pre-loaded.

**Instructions**

- Import `numpy` with the alias `np`.
- Create two DataFrames: one that holds the rows of `food_consumption`
  for `'Belgium'` and another that holds rows for `'USA'`. Call these
  `be_consumption` and `usa_consumption`.
- Calculate the mean and median of kilograms of food consumed per person
  per year for both countries.

<!-- -->

- Subset `food_consumption` for rows with data about Belgium and the
  USA.
- Group the subsetted data by `country` and select only the
  `consumption` column.
- Calculate the mean and median of the kilograms of food consumed per
  person per year in each country using `.agg()`.

**Answer**

```{python}

```

### Mean vs. median

In the video, you learned that the mean is the sum of all the data
points divided by the total number of data points, and the median is the
middle value of the dataset where 50% of the data is less than the
median, and 50% of the data is greater than the median. In this
exercise, you'll compare these two measures of center.

`pandas` is loaded as `pd`, `numpy` is loaded as `np`, and
`food_consumption` is available.

**Instructions**

- Import `matplotlib.pyplot` with the alias `plt`.
- Subset `food_consumption` to get the rows where `food_category` is
  `'rice'`.
- Create a histogram of `co2_emission` for rice and show the plot.

**Answer**

```{python}

```

### Quartiles, quantiles, and quintiles

Quantiles are a great way of summarizing numerical data since they can
be used to measure center and spread, as well as to get a sense of where
a data point stands in relation to the rest of the data set. For
example, you might want to give a discount to the 10% most active users
on a website.

In this exercise, you'll calculate quartiles, quintiles, and deciles,
which split up a dataset into 4, 5, and 10 pieces, respectively.

Both `pandas` as `pd` and `numpy` as `np` are loaded and
`food_consumption` is available.

**Instructions**

- Calculate the quartiles of the `co2_emission` column of
  `food_consumption`.

<!-- -->

- Calculate the six quantiles that split up the data into 5 pieces
  (quintiles) of the `co2_emission` column of `food_consumption`.

<!-- -->

- Calculate the eleven quantiles of `co2_emission` that split up the
  data into ten pieces (deciles).

**Answer**

```{python}

```

### Variance and standard deviation

Variance and standard deviation are two of the most common ways to
measure the spread of a variable, and you'll practice calculating these
in this exercise. Spread is important since it can help inform
expectations. For example, if a salesperson sells a mean of 20 products
a day, but has a standard deviation of 10 products, there will probably
be days where they sell 40 products, but also days where they only sell
one or two. Information like this is important, especially when making
predictions.

Both `pandas` as `pd` and `numpy` as `np` are loaded, and
`food_consumption` is available.

**Instructions**

- Calculate the variance and standard deviation of `co2_emission` for
  each `food_category` by grouping and aggregating.
- Import `matplotlib.pyplot` with alias `plt`.
- Create a histogram of `co2_emission` for the `beef` `food_category`
  and show the plot.
- Create a histogram of `co2_emission` for the `eggs` `food_category`
  and show the plot.

**Answer**

```{python}

```

### Finding outliers using IQR

Outliers can have big effects on statistics like mean, as well as
statistics that rely on the mean, such as variance and standard
deviation. Interquartile range, or IQR, is another way of measuring
spread that's less influenced by outliers. IQR is also often used to
find outliers. If a value is less than \\\text{Q1} - 1.5 \times
\text{IQR}\\ or greater than \\\text{Q3} + 1.5 \times \text{IQR}\\, it's
considered an outlier. In fact, this is how the lengths of the whiskers
in a `matplotlib` box plot are calculated.

![Diagram of a box plot showing median, quartiles, and
outliers](https://assets.datacamp.com/production/repositories/5758/datasets/ca7e6e1832be7ec1842f62891815a9b0488efa83/Screen%20Shot%202020-04-28%20at%2010.04.54%20AM.png)

In this exercise, you'll calculate IQR and use it to find some outliers.
`pandas` as `pd` and `numpy` as `np` are loaded and `food_consumption`
is available.

**Instructions**

- Calculate the total `co2_emission` per country by grouping by country
  and taking the sum of `co2_emission`. Store the resulting DataFrame as
  `emissions_by_country`.

**Answer**

```{python}

```

## Random Numbers and Probability

### Calculating probabilities

You're in charge of the sales team, and it's time for performance
reviews, starting with Amir. As part of the review, you want to randomly
select a few of the deals that he's worked on over the past year so that
you can look at them more deeply. Before you start selecting deals,
you'll first figure out what the chances are of selecting certain deals.

Recall that the probability of an event can be calculated by \$\$
P(\text{event}) = \frac{\text{# ways event can happen}}{\text{total \#
of possible outcomes}} \$\$

Both `pandas` as `pd` and `numpy` as `np` are loaded and `amir_deals` is
available.

**Instructions**

- Count the number of deals Amir worked on for each `product` type and
  store in `counts`.

**Answer**

```{python}

```

### Sampling deals

In the previous exercise, you counted the deals Amir worked on. Now it's
time to randomly pick five deals so that you can reach out to each
customer and ask if they were satisfied with the service they received.
You'll try doing this both with and without replacement.

Additionally, you want to make sure this is done randomly and that it
can be reproduced in case you get asked how you chose the deals, so
you'll need to set the random seed before sampling from the deals.

Both `pandas` as `pd` and `numpy` as `np` are loaded and `amir_deals` is
available.

**Instructions**

- Set the random seed to `24`.
- Take a sample of `5` deals **without** replacement and store them as
  `sample_without_replacement`.

**Answer**

```{python}

```

### Creating a probability distribution

A new restaurant opened a few months ago, and the restaurant's
management wants to optimize its seating space based on the size of the
groups that come most often. On one night, there are 10 groups of people
waiting to be seated at the restaurant, but instead of being called in
the order they arrived, they will be called randomly. In this exercise,
you'll investigate the probability of groups of different sizes getting
picked first. Data on each of the ten groups is contained in the
`restaurant_groups` DataFrame.

Remember that expected value can be calculated by multiplying each
possible outcome with its corresponding probability and taking the sum.
The `restaurant_groups` data is available. `pandas` is loaded as `pd`,
`numpy` is loaded as `np`, and `matplotlib.pyplot` is loaded as `plt`.

**Instructions**

- Create a histogram of the `group_size` column of `restaurant_groups`,
  setting `bins` to `[2, 3, 4, 5, 6]`. Remember to show the plot.

<!-- -->

- Count the number of each `group_size` in `restaurant_groups`, then
  divide by the number of rows in `restaurant_groups` to calculate the
  probability of randomly selecting a group of each size. Save as
  `size_dist`.
- Reset the index of `size_dist`.
- Rename the columns of `size_dist` to `group_size` and `prob`.

<!-- -->

- Calculate the expected value of the `size_dist`, which represents the
  expected group size, by multiplying the `group_size` by the `prob` and
  taking the sum.

<!-- -->

- Calculate the probability of randomly picking a group of 4 or more
  people by subsetting for groups of size 4 or more and summing the
  probabilities of selecting those groups.

**Answer**

```{python}

```

### Data back-ups

The sales software used at your company is set to automatically back
itself up, but no one knows exactly what time the back-ups happen. It is
known, however, that back-ups happen exactly every 30 minutes. Amir
comes back from sales meetings at random times to update the data on the
client he just met with. He wants to know how long he'll have to wait
for his newly-entered data to get backed up. Use your new knowledge of
continuous uniform distributions to model this situation and answer
Amir's questions.

**Instructions**

- To model how long Amir will wait for a back-up using a continuous
  uniform distribution, save his lowest possible wait time as `min_time`
  and his longest possible wait time as `max_time`. Remember that
  back-ups happen every 30 minutes.

<!-- -->

- Import `uniform` from `scipy.stats` and calculate the probability that
  Amir has to wait less than 5 minutes, and store in a variable called
  `prob_less_than_5`.

<!-- -->

- Calculate the probability that Amir has to wait more than 5 minutes,
  and store in a variable called `prob_greater_than_5`.

<!-- -->

- Calculate the probability that Amir has to wait between 10 and 20
  minutes, and store in a variable called `prob_between_10_and_20`.

**Answer**

```{python}

```

### Simulating wait times

To give Amir a better idea of how long he'll have to wait, you'll
simulate Amir waiting 1000 times and create a histogram to show him what
he should expect. Recall from the last exercise that his minimum wait
time is 0 minutes and his maximum wait time is 30 minutes.

As usual, `pandas` as `pd`, `numpy` as `np`, and `matplotlib.pyplot` as
`plt` are loaded.

**Instructions**

- Set the random seed to `334`.

**Answer**

```{python}

```

### Simulating sales deals

Assume that Amir usually works on 3 deals per week, and overall, he wins
30% of deals he works on. Each deal has a binary outcome: it's either
lost, or won, so you can model his sales deals with a binomial
distribution. In this exercise, you'll help Amir simulate a year's worth
of his deals so he can better understand his performance.

`numpy` is imported as `np`.

**Instructions**

- Import `binom` from `scipy.stats` and set the random seed to 10.

<!-- -->

- Simulate 1 deal worked on by Amir, who wins 30% of the deals he works
  on.

<!-- -->

- Simulate a typical week of Amir's deals, or one week of 3 deals.

<!-- -->

- Simulate a year's worth of Amir's deals, or 52 weeks of 3 deals each,
  and store in `deals`.
- Print the mean number of deals he won per week.

**Answer**

```{python}

```

### Calculating binomial probabilities

Just as in the last exercise, assume that Amir wins 30% of deals. He
wants to get an idea of how likely he is to close a certain number of
deals each week. In this exercise, you'll calculate what the chances are
of him closing different numbers of deals using the binomial
distribution.

`binom` is imported from `scipy.stats`.

**Instructions**

- What's the probability that Amir closes all 3 deals in a week? Save
  this as `prob_3`.

**Answer**

```{python}

```

### How many sales will be won?

Now Amir wants to know how many deals he can expect to close each week
if his win rate changes. Luckily, you can use your binomial distribution
knowledge to help him calculate the expected value in different
situations. Recall from the video that the expected value of a binomial
distribution can be calculated by \\n \times p\\.

**Instructions**

- Calculate the expected number of sales out of the **3** he works on
  that Amir will win each week if he maintains his 30% win rate.
- Calculate the expected number of sales out of the 3 he works on that
  he'll win if his win rate drops to 25%.
- Calculate the expected number of sales out of the 3 he works on that
  he'll win if his win rate rises to 35%.

**Answer**

```{python}

```

## More Distributions and the Central Limit Theorem

### Distribution of Amir's sales

Since each deal Amir worked on (both won and lost) was different, each
was worth a different amount of money. These values are stored in the
`amount` column of `amir_deals` As part of Amir's performance review,
you want to be able to estimate the probability of him selling different
amounts, but before you can do this, you'll need to determine what kind
of distribution the `amount` variable follows.

Both `pandas` as `pd` and `matplotlib.pyplot` as `plt` are loaded and
`amir_deals` is available.

**Instructions**

- Create a histogram with 10 bins to visualize the distribution of the
  `amount`. Show the plot.

**Answer**

```{python}

```

### Probabilities from the normal distribution

Since each deal Amir worked on (both won and lost) was different, each
was worth a different amount of money. These values are stored in the
`amount` column of `amir_deals` and follow a normal distribution with a
mean of 5000 dollars and a standard deviation of 2000 dollars. As part
of his performance metrics, you want to calculate the probability of
Amir closing a deal worth various amounts.

`norm` from `scipy.stats` is imported as well as `pandas` as `pd`. The
DataFrame `amir_deals` is loaded.

**Instructions**

- What's the probability of Amir closing a deal worth less than \$7500?

<!-- -->

- What's the probability of Amir closing a deal worth more than \$1000?

<!-- -->

- What's the probability of Amir closing a deal worth between \$3000 and
  \$7000?

<!-- -->

- What amount will 25% of Amir's sales be *less than*?

**Answer**

```{python}

```

### Simulating sales under new market conditions

The company's financial analyst is predicting that next quarter, the
worth of each sale will increase by 20% and the volatility, or standard
deviation, of each sale's worth will increase by 30%. To see what Amir's
sales might look like next quarter under these new market conditions,
you'll simulate new sales amounts using the normal distribution and
store these in the `new_sales` DataFrame, which has already been created
for you.

In addition, `norm` from `scipy.stats`, `pandas` as `pd`, and
`matplotlib.pyplot` as `plt` are loaded.

**Instructions**

- Currently, Amir's average sale amount is \$5000. Calculate what his
  new average amount will be if it increases by 20% and store this in
  `new_mean`.
- Amir's current standard deviation is \$2000. Calculate what his new
  standard deviation will be if it increases by 30% and store this in
  `new_sd`.
- Create a variable called `new_sales`, which contains 36 simulated
  amounts from a normal distribution with a mean of `new_mean` and a
  standard deviation of `new_sd`.
- Plot the distribution of the `new_sales` `amount`s using a histogram
  and show the plot.

**Answer**

```{python}

```

### The CLT in action

The central limit theorem states that a sampling distribution of a
sample statistic approaches the normal distribution as you take more
samples, no matter the original distribution being sampled from.

In this exercise, you'll focus on the sample mean and see the central
limit theorem in action while examining the `num_users` column of
`amir_deals` more closely, which contains the number of people who
intend to use the product Amir is selling.

`pandas` as `pd`, `numpy` as `np`, and `matplotlib.pyplot` as `plt` are
loaded and `amir_deals` is available.

**Instructions**

- Create a histogram of the `num_users` column of `amir_deals` and show
  the plot.

**Answer**

```{python}

```

### The mean of means

You want to know what the average number of users (`num_users`) is per
deal, but you want to know this number for the entire company so that
you can see if Amir's deals have more or fewer users than the company's
average deal. The problem is that over the past year, the company has
worked on more than ten thousand deals, so it's not realistic to compile
all the data. Instead, you'll estimate the mean by taking several random
samples of deals, since this is much easier than collecting data from
everyone in the company.

`amir_deals` is available and the user data for all the company's deals
is available in `all_deals`. Both `pandas` as `pd` and `numpy` as `np`
are loaded.

**Instructions**

- Set the random seed to `321`.
- Take 30 samples (with replacement) of size 20 from
  `all_deals['num_users']` and take the mean of each sample. Store the
  sample means in `sample_means`.
- Print the mean of `sample_means`.
- Print the mean of the `num_users` column of `amir_deals`.

**Answer**

```{python}

```

### Tracking lead responses

Your company uses sales software to keep track of new sales leads. It
organizes them into a queue so that anyone can follow up on one when
they have a bit of free time. Since the number of lead responses is a
countable outcome over a period of time, this scenario corresponds to a
Poisson distribution. On average, Amir responds to 4 leads each day. In
this exercise, you'll calculate probabilities of Amir responding to
different numbers of leads.

**Instructions**

- Import `poisson` from `scipy.stats` and calculate the probability that
  Amir responds to 5 leads in a day, given that he responds to an
  average of 4.

<!-- -->

- Amir's coworker responds to an average of 5.5 leads per day. What is
  the probability that she answers 5 leads in a day?

<!-- -->

- What's the probability that Amir responds to 2 or fewer leads in a
  day?

<!-- -->

- What's the probability that Amir responds to more than 10 leads in a
  day?

**Answer**

```{python}

```

### Modeling time between leads

To further evaluate Amir's performance, you want to know how much time
it takes him to respond to a lead after he opens it. On average, he
responds to 1 request every 2.5 hours. In this exercise, you'll
calculate probabilities of different amounts of time passing between
Amir receiving a lead and sending a response.

**Instructions**

- Import `expon` from `scipy.stats`. What's the probability it takes
  Amir less than an hour to respond to a lead?

<!-- -->

- What's the probability it takes Amir more than 4 hours to respond to a
  lead?

<!-- -->

- What's the probability it takes Amir 3-4 hours to respond to a lead?

**Answer**

```{python}

```

## Correlation and Experimental Design

### Relationships between variables

In this chapter, you'll be working with a dataset `world_happiness`
containing results from the [2019 World Happiness
Report](https://worldhappiness.report/ed/2019/). The report scores
various countries based on how happy people in that country are. It also
ranks each country on various societal aspects such as social support,
freedom, corruption, and others. The dataset also includes the GDP per
capita and life expectancy for each country.

In this exercise, you'll examine the relationship between a country's
life expectancy (`life_exp`) and happiness score (`happiness_score`)
both visually and quantitatively. `seaborn` as `sns`,
`matplotlib.pyplot` as `plt`, and `pandas` as `pd` are loaded and
`world_happiness` is available.

**Instructions**

- Create a scatterplot of `happiness_score` vs. `life_exp` (without a
  trendline) using `seaborn`.
- Show the plot.

**Answer**

```{python}

```

### What can't correlation measure?

While the correlation coefficient is a convenient way to quantify the
strength of a relationship between two variables, it's far from perfect.
In this exercise, you'll explore one of the caveats of the correlation
coefficient by examining the relationship between a country's GDP per
capita (`gdp_per_cap`) and happiness score.

`pandas` as `pd`, `matplotlib.pyplot` as `plt`, and `seaborn` as `sns`
are imported, and `world_happiness` is loaded.

**Instructions**

- Create a `seaborn` scatterplot (without a trendline) showing the
  relationship between `gdp_per_cap` (on the x-axis) and `life_exp` (on
  the y-axis).
- Show the plot

**Answer**

```{python}

```

### Transforming variables

When variables have skewed distributions, they often require a
transformation in order to form a linear relationship with another
variable so that correlation can be computed. In this exercise, you'll
perform a transformation yourself.

`pandas` as `pd`, `numpy` as `np`, `matplotlib.pyplot` as `plt`, and
`seaborn` as `sns` are imported, and `world_happiness` is loaded.

**Instructions**

- Create a scatterplot of `happiness_score` versus `gdp_per_cap` and
  calculate the correlation between them.

<!-- -->

- Add a new column to `world_happiness` called `log_gdp_per_cap` that
  contains the log of `gdp_per_cap`.
- Create a `seaborn` scatterplot of `happiness_score` versus
  `log_gdp_per_cap`.
- Calculate the correlation between `log_gdp_per_cap` and
  `happiness_score`.

**Answer**

```{python}

```

### Does sugar improve happiness?

A new column has been added to `world_happiness` called
`grams_sugar_per_day`, which contains the average amount of sugar eaten
per person per day in each country. In this exercise, you'll examine the
effect of a country's average sugar consumption on its happiness score.

`pandas` as `pd`, `matplotlib.pyplot` as `plt`, and `seaborn` as `sns`
are imported, and `world_happiness` is loaded.

**Instructions**

- Create a `seaborn` scatterplot showing the relationship between
  `grams_sugar_per_day` (on the x-axis) and `happiness_score` (on the
  y-axis).
- Calculate the correlation between `grams_sugar_per_day` and
  `happiness_score`.

**Answer**

```{python}

```
