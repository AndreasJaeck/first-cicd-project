# Batch Inference
To set up batch inference job via scheduled Databricks workflow, please refer to [first_cicd_project/resources/README.md](../../resources/README.md)

## Prepare the batch inference input table for the example Project
Please run the following code in a notebook to generate the example batch inference input table.

```
df = spark.table(
    "delta.`dbfs:/databricks-datasets/nyctaxi-with-zipcodes/subsampled`"
).drop("fare_amount")

df.write.mode("overwrite").saveAsTable(
    name="<catalog>.first_cicd_project.feature_store_inference_input"
)
```

