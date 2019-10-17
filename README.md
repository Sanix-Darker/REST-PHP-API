# REST-PHP-API

This is a simple Boilerplate of a RESTAPI in PHP from "SCRATCH", handleling a CRUD example and authentification process with a MVC structure.

This Boilerplate is connected to a database that can be a SQLite or a real SQL database.

## How to launch

- Make sure to create your database first or import orm.sql.
- configure the db.php with the name of your database.
- Start the server and try accessing to `index.php`.

## ORM

Go to `./models/example.php` to get a whole documentation of the ORM used here.

## Usage

We are in an MVC architecture, we can then have :


#### - Model

Code:

```php
<?php

/**
 * User Models
 */
class Model
{
	function __construct()
	{
		# code...
	}

    // Declare a public method
    public function MyPublic() { }

    // Declare a protected method
    protected function MyProtected() { }

    // Declare a private method
    private function MyPrivate() { }

    // This is public
    function Foo(){
		# code ....
	}
}
?>

```


#### - View

Code:

```php
<?php
	// For example, the Create view :
	$result = array();
	$output = array();
	if($required){

		// Insertion
		$BD->from($element)
		    ->insert($data)
		    ->execute();

		$rows = $BD->from($element)
			->where(array($element.'_id' => $BD->insert_id))
			->select()
			->one();

		foreach ($rows as $key => $val)
		  if (!is_int($key))
		    $output[$key]=$rows[$key];

		$result['status'] = 'success';
		$result['output'] = $output;

	}else{
		$result['status'] = 'error';
		$result['output'] = "Please, check your entries";
	}

	echo json_encode($result);
?>
```


#### - Controller

Code:

```php
<?php
	// An example of a controller
	$cible = isset($_GET['cible'])? $_GET['cible'] : "load";

	switch($cible){
		case 'something':{
			include 'views/'.$ctrl.'/something.php';
			break;
		}
		default :{
			$result = array();
			$result['status'] = 'error';
			$result['reason'] = "Bad paramters";
			echo json_encode($result);
			break;
		}
	}
?>
```

## Specs

Integrating database :

- mysql,
- mysqli,
- pgsql,
- sqlite and sqlite3
- mongoDB (Working on it)

## Addons

An integrated `PhpLiteAdmin` is provide for managing your own SQLite database (Any installation required):
<img src="./phpLiteAdmin.png" />

## Author

- Sanix-darker