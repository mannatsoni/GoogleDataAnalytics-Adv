## Type Error : datetime64 type does not support sum operations

<b> Course Notebook Code : </b>

df.groupby(['month','month_txt']).sum().sort_values('month', ascending=True).head(12).reset_index()

This code above was throwing an error which was part of the original notebook provided in the course. It is basically summing all the columns, numeric or non-numeric including Datetime64[ns]. Unfortunately pandas can not sum non numeric values (at least not in latest version).

The notebook provided in this course does not throw this error because the pandas version used is 1.3.5, whereas I am suing 2.2.2. This reflects that maybe in order versions Pandas would ignore this automatically, but the way newer versions handle data types, it does not ignore and must be told explicitly. 

Now one might argue that why does Pandas not ignore non-numeric values automatically? Actually Pandas does. However, it treats datetime columns as numeric-like, which are not purely numeric. They are handled differently because they can be used in operations like difference between dates. That is why Pandas when asked to, will perform sum operation on a datetime column. 

