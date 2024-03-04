Just a way of adding matrices with different dimensions together
- If dimension shape does not match (e.g. 2x1 and 1), then prepend the smaller pytorch tensor with a 1
- If the dimension size does not match and one of them is 1 (e.g. 2x1 and 1x1), then broadcast the tensor along the '1' dimension such that it matches that of the larger one (2x1)

#ml