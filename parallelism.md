## Data Parallelism vs Model Parallelism
Decreasing a program's total run time is always a benefit. Data parallelism and model parallelism provide two unique and efficient ways for doing this. In this post we will discuss what these terms mean and what makes them distinct.

## Data Parallelism
Data parallelism is a common method and generally easier to implement. In this approach, we split the data up into n sections where n is the number of cores or machines you'll be distributing across. Each core or machine then independently tries to estimate the same parameters and their results are sent to a "master" model. In our project, we use Uber's Horovod pip package which uses Data Parallelism to distribute our keras model across several machines.

![alt text](https://github.com/maxpumperla/elephas/blob/master/elephas.gif?raw=true)


## Model Parallelism
Model parallelism is more difficult to implement and not as easily available through third party packages. In model parallelism, all of the data is sent to all of the cores or machines you are using. Each core or machines estimates different parameters then combines the results in a "master" model. 

## When to Use
If there are a large number of parameters and nodes then model parallelism is preferred. Otherwise, use data parallelism.
