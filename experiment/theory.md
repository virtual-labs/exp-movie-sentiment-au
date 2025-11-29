<h4>Understanding Naive Bayes for Sentiment Analysis</h4>

<h5>1. Introduction</h5>
<p>Sentiment analysis is a natural language processing (NLP) technique used to determine whether a given piece of text expresses a positive, negative, or neutral sentiment. It is widely applied in various domains such as customer feedback analysis, social media monitoring, and market research.</p>

<h5>2. Importance of Sentiment Analysis</h5>
<ul>
  <li>Enables businesses to understand customer emotions and opinions.</li>
  <li>Automates the analysis of large volumes of text data.</li>
  <li>Improves decision-making by identifying trends and customer satisfaction levels.</li>
  <li>Used in recommendation systems, brand monitoring, and product reviews.</li>
</ul>

<h5>3. What is Naive Bayes?</h5>
<p>Naive Bayes is a supervised learning algorithm based on Bayes' Theorem. It is particularly effective for text classification tasks like spam detection and sentiment analysis.</p>

<h5>3.1 Bayes' Theorem</h5>
<p>Bayes' Theorem describes the probability of an event occurring based on prior knowledge of related conditions.</p>

**Formula:**

$$ P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)} $$

<ul>
  <li><b>P(A|B)</b> → Posterior probability of class A given feature B</li>
  <li><b>P(B|A)</b> → Likelihood: probability of feature B given class A</li>
  <li><b>P(A)</b> → Prior probability of class A</li>
  <li><b>P(B)</b> → Evidence: probability of feature B</li>
</ul>

<h5>3.2 Why is it Called "Naive"?</h5>
<p>The algorithm assumes that all features (words in a review) are conditionally independent given the class label — a "naive" assumption that is rarely true in language, yet the classifier still performs remarkably well.</p>

<h5>3.3 Mathematical Formulation of Naive Bayes for Sentiment Analysis</h5>

<p>Given a document (review) <i>X</i> with words \( w_1, w_2, ..., w_n \), we want to find the most probable class <i>C</i> (Positive or Negative):</p>

$$ P(C|X) = \frac{P(X|C) \cdot P(C)}{P(X)} $$

Since \( P(X) \) is constant across classes, we only need to maximize:

$$ P(C|X) \propto P(C) \cdot P(X|C) $$

Under the <strong>naive independence assumption</strong>:

$$ P(X|C) = P(w_1, w_2, \dots, w_n | C) = \prod_{i=1}^{n} P(w_i | C) $$

So the final scoring function becomes:

$$ P(C|X) \propto P(C) \cdot \prod_{i=1}^{n} P(w_i | C) $$

<h5>Laplace (Add-One) Smoothing</h5>
<p>To avoid zero probabilities for unseen words:</p>

$$ P(w_i | C) = \frac{\text{count}(w_i, C) + 1}{\text{total words in } C + |V|} $$

where \( |V| \) = vocabulary size.

<h5>Log Probabilities (for Numerical Stability)</h5>
<p>Instead of multiplying many small probabilities (risking underflow), we use logarithms:</p>

$$ \log P(C|X) = \log P(C) + \sum_{i=1}^{n} \log P(w_i | C) $$

We classify the review to the class with the highest log probability.

<h5>4. Steps in Sentiment Analysis Using Naive Bayes</h5>

<h5>Step 1: Obtain a Dataset</h5>
<p>A labeled dataset of movie reviews (positive/negative) is collected.</p>

<h5>Step 2: Preprocess the Data</h5>
<ul>
  <li><b>Convert to lowercase</b></li>
  <li><b>Remove punctuation and special characters</b></li>
  <li><b>Remove stopwords</b> (e.g., "the", "is", "and")</li>
  <li><b>Tokenization</b> – split text into words</li>
  <li>(Optional) Stemming/Lemmatization</li>
</ul>

<h5>Step 3: Split Data into Training and Testing Sets</h5>
<p>Typically 80% training, 20% testing (or use cross-validation).</p>

<h5>Step 4: Train the Naive Bayes Model</h5>
<ul>
  <li>Compute prior: \( P(C) = \frac{\text{# documents in class C}}{\text{total documents}} \)</li>
  <li>Compute likelihoods \( P(w_i | C) \) with Laplace smoothing</li>
</ul>

<h5>Step 5: Classify New Reviews</h5>
<p>For a new review, compute log probability for each class and pick the highest.</p>

<h5>Step 6: Evaluate Model Performance</h5>
<ul>
  <li><b>Accuracy</b></li>
  <li><b>Precision, Recall, F1-score</b> (especially important for imbalanced datasets)</li>
  <li>Confusion matrix</li>
</ul>

<h5>5. Advantages of Naive Bayes in Sentiment Analysis</h5>
<ul>
  <li>Very fast training and prediction</li>
  <li>Works well with high-dimensional text data</li>
  <li>Surprisingly effective despite strong independence assumption</li>
  <li>Requires relatively little training data</li>
</ul>

<h5>6. Limitations of Naive Bayes</h5>
<ul>
  <li>Feature independence assumption is violated in real language</li>
  <li>Poor at capturing sarcasm, negation ("not good"), and context</li>
  <li>Zero probability problem if a word wasn't seen in training (mitigated by smoothing)</li>
</ul>

<h5>7. Key Takeaways</h5>
<ul>
  <li>Naive Bayes is a simple, fast, and surprisingly powerful baseline for sentiment analysis</li>
  <li>Text preprocessing significantly impacts performance</li>
  <li>Laplace smoothing and log probabilities are essential practical tricks</li>
  <li>Always evaluate using proper metrics on unseen data</li>
</ul>