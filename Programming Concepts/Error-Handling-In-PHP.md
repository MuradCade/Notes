errors occur when we programming software , its normal to display error inside website when its local but when website or software is live and their is users who using it we don't want to display ugly error to them. then how the developer will see the error in order to fix it ? that is good question, we can create log(means file that will store related information about the error)and developer can easily open the log and find out information about error.

- code below we will see how to store the error occur during using our software in file.

```php
//enable error to be displayed
error_reporting(E_ALL);
//hide the error to be directly displayed inside software/website.
ini_set("display_errors",0);

//create function that will contains error information.
// function below will have 4 parameter : $errno(means error number),
//$errsstr(means error message) , $errfile(means which file is the error inside of it) , $errline(means which line does error occur inside the file)
function customerrorhandler($errno,$errstr,$errfile,$errlinr){
	$message = "Error : [$errno] $errstr - $errfile:$errline";
	//generate file with error information
	error_log($message,3,"error_log.text");
	//note:create filename called err_log.text in order to store the errors inside of it.
}

// in order we store the function data we should run it every time error ouccur
set_error_handler("customerrorhandler");


```