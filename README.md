# Experimental Design
Within the experimental design layout in this project, there are three lessons:

[I. Concepts of Experiment Design](#I-.-Concepts-of-Experiment-Design) <br>
  + [Type of study](#Types-of-Study)
    + What is an Experiment, Observational Study and Quasi-Experiment?
    + What it means to run an experiment?
    + how this differs from observational studies
  + [Type of Experiment](#-Type-of-Experiments)
    + **Between-subjects design**: one condition per participant  e.g: A/B test
    + **Within-subjects design**: many conditions per participants`
  + [Sampling techniques](#-Type-of-Samplings)
    + Simple Random Sampling
    + Stratified random sampling
  + [Measuring Outcomes](#Measuring-Outcomes)
    + Creating Metrics
    + Controlling Variables
    + Checking Validity
    + Checking Bias
  + [Ethics in Experimental](#-Ethics-in-Experimentation)
  + [SMART Mnemomic for Experimental Design](#SMART-Mnemomic-for-Experimental-Design)
  
[II. Statistical Considerations in Testing](#II-.-Statistical-Considerations-in-Testing) <br>
  + Basic of statistical techniques
    + [Practical Significance](#Practical-Significance)
    + [Experiment Size](#Experiment-Size)
  + Statistical techniques and considerations used when evaluating the data collected during an experiment
    + [Using Dummy Tests](#Using-Dummy-Tests)
    + [Non-Parametric Tests](#Non-Parametric-Tests)
      + [Bootstrapping](#Bootstrapping)
      + [Permutation Tests](#Permutation-Tests)
      + [Rank-Sum Test (Mann-Whitney)](#Rank-Sum-Test)
      + [Sign Test](#Sign-Test)
  + [Analyze Multiple metric](#Analyze-Multiple-metric)
  + [Early Stopping](#Early-Stopping)
    

[III. A/B Testing Case Study](#III.-A/B-Testing-Case-Study)
  + Analyze data related to a change on a web page designed to increase purchasers of software
    + [Scenario Description](#Scenario-Description)
    + [Building a Funnel](#Building-a-Funnel)
      + [An expected flow](#An-expected-flow)
      + [Atypical events](#Atypical-events)
    + [Deciding on Metrics](#Deciding-on-Metrics)
      + [Unit of Diversion](#Unit-of-Diversion)
      + [Potential Metrics](#Potential-Metrics)
    + [Experiment Sizing](#Experiment-Sizing)
    + [Validity, Bias, and Ethics](#Validity,-Bias,-and-Ethics)
    + [Analyze Data](#Analyze-Data)
      + [Invariant Metric](#Invariant-Metric)
      + [Evaluation Metrics](#Evaluation-Metrics)
    + [Draw Conclusions](#Draw-Conclusions)
  + Portfolio Exercise in coordination with Starbucks: 
    + Learn more about how Starbucks conducts experiments. 
    + Get access to data related to a hiring screen that was once conducted by Starbucks to test ideas related to 
  experimental design and statistical metrics.


# I. Concepts of Experiment Design
## Types of Study
There are many ways in which data can be collected in order to test or understand the relationship between two variables 
of interest. These methods can be put into three main bins, based on the amount of control that you hold over the 
variables in play:

+ If you have a lot of control over features, then you have an **experiment**.
+ If you have no control over the features, then you have an **observational study**.
+ If you have some control, then you have a **quasi-experiment**.

While the experiment is the main focus of this project, it's also useful to know about the other types of study so that 
you can use them in effective ways, especially if an experiment cannot be run.

### Experiments
In the social and medical sciences, an experiment is defined by comparing outcomes between two or more groups, and 
ensuring equivalence between the compared groups ***except*** for the manipulation that we want to test. Our interest in an 
experiment is to see if a change in one feature has an effect in the value of a second feature, like seeing if changing 
the layout of a button on a website causes more visitors to click on it. Having multiple groups is necessary in order to 
compare the outcome for when we apply the manipulation to when we do not (e.g. old vs. new website layout), or to 
compare different levels of manipulation (e.g. drug dosages). We also need equivalence between groups so that we can be 
as sure as possible that the differences in the outcomes were only due to the difference in our manipulated feature.

Equivalence between groups is typically carried out through some kind of randomization procedure. A **unit of analysis** is 
the entity under study, like a page view or a user in a web experiment. If we randomly assign our units of analysis to 
each group, then on the whole, we should expect the feature distributions between groups to be about the same. 
This theoretically isolates the changes in the outcome to the changes in our manipulated feature. Of course, we can 
always dig deeper afterwards to see if certain other features worked in tandem with, or against, our manipulation.

### Observational Studies
In an experiment, we exert a lot of control on a system in order to narrow down the changes in our system from one 
source to one output. Observational studies, on the other hand, are defined by a lack of control. Observational studies 
are also known as naturalistic or correlational studies. In an observational study, no control is exerted on the 
variables of interest, perhaps due to ethical concerns or a lack of power to enact the manipulation. This often comes up 
in medical studies. For example, if we want to look at the effects of smoking on health, the potential risks make it 
unethical to force people into smoking behaviors. Instead, we need to rely on existing data or groups to make our 
determinations.

We typically cannot infer causality in an observational study due to our lack of control over the variables. Any 
relationship observed between variables may be due to unobserved features, or the direction of causality might be 
uncertain. (We'll discuss this more later in the lesson.) But simply because an observational study does not imply 
causation does not mean that it is not useful. An interesting relationship might be the spark needed to perform 
additional studies or to collect more data. These studies can help strengthen the understanding of the relationship 
we're interested in by ruling out more and more alternative hypotheses.

### Quasi-Experiments
In between the observational study and the experiment is the quasi-experiment. This is where some, but not all, of the 
control requirements of a true experiment are met. For example, rolling out a new website interface to all users to see 
how much time they spend on it might be considered a quasi-experiment. While the manipulation is controlled by the 
experimenter, there aren't multiple groups to compare. The experimenter can still use the behavior of the population 
pre-change and compare that to behaviors post-change, to make judgment on the effects of the change. However, there is 
the possibility that there are other effects outside of the manipulation that caused the observed changes in behavior. 
For the example earlier in this paragraph, it might be that users would have naturally gravitated to higher usage rates, 
regardless of the website interface.

As another example, we might have two different groups upon which to make a comparison of outcomes, but the original 
groups themselves might not be equivalent. A classic example of this is if a researcher wants to test some new 
supplemental materials for a high school course. If they select two different schools, one with the new materials and 
one without, we have a quasi-experiment since the differing qualities of students or teachers at those schools might 
have an effect on the outcomes. Ideally, we'd like to match the two schools before the test as closely as possible, but 
we can't call it a true experiment since the assignment of student to school can't be considered random.

While a quasi-experiment may not have the same strength of causality inference as a true experiment, the results can 
still provide a strong amount of evidence for the relationship being investigated. This is especially true if some kind 
of matching is performed to identify similar units or groups. Another benefit of quasi-experimental designs is that the 
relaxation of requirements makes the quasi-experiment more flexible and easier to set up.

### Examples
| STUDY DESCRIPTION   |      TYPE OF STUDY |
|----------|:-------------:|
| A blogger tries out a celebrity diet and exercise regimen, and documents their changes in weight and energy. |  Quasi-Experiment |
| An online retailer sends out personal coupon codes to half of their mailing list. |    Experiment   |
| Historic data is collected to compare the effect of local curfew ordinances and downtown foot traffic. | Observational Study |
| A regional store chain tests out a promotional discount at some of their stores to see if it increases sales. |    Quasi-Experiment   |
| Researchers compare the race times for runners based on the type of shoe that they wear. |    Observational Study   |

## Type of Experiments
There are two main types of experiments:
  + **Between-subjects design**: one condition per participant  e.g: A/B test
  + **Within-subjects design**: many conditions per participants

Most of the time, when you think of an experiment, you think of a **between-subjects** experiment. In a between-subjects 
experiment, each unit only participates in, or sees, one of the conditions being used in the experiment. The simplest of 
these has just two groups or conditions to compare. In one group, we have either no manipulation, or maintenance of the 
status quo. This is like providing a known drug treatment, or an old version of a website. This is known as the 
**control group**. The other group includes the manipulation we wish to test, such as a new drug or new website layout. 
This is known as our **experimental group**. We can compare the outcomes between groups (e.g. recovery time or click-through 
rate) in order to make a judgement about the effect of our manipulation. (Since we have an experiment, we'll randomly 
assign each unit to either the control or experimental group.) For web-based experiments, this kind of basic experiment 
design is called an **A/B test**: the "A" group representing the old control, and "B" representing the new experimental 
change.

We aren't limited to just two groups. We could have multiple experimental groups to compare, rather than just one 
control group and one experimental group. This could form an A/B/C test for a web-based experiment, with control group 
"A" and experimental groups "B" and "C".

If an individual completes all conditions, rather than just one, this is known as a **within-subjects** design. 
Within-subjects designs are also known as repeated measures designs. By measuring an individual's output in all 
conditions, we know that the distribution of features in the groups will be equivalent. We can account for individuals' 
aptitudes or inclinations in our analysis. For example, if an individual rates three different color palettes for a 
product, we can know if a high rating for one palette is particularly good compared to the others (e.g. 10 vs. 5, 6) or 
if it's not a major distinction (e.g. 10 vs. 8, 9).

Randomization still has a part in the within-subjects design in the order in which individuals complete conditions. 
This is important to reduce potential bias effects, as will be discussed later in the lesson. One other downside of the 
within-subjects design is that it's not always possible to pull off a within-subjects design. For example, when a user 
visits a website and completes their session, we usually can't guarantee when they'll come back. The purpose of their 
following visit also might not be comparable to their first. It can take a lot more effort in control in order to set 
up an effective within-subjects design.

### Factorial Designs
Factorial designs manipulate the value of multiple features of interest. For example, with two independent manipulations 
"X" and "Y", we have four conditions: "control", "X only", "Y only", "X and Y". Experimental designs where multiple 
features are manipulated simultaneously are more frequently seen in engineering and physical sciences domains, where the 
system units tend to be under stricter control. They're less seen in the social and medical realms, where individual 
differences can impede experiment creation and analysis.


## Type of Samplings
While web and other online experiments have an easy time collecting data, collecting data from traditional methods 
involving real populations is a much more difficult proposition. If you need to perform a survey of a population, it 
could be unreasonable in both time and money costs to try and collect thoughts from every single person in the 
population. This is where sampling comes in. The goal of sampling is to only take a subset of the population, using 
the responses from that subset to make an inference about the whole population. Here, we'll cover two basic 
probabilistic techniques that are commonly used:
1. simple random sampling
2. stratified random sampling

### simple random sampling
The simplest of these approaches is **simple random sampling**. In a simple random sample, each individual in the population 
has an equal chance of being selected. We just randomly make draws from the population until we have the sample size 
desired; your sample size depends on the level of uncertainty you are willing to have about the collected data. Since 
everyone has an equal chance of being drawn, we can expect the feature distribution of selected units to be similar to 
the distribution of the population as a whole. In addition, a simple random sample is easy to set up.

### stratified random sampling
However, it is possible that certain groups are underrepresented in a simple random sample, especially those that make 
up a low proportion of the population. If there are certain rarer subgroups of interest, it can be worth adding one 
additional step and performing **stratified random sampling**. In a stratified random sample, we need to first divide 
the entire population into disjoint groups, or strata. That is, each individual must be a part of one group, and only 
one group. For example, you could divide people by gender (male, female, other), or age (e.g. 18-25, 26-35, etc.).

Then, from each group, you take a simple random sample. In a proportional sample, the sample size is proportional to 
how large the group is in the full population. For example, if you require 1000 data points, and stratified individuals 
of proportion {0.5, 0.3, 0.2}, then you would take 500 people from the first group, 300 from the second, and 200 from 
the third. This guarantees a certain level of knowledge from each subset, and theoretically a more representative 
overall inference on the population.

An alternative approach is to take a ***non-proportional sample*** from each group. For example, we could simply sample 
500 people from each group. Computing the overall statistics in this case requires weighting each group separately, 
but this extra effort offers a higher understanding of each subgroup in a deeper investigation.

### Non-Probabilistic Sampling
As noted at the start, the goal of sampling is to use a subset of the whole population to make inferences about the 
full population, so that we didn't need to record data from everyone. To that end, probabilistic sampling techniques 
were described above to try and obtain a sample that was representative of the whole. However, it's useful to note that 
there also exist non-probabilistic sampling techniques that simplify the sampling process, at the risk of harming the 
validity of the results.

For example, a ***convenience sample*** records information from readily available units. Studies performed in the 
social sciences at colleges often fall into this kind of sampling. The people participating in these tasks are often 
just college students, rather than representatives of the population at large. When performing inferences from this 
type of study, it's important to consider how well your results might apply to the population at large.

One notable example of a convenience sample resulting in a grave error comes from the prediction made by magazine 
"The Literary Digest" on the 1936 U.S. presidential election. While they predicted a healthy victory by candidate 
Alf Landon, the final result ended with a landslide victory by opposing candidate Franklin D. Roosevelt. This major 
error is attributed to their methods capturing a non-representative sample of the population, which included looking 
at the results of a mail-in survey from their magazine readers. Since the mail-ins were voluntary, and the magazine 
subscribers were already not well-representative of the general population, focusing on the people who returned surveys 
gave a large bias toward Landon.


## Measuring Outcomes
The goals of your study may not be the same as the way you evaluate the study's success. Perhaps this is because the 
goal is something that can't be measured directly. Let's say that you have an idea of a website addition that improves 
user satisfaction. How should we measure this? In order to evaluate whether or not this improvement has happened, you 
need to have a way to objectively measure the effect of the addition. For example, you might include a survey to 
random users to have them rate their website experience on a 1-10 scale. If the addition is helpful, then we should 
expect the average rating to be higher for those users who are given the addition, versus those who are not. The 
rating scale acts as a concrete way of measuring user satisfaction. These objective features by which you evaluate 
performance are known as **evaluation metrics**.

As a rule of thumb, it's a good idea to consider the goals of a study separate from the evaluation metrics. 
This provides a couple of useful benefits. First, this makes it clear that the metric isn't the main point of a 
study: it's the implications of the metric relative to the goal that matters. This is especially important if a 
metric isn't directly attached to the goal. For example, measuring students' confidence going into a standardized 
test might be a proxy for the goal of test preparedness, in the absence of being able to get their test scores 
directly or in a timely fashion.

Secondly, having the metric separate from the goal can clarify the purpose of conducting the study or experiment. 
t makes sure we can answer the question of why we want to run a study or experiment. From the above example, 
we aren't measuring confidence just to make people feel good about themselves: we're doing it to try and improve 
their actual performances.

### Alternate Terminology
You might hear other terminology for goals and evaluation metrics than those used in this project. In the social 
sciences, it's common to hear a "construct" as analogous to the goal or objective under investigation, and the 
"operational definition" as the way outcomes are measured. For example, the construct of "reaction time" could be 
operationally defined as "time in milliseconds to click on the correctly indicated button."

In general company operations, you might encounter the terms "key results" (KRs) or "key performance indicators" 
(KPIs) as ways of measuring progress against quarterly or annual "objectives." These objectives and KRs / KPIs serve 
a similar purpose as study goals and evaluation metrics, and might even be driving factors in the creation of an 
experiment.

## Creating Metrics
### Funnels
There are additional concepts and terms that are commonly used for designing experiments, especially for web-based 
studies. In a web experiment, you'll often think of the user **funnel**. A funnel is the flow of steps you expect a user 
of your product to take. Typically, the funnel ends at the place where your main evaluation metric is recorded, and 
includes a step where your experimental manipulation can be performed. For example, we might think of the following 
steps for someone to purchase a product in an online store:
+ Visit the site homepage
+ Search for a desired product or click on a product category
+ Click on a product image
+ Add the product to the cart
+ Check out and finalize purchase

One property to note about user funnels is that typically there will be some dropoff in the users that move from step 
to step. This is much like how an actual funnel narrows from a large opening to a small exit. Outside of an experiment, 
funnels can be used to analyze user flows. Observations from these flows can then be used to motivate experiments to 
try and improve the dropoff rates.

It's also worth noting that the flow through a funnel might be idealized compared to actual user practice. In the above 
xample, users might perform multiple searches in a single session, or want to purchase multiple things. A user might 
access the site through a specific link, subverting the top part of the funnel. Refining the funnel and being specific 
about the kinds of events that are expected can help you create a consistent, reliable design and analysis.

### Unit of Diversion
Once you have a funnel, think about how you can implement your experimental manipulation in the funnel. If the goal 
of the above experiment was to change the way the site looks after a user clicks on a product image, we need to 
figure out a way to assign users to either a control group or experimental group. The place in which you make this 
assignment is known as the **unit of diversion**. Depending on the type of experiment you have, you might have different 
options for diversion, each with its own pros and cons:
+ Event-based diversion (e.g. pageview): Each time a user loads up the page of interest, the experimental condition is 
randomly rolled. Since this ignores previous visits, this can create an inconsistent experience, if the condition 
causes a user-visible change.
+ Cookie-based diversion: A cookie is stored on the user's device, which determines their experimental condition as 
long as the cookie remains on the device. Cookies don't require a user to have an account or be logged in, but can be 
subverted through anonymous browsing or a user just clearing out cookies.
+ Account-based diversion (e.g. User ID): User IDs are randomly divided into conditions. Account-based diversions are 
reliable, but requires users to have accounts and be logged in. This means that our pool of data might be limited in 
scope, and you'll need to consider the risks of using personally-identifiable information.

When it comes to selecting a unit of diversion, the consistency of the experience required can be a major factor to 
consider. For the example provided, we need something more consistent than pageview events. So we then consider the 
cookie-based diversion. If the differences in interface between control and experiment are fairly minor, then we're 
probably okay with cookie-based diversion. But if we think that users will notice the change and we believe that it 
will have a major effect on experience, then we might be inclined to choose an account-based diversion.

### Invariant and Evaluation Metrics
A funnel will also be of benefit when it comes to deciding on metrics to track and analyze as part of the experiment. 
The immediate features that come out of a funnel come in the form of counts and ratios. For example, we could count the 
number of times a search results in a product being selected (a count), or the ratio of selections to searches as 
adjacent slices in the funnel (a ratio).

There are two major categories that we can consider features: as evaluation metrics or as ***invariant metrics***. 
**Evaluation metrics** were mentioned in the previous page as the metrics by which we compare groups. Ideally, we hope 
to see a difference between groups that will tell us if our manipulation was a success. We might want to see an 
increased click-through-rate from search results to products, or an increase in overall revenue. On the flip side, 
**invariant metrics** are metrics that we hope will not be different between groups. Metrics in this category serve 
to check that the experiment is running as expected. For example, in an experiment with cookie-based diversion, 
the number of cookies generated for each condition would be a good invariant metric. Another metric could compare 
the distribution of times in which cookies were generated, to check the bias in the randomization procedure.

We're not limited to tracking just one metric of each type. It's not unusual to track multiple invariant metrics as 
checks on the system's integrity, or multiple evaluation metrics to check different potential facets of a 
manipulation's effects. Don't think that you need to track every possible metric, however. It's better to focus on a 
few key metrics, ignoring features that might be less reliable or highly correlated to other, more informative features. 
We'll discuss statistical considerations surrounding metrics in the next lesson.

## Controlling Variables
If we want to determine causality between two features, there are two main things to control. First of all, we need to 
enact the manipulation on one of the features of interest, so that we know that it is causing the change in the other 
feature. In order to know that it was our manipulated variable and not any other, the second major control point is 
that we want to make sure that all other features are accounted for. These two requirements make the arguments for 
causality much stronger with an experiment compared to a quasi-experiment or observational study.

If we aren't able to control all features or there is a lack of equivalence between groups, then we may be susceptible 
to **confounding variables**. A confounding variable is one that is not part of the variables of interest, but 
nonetheless has an interaction with those variables that we do care about. The correlation observed between two variables might be due to changes in a third variable, 
rather than one causing the other. Another possibility is that there is a causal relationship between the two features, 
but it is an indirect relationship mediated by a third, intermediate variable. This intermediate variable might be a 
larger driver of the changes in the output, with the manipulated variable only having a direct effect on the 
intermediate feature.

For the case where we see a relationship but don't perform a manipulation, we also need to be careful about the 
direction of effect. A relationship between variables "A" and "B" might be due to "A" having an effect on "B" or 
the reverse, "B" having an effect on "A". It might even be the case that "A" and "B" are related through some other 
function like a third variable.

## Checking Validity
When designing an experiment, it's important to keep in mind validity, which concerns how well conclusions can be 
supported. There are three major conceptual dimensions upon which validity can be assessed:
+ Construct Validity
+ Internal Validity
+ External Validity

### Construct Validity
Construct validity is tied to the earlier discussion of how well one's goals are aligned to the evaluation metrics 
used to evaluate it. Poor construct validity can come about when an evaluation metric does not actually measure 
something related to the desired outcome concept. Alternatively, it might be that a metric is ill-constructed, 
such that it does not make clear distinctions on the outcome concept.

### Internal Validity
Internal validity refers to the degree to which a causal relationship can be derived from an experiment's results. 
Controlling for and accounting for other variables is key to maintaining good internal validity. The previous page on 
controlling variables shows ways in which internal validity might not be met.

### External Validity
External validity is concerned with the ability of an experimental outcome to be generalized to a broader population. 
This is most relevant with experiments that involve sampling: how representative is the sample to the whole? 
For studies at academic institutions, a frequent question is if data collected using only college students can be 
generalized to other age or socioeconomic groups.


## Checking Bias
Biases in experiments are systematic effects that interfere with the interpretation of experimental results, 
mostly in terms of internal validity. Just as humans can have a lot of different [biases](https://en.wikipedia.org/wiki/List_of_cognitive_biases), 
there are numerous ways in which an experiment can become unbalanced.

### Sampling Bias
Many experimental biases fall under the sampling bias umbrella. Sampling biases are those that cause our observations 
to not be representative of the population. For example, if assignment to experimental groups is done in an arbitrary 
fashion (as opposed to random assignment or matched groups), we risk our outcomes being based less on the experimental 
manipulation and more on the composition of the underlying groups.

Studies that use surveys to collect data often have to deal with the **self-selection bias**. The types of people that 
respond to a survey might be qualitatively very different from those that do not. A straight average of responses 
would not necessarily reflect the feelings of the full population; weighting responses based on the differences 
between the observed responses and properties of the target population may be needed to come to reasonable conclusions.

One type of sampling bias related to missing data is the **survivor bias**. Survivor bias is one where losses or dropout 
of observed units is not accounted for in an analysis. A key example of this was in British World War II operations 
research, where engineers avoided using survivor bias when they considered where to add armor to their planes. Rather 
than add armor to the spots where returning planes had bullet holes, armor was added to the spots where the planes 
didn't have bullet holes. That's because the planes that took shots to those places probably crashed, due to those 
locations being more vital for maintaining flight, so they didn't "survive" and weren't available for observation.

### Novelty Bias
A novelty effect is one that causes observers to change their behavior simply because they're seeing something new. 
We might not be able to gauge the true effect of a manipulation until after the novelty wears off and population 
metrics return to a level that actually reflects the changes made. This will be important for cases where we want to 
track changes over time, such as trying to get users to re-visit a webpage or use an app more frequently. Novelty is 
probably not a concern (or perhaps what we hope for) when it comes to manipulations that are expected to only have a 
one-shot effect.

### Order Biases
There are a couple of biases to be aware of when running a within-subjects experiment. Recall that in a within-subjects 
design, each participant performs a task or makes a rating in multiple experimental conditions, rather than just one. 
The order in which conditions are completed could have an effect on participant responses. 
A **primacy effect** is one that affects early conditions, perhaps biasing them to be recalled better or to serve as anchor 
values for later conditions. 
A **recency effect** is one that affects later conditions, perhaps causing bias due to being fresher in memory or task 
fatigue.

There are a couple of biases to be aware of when running a within-subjects experiment. Recall that in a within-subjects 
design, each participant performs a task or makes a rating in multiple experimental conditions, rather than just one. 
The order in which conditions are completed could have an effect on participant responses. A primacy effect is one that 
affects early conditions, perhaps biasing them to be recalled better or to serve as anchor values for later conditions. 
A recency effect is one that affects later conditions, perhaps causing bias due to being fresher in memory or task 
fatigue.

### Experimenter Bias
One bias to watch out for, especially in face-to-face experiments, is the experimenter bias. This is where the presence 
or knowledge of the experimenter can affect participants' behaviors or performance. If an experimenter knows what 
condition a participant is in, they might subtly nudge the participant towards their expected result with their 
interactions with the participant. In addition, participants may act differently in the presence of an experimenter, 
to try and act in the 'right' way ??? regardless of if a subject actually knows what the experimenter is looking for or 
not.

This is where design steps like blinding are important. In [blinding](https://en.wikipedia.org/wiki/Blinded_experiment), 
the administrator of a procedure or the participant do not know the condition being used, to avoid that subconscious 
bias from having an effect. In particular, the double-blind design hides condition information from both the 
administrator and participant in order to have a strong rein on experimenter-based biases.

## Ethics in Experimentation
Before you run an experiment, it's important to consider the ethical treatments to which you subject your participants. 
Through the mid-20th century, exposure of questionable and clearly unethical research in the social and medical 
sciences spurred the creation of guidelines for ethical treatment of human subjects in studies and experiments. 
While different fields have developed different standards, they still have a number of major points in common:
+ **Minimize participant risk**: Experimenters are obligated to construct experiments that minimize the risks to 
participants in the study. Risk of harm isn't just in the physical sense, but also the mental sense. If an 
experimental condition has potential to negatively affect a participant's emotions or mentality, then it's worth 
thinking about if the risks are really necessary to perform the desired investigation.
+ **Have clear benefits for risks taken**: In some cases, risks may be unavoidable, and so they must be weighed 
against the benefits that may come from performing the study. When expectations for the study are not clearly 
defined, this throws into question the purpose of exposing subjects to risk. However, if the benefits are shown to
be worth the risks, then it is still possible for the study to be run. This often comes up in medicine, where test 
treatments should show worthy potential against alternative approaches.
+ **Provide informed consent**: Building up somewhat from the previous two points, subjects should be informed of 
and agree to the risks and benefits of participation before they join the study or experiment. This is also an 
opportunity for a participant to opt out of participation. However, there are some cases where deception is 
necessary. This might be to avoid biasing the participant's behavior by seeding their expectations, or if there is a 
dummy task surrounding the actual test to be performed. In cases like this, it's important to include a debriefing 
after the subject's participation so that they don't come away from the task feeling mislead.
+ **Handle sensitive data appropriately**: If you're dealing with identifiable information in your study, make sure 
that you take appropriate steps to protect their anonymity from others. Sensitive information includes things like 
names, addresses, pictures, timestamps, and other links from personal identifiers to account information and history. 
Collected data should be anonymized as much as possible; surveys and census results are often also aggregated to avoid 
tracing outcomes back to any one person.

In the formal sciences, an experiment proposal must go through a review board before it can be run, to ensure that 
ethical principles have been followed. It's likely that you won't have a review board to submit your designs to prior 
to running an experiment. You'll need to evaluate these principles for yourself or with your colleagues to check for 
potential ethical issues before going forward with a study design.

One particular point worth further discussion is that of informed consent for web-based experiments. It's often the case 
that when an experiment is run, users who are included in an experiment often don't know that they're participating in 
an experiment. If a manipulation carries no risk and is so minor as to be hidden away from the user (e.g. a change in 
recommendation engine), perhaps there is no need for informed consent. And when it comes to bias, it's known that 
peoples' behaviors can change when they know they are under observation. In practice, informed consent is often not 
considered when performing a web experiment.

However, informed consent is still an important ethical principle, so there is continuing debate on how to best obtain 
consent for users of a website. One option could be to allow users to opt out of experiment participation, with the 
default user agreement implying consent to participation in unobtrusive experiments. An opposing option would only run 
experiments on users who opt-in to participation, asking the user to set their preference on their initial visit or 
registration. The opt-in approach is more in line with the core idea of informed consent, but also risks fewer users 
available for testing changes.

### Examples in Experimental Ethics
Here are three studies in the social and medical sciences that are often brought up as examples of violations of 
experimental ethics and progenitors of the movement to establish ethics guidelines and boards:
+ [Tuskegee Syphilis Study](https://en.wikipedia.org/wiki/Tuskegee_Syphilis_Study): This study was started in 1932, 
where hundreds of African-American men were tracked over the course of up to forty years to study the natural 
progression of syphilis. The subjects were denied treatment, even after the development of effective syphilis 
treatments like penicillin, and there were active steps taken to hide the truth of their conditions and treatments 
to the subjects.
+ [Milgram obedience study](https://en.wikipedia.org/wiki/Milgram_experiment): During the mid 1960s, psychologist 
Stanley Milgram tested to what degree people follow authority figures. Participants were asked to administer gradually 
increasing shocks to an acting confederate participant at the behest of a lead experimenter based on mistakes made on 
a dummy memory test used as a cover story. While no shocks were actually administered, the study did bing forth 
questions on what constitutes adequate debriefing and what level of information and informed consent needs to be 
provided to a participant in a study that includes necessary deceptive elements.
+ [Stanford Prison Experiment](https://en.wikipedia.org/wiki/Stanford_prison_experiment): This 1971 study conducted 
by psychologist Philip Zimbardo was built to test the dynamics and effects of power differences, using a prison 
scenario. Study volunteers were divided into prisoner and guard groups and their dynamics observed; the study had to 
be ended after less than a week due to the increasingly harsh conditions the 'guards' had settled into treating the 
'prisoners'. It has since served as a major ground for ethical criticisms, violating now-established guidelines around 
risks to participants and clarity of purpose. There are also methodological criticisms, as experimenter biases may have 
shaped the behavior of the 'guards' group in their interactions with 'prisoners'.

And here's a [Techcrunch article](https://techcrunch.com/2014/06/29/ethics-in-a-data-driven-world/) discussing the 
ethics of the 2014-published Facebook study on the impact of changing the affect of posts seen on users' feeds to 
their own posting habits.

## SMART Mnemomic for Experimental Design
There's a mnemonic called **SMART** for teams to plan out projects that also happens to apply pretty well for creating 
experiments. The letters of SMART stand for:
+ **S**pecific: Make sure the goals of your experiment are specific.
+ **M**easurable: Outcomes must be measurable using objective metrics
+ **A**chievable: The steps taken for the experiment and the goals must be realistic.
+ **R**elevant: The experiment needs to have purpose behind it.
+ **T**imely: Results must be obtainable in a reasonable time frame.

There are also other words possible for the mnemonic, such as **A**ctionable and **R**ealistic. Ultimately, however, 
the message is pretty much the same, with the dimensions switched around a bit. Note, however, that the mnemonic 
doesn't cover certain considerations important to experiment design. Considerations of ethical issues or bias will 
need to be considered separately, so don't just take the mnemonic as the final judge of whether your experiment is 
ready to proceed!


# II. Statistical Considerations in Testing
There are more important to statistical consideration in the experimental design, rather than just coming in at the end 
of the study. For example, for setting up the experiment, the point about collecting some data seems a bit vague. 
Specifically, there are some question raisin, like:

How much data will we need before we can judge our experiment's success on solid grounds? Do I need a thousand data
  points, 10,000, or 100,000?

Factors like the size of the effect that we want to see can can have a major effect on how much data we need to collect,
and how long it will take before we get our results. 

This is where we need to have some statistical considerations.
Below are the main points to cover: 
+ How can statistics be used to setup an experiment?
+ What pitfalls are there in analysing an experiment?

### Practical Significance
Even if an experiment result shows a statistically significant difference in an evaluation metric between control and 
experimental groups, that does not necessarily mean that the experiment was a success. If there are any costs associated 
with deploying a change, those costs might outweigh the benefits expected based on the experiment results. 
**Practical significance** refers to the level of effect that you need to observe in order for the experiment to be 
called a true success and implemented in truth. Not all experiments imply a practical significance boundary, but it's 
an important factor in the interpretation of outcomes where it is relevant.

If you consider the confidence interval for an evaluation metric statistic against the null baseline and practical 
significance bound, there are a few cases that can come about.

#### Confidence interval is fully in practical significance region
(Below, m_0 indicates the null statistic value, d_min the practical significance bound, and the blue line the confidence 
interval for the observed statistic. We assume that we're looking for a positive change, ignoring the negative 
equivalent for d_min)

![img1](images/practical_sign1.PNG)

If the confidence interval for the statistic does not include the null or the practical significance level, then the 
experimental manipulation can be concluded to have a statistically and practically significant effect. It is clearest 
in this case that the manipulation should be implemented as a success.

#### Confidence interval completely excludes any part of practical significance region

![img2](images/practical_sign2.PNG)

If the confidence interval does not include any values that would be considered practically significant, this is a clear 
case for us to not implement the experimental change. This includes the case where the metric is statistically 
significant, but whose interval does not extend past the practical significance bounds. With such a low chance of 
practical significance being achieved on the metric, we should be wary of implementing the change.

#### Confidence interval includes points both inside and outside practical significance bounds

![img3](images/practical_sign3.PNG)

This leaves the trickiest cases to consider, where the confidence interval straddles the practical significance bound. 
In each of these cases, there is an uncertain possibility of practical significance being achieved. In an ideal world, 
you would be able to collect more data to reduce our uncertainty, reducing the scenario to one of the previous cases. 
Outside of this, you'll need to consider the risks carefully in order to make a recommendation on whether or not to 
follow through with a tested change. Your analysis might also reveal subsets of the population or aspects of the 
manipulation that do work, in order to refine further studies or experiments.


## Experiment Size
After computing the number of observations needed for an experiment to reliably detect a specified level of 
experimental effect (i.e. statistical power), we need to divide by the expected number of observations per day in 
order to get a minimum experiment length. We want to make sure that an experiment can be completed in a reasonable 
time frame so that if we do have a successful effect, it can be deployed as soon as possible and resources can be 
freed up to run new experiments. What a 'reasonable time frame' means will depend on how important a change will be, 
but if the length of time is beyond a month or two, that's probably a sign that it's too long.

There are a few ways that an experiment's duration can be reduced. We could, of course, change our statistical 
parameters. Accepting higher Type I or Type II error rates will reduce the number of observations needed. So too will 
increasing the effect size: it's much easier to detect larger changes.

Another option is to change the unit of diversion. A 'wider' unit of diversion will result in more observations being 
generated. For example, you could consider moving from a cookie-based diversion in a web-based experiment to an 
event-based diversion like pageviews. The tradeoff is that event-based diversion could create inconsistent website 
experiences for users who visit the site multiple times.

## Using Dummy Tests
When it comes to designing an experiment, it might be useful to run a dummy test as a predecessor to or as part of that 
process. In a dummy test, you will implement the same steps that you would in an actual experiment to assign the 
experimental units into groups. However, the experimental manipulation won't actually be implemented, and the groups 
will be treated equivalently.

There are multiple reasons to run a dummy test: 
1. **Check if an experiment is implemented correctly**: a dummy test can expose if there are any errors in the 
randomization or assignment procedures. A short dummy test can be worth the investment if an invariant metric is found 
to have a statistically significant difference, or if some other systematic bias is identified, because it can help 
avoid larger problems down the line
2. **Collect information about metric behaviour**: a second reason to run a dummy test is to collect data on metrics' 
behaviors. If historic data is not enough to predict the outcome of recorded metrics or allow for experiment duration to 
be computed, then a dummy test can be useful for getting baselines.

Of course, performing a dummy test requires an investment of resources, the most important of which is time. If time 
is of the essence, then you may need to just go ahead with the experiment, keeping an eye on invariant metrics for any 
trouble. An alternative approach is to perform a hybrid test. In the A/B testing paradigm, this can take the form of an 
A/A/B test. That is, we split the data into three groups: two control and one experimental. A comparison between 
control groups can be used to learn about null-environment properties before making inferences on the effect of 
the experimental manipulation.

## Non-Parametric Tests
Up until now, you've been using standard hypothesis tests on means of normal distributions to design and analyze 
experiments. However, it's possible that you will encounter scenarios where you can't rely on only standard tests. 
This might be due to uncertainty about the true variability of a metric's distribution, a lack of data to assume 
normality, or wanting to do inference on a statistic that lacks a standard test. It's useful to know about some 
non-parametric tests, not just as a workaround for cases like this, but also as a second check on your experimental 
results. The main benefit of non-parametric tests is that they don't rely on many assumptions of the underlying 
population, and so can be used in a wider range of circumstances compared to standard tests.

### Bootstrapping
Bootstrapping is used to estimate sampling distributions by using the actually collected data to generate new samples 
that could have been hypothetically collected. In a standard bootstrap, a bootstrapped sample means drawing points 
from the original data with replacement until we get as many points as there were in the original data. 
Essentially, we're treating the original data as the population: without making assumptions about the original 
population distribution, using the original data as a model of the population is the best that we can do.

Taking a lot of bootstrapped samples allows us to estimate the sampling distribution for various statistics on our 
original data. For example, let's say that we wanted to create a 95% confidence interval for the 90th percentile from 
a dataset of 5000 data points. (Perhaps we're looking at website load times and want to reduce the worst cases.) 
Bootstrapping makes this easy to estimate. First of all, we take a bootstrap sample (i.e., draw 5000 points with 
replacement from the original data), record the 90th percentile, and then repeat this a large number of times, 
let's say 100 000. From this bunch of bootstrapped 90th percentile estimates, we form our confidence interval by 
finding the values that capture the central 95% of the estimates (cutting off 2.5% on each tail). Implement this 
operation in the cells below, using the following steps:
+ Initialize some useful variables by storing the number of data points in n_points and setting up an empty list for the bootstrapped quantile values in sample_qs.
+ Create a loop for each trial:
   + First generate a bootstrap sample by sampling from our data with replacement. (random.choice will be useful here.)
   + Then, compute the qth quantile of the sample and add it to the sample_qs list. If you're using NumPy v0.15 or later, you can use the quantile function to get the quantile directly with q; on v0.14 or earlier, you'll need to put q in terms of a percentile and use percentile instead.
+ After gathering the bootstrapped quantiles, find the limits that capture the central c proportion of quantiles to form the estimated confidence interval.

#### Bootstrapping notes
Confidence intervals coming from the bootstrap procedure will be optimistic compared to the true state of the world. This is because there will be things that we don't know about the real world that we can't account for, due to not having a parametric model of the world's state. Consider the extreme case of trying to understand the distribution of the maximum value: our confidence interval would never be able to include any value greater than the largest observed value and it makes no sense to have any lower bound below the maximum observation. Intuitively, however, there's a pretty clear possibility for there to be unobserved values that are larger than the one we've observed, especially for skewed data like shown in the example.

This doesn't override the bootstrap method's advantages, however. The bootstrap procedure is fairly simple and straightforward. Since you don't make assumptions about the distribution of data, it can be applicable for any case you encounter. The results should also be fairly comparable to standard tests. But it does take computational effort, and its output does depend on the data put in. For reference, for the 95% CI on the 90th percentile example explored above, the inferred interval would only capture about 83% of 90th percentiles from the original generating distribution. But a more intricate procedure using a binomial assumption to index on the observed data only does about one percentage point better (84%). And both of these depend on the specific data generated: a different set of 5000 points will produce different intervals, with different accuracies.

### Permutation Tests
The permutation test is a resampling-type test used to compare the values on an outcome variable between two or more 
groups. In the case of the permutation test, resampling is done on the group labels. The idea here is that, under the 
null hypothesis, the outcome distribution should be the same for all groups, whether control or experimental. Thus, 
we can emulate the null by taking all of the data values as a single large group. Applying labels randomly to the data 
points (while maintaining the original group membership ratios) gives us one simulated outcome from the null.

The rest is similar to the sampling approach used in a standard hypothesis test, except that we haven't specified a 
reference distribution to sample from ??? we're sampling directly from the data we've collected. After applying the 
labels randomly to all the data and recording the outcome statistic many times, we compare our actual, observed 
statistic against the simulated statistics. A p-value is obtained by seeing how many simulated statistic values are 
as or more extreme than the one actually observed, and a conclusion is then drawn.

Try implementing a permutation test in the cells below to test if the 90th percentile of times is statistically 
significantly smaller for the experimental group, as compared to the control group:
+ Initialize an empty list to store the difference in sample quantiles as `sample_diffs`.
+ Create a loop for each trial:
   + First generate a permutation sample by randomly shuffling the data point labels. (`random.permutation` will be useful here.)
   + Then, compute the `q`th quantile of the data points that have been assigned to each group based on the permuted labels. Append the difference in quantiles to the `sample_diffs` list.
+ After gathering the quantile differences for permuted samples, compute the observed difference for the actual data. Then, compute a p-value from the number of permuted sample differences that are less than or greater than the observed difference, depending on the desired alternative hypothesis.


### Rank-Sum Test (Mann-Whitney)
The rank-sum test is fairly different from the two previous approaches. There's no resampling involved; the test is performed only on the data present. The rank-sum test, also known as the Mann-Whitney U test, is not a test of any particular statistic, like the mean or median. Instead, it's a test of distributions: let's say we draw one value at random from the populations behind each group. The null hypothesis says that there's an equal chance that the larger value is from the first group as the second group; the alternative hypothesis says that there's an unequal chance, which can be specified as one- or two-tailed.

In order to test this hypothesis, we should look at the data we've collected and see in how many cases values from one group win compared to values in the second. That is, for each data point in the first group, we count how many values in the second group that are smaller than it. (If both values are equal, we count that as a tie, worth +0.5 to the tally.) This number of wins for the first group gives us a value $U$.

It turns out that $U$ is approximately normally-distributed, given a large enough sample size. If we have $n_1$ data points in the first group and $n_2$ points in the second, then we have a total of $n_1 n_2$ matchups and an equivalent number of victory points to hand out. Under the null hypothesis, we should expect the number of wins to be evenly distributed between groups, and so the expected wins are $\mu_U = \frac{n_1 n_2}{2}$. The variability in the number of wins can be found to be the following equation (assuming no or few ties):


    $$ 
    \sigma_U = \sqrt{\frac{n_1n_2(n_1+n_2+1)}{12}}
    $$


These $\mu_U$ and $\sigma_U$ values can then be used to compute a standard normal z-score, which generates a p-value. Implement this method of performing the rank-sum test in the cells below!

### Sign Test
For smaller sample sizes, something like the permutation test can be performed. After exhaustively checking the distribution of victories for every possible assignment of group labels to value, a p-value can be computed for how unusual the actually-observed $U$ was.

Also, there already exists a function in the scipy stats package [`mannwhitneyu`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.mannwhitneyu.html) that performs the Mann Whitney U test. This function considers more factors than the implementation above, including a correction on the standard deviation for ties and a continuity correction (since we're approximating a discretely-valued distribution with a continuous one). In addition, the approach they take is computationally more efficient, based on the sum of value ranks (hence the rank-sum test name) rather than the matchups explanation provided above.

Reference: [Wikipedia](https://en.wikipedia.org/wiki/Mann%E2%80%93Whitney_U_test)


## Analyze Multiple Metrics
If you're tracking multiple evaluation metrics, make sure that you're aware of how the Type I error rates on individual metrics can affect the overall chance of making some kind of Type I error. The simplest case we can consider is if we have _n_ independent evaluation metrics, and that seeing one with a statistically significant result would be enough to call the manipulation a success. In this case, the probability of making at least one Type I error is given by
    
    alpha_over = 1 - (1 - alpha_ind)^n

illustrated in the below image for individual `alpha_ind = 0.05` and `alpha_ind = 0.01`

![img4](images/analyze_mul_metric1.png)

To protect against this, we need to introduce a correction factor on the individual test error rate so that the overall error rate is at most the desired level. A conservative approach is to divide the overall error rate by the number of metrics tested:

    alpha_ind = alpha_over/n

This is known as the **Bonferroni correction**. If we assume independence between metrics, we can do a little bit better 
with the **??id??k correction**:

    alpha_ind = 1 - (1 - alpha_over)^(1/n)

![The ??id??k correction is only slightly higher than the line drawn by the Bonferroni correction.](images/analyze_mul_metric2.png)

In real life, evaluation scenarios are rarely so straightforward. Metrics will likely be correlated in some way, rather than being independent. If a positive correlation exists, then knowing the outcome of one metric will make it more likely for a correlated metric to also point in the same way. In this case, the corrections above will be more conservative than necessary, resulting in an overall error rate smaller than the desired level. (In cases of negative correlation, the true error rate could go either way, depending on the types of tests performed.)

In addition, we might need multiple metrics to show statistical significance to call an experiment a success, or there may be different degrees of success depending on which metrics appear to be moved by the manipulation. One metric may not be enough to make it worth deploying a change tested in an experiment. Reducing the individual error rate will make it harder for a truly significant effect to show up as statistically significant. That is, reducing the Type I error rate will also increase the Type II error rate ??? another conservative shift.

Ultimately, there is a small balancing act when it comes to selecting an error-controlling scheme. Being fully conservative with one of the simple corrections above means that you increase the risk of failing to roll out changes that actually have an impact on metrics. Consider the level of dependence between metrics and what results are needed to declare a success to calibrate the right balance in error rates. If you need to see a significant change in all of your metrics to proceed with it, you might not need a correction factor at all. You can also use dummy test results, bootstrapping, and permutation approaches to plan significance thresholds. Finally, don't forget that practical significance can be an all-important quality that overrides other statistical significance findings.

While the main focus of this page has been on interpretation of evaluation metrics, it's worth noting that these cautions also apply to invariant metrics. The more invariant metrics you test, the more likely it will be that some test will show a statistically significant difference even if the groups tested are drawn from equivalent populations. However, it might not be a good idea to apply a correction factor to individual tests since we want to avoid larger issues with interpretation later on. As mentioned previously, a single invariant metric showing a statistically significant difference is not necessarily cause for alarm, but it is something that merits follow-up in case it does have an effect on our analysis.


## Early Stopping
While an experiment is running, we'll probably be tempted at some point to take a peak at how it's going. 
And if we see from that peak that the experiment is going well, we might be tempted to just end the experiment early 
and deploy the tested changes right away. It's important to resist these temptations since:

There are significant risks for peeking ahead and making an early decision if it is not planned for in the design. If you haven't accounted for the effects of peeking on your error rate, then it's best to resist the temptation to look at the results early, and only perform a final analysis at the end of the experiment. This is another reason why it's important to design an experiment ahead of any data collection.

Note that there are ways of putting together a design to allow for making an early decision on an experiment. In the 
`Early_Stopping.ipynb`, we showed how to treat the problem like a multiple comparisons problem, adjusting the individual 
test-wise error rate to preserve an overall error rate. For continuous tracking, [this page](https://www.evanmiller.org/sequential-ab-testing.html) 
describes a rule of thumb for rate-based metrics, tracking the number of successes in each group and stopping the 
experiment once the counts' sum or difference exceeds some threshold. More generally, tests like the 
[sequential probability ratio test](https://en.wikipedia.org/wiki/Sequential_probability_ratio_test) can be developed 
to make an early stopping decision while an experiment is running, if it looks statistically unlikely for a metric to 
move past or fall back against the statistical significance bound.


# III. A/B Testing Case Study
## Scenario Description
Let's say that you're working for a fictional productivity software company that is looking for ways to increase the
number of people who pay for their software. The way that the software is currently set up, users can download and use
the software free of charge, for a 7-day trial. After the end of the trial, users are required to pay for a license to
continue using the software.

One idea that the company wants to try is to change the layout of the homepage to emphasize more prominently and higher
up on the page that there is a 7-day trial available for the company's software. The current fear is that some potential
users are missing out on using the software because of a lack of awareness of the trial period. If more people download
the software and use it in the trial period, the hope is that this entices more people to make a purchase after seeing
what the software can do.

In this case study, you'll go through steps for planning out an experiment to test the new homepage. You will start by
constructing a user funnel and deciding on metrics to track. You'll also perform experiment sizing to see how long it
should be run. Afterwards, you'll be given some data collected for the experiment, perform statistical tests to analyze
the results, and come to conclusions regarding how effective the new homepage changes were for bringing in more users.

## Building a Funnel
Before we do anything else, the first thing we should do is specify the objective or goal of our study:

> Revising the structure of the homepage will increase the number of people that download the software and, ultimately,
the number of people that purchase a license.

Now, we should think about the activities that a user will take on the site that are relevant to measuring our
objective. This path or funnel will help us figure out how we will create experimental condition groups and which
metrics we'll need to track to measure the experiment's effect. To help you construct the funnel, here's some
information about the way the company's website is structured, and how the software induces users to purchase a license.

The company's website has five main sections:
1. the homepage;
2. a section with additional information, gallery, and examples;
3. a page for users to download the software;
4. a page for users to purchase a license;
5. a support sub-site with documentation and FAQs for the software.

For the software itself, the website requires that users create an account in order to download the software program.
The program is usable freely for seven days after download. When the trial period is hit, the program will bring up a
dialog box that takes the user to the license page. After purchasing a license, the user will receive a unique code
associated with their site account. This code can then be used with the program to register it with that user, and the
program can be used thereafter without issue.

### An expected flow
A straightforward flow might include the following steps:
+ Visit homepage
+ Visit download page
+ Sign up for an account
+ Download software
+ After 7-day trial, software takes user to license-purchase page
+ Purchase license

Note that it is possible for the visitor to drop from the flow after each step, forming a funnel. There might be
additional steps that a user might take between visiting the homepage and visiting the download page that aren't
accounted for in the above flow. For example, someone might want to check out the additional informational pages before
visiting the download page, or even visit the license purchase page to check the license price before even deciding to
download. Considering the amount of browsing that a visitor could perform on the page, it might be simplest just to
track whether or not a user gets to the download page at some point, without worrying about the many paths that they
could have taken to get there.

### Atypical events
There are a few events in the expected flow that might not correspond with the visitors we want to target. For example,
there might be users on the homepage who aren't new users. Users who already have a license might just be visiting the
homepage as a way to access the support sub-site. A user who wants to buy a license might also come in to the license
page through the homepage, rather than directly from the software.

When it comes to license purchasing, it's possible that users don't come back after exactly seven days. Some users
might come back early and make their purchase during their trial period. Alternatively, a user might end up taking more
than seven days to decide to make their purchase, coming back days after the end of the trial. Anticipating scenarios
like this can be useful for planning the design, and coming up with metrics that come as close as possible to measuring
desired effects.

## Deciding on Metrics
From our user funnel, we should consider two things: where and how we should split users into experiment groups, and
what metrics we will use to track the success or failure of the experimental manipulation. The choice of unit of
diversion (the point at which we divide observations into groups) may affect what metrics we can use, and whether the
metrics we record should be considered invariant or evaluation metrics. To start, decide on a unit of diversion and
brainstorm some ideas for metrics to capture.

To be clear, the overall plan is to test the effect of the new homepage using a true experiment; in particular, we'll
be using an A/B testing framework. This means that prospective users should be split into two groups. The control,
or 'A' group, will see the old homepage, while the experimental, or 'B' group, will see the new homepage that
emphasizes the 7-day trial.

### Unit of Diversion
Three main categories of diversion were presented in the course: event-based diversion, cookie-based diversion, and
account-based diversion.

An event-based diversion (like a pageview) can provide many observations to draw conclusions from, but doesn't quite
hit the mark for this case. If the condition changes on each pageview, then a visitor might get a different experience
on each homepage visit. Event-based diversion is much better when the changes aren't as easily visible to users, to
avoid disruption of experience. In addition, pageview-based diversion would let us know how many times the download
page was accessed from each condition, but can't go any further in tracking how many actual downloads were generated
from each condition.

So this leaves the consideration of cookie-based diversion, which feels like the right choice. We can assign a cookie
to each visitor upon their first page hit, which allows them to be separated into the control and experimental groups.
Cookies also allow tracking of each visitor hitting each page, recording whether or not they eventually hit the
download page and then whether or not they actually register an account and perform the download.

Diverting based on account or user ID can be stable, but it's not the right choice in this case. Since visitors only
register after getting to the download page, this is too late to introduce the new homepage to people who should be
assigned to the experimental condition.

That's not to say that the cookie-based diversion is perfect. The usual cookie-based diversion issues apply: we can get
some inconsistency in counts if users enter the site via incognito window, different browsers, or cookies that expire or
get deleted before they make a download. This kind of assignment 'dilution' could dampen the true effect of our
experimental manipulation. As a simplification, however, we'll assume that this kind of assignment dilution will be
small, and ignore its potential effects.

### Potential Metrics
In terms of metrics, we might want to keep track of the number of cookies that are recorded in different parts of the
website. In particular, the number of cookies on the homepage, download page, and account registration page (in order
to actually make the download) could prove useful. We can track the number of licenses purchased through the user
accounts, each of which can be linked back to a particular condition. Though it hasn't been specified, it's also
possible that the software includes usage statistics that we could track.

The above metrics are all based on absolute counts. We could instead perform our analysis on ratios of those counts.
For example, we could be interested in the proportion of downloads out of all homepage visits. License purchases
could be stated as a ratio against the number of registered users (downloads) or the original number of cookies.

Below is some proposed metrics and their corresponding type:

| PROPOSED METRIC  | METRIC TYPE  |
|---|---|
| Number of cookies @ homepage  | Invariant metric  |
| Number of cookies @ download page  |  Neither  |
| Number of user ids / downloads  | Neither  |
| Number of license purchases  | Neither  |
| Mean software usage time during trial  | Neither  |
| Ratio: # downloads / # cookies  | Evaluation metric |
| Ratio: # licenses / # cookies  | Evaluation metric |
| Ratio: # licenses / # user IDs  | Neither  |

There's one invariant metric that really stands out here, and that's the number of cookies that hit the homepage.
If we've done things correctly, each visitor should have an equal chance of seeing each homepage, and that means that
the number of cookies assigned to each group should be about the same. Since visitors come in without any additional
information (e.g. account info) and the change effected by the experimental manipulation comes in right at the start,
there aren't other invariant metrics we should worry about.

Selecting evaluation metrics is a trickier proposition. Count-based metrics at other parts of the process seem like
natural choices: the number of times the software was downloaded and the number of licenses purchased are exactly what
we want to change with the new homepage. The issue is that even though we expect the number of cookies assigned to each
group to be about the same, it's much more likely than not they they won't be exactly the same. Instead, we should
prefer using the download rate (# downloads / # cookies) and purchase rate (# licenses / # cookies) relative to the
number of cookies as evaluation metrics. Using these ratios allows us to account for slight imbalances between groups.

As for the other proposed metrics, the ratio between the number of licenses and number of downloads is potentially
interesting, but not as direct as the other two ratios discussed above. It's possible that the manipulation increases
both the number of downloads and number of licenses, but increases the former to a much higher rate. In this case, the
licenses-to-downloads ratio might be worse off for the new homepage compared to the old, even though the new homepage
has our desired effects. There's no such inconsistency issue with the ratios that use the number of cookies in the
denominator.

Product usage statistics like the average time the software was used in the trial period are potentially interesting
features, but aren't directly related to our experiment. We might not have a strong feeling about what kind of effect
the homepage will have on people that actually download the software. Stated differently, product usage isn't a direct
target of the homepage manipulation. Certainly, these statistics might help us dig deeper into the reasons for observed
effects after an experiment is complete. They might even point toward future changes and experiments to conduct. But in
terms of experiment success, product usage shouldn't be considered an invariant or evaluation metric.

## Experiment Sizing
Now that we have our main metrics selected: number of cookies as an invariant metric, and the download rate and license purchase rate (relative to number of cookies) as evaluation metrics, we should take a look at the feasibility of the experiment in terms of the amount of time it will take to run. We can use historical data as a baseline to see what it might take to detect our desired levels of change.

Recent history shows that there are about 3250 unique visitors per day, with slightly more visitors on Friday through Monday, than the rest of the week. There are about 520 software downloads per day (a .16 rate) and about 65 licenses purchased each day (a .02 rate). In an ideal case, both the download rate and license purchase rate should increase with the new homepage; a statistically significant negative change should be a sign to not deploy the homepage change. However, if only one of our metrics shows a statistically significant positive change we should be happy enough to deploy the new homepage.

Because we have two evaluation metrics of interest, we should make sure that we are choosing an appropriate significance level to conduct each test, in order to preserve a maximum overall Type I error rate of .05. Since we would be happy to deploy the new homepage if either download rate or license purchase rate showed a statistically significant increase, performing both individual tests at a .05 error rate carries the risk of making too many Type I errors. As such, we'll apply the Bonferroni correction to run each test at a .025 error rate so as to protect against making too many errors. If it were the case that we needed to see both metrics with a statistically significant increase, then we wouldn't need to include the correction on the individual tests.

For an overall 5% Type I error rate with Bonferroni correction and 80% power, we should require 6 days (rounded up from 5.55) to reliably detect a 50 download increase per day and 21 days (rounded up from 20.44) to detect an increase of 10 license purchases per day:
+ we'd need at least six days to get the 10 907 visitors in each condition to detect a 0.015 increase in the download rate.
+ We'd need at least 21 days to get the 33 223 visitors in each condition to detect a 0.0031 increase in the download rate. 21 days is actually a convenient number since the three-week timespan helps to account for weekly cycles. In addition, the 21-day data collection period is a short enough timeframe that running the experiment is a reasonable proposition. If the required experiment length were a few weeks longer, then we might have needed to forego measuring the license purchasing rate as a critical metric.

One thing that isn't accounted for in the base experiment length calculations is that there is going to be a delay between when users download the software and when they actually purchase a license. That is, when we start the experiment, there could be about seven days before a user account associated with a cookie actually comes back to make their purchase. Any purchases observed within the first week might not be attributable to either experimental condition. As a way of accounting for this, we'll run the experiment for about one week longer to allow those users who come in during the third week a chance to come back and be counted in the license purchases tally.

## Validity, Bias, and Ethics
Before getting to the data and its analysis, let's review a few of the conceptual points that go into creation of an experiment: validity, bias, and ethics:

+ **Validity**: We probably don't have too much to worry about in terms of validity. For conceptual validity, the evaluation metrics are directly aligned with the experimental goals, no abstraction needed. Internal validity is maintained by performing an experiment with properly-handled randomization and controls. We don't really need to answer to external validity since we're drawing from the full site population and there's no other population we're looking to generalize to.

+ **Biases**: we might think of novelty bias as being a potential issue. However, we don't expect users to come back to the homepage regularly. Downloading and license purchasing are actions we expect to only occur once per user, so there's no real 'return rate' to worry about. One possibility, however, is that if more people download the software under the new homepage, the expanded user base is qualitatively different from the people who came to the page under the original homepage. This might cause more homepage hits from people looking for the support pages on the site, causing the number of unique cookies under each condition to differ. If we do see something wrong or out of place in the invariant metric (number of cookies), then this might be an area to explore in further investigations.

+ **Ethic**: the changes to the homepage should be benign and present no risk to users. Our experiment objectives are also clearly stated. Considering the low risks of the experiment, informed consent is at worst a minor concern; a standard popup to let visitors know that cookies are used to track user experience on the site will likely suffice. The largest ethics principle we should be concerned about is data sensitivity. We shouldn't get any sensitive data out of the cookie assignment and collection, though some information will be collected from the user when they go to download the software. No sensitive data is required for the metrics we've laid out, so what we should do is just aggregate daily visits, downloads, and purchase counts without looking at any individual outcomes.

## Analyze Data
Let's assume that the experiment was given the green light to go ahead, and data was collected for 29 days. As a reminder of the discussion on experiment sizing, it was found that a three-week period was needed to collect enough visitors to achieve our desired power level. Eight additional days of collection were added to allow visitors in the last week to complete their trials and come back to make a purchase ??? if you look at the data linked in the next paragraph, you will see that it takes about eight days before the license purchases reaches its steady level.

The collected data can be found [here](data/homepage_experiment_data.csv). The data file reports the daily counts for the number of unique cookies, number of downloads, and number of license purchases attributed to each group: the experimental group with the new homepage, or the control group with the old homepage. The number of license purchases only includes purchases by users who joined after the start of the experiment, so there will be some time before the counts reach their steady state. As noted earlier, we'll assume that the potentially muddying effects of visits across multiple days, established user visits, and 'lost' cookie tracking will be ignorable, at least unless we find reason to doubt our findings.

### Invariant Metric
First, we should check our invariant metric, the number of cookies assigned to each group. If there is a statistically significant difference detected, then we shouldn't move on to the evaluation metrics right away. We'd need to first dig deeper to see if there was an issue with the group-assignment procedure, or if there is something about the manipulation that affected the number of cookies observed, before we feel secure about analyzing and interpreting the evaluation metrics.

For the test of the invariant metric, number of cookies, there were a larger number of cookies recorded in the experiment group, 47 346 vs. 46 851. This ends up generating a p-value of 0.107 (z = -1.61), which is within a reasonable range under the null hypothesis. Since we lack sufficient reason to reject the null, we can continue on to evaluating the evaluation metrics. (Note that this doesn't mean that there wasn't something actually different about the cookie counts between groups, only that we couldn't detect it if such a difference existed.)


### Evaluation Metrics
Assuming that the invariant metric passed inspection, we can move on to the evaluation metrics: download rate and license purchasing rate. For a refresher, the download rate is the total number of downloads divided by the number of cookies, and the license purchasing rate the number of licenses divided by the number of cookies.

One tricky point to consider is that there is a seven or eight day delay between when most people download the software and when they make a purchase. There's no direct way of attributing cookies all the way through license purchases due to the daily aggregation of results, so the best we can do is to make a justified argument for handling the data. To answer the question below about the license purchasing rate, you should only take the cookies observed through day 21 as the denominator of the ratio as being responsible for all of the license purchases observed. (A more informed model of license purchasing could come up with a different handling of the data, such as including part of the day 22 cookies in the denominator.) (Note that we don't need to perform this kind of correction for the download rate, since the link between homepage visits and downloads is much closer.)

For the first evaluation metric, download rate, there was an extremely convincing effect. An absolute increase from 0.1612 to 0.1805 results in a z-score of 7.87, well beyond any standard significance bound. However, the second evaluation metric, license purchasing rate, only shows a small increase from 0.0210 to 0.0213 (following the assumption that only the first 21 days of cookies account for all purchases). This results in a p-value of 0.398 (z = 0.26).


## Draw Conclusions
Despite the fact that statistical significance wasn't obtained for the number of licenses purchased, the new homepage appeared to have a strong effect on the number of downloads made. Based on our goals, this seems enough to suggest replacing the old homepage with the new homepage. Establishing whether there was a significant increase in the number of license purchases, either through the rate or the increase in the number of homepage visits, will need to wait for further experiments or data collection.

One inference we might like to make is that the new homepage attracted new users who would not normally try out the program, but that these new users didn't convert to purchases at the same rate as the existing user base. This is a nice story to tell, but we can't actually say that with the data as given. In order to make this inference, we would need more detailed information about individual visitors that isn't available. However, if the software did have the capability of reporting usage statistics, that might be a way of seeing if certain profiles are more likely to purchase a license. This might then open additional ideas for improving revenue.






















