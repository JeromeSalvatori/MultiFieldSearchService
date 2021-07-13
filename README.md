# MultiFieldSearchService
Allows easy mysql request automation from html forms in php.

Returns an array containing the request string and a nested array containing values for prepared requests.

Options :
- $auto_sort : boolean false|true(default)
  Determines if your search request should automatically prioritize the first field in your form over the second one and so on.
- $fields_pr : array (empty by default)
  Define a custom order of priority for your search. See above (example: ['field3', 'field4' , 'field1'...])
- $req_return : mixed string|array 'data_fields'(default)|'ids'|'tables'|array
  'data_fields' returns all the columns corresponsing to your form's fields from the database, 'ids' selects only id columns from all the table names mentioned in your form's fields, 'tables' selects all fields from the chosen tables in your form's fields. The $srchd_tbls parameter is mandatory if you use this option. See below. You can also pass an array of any columns you might want to select. They can be anything as long as it's consistent with your database structure and the data provided in the form. Example ['table1.col1', 'table2.col1',...] 
- $fields_match : boolean|array (default: false)
  Pass an associative array as a parameter to match your database's columns with your form's fields like this : ["input_name" => "tbl.column",...]. You can leave it set to false, but then your form's input names should be formated like this: "tablename___columnname" or an exception will be thrown.
- $table_joins : boolean|array (default: false)
  The script will add joins automatically to the request for you based on assumptions considering the fields' priority order. You can define custom join options if you need too though. Like this : ["main" => "main_table_name",
                              "joined" => [
                                      "join_table_name_1" => [
                                          "main_table_name.join_table_name_1_id" => "join_table_name_1.id"
                                      ],
                                      "join_table_name_2" => [
                                          "main_table_name.join_table_name_2_id" => "join_table_name_2.id"
                                      ],...
                                  ]
                              ]
- $srchd_tbls : boolean|array (default: false)
  See $req_return. If this needs to be defined simply do it like this : ['table1', 'table2', 'table3']
