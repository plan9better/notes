Requires 2 [S3](S3.md) buckets, 1 with the data e.g. a csv file with customer info and another for output.

- To start querying, create a table from S3 datasource or with AWS [Glue Crawler](Glue%20Crawler), in *Data format*  section choose the file format of your data, the rest is how the data will be stored and most of the time doesn't matter.
- Next choose the format of columns in *Column details* section. Remember to remove all quotes and misplaced commas since this will not fix it for you.