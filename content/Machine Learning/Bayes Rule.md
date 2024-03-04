Posterior = (Likelihood * Prior)/ Evidence

Posterior refers to the probability of an event A given event B, which is unknown and smth you want to find
Likelihood refers to the probability of event B given A, which is known to you
Prior refers to the probability of event A, which is also known to you
Evidence refers to probability of event B, which is usually calculated as a sum of conditional probabilities

An excerpt from chatGPT about how to think of Bayes:

Bayes' rule can be useful in a wide range of applications, from medical diagnosis to natural language processing. Here's an intuitive example that illustrates how Bayes' rule can be applied in a medical context:

Suppose a doctor wants to diagnose a patient with a certain disease. The doctor knows that the disease is rare, with a prevalence rate of 1 in 1000 people. The doctor also knows that the test for the disease is not perfect: it correctly identifies the disease 95% of the time (i.e., the test has a sensitivity of 0.95), and it correctly rules out the disease 99% of the time (i.e., the test has a specificity of 0.99).

Now suppose the patient tests positive for the disease. What is the probability that the patient actually has the disease?

Using Bayes' rule, we can calculate this as follows:

P(Disease | Positive Test) = P(Positive Test | Disease) * P(Disease) / P(Positive Test)

where:

-   P(Disease | Positive Test) is the probability that the patient has the disease given a positive test result.
-   P(Positive Test | Disease) is the probability of a positive test result given that the patient has the disease (i.e., sensitivity).
-   P(Disease) is the prior probability of the patient having the disease (i.e., prevalence rate).
-   P(Positive Test) is the probability of a positive test result (which can be calculated as the sum of the probabilities of a true positive and a false positive).

Plugging in the numbers, we get:

P(Disease | Positive Test) = 0.95 * 0.001 / (0.95 * 0.001 + 0.01 * 0.999) ≈ 0.087

So, even though the patient tested positive for the disease, the probability that they actually have the disease is only about 8.7%. This is because the disease is rare, and the test has a relatively high false positive rate. The doctor may want to consider further tests or follow-up to confirm the diagnosis before starting treatment.

Bayes rule will be a core concept in [[Maximum Likelihood Estimation]] (MLE)
#ml