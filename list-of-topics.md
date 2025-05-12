1.  [**Logistic regression has been a regression since its birth - and is used this way every day**](https://github.com/adrianolszewski/Logistic-regression-is-regression)

> Despite the popular yet wrong claim that logistic regression "is not a regression", it's one of the key regression and hypothesis testing tools in experimental research (like clinical trials). I share information from my field to break the bizarre situation, when people from Machine Learning tell me that "what we do every day cannot be done".

2.  [**Model based hypothesis testing - notes**](https://github.com/adrianolszewski/model-based-testing-hypotheses/blob/main/README.md)

    a.  **General Linear Model**
    b.  [Generalized Linear Model :: **Logistic Regression**](https://github.com/adrianolszewski/Logistic-regression-is-regression/blob/main/Testing%20hypotheses%20about%20proportions%20using%20logistic%20regression.md)
        I.  *proof*: [Proving the equivalence between the 2-sample Wald's z-statistic for comparing proportions with unpooled variances and the Average Marginal Effect over logistic regression with a single binary predictor](https://github.com/adrianolszewski/Logistic-regression-is-regression/blob/main/logistic_regression_AME_Wald_z_test_proportions.md)
        II. *proof*: [Proving the equivalence between the 2-sample Wald's z-statistic for comparing proportions with pooled variances and the Rao score test over logistic regression with a single binary predictor](https://github.com/adrianolszewski/Logistic-regression-is-regression/blob/main/logistic_regression_Rao_Wald_z_test_proportions.md)
        III. *proof*: [Proving the equivalence between the 2-sample Wald's z-statistic for comparing proportions with pooled variances and the Pearson's χ2 (independence) test for a 2×2 contingency table](https://github.com/adrianolszewski/Logistic-regression-is-regression/blob/main/Pearson_chi2_Wald_z_test_proportions.md)

3.  [**Olszewski's vs. Anscombe's quartet**](https://github.com/adrianolszewski/R_and_statistics_miscellany/blob/main/Olszewski's%20quartet/Olszewski's%20quartet.md)

> You probably heard about the Anscombe's quartet. It's almost a textbook justification for looking at the data first and not trusting solely descriptive statistics. I decided to make my own, Olszewski's quartet. It shows 4 faces in different moods. The mean and variance of the Y coordinate is exactly (NOT approximately!) the same for all 4 faces. Also, the Pearson's correlation is almost 0.

4. [The role of the frequentist framework, p-values, statistical (NHST) and practical significance (MCID) in randomised controlled (clinical) trials](https://github.com/adrianolszewski/thougths-on-clinical-trials-biostatistics/blob/main/the-role-of-frequentist-framework-pvalues-statistical-and-practical-significance-in-randomised-controlled-clinical-trials.md)

> Despite frequent calls to “ban p-values” and “ditch/abandon statistical significance,” the NHST framework remains the primary (though not the only; Bayesians mark their presence as well) “engine” of inference in phase-3 randomised controlled clinical trials. Why is this and how is it used, given the well-known and - unfortunately - frequent abuses of this framework? What specific steps are taken to achieve reliable inference?
