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
**`P(A|B) = [P(B|A) × P(A)] / P(B)`**

<ul>
  <li><strong>P(A|B)</strong> → Posterior probability</li>
  <li><strong>P(B|A)</strong> → Likelihood</li>
  <li><strong>P(A)</strong> → Prior probability of class</li>
  <li><strong>P(B)</strong> → Evidence</li>
</ul>

<h5>3.2 Why is it Called "Naive"?</h5>
<p>The algorithm assumes that all features (words in a review) are conditionally independent given the class label — a "naive" assumption that is rarely true in language, yet the classifier still performs remarkably well.</p>

<h5>3.3 Mathematical Formulation of Naive Bayes for Sentiment Analysis</h5>

<p>Given a document X with words w₁, w₂, …, wₙ, we want to find the most probable class C:</p>

**`P(C|X) = [P(X|C) × P(C)] / P(X)`**

Since P(X) is constant, we maximize:

**`P(C|X) ∝ P(C) × P(X|C)`**

Under the naive independence assumption:

**`P(X|C) = Π(i=1 to n) P(w_i|C)`**

Final scoring function:

**`P(C|X) ∝ P(C) × Π(i=1 to n) P(w_i|C)`**

<h5>Laplace (Add-One) Smoothing</h5>
<p>To avoid zero probabilities for unseen words:</p>

**`P(w_i|C) = (count(w_i, C) + 1) / (total words in class C + |V|)`**

where |V| = vocabulary size.

<h5>Log Probabilities (for Numerical Stability)</h5>
<p>Instead of multiplying tiny numbers, we use log:</p>

**`log P(C|X) = log P(C) + Σ(i=1 to n) log P(w_i|C)`**

We pick the class with the highest log score.

<h5>4. Steps in Sentiment Analysis Using Naive Bayes</h5>

<h5>Step 4: Train the Naive Bayes Model</h5>
<ul>
  <li>Prior probability:<br>
  **`P(C) = (number of documents in class C) / (total number of documents)`**</li>
  <li>Likelihoods computed using Laplace smoothing (formula above)</li>
</ul>

(All other steps remain the same — only formulas are highlighted)

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