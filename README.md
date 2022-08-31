# Mining Big Datasets
 
# Assignment 1 ( Data Mining ) 

The goal of this assignment is to implement a simple workflow that will assess the
similarity between bank customers and suggest for any input customer a list of his/her
10 most similar other customers. Moreover, you will be using these results to predict
the rating of the customer to the bank. To calculate the similarity between customers
you will first have to compute the dissimilarity for every given attribute as discussed
in lecture “Measuring Data Similarity”.
In order to fulfill this assignment, you will have to perform the following tasks:
##### 1) Import and pre-process the dataset with customers
Download the bank.csv dataset from moodle. This dataset is related with direct
marketing campaigns of a Portuguese banking institution. The marketing campaigns
were based on phone calls to access the opinion of the customer to the bank service
and products. The dataset includes 43191 bank customer profiles with 10 attributes
each. Below is a description of the available attributes:
Age: The age of the customer.
Job: type of job (admin, unknown, unemployed, management, housemaid,
entrepreneur, student, blue-collar, self-employed, retired, technician, services).
Marital Status: Married, Single, Divorced.
Education: Primary, Secondary, Tertiary.
Default: If the customer has credit in default (yes/no).
Balance: average yearly balance, in euros.
Housing: if the customer has a housing loan (yes/no).
Loan: if the customer has a personal loan (yes/no)
Customer Rating: The rating of the bank from the customer (Poor, Fair, Good, Very
Good, Excellent).
Products: An array containing the bank products (1-20) each customer has.
For any numerical values missing, you should replace them with the average value of
the attribute in the dataset (rounded to the nearest integer). The replaced average
values calculated should be reported in the pdf.
##### 2) Compute data (dis-)similarity
To assess the similarity between the customers you could form the dissimilarity matrix
for all given attributes. As described in lecture “Measuring Data Similarity”, for every
given attribute you first distinguish its type (categorical, ordinal, numerical or set) and
then compute the dissimilarity of its values accordingly. For set similarity use the
Jaccard similarity between sets. Then, you can calculate the average of the computed
dissimilarities to derive the dissimilarity over all attributes. Depending on the machine
used to implement this assignment you should decide whether it is feasible to
compute the dissimilarity matrices, or, have the computations performed on-the-fly
for a pair of customers.
#### 3) Nearest Neighbor (NN) search
Using the implementation of the previous step, you will calculate the 10-NN (most
similar) customers for the customers with ids listed below (customer id=line number-
1):
1200, 3650, 10400, 14930, 22330, 25671, 29311, 34650, 39200, 42000
For this task your script must take as input the customer-id and return the list of her
10 nearest neighbors (most similar), along with the corresponding similarity score.
