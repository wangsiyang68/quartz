To detect Edges, one of the commmon filters used is a **Sobel filter**, which also happens to be separable
![[Pasted image 20230316135404.png]]
- Food for thought: why does the above detect horizontal lines more?

**Why is blurring required during detecting edges?**
![[Pasted image 20230316140430.png]]
Answer: Without blurring, the derivative will not be understandable due to the noise in the image.
Differentiation is very sensitive to noise! Thats why sometimes, the gaussian and derivative is combined to form a DoG filter to be run over the image

**Laplace filter**
- Also known as the second derivative filter
- Difference between the DoG filter is that the edge is found at x-intercept in LoG, and the same edge is found at the maximum point 
- More difficult to implement IRL because difficult to detect x-intercepts (values may not be exact zero)

FAQs
- How is detecting edges related to finding derivatives?
	- Because at edges, derivatives are large at discontinuities
	- Given a discrete image, we use finite differences. **How does this lead us to the 1D derivative filter of (1,0,-1) though?**

#pp