# AI Fairness

1. Demographic parity / statistical parity
says the model is fair if the composition of people who are selected by the model matches the group membership percentages of the applicants.

2. Equal opportunity
ensures that the proportion of people who should be selected by the model ("positives") that are correctly selected by the model is the same for each group. We refer to this proportion as the true positive rate (TPR) or sensitivity of the model.

3. Equal accuracy  
the percentage of correct classifications (people who should be denied and are denied, and people who should be approved who are approved) should be the same for each group. If the model is 98% accurate for individuals in one group, it should be 98% accurate for other groups.

4. Group unaware / "Fairness through unawareness"
removes all group membership information from the dataset. For instance, we can remove gender data to try to make the model fair to different gender groups. Similarly, we can remove information about race or age.