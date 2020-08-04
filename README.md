Login Retrofit is a simple login signup app.
Try understanding code and implementing as importing might get you errors due to version issues

Add these two files to your server xampp/wampp
I used xampp
directory c:/xampp/icousers/

#1
Login.php

<?php 
if(isset($_GET['email']))
{
	echo "entered";
	$conn = mysqli_connect("localhost","root","","icousers");

	
	$email = $_GET['email'];
	$password = $_GET['password'];

	$select = "SELECT * FROM users WHERE email = '$email' AND
	password = '$password'";

	$run_sel = mysqli_query($conn,$select);
	
	if(mysqli_num_rows($run_sel)>0){
		$status = "ok";

		$row = mysqli_fetch_array($run_sel);
		$id = $row['id'];
	}
	else{
		$status = "failed";
	}
	echo json_encode(array("response"=>$status,"id"=>$id));
	
}
?>

 <!-- yourip/icousers/Login..php -->
 
 #2 
 Register.php
 
 <?php 

if(isset($_GET['email']))
{
	$conn = mysqli_connect("localhost","root","","icousers");

	$name = $_GET['name'];
	$email = $_GET['email'];
	$password = $_GET['password'];

	$insert = "insert into users(name,email,password) values('$name','$email','$password')";

	$run_insert = mysqli_query($conn,$insert);
	
	if($run_insert){
		$status = "ok";

		$row = mysqli_fetch_array($run_insert);
		$id = $row['id'];
	}
	else{
		$status = "failed";
	}
	echo json_encode(array("response"=>$status,"id"=>$id));


}

 ?>
 <!-- http://yourip/icousers/Register.php -->
