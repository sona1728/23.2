Ques: Explain Primary data types and complex data types in Hive with an example in brief.

Ans:
# Primitive Data Types:
primitive Data Types also divide into 4 types there are mentioned below

- Numeric Data Type
- String Data Type
- Date/Time Data Type
- Miscellaneous Data Type

Here is the common thing between Java,Sql and Hive is The Data types and sizes of Hadoop hive data types is similar to Java and SQL Primitive Data types

1.Numeric Data Type:
Numerical Data types are mainly divided into 2 types

- Integral Data Types
- Floating Data Types
- Integral Data Types 

> TINYINT (This TINYINT is equal to Java’s BYTE data type)
> SMALLINT (This SMALLINT is equal to Java’s SHORT data type)
> INT (This INT is equal to Java’s INT data type)
> BIGINT (This BIGINTis equal to Java’s LONG data type)
> Floating Data Types

> FLOAT (This FLOAT is equal to Java’s FLOAT data type )
> DOUBLE (This DOUBLE is equal to Java’s DOUBLE data type)
> DECIMAL (This DECIMAL is equal to SQL’s DECIMAL data type)


# COMPLEX DATA TYPES:

There are three complex types in hive,

- arrays: It is an ordered collection of elements.The elements in the array must be of the same type.

- map: It is an unordered collection of key-value pairs.Keys must be of primitive types.Values can be of any type.

- struct: It is a collection of elements of different types.

*Examples: complex datatypes

1.ARRAY:

$ cat >arrayfile
1,abc,40000,a$b$c,hyd
2,def,3000,d$f,bang

hive> create table tab7(id int,name string,sal bigint,sub array<string>,city string)
    > row format delimited   
    > fields terminated by ','
    > collection items terminated by '$';

hive>select sub[2] from tab7 where id=1;

hive>select sub[0] from tab7;

2.MAP:

$ cat >mapfile
1,abc,40000,a$b$c,pf#500$epf#200,hyd
2,def,3000,d$f,pf#500,bang

hive>create table tab10(id int,name string,sal bigint,sub array<string>,dud map<string,int>,city string)
row format delimited 
fields terminated by ','
collection items terminated by '$'
map keys terminated by '#';

hive> load data local inpath '/home/training/mapfile' overwrite into table tab10;

hive>select dud["pf"] from tab10; 

hive>select dud["pf"],dud["epf"] from tab10; 

3.STRUCT:

cat >mapfile
1,abc,40000,a$b$c,pf#500$epf#200,hyd$ap$500001
2,def,3000,d$f,pf#500,bang$kar$600038

hive> create table tab11(id int,name string,sal bigint,sub array<string>,dud map<string,int>,addr struct<city:string,state:string,pin:bigint>)
    > row format delimited 
    > fields terminated by ','
    > collection items terminated by '$'
    > map keys terminated by '#';

hive> load data local inpath '/home/training/structfile' into table tab11;

hive>select addr.city from tab11;

