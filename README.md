# Tukey's HSD Test

After determining that the continuous and categorical variables are significantly related to each other using an ANOVA test (visit here : https://github.com/selbydiva/anova-test), the next step is to run Tukey’s HSD test. In an ANOVA test, we conclude that there is a significant difference among groups if at least one group significantly differs from the others, but it does not specify which groups differ. By using Tukey’s HSD test, we can identify which specific groups are significantly different from each other.

<img width="716" alt="HSD-1" src="https://github.com/user-attachments/assets/29b229a5-8122-4023-b42f-110a9c061c9a">


First, let's outline the comparisons we will be making. Since we have three groups (Romance, Horror, and Comedy), the comparisons we will examine are:
1.	Romance vs. Horror
2.	Romance vs. Comedy
3.	Horror vs. Comedy
   
Next, we calculate the mean difference between the groups as follows:

<img width="1432" alt="HSD-2" src="https://github.com/user-attachments/assets/24e262de-f261-4e51-ac2f-0d639a6bc19b">

To determine if the mean difference is significant, we need to find the threshold known as 'Tukey's Honest Significance Difference (HSD)' using this formula

<img width="1434" alt="HSD-3" src="https://github.com/user-attachments/assets/aba88659-79da-4c67-88a6-7389aba6f853">

# Steps to Find Tukey’s HSD

**Determine the Studentized Range Distribution**

o	We use a significance level of 0.05.<br>
o	Since we have 3 groups and 9 observations, we find q0.05(3,6)  in the studentized range distribution table.<br>
o	For a 0.05 significance level, with 3 groups and 6 degrees of freedom (df), the value of q is 4.399.<br>

<img width="1435" alt="HSD-4" src="https://github.com/user-attachments/assets/038c5a8a-d1fe-4b2b-88a0-f37262c7cc60">

**Calculate the Mean Square Error (MSE)**

o	The MSE value is obtained from the ANOVA table, calculated as the sum of squares of the error divided by the error degrees of freedom (df).<br>
o	In this case, the MSE value is 0.4339.

<img width="1092" alt="HSD-5 copy" src="https://github.com/user-attachments/assets/9880dc8b-0dee-4ed1-97a7-5628489ec873">


**Calculate the HSD**

o	Use the formula for Tukey’s HSD to determine the threshold for significance.

<img width="1068" alt="HSD-5" src="https://github.com/user-attachments/assets/caa6c359-9c99-492e-8f3a-8fe22b7fef47">

We can use the HSD value as a threshold to determine if the differences between group means are significant.

•	If the mean difference between groups is greater than the HSD value, those groups are significantly different.<br>
•	If the mean difference between groups is less than the HSD value, those groups are not significantly different.

<img width="1432" alt="HSD-6" src="https://github.com/user-attachments/assets/e92b9f85-ca4e-450e-bcf7-ef9fb45cf3c6">

From our results, only the mean difference between the Horror and Comedy genres is greater than the HSD value, indicating a statistically significant difference in their ratings. In contrast, the mean differences between Romance and Horror, and Romance and Comedy, are not greater than the HSD value, indicating no statistically significant differences in their ratings.

<img width="1434" alt="HSD_7" src="https://github.com/user-attachments/assets/668cbdc3-2e35-412a-ae6e-40dd35729149">

# Using Python

In Python, we can easily conduct Tukey’s HSD test using the `pairwise_tukeyhsd` library.

Here are the results obtained using the `pairwise_tukeyhsd` library:

<img width="1175" alt="HSD-8" src="https://github.com/user-attachments/assets/997609cb-f137-4c91-bbcd-ac984416cfb2">

We can focus directly on the "p-adj" (adjusted p-value) column. Given our significance level of 0.05, we reject the null hypothesis (H0) for groups with a p-adj value less than 0.05. Specifically, this applies to the Comedy and Horror groups.




