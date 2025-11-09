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
  <option value="AcB">ABc</option>
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
    <td style="text-align: center;">1</td>
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

  <table data-csv=BBS_Connection_Info.csv></table>

<script>

const CsvToTable = async (tableElement) => {
  try {
    const req = await fetch(tableElement.dataset.csv, {
      method: 'get',
      headers: { 'content-type': 'text/csv;charset=UTF-8' }
    });
    if (req.status === 200) {
      const csv = await req.text();
      let myTableArray = csv.split('\n');
      let myTable = `<thead><tr><th>${myTableArray.replaceAll(';', '<th>')}</tr></thead><tbody>`;
      myTableArray.shift();
      myTableArray.forEach((aktRow) => {
        myTable += `<tr><td>${aktRow.replaceAll(';', '<td>')}</tr></tbody>`;
      });
      document.querySelector('table').insertAdjacentHTML('afterBegin', myTable);
    } else {
      console.log(`Error code ${req.status}`);
    }
  } catch (err) {
    console.log(err);
  }
};
CsvToTable(document.querySelector('[data-csv]'));
});   
</script>
  
</body>

</html>
