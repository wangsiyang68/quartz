## What is it?
- The ideal representation of 3D motion projected onto a 2D plane
- The motion field can be represented as a function which maps image coordinates to a 2-dimensional vector

## Components:  
- moving 3D point
- projection of 3D points
- velocity at scene (?) point

## Relation to Optical Flow
The motion field is an ideal construction, based on the idea that it is possible to determine the motion of each image point, and above it is described how this 2D motion is related to 3D motion. In practice, however, the true motion field can only be approximated based on measurements on image data. 

The problem is that in most cases each **image point has an individual motion**(?) which therefore has to be locally measured by means of a [neighborhood operation](https://en.wikipedia.org/wiki/Neighborhood_operation "Neighborhood operation") on the image data. 

As consequence, the correct motion field cannot be determined for certain types of neighborhood and instead an approximation, often referred to as the [[optical flow]], has to be used. For example, a neighborhood which has a constant intensity may correspond to a non-zero motion field, but the optical flow is zero since no local image motion can be measured.


#cv 