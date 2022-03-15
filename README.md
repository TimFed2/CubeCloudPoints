# CubeCloudPoints
Given a cloud of 500 points, at least 30% of them belong to the cube, other are noise. The side of the cube is 20-40% long from cloud diamiter. 
The goal is to detect all angles of the cube.

Solution description:
Firstly, I got rid of most noise points by scaning the space and finding areA with the most amount if points in it.
The main algoritm of finding the plane is Ransac. I tunned and trasnformed this algoritm to my problem.
To start with I apply rasnac 3 times and find 3 planes. After I check if they are correct (perpenicular or paralel to each other and unequal). If there are some problems, I fix them by applying rasnac algoritm with another parameteres.
Then we find the 4th plane, and if we have 2 pairs of paralel planes, we need to find the 5th one, in another case 4 planes are enought to find all the angle coordinates with help of geometry.
After finding new planes we also make a correction check
