## Definition
**Task**: Given two subsequent frames, estimate the apparent motion field u(x,y) and v(x,y) between them

Optical Flow is the apparent motion of brightness patterns in the image
-  Ideally, optical flow would be the same as the [[Motion Field]]. Realistically, it is instead an approximation of it
- **Note**: apparent motion can be caused by lighting changes without any actual motion

## Estimating optical flow
- Given two subsequent frames, estimate the apparent motion field between them
- Assumptions
	1. Brightness constancy: projection of the same point looks the same in every frame
	2. Small motion: Objects do not move very far
	3. Spatial coherence: points move like their neighbors


Link to [[Aperture Problem]]?
#cv