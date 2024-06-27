M PowerQuery query to create tables with columns and rows, 

This is useful for testing and learning purposes, we will need to change the data frequently

To change the data, go to data model tab in power bi and right click on the table and select 'Edit query' and edit away to your hearts content

PS> Use ChatGPT to autogenerate scripts


// Create the Sales table
let
    Source_Sales = Table.FromRecords({
        [SalesID = 101, ProductID = 1, Quantity = 10, Date = #date(2023, 6, 1)],
        [SalesID = 102, ProductID = 2, Quantity = 20, Date = #date(2023, 6, 2)],
        [SalesID = 103, ProductID = 3, Quantity = 15, Date = #date(2023, 6, 3)],
        [SalesID = 104, ProductID = 4, Quantity = 10, Date = #date(2023, 6, 4)],
        [SalesID = 105, ProductID = 5, Quantity = 5, Date = #date(2023, 6, 5)]
    }),
    Sales_Table = Table.TransformColumnTypes(Source_Sales, {
        {"SalesID", Int64.Type}, 
        {"ProductID", Int64.Type}, 
        {"Quantity", Int64.Type}, 
        {"Date", type date}
    })
in
    Sales_Table
Follow these steps to create the tables:

Open Power BI Desktop.
Click on the "Home" tab.
Click on "Get Data" and select "Blank Query".
Click on "Advanced Editor" in the "Home" tab.
Copy and paste the script for the Product table into the Advanced Editor and click "Done".
Rename this query to Product.
Repeat steps 2 to 6, but this time paste the script for the Sales table.
Rename this query to Sales.
