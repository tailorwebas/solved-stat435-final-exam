Download Link: https://assignmentchef.com/product/solved-stat435-final-exam
<br>
<strong>Problem 1: </strong>This problem motivates the use of the Gini index as a splitting criterion in CART classification. For background see ISLR Chapter 8.1.3. We will consider a two class classification problem with unit loss:

<table width="210">

 <tbody>

  <tr>

   <td width="95"><em>R</em><sub>0</sub></td>

   <td width="25">=</td>

   <td width="89">[0<em>,</em>3] × [0<em>,</em>3]</td>

  </tr>

  <tr>

   <td width="95"><em>R</em><sub>1</sub></td>

   <td width="25">=</td>

   <td width="89">[0<em>,</em>1] × [0<em>,</em>1]</td>

  </tr>

  <tr>

   <td width="95"><em>p</em>(<strong>x </strong>|<em>Y </em>= 0)</td>

   <td width="25">=</td>

   <td width="89">Uniform(<em>R</em><sub>0</sub>)</td>

  </tr>

  <tr>

   <td width="95"><em>p</em>(<strong>x </strong>|<em>Y </em>= 1)</td>

   <td width="25">=</td>

   <td width="89">Uniform(<em>R</em><sub>1</sub>)</td>

  </tr>

  <tr>

   <td width="95"><em>π</em><sub>0</sub></td>

   <td width="25">=</td>

   <td width="89">7<em>/</em>8</td>

  </tr>

  <tr>

   <td width="95"><em>π</em><sub>1</sub></td>

   <td width="25">=</td>

   <td width="89">1<em>/</em>8</td>

  </tr>

  <tr>

   <td width="95"><em>L</em>(0<em>,</em>1)</td>

   <td width="25">=</td>

   <td width="89"><em>L</em>(1<em>,</em>0) = 1</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>What is the minimum risk prediction rule for a tree consisting only of the root node? What is the corresponding risk?</li>

 <li>Now consider a tree with leaves <em>N<sub>l </sub></em>= [0<em>,</em>1] × [0<em>,</em>3] and <em>N<sub>r </sub></em>= (1<em>,</em>3] × [0<em>,</em>3] What is the minimum risk prediction rule for this tree? What is the corresponding risk? Did splitting reduce the risk?</li>

 <li> Is there a different split of <em>R</em><sub>0 </sub>into two axis parallel boxes that would the reduce the risk? Justify your answer.</li>

</ul>

Now consider the probabilistic classification rule that predicts <em>y </em>= <em>i </em>with probability <em>p<sub>i </sub></em>(in contrast to the optimal rule that predicts <em>y </em>= argmax<em><sub>i</sub></em>(<em>p<sub>i</sub></em>)).

<ul>

 <li>(10 points) What is the risk of the probabilistic rule for the tree that consists only of the root node?</li>

 <li>(10 points) Now consider a tree with leaves <em>N<sub>l </sub></em>= [0<em>,</em>1] × [0<em>,</em>3] and <em>N<sub>r </sub></em>= (1<em>,</em>3] × [0<em>,</em>3]. What is the risk of the probabilistic rule for this tree? Did splitting reduce the risk?</li>

 <li>(10 points) Is there a different split of <em>R</em><sub>0 </sub>into two axis parallel boxes for which the probabilistic rule has a smaller risk than computed in (e)?</li>

</ul>

<strong>Problem 2: </strong> In this problem you will do spam classification. Consider the email spam dataset (in “spam.data”). This consists of 4601 email messages, from which 57 features (or covariates) have been extracted. These are as follows:

<ul>

 <li>48 features, in [0<em>,</em>100], giving the percentage of words in a given message which match a given word on the list. The list contains words such as “business”, ‘ ‘free”, “george”, etc.</li>

 <li>6 features, in [0<em>,</em>100], giving the percentage of characters in the email that match a given character on the list. The characters are ; ( [ ! $ #</li>

 <li>Feature 55: The average length of an uninterrupted sequence of capital letters</li>

 <li>Feature 56: The length of the longest uninterrupted sequence of capital letters</li>

 <li>Feature 57: The sum of the lengths of uninterrupted sequence of capital letters</li>

</ul>

More detail about the data can be found in the file “spam.info”.

Load the data from “spam.data”, in which Columns 1-57 are the features and Column 58 is our response variable, the indicator of spam emails (1 is spam and 0 is non-spam). Divide the dataset into a training set (of size 3065) and a test set (of size 1536) by the indicator in the file “spam.traintest” (1 is test set and 0 is training set).

<ul>

 <li> Fit a classification tree to the training set. Plot the fitted un-pruned tree. Make binary predictions and report the error rate on the training and test sets.</li>

 <li>Prune the tree and select the optimal tuning parameter <em>λ </em>by minimizing the 10-fold cross validation error with the one standard error rule (1-SE Rule). The 1-SE Rule means that we should choose a simpler model if its penalized RSS is less than 1 SE worse than the next complex model. Plot the fitted pruned tree. Make binary predictions and report the error rate on the training and test sets.</li>

</ul>

<em>Hint: You may find the “rpart” package in R helpful. The examples in the introduction below are also helpful.</em>

<em>http://cran.r-project.org/web/packages/rpart/vignettes/longintro.pdf </em><strong>Problem 4: </strong>(60 points) In this problem you will apply a k-nearest neighbor classifier to the handwritten digit data. The data are divided into a training set zip-train.dat and test set zip-test.dat. Both data sets have lines of length 257. The first entry in each line is the digit that was written (0<em>,…</em>9) and the remaining 256 entries are grey levels pixels in a 16 × 16 bitmap.

<strong>(a) </strong> Write an R function knn.classifier(X.train, y.train, X.test, k.try = 1, pi = rep(1/K, K), CV = F)

where X.train, y.train, X.test have the obvious meanings; k.try is a vector of neighborhood sizes; pi is a vector of prior probabilities; CV = T if leave-onout cross-validation is to be used.

CV = T only makes sense if X.train = X.test

The function should return a (n.test x length(k.try)) matrix of predicted class identities for the n.test test observations and the different values of <em>k </em>provided in k.try.

<ul>

 <li> Run the function on the Iris data with k = 5 and with both choices for CV. Print the respective number of misclassifications.</li>

 <li> Run the function on the hand-written digit training data with k.try = c(1, 3, 7, 11, 15, 21, 27, 35, 43) and CV = T. Use unweighted Euclidean distance as a dissimilarity measure. Choose the priors to reflect the class frequencies in the training data. What is the optimal choice of k and the corresponding training error rate?</li>

 <li> Calculate the test set error rate.</li>

</ul>