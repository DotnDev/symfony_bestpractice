# symfony_bestpractice

<b>[IN PROGRESS] Symfony 4 - Best Practice</b>


--------------------------
         SET UP
--------------------------

<b>1. Create a new project</b>


Create a new Symfony project  in the desired location from the command line.
To make sure your project is in LTS (Long-Term Support), use the following command :

> symfony new project-name --version=lts –full

Open your project in your favourite IDE (PhpStorm will be used for this documentation)

<b>2. Create .env local files</b>

Create .env.local and env.test.local files in the root directory of your project.
The files you can edit with your database information are the local ones.

env.test.local : add the following line:

DATABASE_URL=mysql://USERNAME:PASSWORD@127.0.0.1/DB_NAME

replace USERNAME, PASSWORD and DB_NAME with the correct information. Your database name for test should end with _test for consistency.

Note : the database should ne exist yet in PhpMyAdmin, just insert the name you want it to have, Doctrine will then take care of creating it.


--------------------------
     CREATE ENTITIES
--------------------------

Create Maker Bundle to generate your entities.

> composer require maker --dev

Create your entities with:

> php bin/console make:entity


--------------------------
     UNIT TESTS
--------------------------

Use Php Unit Bridge instead of PhpUnit:
<i>The PHPUnit Bridge provides utilities to report legacy tests and usage of deprecated code and helpers for mocking native functions related to time, DNS and class existence.</i>

> composer require --dev symfony/phpunit-bridge


<b>1. Tests creation</b>

Project structure: 

The ‘tests’ folder should reflect the ‘src’ folder structure.

Naming convention: 

*Test classes should always end with Test, example : UserTest
*Test functions names should always start with test, example: public function testConstructor()

Test Classes:

They should extend TestCase (gives access to Asserts), example : UserTest extends TestCase


--------------------------
     DATABASE TESTS
--------------------------

<b>Database Tests</b>


Create a test database: 
php bin/console doctrine:database:create --env=test

Data Fixtures:
composer require --dev doctrine/doctrine-fixtures-bundle
php bin/console doctrine:fixtures:load

Data Fixtures (library to create and load fake data into database):<br/>
composer require --dev orm-fixtures<br/>

To empty the database and reload all fixture classes:<br/>

php bin/console doctrine:fixtures:load<br/>



<b>4. Create your test database:</b>


php bin/console doctrine:database:create --env=test

(le nom de la database sera celui spécifié dans le env.test.local)


<b>A. Set up</b>

<b>1. Create a Symfony project</b>

Create a new Symfony project  in the desired location from the command line. To make sure your project is in LTS (Long-Term Support), use the following command :

symfony new project-name --version=lts –full


Open your project in your favourite IDE (PhpStorm will be used for this documentation)

<b>2. Create .env local files</b>

Create .env.local and env.test.local files in the root directory of your project.
The files you can edit with your database information are the local ones.

env.test.local : add the following line:

DATABASE_URL=mysql://USERNAME:PASSWORD@127.0.0.1/DB_NAME

replace USERNAME, PASSWORD and DB_NAME with the correct information. Your database name for test should end with _test for consistency.
 Note : the database should ne exist yet in PhpMyAdmin, just insert the name you want it to have, Doctrine will then take care of creating it.

---------------------------------------------------------------

<b>3. Install all the necessary bundles for your app:</b>

PHPUnit library: composer require --dev symfony/phpunit-bridge<br/>
PHPUnit : ./bin/phpunit<br/>

Doctrine (takes care of database operations) :<br/>  
composer require symfony/orm-pack<br/>
Doctrine Test Bundle (resets the database automatically before each test) : <br/>
composer require --dev dama/doctrine-test-bundle <br/>



5. Start your server

symfony server:start —no-tls : 
WARNING unable to find the application log




*Assert
use them as well to secure your data!












https://phpunit.readthedocs.io/fr/latest/assertions.html




