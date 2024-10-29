# Quicksort Pivots

in the lectures I only briefly mentioned strategies for determining a good pivot
for quicksort. The implementation on the slides simply picks the leftmost
element in the part of the array that we consider as a pivot. I also mentioned a
few other ways of picking a good pivot, e.g. randomly.

Median-of-three is also a good way of picking a pivot -- inspect the first,
middle, and last elements of the part of the array under consideration and
choose the median value. Using the probabilities for picking a pivot in a
particular part of the array (in the same way as we did on slide 34), argue
whether this method is more or less (or equally) likely to pick a good pivot
compared to simply choosing the first element. Assume that all permutations are
equally likely, i.e. the input array is ordered randomly.

Your answer must derive probabilities for choosing a good pivot and
quantitatively reason with them.

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

## Analysis

A pivot is considered "good" if it falls within the middle 50% of the sorted array, as this leads to reasonably balanced partitions.

**Left-Most Element Approach**

Since we're choosing the leftmost element as our pivot element and all possible orderings of the array are equally probable, there's a 50% chance that our chosen pivot will partition the array into balanced segments.

We can show this as $\frac{1}{2}$ or 50%

**Median-of-Three Approach**

For the median-of-three method, we should consider all possible scenarios when picking three elements to get a good pivot value. It follows that:
- Probability of selecting a good pivot (middle 50%): $\frac{1}{2}$
- Probability of selecting a value too small (bottom 25%): $\frac{1}{4}$
- Probability of selecting a value too big (top 25%): $\frac{1}{4}$

The scenarios that result in a good pivot are:

1. All three elements are good pivots (1 possible ordering):
   $1 \cdot (\frac{1}{2})^3$

2. Two good pivots and one too small (3 possible orderings):
   $3 \cdot (\frac{1}{2})^2 \cdot \frac{1}{4}$

3. Two good pivots and one too big (3 possible orderings):
   $3 \cdot (\frac{1}{2})^2 \cdot \frac{1}{4}$

4. One good pivot, one too small, and one too big (6 possible orderings):
   $6 \cdot \frac{1}{2} \cdot \frac{1}{4} \cdot \frac{1}{4}$

So, the total probability = $1 \cdot (\frac{1}{2})^3 + 3 \cdot (\frac{1}{2})^2 \cdot \frac{1}{4} + 3 \cdot (\frac{1}{2})^2 \cdot \frac{1}{4} + 6 \cdot \frac{1}{2} \cdot \frac{1}{4} \cdot \frac{1}{4} = 0.6875$


The median-of-three approach has a 68.75% chance of selecting a good pivot, which is much better than the 50% chance of selecting a good pivot when picking the leftmost element.

I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.
