Modify the Binary Cross Entropy formula to do essentially the same thing (calculate the probability of getting the class right for a sample)
Changes made to get the math right:
- Add one-hot vector to only select the Loss result for the correspondingly correct label for that sample
- Calculate the probability for that sample being classified by each of the avail class
- Multiply the above two things element wise and then sum it to neatly show what is the probability of getting the class right for one sample

#dl
