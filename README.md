# Map-Reduce

Specifically, the task is divided into 3 parts. :

I Part - PartitionFunction 
Complete the partition function, making sure to use a hash that can handle: integers and strings.

II Part - RunSystem 
Complete the “runSystem(self)” method which divides the data into chunks and schedules the running of mapTasks and reduceTasks. The are two places to complete:
(1) Divide up the data into chunks according to num_map_tasks, and launch a map task per chunk.
(2) Send each key-value pair to its assigned reducer.

III Part - Combiner
Edit the “MapTask” method to add support for running a Combiner. Look for “#<<COMPLETE>>”  within the method. Remember, a combiner runs the reduce task at the end of the map task in order to save communication cost of sending to multiple reducers. Note: main will run the WordCountBasicMR to test with and without the combiner. It is recommended that you look over the WordCountBasicMR to understand what it is doing.  You can assume your combiner code will only run on reducers that are both commutative and associative (see hint at bottom).

IV Part - Mean CharsMR 
Edit the “map” and “reduce” methods of “MeanCharsMR” to implement a map-reduce computation of the mean and standard deviation of the number of each character (a-z, case insensitive) per document (i.e. the mean is across all documents; the count of each character is per document). Consider each record (i.e. single key value pairs arriving at mapper) to be a single document. Reduce can return more than the mean, and standard deviation (hint: including other items will be helpful for the combiner to run).  
Example: if one had three documents: [‘a bacd a’, ‘cda’, ‘bcd’], then the mean of each char would be:
(‘a’: {‘mean’: 1.333 = (3+1+0) / 3, ‘std-dev’: 1.52 = sqrt(((3-1.333)^2 + (1-1.333)^2 + (0 - 1.333)^2)/2)}),

(‘b’: {‘mean’: 0.666 = (1+0+1)/3; … }), …
