<?php
if(isset($_POST["upload"])) {
      $errors= array();
      $file_name = $_FILES['txtfile']['name'];
      $file_size =$_FILES['txtfile']['size'];
      $file_tmp =$_FILES['txtfile']['tmp_name'];
      $file_type=$_FILES['txtfile']['type'];
      $file_ext=strtolower(end(explode('.',$_FILES['txtfile']['name'])));
      
      $expensions= array("csv","txt");
      
      if(in_array($file_ext,$expensions)=== false){
         $errors[]="extension not allowed, please choose a TXT or csv or txt file.";
      }

      if(empty($errors)==true){
	//$str = file_get_contents($file_name);
	$row = 1;
	if (($handle = fopen($file_name, "r")) !== FALSE) {
		while (($data = fgetcsv($handle, 1000, ",")) !== FALSE) {
			$num = count($data);
			//echo "<p> $num fields in line $row: <br /></p>\n";
			$row++;
			$a = array();
			 for ($c=0; $c < $num; $c++) {
				//print_r(explode("\t",$data[$c]));
				$a[$c] = $data[$c];
            			
				//echo  "<br />\n";
				//$rowline = explode("\t",$data[$c]);
//print_r($rowline);
//				echo $rowline[1];
//				echo "\n";
//die();
        		}
	

	  
	    $names = explode(" ", $a[3]);
//echo count($names);
//die();
            if(count($names)==1)
	    {
	    $firstName = $names[0];
	    $lastName = "John";
	    }else{
	    $firstName = $names[0];
	    $lastName = $names[1];
	    }
	    $tarrif = $a[5];
	    $address = $a[6];
	    $meter = $a[4];
	    $phcn = $a[0];
	    $nerc = $a[1];
	    $kaedc = $a[2];

 	    //lets generate transformer code
		$nj = explode("/",$nerc);
		$kj = explode("/",$kaedc);
		$transformer = $nj[5].$kj[5];
	   //




	    $bookcode =  str_replace('/', '', $a[9]);

	    $areaofficenerchalf = explode("/",$nerc);
	    $areaofficekaedchalf = explode("/",$kaedc);
	    $areaoffice = $areaofficenerchalf[1].'-'.$areaofficenerchalf[1];
	    $current_balance = $a[7];
	    if($meter =="NOMETER")
	    {
		$m = "unmetered";
		$mt = "";
	    }else{
		$m = "metered";
		$mt = $meter;
	    }

$my_file = 'seed.php';
$hand = fopen($my_file, 'a') or die('Cannot open file:  '.$my_file);

	$seed ="\n". "DB::table('customers')->insert([
        ['first_name' => '$firstName', 'last_name' => '$lastName', 'tariff_type' => '$tarrif', 'address' => '$address',
  'phone' => '09098787263', 'category' => 'post-paid', 'area_office_codes' => '$areaoffice', 'transformer_codes' => '$transformer',
  'book_code' => '$bookcode', 'metered'=>'$m', 'meter_number' => '$mt', 'average_consumption' => '000',
  'classification' => 'non-md', 'initial_meter_reading' => '0000', 'current_balance'=>'$current_balance','institution' => 'Ministry','customer_phcn_number_full'=>'$phcn',customer_nerc_number_full=>'$nerc',customer_kaedc_number_full=>'$kaedc','status'=>'active'],";
fwrite($hand, $seed);

		}//while
		fclose($handle);

	}//if fopen
      }
//echo "DASER YOU DID PRINT :". $row . " ROWS";
	
}

?>

<form action="<?php echo $_SERVER['PHP_SELF']; ?>" method="POST" enctype="multipart/form-data">
<input type="file" name="txtfile" />
<input type="submit" value="Upload" name="upload" />


</form>
