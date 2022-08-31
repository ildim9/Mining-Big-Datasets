# Mining Big Datasets
 
# Assignment 1 ( Data Mining ) 

The goal of this assignment is to implement a simple workflow that will assess the
similarity between bank customers and suggest for any input customer a list of his/her
10 most similar other customers. Moreover, you will be using these results to predict
the rating of the customer to the bank. To calculate the similarity between customers
you will first have to compute the dissimilarity for every given attribute as discussed
in lecture “Measuring Data Similarity”.
In order to fulfill this assignment, you will have to perform the following tasks:
#### 1) Import and pre-process the dataset with customers
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
#### 2) Compute data (dis-)similarity
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
 
#### 4) Customer rating prediction
For this assignment you will implement a classification algorithm which, for a given
customer, will predict his rating (poor, fair, good, very good, excellent) for the bank.
In order to implement the classification for a given customer you need to:
1) Calculate the similarities between the given customer and all other customers and
compute his 10-nn (most similar) customers. IMPORTANT: In the similarity
calculations for this step you need to exclude the customer rating attribute.
2) Based only on the 10 most similar customers computed in the previous step, predict
the customer rating rank using:
 The average rating rank of the 10 most similar customers (rounded to the
nearest integer).
 The weighted average rating rank of the 10 most similar customers (rounded
to the nearest integer).
Weighted average rating_rank = ∑ [similarity(i) ∗ rank(rating(i))]10
i=1
∑ similarity(i)10
i=1
Where:
o rating(i) = the rating of the i-th nearest neighbor (i=1 for the most
similar customer)
o similarity(i) = the similarity of the i-th nearest neighbor with the
given customer
3) For the evaluation of your classification algorithm you will use the 50 first records
of the bank dataset and predict the rating for them. Then, for all n=50 records
calculate the Mean Prediction Error for both prediction methods.


# Assignment 2 ( Neo4j ) 
##### Dataset:
You are given a part of OpenFlights Airports network, which contains airports, airlines
and flights between airports. In particular, the dataset contains 7698 Airports, 6161
Airlines, 6956 Cities, 237 Countries and 65.935 Flights between Airports. You can
download the dataset (Airline Dataset) from moodle in csv format. The dataset
contains 3 csv files and a description for the attributes in each file.
##### Property graph model
You are asked to model the data as a property graph by designing the appropriate
entities and assigning the relevant labels, types and properties. For your modeling,
you need to study the details of all the files that describe the airline network and
represent the required attributes on nodes and edges of a graph (Not all attributes in
the csv files are required in the model). In your model you should include only the
attributes that describe each node and edge type, without repetitions of elements
(e.g. same property being displayed on both a node and an edge). Finally, nodes
should not be connected when this is not required by the model.
##### Importing the dataset into Neo4j
Based on your model, you should create a graph database on Neo4j and load the
airline network elements (nodes, edges, attributes). You can load the dataset directly
from the provided csv files, by using either the neo4j browser or the neo4j import tool,
or any programming language that is supported by neo4j. To speed up loading and
query response times, you could also create proper indexes on your model properties.
##### Querying the database
After the creation of your database, you are asked to write and execute the following
queries using the Cypher language.
Queries:
1) Which are the top 5 airports with the most flights. Return airport name and number
of flights.
2) Which are the top 5 countries with the most airports. Return country name and
number of airports.
3) Which are the top 5 airlines with international flights from/to ‘Greece’. Return
airline name and number of flights.
4) Which are the top 5 airlines with local flights inside ‘Germany’. Return airline name
and number of flights.
5) Which are the top 10 countries with flights to Greece. Return country name and
number of flights.
6) Find the percentage of air traffic (inbound and outbound) for every city in Greece.
Return city name and the corresponding traffic percentage in descending order.
7) Find the number of international flights to Greece with plane types ‘738’ and ‘320’.
Return for each plane type the number of flights.
8) Which are the top 5 flights that cover the biggest distance between two airports
(use function point({ longitude: s1.longitude, latitude: s1.latitude }) and function
distance(point1, point2)). Return From (airport), To (airport) and distance in km.
9) Find 5 cities that are not connected with direct flights to ‘Berlin’. Score the cities in
descending order with the total number of flights to other destinations. Return city
name and score.
10) Find all shortest paths from ‘Athens’ to ‘Sydney’. Use only relations between flights
and city airports
