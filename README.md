# US_house_vote_prediction
United States house of representatives vote prediction.


Load “votes.csv” dataset specifying the col names and store it into a local R variable named “votes”


Display the content of the “votes” variable by typing the variable name in RStudio.







=> “summary” R command:
Gives high-level general information about the datasets. According to the t_votes data, the summary displays information regarding the number of rows(434), columns(50), density(0.34), and most frequent items in the dataset. The density is a truly pretty impressive figure that it displays the total number of non-empty cells in the votes matrix. In other words, it is the total number of votes divided by a total number of possible items in the matrix.

Next: element (itemset/transaction) length distribution: sizes
Indicated how many transactions for just one item in the votes dataset: 17 , 434

Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
     17      17      17      17      17      17
Indicates that the minimum vote transaction was 17, the maximum was also 17, and other pieces of information.
The other information we will get from the summary is the label. I will show how the data labels are organized.

includes extended item information - examples:
           labels variables     levels
1   col1=democrat      col1   democrat
2 col1=republican      col1 republican
3          col2=?      col2          ?


Examine the frequency of democrat and republican using the “itemFrequency” R Command. 
Before I started working on the frequency of democrats and republican I have to install a few necessary packages. First, I will install packages called “arules” that provides the infrastructure for representing manipulating, and analyzing data patterns.
To do that: I will use the following command
> install.packages("arules") 
Install “arulesViz”
> install.packages("arulesViz") 

Adding the library called “arules” and “arulesViz” as follow: 




Now if I type “?itemFrequency” I can see some of the R functions to do data manipulation and pattern analysis

Next:
I read the dataset as transactions and saved it by the name t_votes.
t_votes = as(votes, "transaction")




“itemFrequency” will give me 
Democrats frequency is 0.615 whereas republican 0.385.


# itemFrequencyPlot
> itemFrequencyPlot(t_votes, type = ("absolute"))

Democrats are the dominat and voting on export-administration-act-south-africa has height posibility for geting both democrat and republican support.

Plot






“inspect” R command: used to display the list of all items. I have to snapshot some of the results for the command.

If I want to show only the first five elements the command and snapshot will look like as below.


I have used the following command to construct a chart for the first 10 rows.
> itemFrequencyPlot(votes, topN=10, type="absolute")


Construct association rules using the Apriori algorithm. In this exercise, don’t use default values of support and confidence. Instead, try different combinations and select the one you find more appropriate.
Calculate frequent items with support value of 0.07

To see the result I will write this code: Inspect(frequentItems)



Evaluate the association model rule that you constructed using the “summary” R command.
Display all the rules constructed by the model using the “inspect” R command.















Construct association rules using the Apriori algorithm. 


With higher support and confidence value
Democrat:

Democrat will likely to vote yes for adoption-of-the-budget-resolution and aid to Nicaragua contract but will vote no to physician fee freeze.












With lower support and confidence values:
R command rule for the democrat: 


Inspect the rule:



Interpretation: Democrats will most likely say no to crime vote.
		Democrat will most likely say yes to duty-free-exports


Let’s see the possibility of republican will likely to vote yes, or no?



Inspect rules:


• There is a higher probability of Republicans voting yes to physician fee freeze. 

During this exercise I found the popular itemsets by first starting with itemsets containing just a single item as {col1} and {democrat}. And then determine the support for itemsets and generate all the possible itemset configurations. Finally, I repeat until there are no more new itemsets.
I have tried changing the confidence to a very small and big number not seen that much difference. When I come to the confidence, it actually measures how likely republican or democrats will vote positively or negatively to given rules. It measures the likely hood of the party voting, let say yes to one and how likely say yes to another vote as {X -> Y}. This is estimated by the relationship of events with item X, in which item Y also resembles. In the end, I have really enjoyed working with the apriori algorithm since it was a little challenging at the beginning.  What was hard for me was considering votes as a transaction but later on, I will be able to get back on track and finish my assignment. 

References:
R-Statistics.com (no date)Association Mining (Market Basket Analysis)[Online] http://r-statistics.co/Association-Mining-With-R.html [Accessed 30 Dec 2018]
Rprogramming.net (no date)R Programming – Help, How-To’s, and Examples [Online] http://rprogramming.net/ [Accessed 31 Dec 2018]


