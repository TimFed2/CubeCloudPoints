# CubeCloudPoints
There is a point cloud of 500 points where at least 30% of them belong to the cube and the rest are noise. The length of a side of the cube is from 20 to 40% of the diameter of the cloud. The goal is to detect all angles of the cube.

## Solution description
The main algorithm for finding the plane is RANSAC. I tuned and transformed this algorithm to my problem. 

1. I get rid of the most noise points by scanning the space and finding an area with the highest number of points in it. 
2. I apply the RANSAC algorithm 3 times and find the first 3 planes. 
3. I check if those planes are unique (perpendicular or paralel to each other). If the found planes are incorrect, I then apply RANSAC algorithm with another set of parameters. 
4. Then we find the 4th plane. Let's consider the following options:
  1. If we have 2 pairs of parallel planes, we need to find the 5th one.
  2. If we don't have 2 pairs of parallel planes, then those 4 planes are enough to find all the vertices coordinates with the help of geometry.
5. After finding the 4th and the 5th planes we also make the same check on uniqueness of the planes.
