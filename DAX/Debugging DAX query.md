We can debug DAX queries and measures using **POWER BI DAX Query View** or **DAX Studio**

https://www.youtube.com/watch?v=tQrr7RPSvsQ

This video contains some useful queries on how to query data from tables with DAX



## My experience 

DAX query to be executed, if we want to see how a measure executes in a filter context :

```
DEFINE
    MEASURE 'Artist'[m1] =
        CONCATENATEX (
            FILTER (
                Track,
                Track[US Billboard Hot 100 peak] = 1
            ),
            Track[Track name],
            " | "
        )

EVALUATE
// {[m1]}
{
    CALCULATE (
        [m1],
        TREATAS (   ---- TREATAS works as filter context for the execution of the measure
            {
                "Bon Jovi"
            },
            Artist[Artist]
        )
    )
}
```

