# The role of the frequentist framework, p-values, statistical (NHST) and practical significance (MCID) in randomised controlled (clinical) trials

_**Despite frequent calls to “ban p-values” and “ditch/abandon statistical significance,” the NHST framework remains the primary (though not the only; Bayesians mark their presence as well) “engine” of inference in phase-3 randomised controlled clinical trials. Why is this and how is it used, given the well-known and - unfortunately - frequent abuses of this framework? What specific steps are taken to achieve reliable inference?**_

![obraz](https://github.com/user-attachments/assets/48a0cb86-fe50-4bf3-9e96-5ab5bb8c32ee)

## 1. Introduction: different goals --- different needs

**In exploratory studies** we are mostly interested **in learning new
things, building our knowledge base**. We may just explore a new *terra
incognita* --- with no or very limited prior knowledge about it, just
like a toddler explores the unknown world of their parents. So we are
interested in everything: signs and magnitudes of effects, plausible
ranges of values it may take (it's typical, most common domain),
relationships of any kind, patterns...

**We don't want any limiting thresholds here**, we want the **full
picture**, a **perspective as wide as possible**, **not collapsed**
("compressed") to just single numbers. When we describe the data --- we
don't report just mean, rather a full set of useful descriptive
measures, describing locations, dispersions, shapes, modes, changes over
time. We want full ranges, not just their "midpoints", and ideally not
even ranges --- but **the entire empirical distributions**, with all
their details visible (modes, shapes, change over time).

Such studies may neither be planned nor designed (also for statistical
power), analyses may be decided and performed post-hoc (as the data are
obtained). This is where the Tukey's "all-pairwise" analyses are so
commonly performed --- without a certainty what is specifically
important and what is meaningless. This will be decided a bit later...
We also do not care much about controlling all those "type-1" and
"type-2" errors. We also understand that [in low-powered studies we may
experience also the type-S (sign) and type-M (magnitude)
errors](https://mzloteanu.substack.com/p/what-not-to-do-with-non-null-results).
We may find a lot of spurious patterns and fake patterns of no practical
importance. We may have no sufficient ground for making even smallest
causal statements ("what causes what").

**No surprise then that thresholds may not be welcomed at this stage!**
OK, we may want a kind of a "flagging tool" that will "mark" potentially
interesting patterns and hypotheses for further research. We may decide
to confirm (some of) them in dedicated, planned, randomised studies.
When we finally decide to test some hypotheses, we may try different
priors (Bayesian approach) and different tests (means? medians? other
kind of characteristics?). We may prefer weaker controlling for false
findings (if any) --- FDR rather than FWER.

In such studies we may find lots of outcomes negligible from the
practical perspective, yet highly statistically discernible (very low
p-values). Well, is this surprising? **This is precisely how people do
every day:** the more information they have, the more certain they are,
so even smallest patterns may look "convincing". It's just like using a
detector, which sensitivity is driven by the sample size. And the
contrary --- if you have only a small piece of information, it's rather
difficult to make a strong convincing statements about the phenomenon
without additional knowledge (*although people often behave as if they
possessed the knowledge and form strong opinions under limited
knowledge...*).

In both cases we need something more: **the context**. The context that
says: "*this is discernible, OK, but NOT important*" or "*this seems a
noise, but MAY be worth noticing"*. And this can be done in both
frequentist and Bayesian frameworks (yes, frequentists can combine
knowledge --- but you might have been lied they cannot...). **But it
requires you to KNOW what is important and what is garbage.** You cannot
make information out of nowhere, **so either you have an external source
of it or you ASSUME something**. Without that --- neither frequentist
nor Bayesian framework will do this magic for you, regardless of the
type of study, exploratory, A/B online testing, whatever.

If you spend most of our time in such studies, p-values and statistical
significance are not your primary tool (if ever). If inference is of
interest, in such studies we prefer the **interval estimation**
(confidence intervals) about the compared quantities --- their
differences or ratios. We can visualise them nicely with the
**Gardner-Altman estimation plots** (in R it's the
[dabestr](https://acclab.github.io/dabestr/index.html) package,
implementing the ideas from
[https://www.estimationstats.com](https://www.estimationstats.com/#/))
and coloured confidence bands.

![obraz](https://github.com/user-attachments/assets/8ebe0f79-67f7-46d7-ac98-9c179716375a)

Examples of the interval estimation (Gardner-Altman) plots; generated
with the R dabestr package

In **confirmatory randomised clinical trials** the situation is
completely different. The research takes place after the initial
exploratory work has already been done, and now we want to confirm
carefully selected hypotheses so that the information from the sample is
generalisable.

Such studies are **designed** from many perspectives, including the
**schema** (affecting duration, costs, and ease of causal inference),
**statistical power** (to enable detection of the magnitude of
interest), which also determines the **minimum number of patients** to
recruit, and **interim analysis scenarios** and **early stopping**
conditions in **adaptive studies**. Any **acceptance thresholds** are
also determined at this stage. **All key analyses** (tests used, models,
methods, approaches, alternative scenarios, criteria) **are planned in
advance** (i.e., before the data are seen). All necessary decisions and
assumptions are thoroughly discussed, based on available domain
knowledge. The approach to ensure **data completeness** and optionally
handle **missing data** (*patients may drop out from the study for a
variety of reasons at every stage*) are decided as well.

This preparatory stage can take a very long time before the study is
launched --- because once it is fixed, there is only one way ---
forward. No "forking", no "meandering", no *fiddling* around for the
outcome. **No p-hacking, no "HARKing"** (*Hypothesising After the
Results are Known*).

These studies have one more important feature: **the domain importance
criteria are established for the key endpoints**, to **filter out**
outcomes that are statistically detectable, but of no importance from
the clinical perspective. Not only established, they are embedded into
the tested hypotheses, so from this time forward, **statistical and
practical importance are inseparable.**

Please note, that what I just wrote pertains mostly to **phase-3
clinical RCTs and well designed RWE studies (also their combination:
pragmatic RCT)**. It does not mean that every experimental study,
including the **online A/B studies**, will be similar. For example, if
no randomisation is employed (not every interventional study is
randomised), or if the practical importance is not known or difficult to
determine (sometimes we need a variety of different scenarios to be
covered, representing different conditions and the cost-effective
balance), the old demons may be back. There exist solutions to that,
like *matching algorithms (only mimicking true randomisation as limited
to the features explicitly selected)*, *tipping point analyses* (we
modify some parameters and assess how the results vary as its function).

![obraz](https://github.com/user-attachments/assets/8095351e-b88c-4712-90eb-338b0f81916c)

## 2. Plans, plans, plans... Statistical Analysis Plan (SAP)

All agreements, plans, decisions are compiled into the **Statistical
Analysis Plan (SAP)**, which is the "*cookbook*" of the study (or rather
it's **Statistical Bible** with appropriate commandments "*Thou shalt*"
and "*Thou shalt not*"). Once submitted to a regulatory agency (FDA,
EMA, etc), it's pre-registered and since that time forward only **minor
adjustments** (*amendments*) **are possible**, followed by a thorough
and convincing justification (so forget about changing the primary
question and key methods).

Of course, it's rather **unlikely that all planned scenarios will work
as intended**. As Woody Allen once said: "*If you want to make God
laugh, tell him about your plans*". Biostatisticians writing the SAP are
supposed to anticipate at least the most common issues and challenges
and propose alternative scenarios to handle it. This is totally fine
(more: **this is necessary to not doom a trial only because some
assumption failed!**) as long as it's planned. This is a very complex
process, with lots of discussions, additional research and requiring
both experience and intuition about the possible obstacles. That's why
-not rarely- SAPs may span tens-to-hundreds of pages. "*The more you
sweat in training, the less you bleed in battle*". Check my other
article about this process [The Three Deadly Threats to a Clinical
Trial](https://www.2kmm.pl/blog/The-Three-Deadly-Threats-to-a-Clinical-Trial/)
on our blog.

![obraz](https://github.com/user-attachments/assets/4e3a405e-42a1-4dc7-9d64-73f6aee7cf1f)

So, at the end of this process we have established:

-   the study design and all related details, approaches, etc.

-   all definitions of collected (asked, measured) quantities that will
    be analysed --- study endpoints.

-   all research questions expressed in terms of statistical hypotheses
    (this can be very challenging! Read my article on this very topic:
    [Threat I: Study Design Negligence --- Episode 1:
    Objective-Hypothesis
    Mismatch](https://www.2kmm.pl/blog/The-Three-Threats-Objective-Hypothesis-Mismatch/)

-   the original plans for each key analysis: tests, models, methods,
    parameters, justifications (*yes, you must be able to justify each
    tool and analysis*), notes about the interpretation, etc.

-   a set of "plans B" when the original plans fail for any reason
    (failed assumptions, failed software, a method cannot converge to a
    solution, missing data, specific patterns in data, etc. etc). And
    make sure your alternative plans, your remedies DO NOT change the
    originally asked questions! For example, switching to a rank-based
    or quantile-based method will change the H0 from comparing means to
    quantiles or stochastic superiority. *And NO --- stochastic
    superiority is neither about means nor medians in general. And
    comparing medians is NOT the same as comparing means in general.
    **Be warned!***

-   A set of domain importance thresholds to be reached by each
    endpoint. These threshold may cover a variety of aspects: efficacy,
    safety, cost-benefit, etc. In medicine we often call them **MCID ---
    the Minimal Clinically Important Difference.**

-   A clear separation of work: primary, secondary, and exploratory
    objectives. The first two decide about the study success (or
    failure). The last ones are just supportive, additional analyses
    reflecting the opportunity **to learn something new since we have
    the data --- but of no evidentiary power**! (so no need to control
    FWER for these).

-   Approach to controlling the FWER (type-1 error) on the study level.

...and many more details. Ad-hoc decisions are minimised as much as
possible. Again, no "forking", no "meandering", no fiddling around for
the outcome. No p-hacking, no "HARKing".

PS: Yes, there may be some "last-resort options", equating with post-hoc
made decisions and tool selections, but every such post-hoc selection
must be thoroughly justified, or the statistical reviewers at the
regulatory agency may easily question them and reject. So yes, it's good
to have a backdoor in case of extremal cases, but still it doesn't mean
a "free-ride".

## 3. Binary decision making

The drug approval process is inherently binary: a drug is either
approved or rejected. *Tertium non datur.* No matter how detailed,
"fervent", and exhaustive the discussions were, how sophisticated and
complicated experiments and analyses were conducted, the outcome is
always one: "red light" or "green light." As Master Yoda will probably
say in future: "*Try not. Do. Or do not. There is no try.*". Either you
will be able to buy the new drug in your drug store or not.

## 4. Those cursed thresholds! (= "God loves the .06 nearly as much as .05")

Binary decisions require thresholds. Like it or not --- the lack of a
clear boundary and acceptance criteria opens the door to cheating and
blurring the science.

You've probably heard about the "*theological argument*" that "Surely,
*God loves the .06 nearly as much as the .05"* by Rosnow and Rosenthal
(1989, p. 1277).

Think about it, just moving away from statistical significance. I
understand that you may simply hate that "***s-word***", so for the sake
of convenience and sanity we can choose a whole set of different
measures often used for decision-making: clinical significance,
standardised effect size (Cohen D/h, Hedges g, etc.), Bayes factors, %
some events --- just whatever.

So, let's consider some clinical threshold, such as the MCID (*the
minimal clinically important difference*). Imagine working with a study
assessing the effect of a treatment on lowering LDL cholesterol.
**Initially, you expected a reduction of at least 20 mg/dL**. Byt you
got **19.8 mg/dL**.

Of course --- 19.8 is as good as 20, so all is fine.. Now, your
competitors launch their study and hit **18mg/dL**. They consider that a
complete success. You disagree, you aimed at 20 units and you are not
going to agree at 18. But, at the end of the day, 18mg/dL almost
20mg/dL, so why would you complain? Because "it's too low" for you? Wait
a minute, how is your opinion justified, if you already accepted 19.8 as
as good as 20? Your competitors say that patients won't even notice the
difference! Another competitor hits 16mg/dL and calls it a success. Now
you start protesting loudly: **what the hell? 16 is not good enough!**

![obraz](https://github.com/user-attachments/assets/1833c07b-3a37-45d7-9d0f-63398f1806a0)

But why? What gives you the right to say that? Is that **because 19.8
was yours and 16 is theirs?**Smart move! Only not fair. When YOU missed
the criterion just by 0.2 it's fine. When they missed it just by 2--4
--- now it's wrong. Based on what?

Or maybe everyone should just sit and discuss the threshold that is
generally acceptable? So now **you have to go over it,** just show 20.1
rather than 19.9 and everyone will be happy. Oh, I hear you: "*20 is too
strict, there could be fluctuations! We cannot agree on 20*". OK, then
use a 20% margin. Still not enough? OK, use a 50% margin.

![obraz](https://github.com/user-attachments/assets/ae3d186f-7d33-4b02-9c31-aa43446877a1)

**But once agreed and fixed, respect it, don't cheat, don't argue that
"you missed it just by 0.1% and God loves 16.99 just as 17.01".**

The "*theological argument*" may sound promising and nice, but can
quickly lead to an absurd: 16.99 is just like 16.98, OK, fine, and 16.98
is just like 16.97 (just 0.01 unit!)..... \~16.90, ... \~16.87...
\~16.80... \~16.70 (differ just by 0.1!)... --- and **what will STOP you
from going down** more and more? **Your personal benefit?** Pride (that
it's you who found it)? Money?

This is why in clinical trials we don't want such fiddling around for
the outcome and therefore we pre-register thresholds.

I know, that many physicians will now protest and say: "**It's a BS, we
led studies where the odds ratio was 7 or more but p-value was 0.051 and
this big outcome was ignored! It should be all based on the effect size!
Ditch statistical significance! Ditch binary decisions!**" --- sorry,
this is not something I can agree on in drug approval and other
experimental studies. We just talked about it above --- this enables one
**to justify what they want to justify**, because they invested time and
money. I can understand their anger, but that's not fair.

Why simply you don't design a study to detect a smaller effect (bigger
safety margin) and put this practical relevance into the sample size
determination and the testing procedure? Because it requires more
patients = more money, right? OK, but maybe **exactly this is needed**?

Because if such a big effect had so wide confidence interval attached,
then something went wrong: the variability (dispersion) must have been
very large, covering both spectacular improvements but also very little
changes, and the number of these little or no-changes was likely
dominant. **Would you trust such outcome?** So why didn't you test it at
𝛼=10%? Was it because you wanted a "greater precision"? And when the
precision was not met, you are blaming the entire framework?

**Without inference (of any kind) your results are NOT generalisable to
a population.** They are limited to just the sample you obtained, just
like descriptive statistics, like Cohen's D, like correlation
coefficients.

A few more words about the typical level of statistical significance:
0.1%, 0.5%, 1%, 5%, 10%... **These are not magical numbers.** People
choose them, because they simply like rounded values (don't you as
well?). So it's **a compromise between the acceptable (im)precision and
having just "nice numbers".**

Yes, you **are free to choose** 0.034 or 0.058 if you wish. Actually, if
you use exact tests for discrete outcomes, like the *Fisher's exact
test*, you **do** such thing "behind the scene", but that's a different
story...

If you want to stay consistent with others research --- don't hesitate
using the "standard thresholds". Because **why not**? If you don't like
**0.05** for any reason, pick a liberal **0.1** or more conservative
**0.005**, just as Ioannidis proposed years ago. But then honour it and
don't complain if you missed it, "*because God loves 0.06 just like
0.05"* (do you have it written?). It's a like crossing the allowed speed
limit. When you get your driving license, you agree to obey the road
traffic laws so if you were speeding above the limit and fatally hit
someone, don't expect the police, judge, and insurance agency to take it
lightly. Because every additional 1 km/h meant extra distance your car
travelled, and this extra distance costed someone's life.

## 5. Combined evidence: statistical and practical

We can distinguish two sources of evidence: **statistical** and
**practical**.

**Statistical evidence through the inference.** The role of inference is
to generalise outcomes from the observed sample to the unobserved
population in some way. Let's quickly recall the basic information about
the interval estimation and testing hypotheses:

1\) **interval estimation** produces **confidence intervals**
representing the range of hypothesised values that are ***statistically
compatible*** with our sampled data. In the long run (across many
repeated samples), approximately X% of the time, one of these values
will be the true population value. But what does this imprecise term
"*compatible*" mean? Well, it means that the our **sample data are
obtainable (=could plausibly be obtained) by sampling from a population
where the parameter of interest (e.g. the mean) is equal to a value
inside that interval.** Think about it: if you compare two arms in terms
of -say- means, so you analyse the difference between them Δ, and then
you calculate the confidence interval for this Δ, the CI shows all Δs
that are statistically compatible with your observed data, i.e. that
they could reasonably explain it (under the assumptions of your
model)**.**

Note that this range of compatible hypotheses can also be used to test a
specific hypothesis. For example, if you want to check if Δ is
statistically discernible from 0, just check if the CI for Δ covers 0.

2\) **testing hypotheses**. The classic textbook definition says that a
*p-value is the probability (% over many repeated samples) of obtaining
data as extreme as, or even more extreme than, what we observed* (in a
more human language: "of at least he current magnitude") *assuming the
null hypothesis (H0) is true.* So, hypothesis testing assesses whether
the observed data are statistically **compatible** with an assumed
theoretical pattern --- H0. If the discrepancy between our (or even more
extreme) data and what we would expect under H0, that is expressed by
appropriate test statistic, is **smaller than a predefined threshold**
(the critical value of this test statistic), we cannot reject H0. The
statistical evidence against H0 was just insufficient. Otherwise, the
outcome is considered statistically **detectable beyond what H0 can
reasonably explain**, so we reject H0.

This **critical value** corresponds to the **significance level**, which
is the maximum acceptable probability of wrongly rejecting true H0 (a
type-1 error). In the frequentist framework, this means that the
long-run probability of rejecting a true H0 (assuming the model
assumptions hold) will not exceed some level, typically 1%, 5%, 10%.

**Note: statistical evidence is NOT equivalent to the practical
evidence**, as **their goals differ**. The role of statistical evidence
is to say whether an effect is statistically discernible, detectable
under the true H0, but it cannot say if it's important. The role of
practical evidence is to say whether the effect makes sense.

*Long-story-short, it's like we detected a signal from space that is
above the background noise (statistically distinguishable), but we don't
know if it's from aliens from another star system or if it's just Joe
cooking soup in the microwave 3 floors below...*

**Practical evidence through the dedicated thresholds (MCIDs)**. These
thresholds don't come from smart formulas, but from the researchers. It
can be a value obtained from previous studies (meta-analysis), educated
guess based on one's experience, scientific agreement. Yes, it's a
subjective threshold, but reflects the scientific goal, hopefully
well-grounded in the domain knowledge (at least discussed). One may
consider multiple sources of practical evidence, addressing different
aspects of the examined treatment: efficacy, safety, cost-benefit,
"ethical "measures. They can be combined in some way, like
**weighting**, **voting**, or aggregated in **meta-analysis**, but
still, a clear decision is to be made: *passed or failed*. Therefore,
each source of evidence, representing a different perspective, will have
to pass some threshold of importance --- alone or combined.

We may also don't know for sure (it's a matter of pending discussions,
controversial, etc) good measures of importance, so we may use the
"last-resort" replacements, like the Minimum Detectable Change (MDC),
e.g. based on the 95% confidence interval (MDC95%). So while MDC tells
if the change is unlike to be a random noise, MCID tells is the
treatment clinically matters.

So, the two kinds of evidence are complementary. Practically important
effect CAN be just a noise. Statistically significant effect CAN be just
a sample-specific artifact. **This is why we need both in clinical
trials --- combined.**

![obraz](https://github.com/user-attachments/assets/707eddd1-5171-48b2-aaff-471d6f460aa7)

**Combination of evidence.**

The practical importance expressed in terms of MCID can be embedded into
the process of statistical testing through interval, **directional
hypotheses.** In clinical trials we employ this idea routinely in:

-   **non-inferiority studies,** where we ask if the active treatment is
    no worse than the comparator. We accept it may be worse, but not
    more than some acceptable margin.

-   **clinical superiority studies**, where we ask if the new treatment
    is better than the comparator (can be placebo). The "better" may be
    "trivial", just like Δ\>0, or better reflecting the practical
    relevance, e.g. Δ \> 20mg/dL, so it's not enough to be "just better"
    it must be better than the MCID.

-   **equivalence studies**, where we ask if two treatment are
    equivalent. Notice, this couldn't be done by "proving H0" (one
    cannot prove H0), so instead we need a reversed case: by allowing
    for a margin of equivalence and using two one-sided hypotheses (thus
    the name: *TOST procedure*).

This is often performed through confidence intervals, as they naturally
represent the idea: the range of all hypotheses compatible with your
data must lay above the importance cut-off. **This way neither part of
the CI will lay below the MCID.** Of course you're free to do this with
a test and p-value.

*In this case, **rejection of the H0 will mean not only reaching
statistical significance but also the practical importance.***

If you wish, read these papers talking about the presented approach:

-   [*The minimum clinically important difference is fundamental to all
    clinical
    trials*](https://journals.lww.com/ejanaesthesiology/citation/2016/01000/the_minimum_clinically_important_difference_is.12.aspx),

-   [*Understanding Superiority, Noninferiority, and Equivalence for
    Clinical
    Trials*](https://pmc.ncbi.nlm.nih.gov/articles/PMC7734976/),

-   [Equivalence Testing and the Second Generation
    P-Value](http://daniellakens.blogspot.com/2018/08/equivalence-testing-and-second.html)

-   [*Interval-based hypothesis testing and its applications to
    economics and
    finance*](https://www.econstor.eu/bitstream/10419/247521/1/econometrics-07-00021-v2.pdf).

## 5. But nobody deals with true null hypothesis & assumptions matter!

These two objections are very common: 1) "*H0 is never exactly true*",
2) "*assumptions never perfectly hold*".

Fair points, but...

1\) in **randomised trials**, **H0 is true just by design** (no real
difference between groups at baseline): the values of the assessed
outcome in both compared treatment arms come now from a single,
theoretical (virtual) distribution. Whatever differences occur --- they
are purely obtained by chance (sampling), therefore in randomised
studies we test precisely **under the true H0**! This makes the **ideas
of NHST and RCTs well alligned**. And this is one of the reasons
(another one is the.... *violation of the likelihood principle*) the
frequentist framework is popular in this application.

2\) assumptions are of course "idealisations" (no data follows exactly
Gaussian distribution, no data have ideally same variance in
sub-groups), but we can always assess how well our data aligns with. If
the fit is **good enough** the resulting errors will be small,
acceptable for **for practical inference.** Think about the Simpsons
rule of integration: will we blame approximating integrals with
trapezoids because of the inevitable integration error? Of course not,
because despite being imperfect it can be **precise enough** for
practical use --- we decide about the integration step, it's all up to
us. In fact, much of mathematics relies on idealised constructs, yet we
use them every day to describe and predict real-world physical
processes, don't we?

And remember that you can always prepare for certain challenges in
advance! Just plan the use of sufficiently general, flexible methods. Do
you expect unequal variances? Then try GLS or GEE estimation without
even testing for this homogeneity (just as you use Welch t rather than
the F+t test combo). Correlated responses? Try GLS, GEE or mixed models.
Normality is compromised? Do you expect a concrete functional form? So
maybe the GLM (Generalised Linear Model) family will suffice? If not,
but the violation is just moderate --- try the GEE estimation --- it
makes no assumption about the residuals. If the violation is more
serious, there exists a class of distribution-free methods that can
**retain the original null hypothesis** (e.g. comparing means in terms
of the *parametric Behrens-Fisher problem)**, ***without relying on the
concrete theoretical distribution: permutation and bootstrap test, like
the **permutation Welch t-test or permutation ANOVA** (BTW, permutation
Welch t addresses the old problem of having both samples *exchangeable
under unequal variances*). [Read my post on this very topic with
numerous
resources](https://www.linkedin.com/posts/adrianolszewski_what-teachers-should-know-about-the-bootstrap-activity-7172356573921591296-LA2J?utm_source=share&utm_medium=member_desktop&rcm=ACoAAA0I9gsBMgV_EZKUqj9dxzpDS69h6zwGHmk)**.**
These techniques have their limitations too, but are less strict. Of
course provided (and this is up to you) that such non-normal data CAN be
meaningfully summarised with means. **Because being able to do something
does NOT automatically mean it is meaningful.**

I am not going to name every possible scenario here, but you should feel
the idea: be prepared and don't despair. When in doubt, **always try
additional methods in terms of sensitivity analysis (*provided they
assess a similar thing!*)** --- because this is the best way to check if
a violation of a certain assumption(s) was big enough to affect the
inference greatly. Often it is not and the different methods, despite
some variability in outcomes, will be yield consistent results.

![obraz](https://github.com/user-attachments/assets/55f8d0bd-23e8-454b-95d7-b50f34c058d9)
Examples of sensitivity analyses

And if the results are not consistent at the boundary of the
significance level (some methods reject H0, some cannot), then the
situation is unclear anyway. I mean --- you should **report honestly
what was planned**, but you **should also discuss the result in light of
the sensitivity analysis** results. If it looks unreliable, "unstable"
--- best you can do is to consider another study to replicate the
outcome in either direction. You can also subject it to a meta-analysis.
Just don't ignore it, be transparent and trustworthy. **Just be honest,
don't bend the reality.**

Read also [my LinkedIn post related to this
topic](https://www.linkedin.com/posts/adrianolszewski_i-remember-one-of-my-most-hard-discussions-activity-7264666116805828609-PCwo?utm_source=share&utm_medium=member_desktop&rcm=ACoAAA0I9gsBMgV_EZKUqj9dxzpDS69h6zwGHmk)
--- about my "adventure" with a statistical reviewer.

## 6. p-value answers the wrong question!

In a well designed and conducted RCT, p-value answers **the meaningful
question**.

Let's collect the facts:

1.  randomisation\* ensures testing under the true H0. There are no
    differences between the treatment arms BEFORE the treatment has been
    applied (*and you should NOT test for such differences; they may
    occur, easily, but are only artifacts; you will account for it by
    appropriate adjusting for the baseline response).*

2.  If no treatment has been applied, the data may fluctuate over time
    only according to the RTM (*regression-to-the-mean*) phenomenon or
    natural healing processes --- but then this should "work" equally in
    both study arms.

3.  If a treatment has been applied to one arm, **it's the only causal
    reason for inducing changes in the observed endpoint**. Of course
    natural healing processes may still occur, but we expect them to
    "work" in a similar way across both treatment arms and adjust for it
    in longitudinal models (e.g. *response \~ treatment \* time +
    baseline + baseline : time)*.

Therefore, we can meaningfully ask: **is it probable for the obtained
(sampled) data to be so or even more extreme under the true H0 after
applying the treatment?**

-   **If yes (high p-value)**, then it means that our data remained
    "consistent with the randomisation" even under treatment =
    consistent with what we would expect just by chance, assuming the
    treatment has no real effect. So, either the treatment was not
    applied -**but we know it was!**- or it did not affect the measured
    clinical endpoint enough to claim its effect, both statistically and
    clinically.

-   **If not (low p-value)**, then something affected the data "enough",
    so the observed result falls into the rejection region, where the
    probability of seeing such (or even more extreme!) data under a true
    H0 is smaller than the preset **maximum type-1 error** rate (e.g.,
    5%). And In an RCT the most plausible explanation for it is the
    treatment effect. Embedding the MCID into the test statistics
    ensures both statistical and clinical evidence.

/\* PS: In non-randomised studies you may consider using the *Inverse
Probability Weighting* or *Propensity Score Matching*. These methods can
"mimic" what randomisation does, but in a limited scope, only for the
features you **explicitly declared**. True randomisation accounts for
all features, both known and unknown --- just by its random nature. /

![obraz](https://github.com/user-attachments/assets/6d24acd0-dfc7-4c28-a2b1-e4c869413293)

## 7. P-values and confidence interval violate the principle of likelihood!

**Yes, it does. That's another reason for which this framework is
popular in clinical trials.**

If you look at the formula defining p-value, you will see two things:
repeated sampling (frequentist = frequency) AND the definite integral
over the probability density function of the test statistic from its
observed value to infinity:

![obraz](https://github.com/user-attachments/assets/466ff28e-97c6-49d1-b017-de0c8237bcc7)

or, more generally:

![obraz](https://github.com/user-attachments/assets/1496baa7-6bb7-4713-b668-c4fa885a0bee)

**This means, that p-value takes into account not only the current data,
but also other, unobserved, "more extreme" ones**.

Regulatory agencies like the FDA demand that the family-wise error rate
(FWER) --- the probability of making at least one type-1 error across
all primary hypotheses in a confirmatory trial- to be strictly
controlled. The rationale is to ensure that, **across many trials and
drug approvals, the long-run rate of false positives (approving
ineffective drugs) remains acceptably low.**

This is "offered" by p-values, confidence intervals, and appropriate
multiplicity adjustments. But even for a single hypothesis the idea of
the type-1 error holds. In the pharmaceutical industry almost everything
is "massive" and "frequent" --- studies are repeated (from multiple
perspectives, in different phases), billions of people take millions of
medicines every day. The same biochemical processes are repeated over
and over in an endless loop, physicians "collect" massive feedback from
their patients (treatment working or not working, side effects
occurrence, interactions with concomitant medications, etc).

So, the requirement is justified by a clear regulatory and public health
purpose of doing it: to prevent a flood of false positive findings and
ensure that approved treatments are truly effective, given the high
stakes of drug approval and patient safety. The requirement for
frequentist error control is seen as a "safeguard" against spurious
results, especially in the context of multiple testing and confirmatory
trials. It reflects a trade-off between *philosophical purity* and
public health priorities.

## 8. Bayesian clinical trials may need to demonstrate acceptable frequentist properties as well!

Yes, regulatory agencies may require that the studies be calibrated or
**to demonstrate acceptable frequentist properties** --- specifically,
that the long-run **type-1 error rate** (e.g., the probability of
wrongly declaring efficacy) is controlled at the same level as in a
frequentist design. In practice, this means **running simulations to
show that, under the null hypothesis, the chance of a false positive
does not exceed the pre-specified thresholds!** Concrete details can be
found in the "[Guidance for the Use of Bayesian Statistics in Medical
Device Clinical
Trials](https://www.fda.gov/regulatory-information/search-fda-guidance-documents/guidance-use-bayesian-statistics-medical-device-clinical-trials)"
issued by the FDA, sections: *4.8 Assessing the operating
characteristics of a Bayesian design*, and *7.2 Simulations to Obtain
Operating Characteristics.*

By the way, this is what p-values and confidence intervals do just by
their definition, even though it results from a **violation of the
likelihood principle**. This violation is, however, an important
advantage of the frequency framework in this particular application.

![obraz](https://github.com/user-attachments/assets/d25d8917-1483-4fd3-b503-864f75bd97ce)

## 9. Varia --- other related notes you may find interesting

1.  The **FWER** (Type 1 error) is strictly controlled at the entire
    study level, by using modern, advanced methods, which allows us to
    minimise the significance level penalty by prioritising hypotheses.
    This is the basic principle of the "*graphical method*" based on the
    *Closed-Testing Procedure*, special cases of which include:
    **fixed-sequence,** **fallback,** and **gatekeeping** techniques.
    This leads to extremely flexible adjustments, applicable even to...
    circular testing hypotheses (well, I've never done it, but good to
    know it's possible...). Read more about them in my posts
    "[Bonferroni is not
    enough](https://www.linkedin.com/posts/adrianolszewski_testinghypotheses-clinicaltrials-research-activity-7030553195135262721-ooYg?utm_source=share&utm_medium=member_desktop&rcm=ACoAAA0I9gsBMgV_EZKUqj9dxzpDS69h6zwGHmk)"
    and
    [here](https://www.linkedin.com/posts/adrianolszewski_modern-approaches-to-multiple-hypothesis-activity-7111711025996922880-yguO?utm_source=share&utm_medium=member_desktop&rcm=ACoAAA0I9gsBMgV_EZKUqj9dxzpDS69h6zwGHmk).
    Especially the ***fixed-sequence*** procedure is interesting: it's
    both simple (trivial!) and requires **NO adjustment** as long as all
    previous hypotheses in the ordered chain were rejected (but single
    non-rejection stops the testing procedure, with all remaining
    hypotheses non-rejected). Fallback is it's "brother", allowing also
    for continuation of testing in case of non-rejection. I strongly
    recommend learning these methods, e.g. by reading these two
    books: 1) "***Multiple Testing Problems in Pharmaceutical
    Statistics***" (Dmitrienko, Tamhane, Bretz), and 2) "***Multiple
    Comparisons Using R***" (Bretz, Hothorn, Westfall). Check also these
    materials: [Graphical Approaches to Multiple Test
    Problems](https://baselbiometrics.github.io/home/docs/trainings/20220329/2_Glimm_Bretz_Xi.pdf)
    \| [Introduction to Multiplicity in Clinical
    Trials](http://web.archive.org/web/20230603082437/https:/www2.cscc.unc.edu/impact7/system/files/Bretz_Slides.pdf)
    (Wayback Machine) \| [Multistage and mixture parallel gatekeeping
    procedures in clinical
    trials](https://users.iems.northwestern.edu/~ajit/papers/48)%20Multistage%20and%20mixture%20parallel%20gatekeeping%20procedures%20in%20clinical%20trials.pdf)
    \| [Use of Gatekeeping Strategies in complex study
    designs](https://dumas.ccsd.cnrs.fr/dumas-00517484/document) \|
    G[eneral Multistage Gatekeeping
    Procedures](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=179d7b170048360a00877b55f9b8073ae1143009)
    \| [A Family-based Graphical Approach for Testing Hierarchically
    Ordered Families of Hypotheses](https://arxiv.org/pdf/1812.00250) \|
    [Managing multiplicity in clinical vaccine studies --- A case study
    using a gatekeeping testing
    strategy](https://www.sciencedirect.com/science/article/pii/S0264410X22002444)
    \| [An Application of Graphical Approach to Construct Multiple
    Testing Procedures in a Hypothetical Phase III
    Design](https://pmc.ncbi.nlm.nih.gov/articles/PMC3882873/) \|
    [Analysis of Multiple Endpoints in Clinical
    Trials](https://web.njit.edu/~wguo/Math654_2012/DTB_Chapter4.pdf)

2.  **Missing data** are accounted for at the design stage, e.g. by
    planning techniques of multiple imputation best adapted to the
    structure of the estimates and minimising loss of power. Sure! It's
    better prevent the disease than cure, and always have 100%-complete
    and clean data, but it's rather a wishful thinking. In clinical
    trials there are lots of reasons for patients being lost to the
    follow-up, from obvious (death, consent withdrawal, serious
    drug-emergent adverse reactions, serious protocol non-compliance) to
    sometimes surprising causes...

3.  Various common **MNAR** (*Missing Not At Random*) missing data
    patterns may be planned to evaluate as part of *sensitivity
    analyses* to check if the obtained estimates are stable under these
    patterns, i.e. to see if **certain MNAR patterns can affect the
    results noticeably**. We employ several techniques like the
    *best-worst imputation* (imputing data with the best and worst
    possible cases for the given endpoint and observe the estimates
    under extreme conditions), or the ***tipping point analysis***
    combined with "delta-adjustment" (part of ***Pattern-Mixture
    Model***), allowing to observe how a certain outcome (p-value,
    effect size, sign of estimate) changes over a range of imputations.
    For example, check
    [this](https://stefvanbuuren.name/fimd/sec-nonignorable.html)
    chapter (*3.8 Nonignorable missing data*) from the "*Flexible
    Imputation* of *Missing* Data" book and
    [this](https://bookdown.org/glorya_hu/MNAR-Guide/) (*A Practical
    Guide to Sensitivity Analysis for Causal Effects in the Presence of
    Non-Ignorable Loss to Follow-Up*) tutorial.

4.  Under some circumstances, the FDA or EMA may require **more than one
    additional statistically significant clinical trial** to address
    regulatory concerns before approving a drug! When in doubt, they
    won't "take go easy"...

5.  In the frequentist world **we CAN combine knowledge from past
    studies** for a more *generalisable* conclusions across different
    contexts. It can be done through the **meta-analysis** and
    **random-effect** models (accounting for the effect heterogeneity
    across studies). This is **not the same as using prior beliefs** in
    the Bayesian framework, and it's still entirely data-driven, so the
    interpretation remains within the frequentist framework --- there's
    no prior or posterior. Rather it's *empirical aggregation of
    evidence,* weighted by quantities like sample size or study
    precision. Meta-analyses over RCTs are on the top of the evidence
    ladder in the EBM (*Evidence-Based Medicine*).

6.  We can also employ methods for the assessment of the publication
    bias (a tendency to publish studies with statistically significant
    results and to suppress those with non-significant ones) and
    estimating expected discovery and replicability rates on bases of
    test-statistics of published studies through the
    [Z-curves](https://replicationindex.com/2021/04/25/z-curve-an-even-better-p-curve/).

7.  Clinical trials is a regulated industry, so **biostatisticians must
    follow the official industry guidelines** (and less official
    proposals and "*regulatory perspectives*"). There are LOTS of them:
    ICH E6(R2): Good Clinical Practice (GCP), ICH E8(R1): General
    Considerations for Clinical Studies, ICH E9: Statistical Principles
    for Clinical Trials • ICH E9(R1): Addendum on Estimands and
    Sensitivity Analysis • ICH E10: Choice of Control Group in Clinical
    Trials, Guideline on Adjustment for Baseline Covariates in Clinical
    Trials (CHMP/295050/2013) • Guideline on Missing Data in
    Confirmatory Clinical Trials (CPMP/EWP/1776/99) • Points to Consider
    on Multiplicity Issues in Clinical Trials (CPMP/EWP/908/99) •
    Guideline on the Investigation of Subgroups in Confirmatory Clinical
    Trials (CHMP/539146/2013) • Points to Consider on Switching Between
    Superiority and Non-Inferiority (CPMP/EWP/482/99) •
    CPMP/EWP/2158/99: Choice of a non-inferiority • Application with 1.
    Meta-analyses; 2. One Pivotal Study (CPMP/EWP/2330/99) •
    Extrapolation of Efficacy and Safety in Medicine Development
    (EMA/129698/2012) • FDA (FDA-2016-D-4460): Multiple Endpoints in
    Clinical Trials: Guidance for Industry • FDA: Non-Inferiority
    Clinical Trials to Establish Effectiveness: Guidance for Industry •
    FDA: Adaptive Designs for Clinical Trials of Drugs and Biologics:
    Guidance for Industry • FDA: Adjusting for Covariates in Randomized
    Clinical Trials for Drugs and Biological Products: Guidance for
    Industry • CONSORT 2010 Statement • NCBI: The Prevention and
    Treatment of Missing Data in Clinical Trials • Guidance for the Use
    of Bayesian Statistics in Medical Device Clinical Trials • RECIST...
    and more!

## 10. Epilogue

1.  Statistical tools have their applications where they do their best.
    If you go beyond those uses, expect nonsense. It's like ignoring the
    domain in mathematics --- don't be surprised if 0=1 as a solution to
    some equation. You're really to blame for misusing a screwdriver to
    cut an apple in half. Misusing tools is a pretty weak argument. It's
    like blaming knives because a madman uses them to hurt others
    instead of buttering a sandwich. Read this article: [*Blaming the
    Thermometer for the
    Fever*](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5212117)

2.  Most of the science in the 20th century was done (and much is still
    being done in the 21st century) with the blamed, criticised, and
    shamed frequency framework. Are you going to deny or reject your
    medicines, computers/smartphones, electronic devices, clothes
    (chemicals) just because most of the stuff was manufactured and
    quality checked with frequency methods?

3.  People often "parrot" something --- repeating something just to be
    accepted by the community and follow trends. I call this a "*TikTok
    argument*". "*Too many people abuse it, so it should be banned!*"
    --- ah yes --- because a knife can be used to harm people, let's ban
    all knives and butter a sandwich with spoon, right? No one denies
    the problems with the frequency frame. Every tool has its flaws in
    certain situations. Sometimes a tool just doesn't fit someone's
    problems. If you experience this --- just choose better
    alternatives. But don't ban others their tools.

4.  *"But the 𝘑𝘰𝘶𝘳𝘯𝘢𝘭 𝘰𝘧 𝘉𝘢𝘴𝘪𝘤 𝘢𝘯𝘥 𝘈𝘱𝘱𝘭𝘪𝘦𝘥 𝘚𝘰𝘤𝘪𝘢𝘭 𝘗𝘴𝘺𝘤𝘩𝘰𝘭𝘰𝘨𝘺 banned
    p-values and confidence intervals!"*. Here I fully support prof.
    𝙄𝙤𝙖𝙫 𝘽𝙚𝙣𝙟𝙖𝙢𝙞𝙣𝙞 who briefly described this as "𝘵𝘢𝘬𝘪𝘯𝘨 𝘶𝘴 𝘣𝘢𝘤𝘬 𝘵𝘰 𝘵𝘩𝘦
    19𝘵𝘩 𝘤𝘦𝘯𝘵𝘶𝘳𝘺 𝘸𝘩𝘦𝘯 𝘵𝘩𝘦 𝘳𝘦𝘴𝘶𝘭𝘵𝘴 𝘰𝘧 𝘴𝘵𝘶𝘥𝘪𝘦𝘴 𝘸𝘦𝘳𝘦 𝘳𝘦𝘱𝘰𝘳𝘵𝘦𝘥 𝘮𝘦𝘳𝘦𝘭𝘺 𝘣𝘺
    𝘵𝘢𝘣𝘭𝘦𝘴 𝘢𝘯𝘥 𝘧𝘪𝘨𝘶𝘳𝘦𝘴". [*Selective Inference: The Silent Killer of
    Replicability*](https://hdsr.mitpress.mit.edu/pub/l39rpgyc/release/3)
    and [*So you banned p-values, how's that working out for
    you?*](http://daniellakens.blogspot.com/2016/02/so-you-banned-p-values-hows-that.html)

5.  *"But in 2016 the ASA clearly said in their statement that....".*
    OK, now please read the *[ASA President's Task Force Statement on
    Statistical Significance and Replicability
    (2021)](https://magazine.amstat.org/blog/2021/08/01/task-force-statement-p-value/).*

6.  *"But Prof. Ioannidis said that most of the research is wrong!*".
    OK, now please read why *[Ioannidis is Wrong Most of the
    Time](https://replicationindex.com/2020/12/24/ioannidis-is-wrong/).*

7.  The context is everything for any kind of inference. The "highest
    density", for instance, doesn't mean something is important, if
    priors didn't reflect this very importance. The same way correlation
    is not causation (though it's a good point to start a discussion).

8.  **Exploration is not proving.** **Proving is not exploration**.

9.  When you explore a new territory, no domain knowledge may be known,
    so neither method or framework is safe.

10. *"What about standardised measures of the effect size, like the
    famous Cohen's D?*" --- If you work in psychology or sociology,
    where lots of things are standardised into z-scores, it will work
    well. Otherwise it may not, as it ignores the context. [I wrote a
    post
    explaining](https://www.linkedin.com/posts/adrianolszewski_statistics-datascience-activity-7288333086252048385-9HTR?utm_source=share&utm_medium=member_desktop&rcm=ACoAAA0I9gsBMgV_EZKUqj9dxzpDS69h6zwGHmk)
    why such measures may be useless in clinical biochemistry, where the
    same magnitude (even under same variance) can mean opposite things
    (i.e. be life-saver or a negligible garbage).

## 11. Reflections, judgements, perspectives in the literature

-   ***ASA President's Task Force Statement (2021) on Statistical
    Significance and Replicability:*** <https://lnkd.in/dtJ-tThh>

-   *ASA comment on a journal's ban on null hypothesis statistical
    testing*: <https://lnkd.in/dTawWF-V>

-   ***"So you banned p-values, how's that working out for you?***"
    <https://lnkd.in/dXZmFpsX>

-   ***"Statistical significance and its critics: practicing damaging
    science, or damaging scientific practice?***"
    <https://lnkd.in/dU4-sXez>

-   ***"A psychology journal banned p-values and confidence intervals;
    is it indeed wise to stop using them?"***:
    <https://lnkd.in/d4XbZtwN>

-   ***"Defending the P-value"***: <https://lnkd.in/dQW-RRvg>

-   ***"In Defense of P Values"***: <https://lnkd.in/dVT7Yv7X>

-   ***"Ioannidis is Wrong Most of the Time"***-
    <https://lnkd.in/ddS_msGY>

-   ***"Is the call to abandon p-values the red herring of the
    replicability crisis?"***: <https://lnkd.in/dFBQFc_3>

-   ***"Retiring statistical significance would give bias a free
    pass"***: <https://lnkd.in/dmmMEpcj>

-   ***"Significant? You Really Mean Detectable"***:
    <https://lnkd.in/dSgKR5VB>

-   ***"Too little, too late? The "Don't say significance...***"
    <https://lnkd.in/d2yedSd3>

-   ***"The Null Is Always False (Except When It Is True)"***
    <https://lnkd.in/dEjaqWda>

-   ***"Banned: P Values and Confidence Intervals! A Rebuttal: Part
    1"***: <https://lnkd.in/dGTQXk25> and ***Part 2***:
    <https://lnkd.in/dmVJU8aT>

![obraz](https://github.com/user-attachments/assets/a38a78a4-8425-4f4e-8afc-25c649fb0328)
