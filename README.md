# assignment8.01

Word count using pig:

lines = LOAD '/home/acadgild/file.txt' AS (line:chararray);
words =  FOREACH lines GENERATE FLATTEN(TOKENIZE(line)) as word;
grpwrd = GROUP words by word;
wrd_cnt = FOREACH grpwrd GENERATE group,COUNT(words);
dump wrd_cnt;
