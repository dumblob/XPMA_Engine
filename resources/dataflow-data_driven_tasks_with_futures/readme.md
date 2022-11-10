Slides of Data-Driven Futures: http://cnc11.hpcgarage.org/slides/Tasirlar.pdf

Cholesky with Data-Driven Futures

![image](https://user-images.githubusercontent.com/22738317/71618165-c78e6500-2bbe-11ea-95e8-6b35aa178fe4.png)

This can be benched against either LAPACK Cholesky or a lower-level OpenMP task dependency based Cholesky from http://www.netlib.org/utk/people/JackDongarra/PAPERS/task-based-cholesky.pdf
![image](https://user-images.githubusercontent.com/22738317/71618224-16d49580-2bbf-11ea-8498-b082737f6c7e.png)

Here is LU Decomposition and Cholesky Decomposition in pseudo code and dependency graph from http://www.cs.ucy.ac.cy/dfmworkshop/wp-content/uploads/2014/07/Exploring-HPC-Parallelism-with-Data-Driven-Multithreating.pdf

![image](https://user-images.githubusercontent.com/22738317/71618486-0a047180-2bc0-11ea-8bd9-0769975d6d48.png)

![image](https://user-images.githubusercontent.com/22738317/71618511-1f799b80-2bc0-11ea-94a5-6056af15fa62.png)


## Side thoughts

### Stream Pipeline and graph parallelism

Data-driven futures seem suitable to express pipeline and graph parallelism

### Heterogeneous computing

Besides the distributed computing scenario another thing to keep in my mind is if that helps or hinders heterogeneous (distributed?) CPU + GPU computing
