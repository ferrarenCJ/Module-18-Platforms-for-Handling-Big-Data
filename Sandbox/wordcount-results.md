# Word Count Results

## Command

```bash
hdfs dfs -cat /output/part-r-00000
```

## Sample Output

```text
hadoop      1
hello       3
mapreduce   1
world       1
```

## Notes

The reducer successfully aggregated word counts from
the input dataset.