
![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/43bd1f33-579d-436f-8651-f98b9c5ad3c9)

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/b5773559-8ee3-4a64-b4df-263c1f50b865)


![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/b757de73-5820-4213-aa60-c3e7b9997171)

Changing the sale measure by removing the KeepFilter added previously and using that [Sale] measure directly in a column
![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/c703cb8b-a7a2-4681-9c5a-0ee17be7b53b)
![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/d74da0d3-9e9f-42c1-8eca-598a9e511ea0)




## EXAMPLE DAX CODES


#### example 
```
DEFINE
    MEASURE 'Artist'[m1] =
        VAR tbl_Tracks_peak_1 =
		FILTER(
			Track,
			Track[US Billboard Hot 100 peak] = 1
		)
		
		--- OBSERVE: a variable can use Track, the original table, which it was created from 
		RETURN(CONCATENATEX(tbl_Tracks_peak_1,Track[Track name]," | ")) 
		





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

![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/47b69894-de8d-47c7-935f-8b6daae4930d)
