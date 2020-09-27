# PHP-File-Binder
A simple Multi-File Binary Binding solution in Pure PHP.

It's so simple, the whole custom function fits in this readme,

```
<?php

function bindFiles($filePath1, $filePath2, $bindedOutputFilePath) {

// Make Output File
$outFile = fopen($bindedOutputFilePath, 'w');  
    
  // Get File (1) Binary
     $filesize1 = filesize($filePath1);
     $fp1 = fopen($filePath1, 'rb');
$fileBinary1 = fread($fp1, $filesize1);
     fclose($fp1);
     
  // Get File (2) Binary 
     $filesize2 = filesize($filePath2);
     $fp2 = fopen($filePath2, 'rb');
$fileBinary2 = fread($fp2, $filesize2);
     fclose($fp2);

// Bind File Binary 
$write1 = fwrite($outFile, $fileBinary1);
$write2 = fwrite($outFile, $fileBinary2);
fclose($outFile);

    // Check Failure On Final Write
     if ($write2 === false) {
           
           // Return False on Fail
            return false;
        }
        else {
           // Return True on Success
             return true;
        }
}

?>

```
