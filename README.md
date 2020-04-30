# symfony_bestpractice

<b>[IN PROGRESS] Symfony 4 - Best Practice</b>


## SET UP

<b>1. Create a new project</b>

Create a new Symfony project  in the desired location from the command line.
To make sure your project is in LTS (Long-Term Support), use the following command :

`symfony new project-name --version=lts –full`

Open your project in your favourite IDE (PhpStorm will be used for this documentation)

<b>2. Create .env local files</b>

Create .env.local and env.test.local files in the root directory of your project.
The files you can edit with your database information are the local ones.

env.test.local : add the following line:

DATABASE_URL=mysql://USERNAME:PASSWORD@127.0.0.1/DB_NAME

replace USERNAME, PASSWORD and DB_NAME with the correct information. Your database name for test should end with _test for consistency.

Note : the database should ne exist yet in PhpMyAdmin, just insert the name you want it to have, Doctrine will then take care of creating it.


## ENTITIES

Create MakerBundle to generate your entities.

`composer require maker --dev`

Create your entities with:

`php bin/console make:entity`

- No need to create an id attribute : MakerBundle automatically generates one (and Doctrine will use it to create a constraint key in your database if you set a relation up): 
https://symfony.com/doc/current/doctrine/associations.html


## UNIT TESTS

Use Php Unit Bridge:
<i>The PHPUnit Bridge provides utilities to report legacy tests and usage of deprecated code and helpers for mocking native functions related to time, DNS and class existence.</i>

`composer require --dev symfony/phpunit-bridge`
` ./vendor/bin/simple-phpunit`


<b>1. Tests creation</b>

### Project structure

The ‘tests’ folder should reflect the ‘src’ folder structure.

### Naming convention

*Test classes should always end with Test, example : UserTest
*Test functions names should always start with test, example: public function testConstructor()

Test Classes:

They should extend TestCase (gives access to Asserts), example : UserTest extends TestCase

### SETUP FUNCTION

Use the setUp() function which is automatically called before each test to make sure the object is newly created before each test - each test should be completely independant from each other:

` public function setUp()
    {

        $this -> prenom = new Firstname();

    } `

## DATABASE TESTS

Doctrine (takes care of database operations) :<br/>  
`composer require symfony/orm-pack`

Doctrine Test Bundle (resets the database automatically before each test) : <br/>
`composer require --dev dama/doctrine-test-bundle`

https://symfony.com/doc/current/testing/database.html

<b>Database Tests</b>

Create a test database: 
`php bin/console doctrine:database:create --env=test`
The name of the database will be the one you specified in env.test.local

Fixtures Bundle:
`composer require --dev doctrine/doctrine-fixtures-bundle`

Data Fixtures (library to create and load fake data into database):<br/>
`composer require --dev orm-fixtures`

To empty the database and reload all fixture classes:<br/>
`php bin/console doctrine:fixtures:load`

To reset fake data in database:
 composer require --dev dama/doctrine-test-bundle



---------------------------------------------------------------

5. Start your server

symfony server:start --no-tls
WARNING unable to find the application log




*Assert
use them as well to secure your data!
https://phpunit.readthedocs.io/fr/latest/assertions.html




