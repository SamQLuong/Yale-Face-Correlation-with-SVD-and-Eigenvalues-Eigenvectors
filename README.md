# Homework-2---Machine-Learning

## Abstract

In this assignment, I will be taking a look at the Yale Face data set. We will be examining the correlation between the faces by using the dot product of the X matrix and the transpose X matrix. Also, I will be taking a look at using the Y = XX^T method to find the eigenvectors and the SVD method to find the principal components. Lastly, I computed the percent variance of the SVD methods and graphed the SVD of the first 6 modes. 

## Section 1 - Introduction

The Yale Face data set is set up to have 2414 images but each sample is down-sampled into 32 by 32 pixels. Therefore, the following matrix that is uploaded to the code is 1024 by 2414 matrix. 1024 is from reshaping the 32 by 32 into a single column of numbers for each image. The following code is to have a deep dive into the process of recognizing the features of the image faces and understanding the process of looking at the eigenvectors, eigenvalues, and SVD methods.  

## Section 2 - Theoretical Background

The purpose of creating the C matrix is to find the correlation between the images. The correlation matrix graph can pinpoint images that are closely correlated and uncorrelated. The diagonal components of C are the representation of the same image being compared to each other. Therefore, it is a good idea to ignore these components to avoid mistakes. To reduce redundancies and order the variance, we must diagonalize the C matrix using two different methods, SVD and eigenvectors/eigenvalues. The SVD method has the ability to take any matrix and turn it into a diagonal matrix. This can be done by reducing the matrix into three different components: U, V, and s. We use these components to break down any matrix into a diagonalized matrix. This gives the SVD method power over the eigenvalue method because it has the ability to convert any matrix into a diagonalized matrix while the eigenvalue method does not have that ability. 

## Section 3 - Algorithm, Implementation, and Development

To create a correlation matrix, I had to create a 100 by 100 matrix of the first 100 images. Then, I would use the following equation, C = X^T * X to model the correlation matrix. We can eyeball areas of the graph that has a high correlation between images by examining the lighter colors. However, this is not a proper way to identify the most correlated images. Therefore, I used the numpy.argmax and numpy.unraveled_index to locate the most correlated images. Argmin can be used to find the least correlated images. Afterward, I graphed the images that are correlated and uncorrelated by reshaping the images into a 32 by 32 matrix. The difficulties of finding the images is that we must ignore the diagonal values of the correlation matrix because the images are comparing itself. To do this, we can replace the entire diagonal with 0’s so that the argmax can ignore those values. We did not have to worry about the minimum since the diagonals are in its highest value.

For the next part of the assignment, I did the same steps for a 10 by 10 matrix but looked at different images throughout the 2414 images listed in the Yales Face data set. The images are located in [1, 313, 512, 5, 2400, 113, 1024, 87, 314, 2005] but subtract one for each value to get the actual index of the images. To do this, I used a for loop to find each column from the X matrix and created a new 10 by 10 matrix. However, I had an issue where it inputted a list and not a 2D array so I had to reshape the list into an array and make it 10 by 10.  Next, I did the correlation equation by using the dot product of the transpose X and X matrix. 

Next, I needed to find the eigenvectors and eigenvalues of the X matrix. Therefore, I used the numpy.linalg.eig and inputted Y = XX^T as the parameter. Afterward, I sorted the eigenvalues and find the index values of each eigenvalues to find the eigenvectors. The matrix returns the first six eigenvectors based on the max eigenvalues. 

For the SVD method, I used the numpy.linalg.svd with the X matrix. This returns a U, s, and V matrix. To find the first 6 principal components, I used the V matrix and found the first 6 principal components.

Next, the assignment asks to find the absolute norm of the difference between the first eigenvector and the first principal. We can do this by using finding the absolute difference between the first column of each matrix. Then, I used the numpy.linalg.norm to find the norm of difference.

Finally, the assignment asks to find the percent variance of the first 6 SVD modes. We can do this by finding the total variance by using numpy.sum and squaring the X matrix. Then, we square the s matrix from the SVD and divide it by the total variance, this is returned as var_exp. To get the percentage, we take each var_exp and divide it by the total sum of var_exp, and multiply it by 100 to get the percentage. 

## Section 4 - Computational Results

The correlation results for the 100 by 100 matrix and the 10 by 10 matrix are shown in Figures 1 and 2. 

![Figure 1](https://github.com/SamQLuong/Yale-Face-Correlation-with-SVD-and-Eigenvalues-Eigenvectors/blob/main/100%20by%20100%20Correlation.png)

Figure 1: A 100 by 100 correlation matrix of 100 Yale Faces

![Figure 2](https://github.com/SamQLuong/Yale-Face-Correlation-with-SVD-and-Eigenvalues-Eigenvectors/blob/main/10%20by%2010%20Correlation.png)

Figure 2: A 10 by 10 correlation matrix of 10 Yale Faces 

For the most correlated images, we can see that images 87 and 89 are the most correlated due to the similar lighting showing the same features in Figure 3. Also, we can see that the most uncorrelated images are images 1 and 65 because Image 65 is an unknown image that doesn’t look like a face at all in Figure 4. Therefore, there are no features that are similar to Image 65.

![Figure 3](https://github.com/SamQLuong/Yale-Face-Correlation-with-SVD-and-Eigenvalues-Eigenvectors/blob/main/Most%20Correlated.png)

Figure 3: The most correlated Yale Faces which is image 87 and 89

![Figure 4](https://github.com/SamQLuong/Yale-Face-Correlation-with-SVD-and-Eigenvalues-Eigenvectors/blob/main/Least%20Correlated.png)

Figure 4: The least correlated Yale Faces which is image 1 and image 65. Notice Image 65 barely resembles a face.

The first six eigenvectors and the first six principal components are in Figures 5 and 6. Then the resulting absolute norm of difference is about 0 between the first eigenvector and the first principal components. We know that this is correct since we want to show that the methods output similar results

![Figure 5](https://github.com/SamQLuong/Yale-Face-Correlation-with-SVD-and-Eigenvalues-Eigenvectors/blob/main/Eigenvalues.png)

Figure 5: The first six eigenvectors based on the maximum eigenvalues

![Figure 6](https://github.com/SamQLuong/Yale-Face-Correlation-with-SVD-and-Eigenvalues-Eigenvectors/blob/main/SVD%20prinipal.png)

Figure 6: The first six principal componets from the SVD method

Lastly, the resulting graph of the percent variance of the first six SVD modes is shown in Figure 7. We can see that the first SVD mode has the highest percent variance which is around 75%. Then, the percent variance decreases exponentially as we go along the SVD modes.

![Figure 7](https://github.com/SamQLuong/Yale-Face-Correlation-with-SVD-and-Eigenvalues-Eigenvectors/blob/main/Percent%20Variance.png)

Figure 7: The percent variance graph of the first six SVD modes. Notice the face decrease of percent variance as we move to each mode.

## Section 5 - Conclusion

The correlation matrix can be done by getting the X matrix of the images and using the dot product with its transpose to get the C matrix. Our pcolor mapping helps shows us the most correlated images in a quick glance. However, to find the most correlated and uncorrelated, we can use simple coding to find the maximum and minimum values of correlation. The most correlated is similar images with a lot of lighting and similar features while the least correlated is two images whereas image 64 is a random face with no features that indicate that it’s a face. Lastly, SVD and eigenvectors have a similar process but the SVD method is simpler to get the values we need. Also, the norm of difference is 0 but coding the SVD is simple compared to the eigenvectors.
