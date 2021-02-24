#### Form validation by bootstrap

...php

/**
     * form isseting..
	 */
	 if( isset($_POST['add'])){

		//get value

		$name = $_POST['name'];
		$roll = $_POST['roll'];
		$email = $_POST['email'];
		$cell = $_POST['cell'];
		$uname = $_POST['uname'];
		$age = $_POST['age'];

		$cell_len = strlen($cell);


		/**
		 * file management
		 */
        

		$file_name = $_FILES['photo']['name'];
		$file_size = $_FILES['photo']['size'];
		$file_type = $_FILES['photo']['type'];
		$file_tmp  = $_FILES['photo']['tmp_name'];

		$unique_file_name = md5(rand() . time()) . $file_name;

		move_uploaded_file($file_tmp, 'photo/' . $unique_file_name);




		/**
		 * form validation
		 */

		 if( empty($name) || empty($roll) || empty($email) || empty($cell)  || empty($uname)  ||empty($age)){

         $msg ='<p class="alert alert-danger">All fields are required <button class ="close" data-dismiss="alert">&times;</button></p>';

		 }elseif ( filter_var( $roll, FILTER_VALIDATE_INT)==false ){
			$msg ='<p class="alert alert-danger">Invalid Roll Number !<button class ="close" data-dismiss="alert">&times;</button></p>';

		 }elseif ( filter_var($email,FILTER_VALIDATE_EMAIL )==false){

			$msg ='<p class="alert alert-danger">Invalid Email Address !<button class ="close" data-dismiss="alert">&times;</button></p>';
		 }elseif ($cell_len != 11){
			$msg ='<p class="alert alert-danger">Incorrect cell number !<button class ="close" data-dismiss="alert">&times;</button></p>';
		 }elseif ($age < 18 || $age >38){
			$msg ='<p class="alert alert-danger">Your age is not for institution !<button class ="close" data-dismiss="alert">&times;</button></p>';      

		 }else {

			$msg ='<p class="alert alert-success">Data Stable ! <button class ="close" data-dismiss="alert">&times;</button></p>';
		 }
		

		
	 }
	
	
	
	?>

	<div class="wrap shadow">
		<div class="card">
			<div class="card-body">
				<h2>Add New Student</h2>

				<?php 
                 
				 if(isset($msg)){
                  echo $msg;

				 }


...

