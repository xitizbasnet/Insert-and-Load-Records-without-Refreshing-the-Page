# PHP-Project-Insert-and-Load-Records-without-Refreshing-the-Page
PHP-Project-Insert and Load Records without Refreshing the Page

loadInsertJqueryInsert and load records in the database are used when creating a system. In php, there are two pages (design and process) that are usually used in inserting and loading records in the database. This process may load long enough but with the use of jQuery and Ajax it will instantly insert and load the records in just a click.


In this project, we are going to use MySQL for the database.

Below are the step by step process in making this project:

Create a MySQL database and name it “dbuser”.

Do the following query for creating a table in the MySQL database that you have created.

[mysql]

CREATE TABLE IF NOT EXISTS tblusers (
user_id int(11) NOT NULL AUTO_INCREMENT,
user_name varchar(40) NOT NULL,
user_username varchar(40) NOT NULL,
user_pass varchar(90) NOT NULL,
PRIMARY KEY (user_id)
) ENGINE=InnoDB DEFAULT CHARSET=latin1 AUTO_INCREMENT=2 ;
[/mysql]

These are the codes that we’re going to use in our configuration that bridge between MySQL database and PHP script.
[php]

<?php
$server = ‘localhost’;
$dbuser = ‘root’;
$dbpass = ”;
$dbname = ‘dbuser’;
$con = mysql_connect($server, $dbuser, $dbpass);
if (isset($con)) {
# code…
$dbSelect = mysql_select_db($dbname);
if (!$dbSelect) {
echo “Problem in selecting database! Please contact administraator”;
die(mysql_error());
}
} else {
echo “Problem in database connection! Please contact administraator”;
die(mysql_error());
}
?>

[/php]

Create a design to input and load records in the MySQL database. Name the file “index.php”.
[php]

<?php include ‘config.php’; ?>
<!– bootstrap extension –>
<link rel=”stylesheet” type=”text/css” href=”css/bootstrap.min.css”>
<!– container –>
<div class=”container” >
<!– for inputs –>
<div class=”row”>
<div class=”form-horizontal span6″>
<div class=”row”>
<div class=”col-lg-12″>
<h1 class=”page-header”>Add New User</h1>
</div>
</div>

<div class=”form-group”>
<div class=”col-md-8″>
<label class=”col-md-4 control-label” for=
“U_NAME”>Name:</label>

<div class=”col-md-8″>
<input name=”deptid” type=”hidden” value=””>
<input class=”form-control input-sm” id=”U_NAME” name=”U_NAME” placeholder=
“Account Name” type=”text” value=””>
</div>
</div>
</div>

<div class=”form-group”>
<div class=”col-md-8″>
<label class=”col-md-4 control-label” for=
“U_USERNAME”>Username:</label>

<div class=”col-md-8″>
<input name=”deptid” type=”hidden” value=””>
<input class=”form-control input-sm” id=”U_USERNAME” name=”U_USERNAME” placeholder=
“Email Address” type=”text” value=””>
</div>
</div>
</div>

<div class=”form-group”>
<div class=”col-md-8″>
<label class=”col-md-4 control-label” for=
“U_PASS”>Password:</label>

<div class=”col-md-8″>
<input name=”deptid” type=”hidden” value=””>
<input class=”form-control input-sm” id=”U_PASS” name=”U_PASS” placeholder=
“Account Password” type=”Password” value=”” required>
</div>
</div>
</div>

<div class=”form-group”>
<div class=”col-md-8″>
<label class=”col-md-4 control-label” for=
“idno”></label>

<div class=”col-md-8″>
<button class=”btn btn-primary btn-sm” id =”submit” type=”submit” >Save</button>
</div>
</div>
</div>
</div>

</div>
<!– end inputs –>

<!– for listing –>
<div class=”row” >
<h1 class=”page-header”>List of Users</h1>
<div class=”table-responsive ” >

<table class=”table table-striped table-bordered table-hover table-responsive” style=”font-size:12px” cellspacing=”0″>
<thead>
<tr>
<th>Account Name</th>
<th>Username</th>
<th>Encrypted Password</th>
</tr>
</thead>
<tbody class=”loaddata” >
<?php
$sqlQuery = “SELECT * FROM tblusers“;
$result = mysql_query($sqlQuery) or die(mysql_error());

while ($row = mysql_fetch_array($result)) {
echo ‘<tr>’;
echo ‘<td>’ .$row[‘user_name’].'</a></td>’;
echo ‘<td>’. $row[‘user_username’].'</td>’;
echo ‘<td>’. $row[‘user_pass’].'</td>’;
echo ‘</tr>’;
}

?>
</tbody>

</table>
</div>
</div>
</div>
<!– end listing –>
</div>

[/php]

[javascript]

<!– jquery extension –>
<script type=”text/javascript” src=”jquery/jquery.min.js”></script>

<!– method for saving and retrieving data without refreshing the page. –>
<script type=”text/javascript” >

$(document).on(“click”, “#submit”, function () {

while ($row = mysql_fetch_array($result)) {

echo ‘<tr>’;
echo ‘<td>’ .$row[‘user_name’].'</a></td>’;
echo ‘<td>’. $row[‘user_username’].'</td>’;
echo ‘<td>’. $row[‘user_pass’].'</td>’;
echo ‘</tr>’;

}
}
?>

[/php]










