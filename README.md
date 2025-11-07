<!DOCTYPE html>
<html>

<head>
  <style>
    body {background-color: powderblue;}
    tr { display: block; float: left; }
th, td { display: block; }
  </style>
</head>  

<body>

<label for="BBS_Computer_Type_Focus">Choose a BBS Computer Type Focus:</label>
<select id="BBS_Computer_Type_Focus">
  <option value="AB">AB</option>
  <option value="Amiga">Amiga</option>
  <option value="Commodore">Commodore</option>
  <option value="Mac">Mac</option>
  <option value="N/A">N/A</option>
  <option value="ALL">ALL</option>
</select>

<table style="table-layout: auto; width: 400%;">
  <tr>
    <th>#</th>
    <th>BBS Name</th>
    <th>OS Focus</th>
    <th>Host System Type</th>
    <th>OS</th>
    <th>Last Connected (Telnet)</th>
    <th>telnet</th>
    <th>SSH</th>
    <th>Web</th>
  </tr>
  <tr>
    <td>1</td>
    <td>Devastation BBS</td>
    <td>Commodore</td>
    <td>Vintage (386)</td>
    <td>Linux</td>
    <td>2024-01-20</td>
    <td>TheDevastation12.com:22</td>
    <td>TheDevastation12.com:23</td>
    <td>TheDevastation12.com:24</td>
  </tr>
</table>

<?php

// Source - https://stackoverflow.com/a
// Posted by Nigel Ren
// Retrieved 2025-11-07, License - CC BY-SA 4.0

$str = "<table class=\"table table-hover table-striped\">
                                         <thead>
                                         <th>colum1</th>
                                         <th>colum2</th>
                                         <th>colum3</th>
                                         </thead>
                                         <tbody>

     ";
$f = fopen("/BBS_Names", "r");
if ( $f === FALSE ) {
    exit;
}
while ( $row = fgetcsv($f, null, " ") ) {
    // Ensure all rows have at least 3 cells
    $row = array_pad($row, 3, "");
    // Output data in a row
    $str .= "<tr><td>".implode("</td><td>", $row). "</td></tr>".PHP_EOL;
}
$str .= "</tbody></table>";
echo $str;

?>

</body>

</html>
