# junyperSqlAssignment


## Setup

The first thing to do in this assignment, is to follow the guidelines laid out in the slides, in order to connect to the database


```sh
docker run -p 5432:5432 --name data -d jegp/soft2018-data

docker run -p 8888:8888 --name jupyter --link data -v `pwd`:/home/jovyan -it jegp/soft2018-jupyter

```


Then i go to localhost:8888, and make a new Phyton 3 project/file.


## Jupyter file

The first thing to do is to load the SQL extension and connect to the other docker postgresql docker container (usr: appdev):

```sh
%load_ext sql

%sql postgresql://appdev@data/appdev
```



Then i can start to work on the dataset.

![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")


### Genre Union

This question ask us to find the union of the datasets where track.genreId is 18 and 20 respectively. 
To accomplish this i use the following statement:


```sql
%sql SELECT * FROM chinook.track WHERE genreid = 20 UNION ALL SELECT * FROM chinook.track WHERE genreid = 18;
```

giving the following 39 results:





### Invoice Intersection

Here i need to find the intersection of the result sets where an invoice.otal is less than 10 USD and the set of invoices
where invoice.total is more than 5.

```sql
%sql SELECT * FROM chinook.invoice WHERE total < 10 INTERSECT SELECT * FROM chinook.invoice WHERE total > 5;
```

I find 115 results where total is between 5 and 10.
