# Dual_Coordinate_Descent_for_Large-scale_Linear_SVM

Collaborators: [Dumitrache Larisa](https://github.com/DLarisa),
               [Stegarescu Ana-Maria](https://github.com/StegarescuAnaMaria)
               
We implemented 3 algorithms described in the original paper, in order to determine which gives better results. These algorithms are meant to divide large amounts of data by their classes.

The [dataset](https://www.csie.ntu.edu.tw/~cjlin/libsvmtools/datasets/binary.html#a9a) consists of separate arrays of numbers on each line, representing different n-dimensional points of the cardinal system. The first number represents the class of the point, "-1" or "+1", accompanied by the scaled coordinates (in proportion to 1). The goal of the algorithms is determining the correct weight, so that w*x <= y if y = -1 and    w*x >= y if y = 1, where x is the cardinal point, w is the weight and y is the class, and the distance between the closest to each other 2 points of opposite classes is maximum.

![](images/image1.png)

(the bias (b) from the above graphs will not be taken into consideration)

The first two algoritms are very similar, but the 2nd converges faster:

![](images/image2.png)
![](images/image3.png)

The first algorithm continues to change the value of the weights until w*x >= y or w*x <= y is met for all x. The 2nd algorithm optimizes only the values that need to be optimized.

The 3rd algorithm seems to take more steps than the other two:

![](images/image4.png)

In case the data cannot be completely separable, a small error is allowed. A penalisation variable, C, is introduced. The larger the value of C, the harder the algorithms are trying to separate the data, without paying attention to keeping the distance between two points of separate classes maximum. The lower the value of C, the more outliers are allowed whilst trying to maximize said distance. 

![](images/image7.png)

![](images/image8.png)

We used different types of losses for calculating the convergence, L1-SVM and L2-SVM. Here are the results, in order by the loss, algorithm, the weights, number of steps, and time in seconds.

![](images/image5.png) 

![](images/image6.png)



