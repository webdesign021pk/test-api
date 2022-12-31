# test-api
we have 6 tables, all tables have 8 columns with 10 rows of random data.
example:
Table1 [Table1Id,column2,column3,column4,column5,column6,column7,column8]
Table2 [Table2Id,column2,column3,column4,column5,column6,column7,column8]
Table3 [Table3Id,column2,column3,column4,column5,column6,column7,column8]
Table4 [Table4Id,column2,column3,column4,column5,column6,column7,column8]
Table5 [Table5Id,column2,column3,column4,column5,column6,column7,column8]
Table6 [Table6Id,column2,column3,column4,column5,column6,column7,column8]
Table7 [Table6Id,column2,column3,column4,column5,column6,column7,column8]
Table8 [Table6Id,column2,column3,column4,column5,column6,column7,column8]

Relationship
Table-1
column1 => int(id_pk)
column2 => text(name)
column3 => related to table2, and table2 is related to table6
column4 => related to table3
column5 => related table4, and table4 is related to table7 & table8

and the out put will be api/json created in routes/api.php and using ApiResources and reosurce controller class
Route::apiResource('endpoint1', Table1Controller::class);

result:

{
  "data": [
    {
        "table1.id": 1,
        "table1.column2": "Name Abc",
        "table1.column3": [
            {
            "table2.id": 01,
            "table2.column2": "text field of table 2 column 2",
            "table2.column3": "text field of table 2 column 3",
            "table2.column4": [
                {
                "table6.id": 03,
                "table6.column2": "text field of table 6 column 2",
                "table6.column3": "text field of table 6 column 3",
                }
            ],
            }
        ],
        "table1.column4": [
            {
                "table3.id": 06,
                "table3.column2": "text field of table 3 column 2",
                "table3.column3": "text field of table 3 column 3",
            }
        ],
        "table1.column5": [
            {
            "table4.id": 07,
            "table4.column2": "text field of table 4 column 2",
            "table4.column3": "text field of table 4 column 3",
            "table4.column4": [
                {
                "table7.id": 08,
                "table7.column2": "text field of table 7 column 2",
                "table7.column3": "text field of table 7 column 3",
                },
                {
                "table7.id": 10,
                "table7.column2": "text field of table 7 column 2",
                "table7.column3": "text field of table 7 column 3",
                }
            ],
            "table4.column5": [
                {
                "table8.id": 01,
                "table8.column2": "text field of table 8 column 2",
                "table8.column3": "text field of table 8 column 3",
                }
            ],
            }
        ],
    },
    ]
}
