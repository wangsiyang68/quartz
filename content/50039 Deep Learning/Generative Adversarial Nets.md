## Introduction
Utilise two components: Generator and Discriminator. Both are Neural Networks
- Generator turns random noise into data in dataset to the best of its ability
- Discriminator checks the output from Generator, and checks if it is real (from original dataset) or fake (created by generator)

## Training
- Step 1: Fix generator G, update Discriminator
	- First, train D be able to differentiate between real and fake images real good
	- Second, Train G to fool the discriminator
		- Why don't we use FGSM formula when doing gradient descent update? why need to use some crazy formula?
#dl