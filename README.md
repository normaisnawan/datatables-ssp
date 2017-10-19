# datatables-ssp
Customized Server Side Processing Class (ssp.class.php) For [Datatables](http://datatables.net/) Library

### Additional features ####
 - Add support join tables
 - Add debug SQL query
 - Add support for manually group by, order by
 
### How to Use ####
 
    $columns = [
        ['db' => 'table_a.id', 'as' => 'a_id', 'dt' => 'a_id'],
        ['db' => 'table_a.name', 'as' => 'a_name', 'dt' => 'a_name'],
        ['db' => 'table_b.id', 'as' => 'b_id', 'dt' => 'b_id'],
        ['db' => 'table_b.name', 'as' => 'b_name', 'dt' => 'b_name'],
    ];

    $table = [
        "table_a",
        "JOIN table_b USING (map_id)"
    ];
    
    $primaryKey = 'table_a.id';

    $whereAll = [
        "table_a.active = 1",
        "table_b.active = 1",
    ];
    
    $groupBy = [
        'table_b.name',
    ];
    
    $orderBy = [
        'table_a.id',
    ];
    
    $debug = true;
    
    $result = SSP::complex(
        $_GET,
        {SQL_Details, PDO connection},
        $table,
        $primaryKey,
        $columns,
        null,
        $whereAll,
        $groupBy,
        $orderBy,
        $debug
    );
