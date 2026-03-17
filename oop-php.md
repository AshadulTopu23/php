পিএইচপি-তে অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং (OOP) সম্পূর্ণ গাইড
OOP কী?
অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং (OOP) একটি প্রোগ্রামিং প্যারাডাইম যা "অবজেক্ট" ব্যবহার করে সফটওয়্যার ডিজাইন করে। অবজেক্টে ডাটা (প্রপার্টি) এবং মেথড (ফাংশন) উভয়ই থাকে।

১. ক্লাস ও অবজেক্ট (Class & Object)
ক্লাস কী?
ক্লাস হচ্ছে একটি ব্লুপ্রিন্ট বা খসড়া যার মাধ্যমে অবজেক্ট তৈরি করা হয়।

অবজেক্ট কী?
অবজেক্ট হচ্ছে ক্লাসের একটি ইনস্ট্যান্স বা বাস্তব রূপ।

উদাহরণ ১: বেসিক ক্লাস ও অবজেক্ট
php
<?php
// ক্লাস ডিক্লেয়ারেশন
class Car {
    // প্রপার্টি (Properties)
    public $brand;
    public $color;
    public $price;
    
    // মেথড (Method)
    public function startEngine() {
        return "ইঞ্জিন চালু হয়েছে";
    }
    
    public function getCarInfo() {
        return "ব্র্যান্ড: " . $this->brand . ", রঙ: " . $this->color;
    }
}

// অবজেক্ট তৈরি
$myCar = new Car();
$myCar->brand = "Toyota";
$myCar->color = "লাল";
$myCar->price = 2500000;

echo $myCar->getCarInfo(); // ব্র্যান্ড: Toyota, রঙ: লাল
echo $myCar->startEngine(); // ইঞ্জিন চালু হয়েছে

// আরেকটি অবজেক্ট
$anotherCar = new Car();
$anotherCar->brand = "BMW";
$anotherCar->color = "কালো";
?>
$this কী?
$this একটি সিউডো-ভেরিয়েবল যা বর্তমান অবজেক্টকে রেফার করে।

২. কনস্ট্রাক্টর ও ডেস্ট্রাক্টর (Constructor & Destructor)
কনস্ট্রাক্টর (__construct())
অবজেক্ট তৈরি হওয়ার সাথে সাথেই অটোমেটিক কল হয়।

ডেস্ট্রাক্টর (__destruct())
অবজেক্ট ধ্বংস হওয়ার সময় অটোমেটিক কল হয়।

উদাহরণ ২: কনস্ট্রাক্টর ও ডেস্ট্রাক্টর
php
<?php
class Student {
    public $name;
    public $roll;
    
    // কনস্ট্রাক্টর
    public function __construct($name, $roll) {
        $this->name = $name;
        $this->roll = $roll;
        echo "ছাত্র $name ক্লাসে এসেছে<br>";
    }
    
    public function displayInfo() {
        return "নাম: $this->name, রোল: $this->roll<br>";
    }
    
    // ডেস্ট্রাক্টর
    public function __destruct() {
        echo "ছাত্র $this->name ক্লাস ছেড়েছে<br>";
    }
}

$student1 = new Student("রহিম", 101);
$student2 = new Student("করিম", 102);

echo $student1->displayInfo();
echo $student2->displayInfo();

// প্রোগ্রাম শেষ হলে ডেস্ট্রাক্টর অটো কল হবে
?>
৩. এক্সেস মডিফায়ার (Access Modifiers)
তিন ধরণের এক্সেস মডিফায়ার আছে:

public - যে কোন জায়গা থেকে এক্সেস করা যায়

private - শুধুমাত্র নিজ ক্লাসের ভিতর থেকে এক্সেস করা যায়

protected - নিজ ক্লাস এবং চাইল্ড ক্লাস থেকে এক্সেস করা যায়

উদাহরণ ৩: এক্সেস মডিফায়ার
php
<?php
class BankAccount {
    public $accountHolder;     // সবার জন্য
    private $balance;          // শুধু এই ক্লাসের জন্য
    protected $accountNumber;  // এই ক্লাস ও চাইল্ড ক্লাসের জন্য
    
    public function __construct($holder, $number, $initialBalance) {
        $this->accountHolder = $holder;
        $this->accountNumber = $number;
        $this->balance = $initialBalance;
    }
    
    // পাবলিক মেথড - বাইরে থেকে কল করা যাবে
    public function deposit($amount) {
        if($amount > 0) {
            $this->balance += $amount;
            return "$amount টাকা জমা হয়েছে";
        }
        return "ভুল পরিমাণ";
    }
    
    // প্রাইভেট মেথড - শুধু এই ক্লাসের ভিতর থেকে কল করা যাবে
    private function calculateInterest() {
        return $this->balance * 0.05;
    }
    
    public function getBalance() {
        return "বর্তমান ব্যালেন্স: " . $this->balance . " টাকা";
    }
}

$account = new BankAccount("রহিম", "ACC123", 5000);
echo $account->accountHolder; // OK
echo $account->getBalance();   // OK
// echo $account->balance;     // Error - private
// echo $account->accountNumber; // Error - protected
echo $account->deposit(1000);  // OK
?>
৪. ইনহেরিটেন্স (Inheritance)
একটি ক্লাস আরেকটি ক্লাসের প্রপার্টি ও মেথড উত্তরাধিকার সূত্রে পেতে পারে।

উদাহরণ ৪: ইনহেরিটেন্স
php
<?php
// প্যারেন্ট ক্লাস
class Animal {
    public $name;
    public $age;
    
    public function __construct($name, $age) {
        $this->name = $name;
        $this->age = $age;
    }
    
    public function eat() {
        return "$this->name খাচ্ছে";
    }
    
    public function sleep() {
        return "$this->name ঘুমাচ্ছে";
    }
}

// চাইল্ড ক্লাস
class Dog extends Animal {
    public $breed;
    
    public function __construct($name, $age, $breed) {
        parent::__construct($name, $age); // প্যারেন্ট কনস্ট্রাক্টর কল
        $this->breed = $breed;
    }
    
    // নতুন মেথড
    public function bark() {
        return "$this->name ঘেউ ঘেউ করছে";
    }
    
    // প্যারেন্ট মেথড ওভাররাইড
    public function eat() {
        return parent::eat() . " এবং কুকুরের খাবার খাচ্ছে";
    }
}

class Cat extends Animal {
    public function meow() {
        return "$this->name মিউ মিউ করছে";
    }
}

$dog = new Dog("টমি", 3, "জার্মান শেফার্ড");
echo $dog->eat();     // প্যারেন্ট থেকে
echo $dog->bark();    // নিজের মেথড
echo $dog->sleep();   // প্যারেন্ট থেকে

$cat = new Cat("মিনি", 2);
echo $cat->meow();
?>
৫. পলিমরফিজম (Polymorphism)
একই মেথড বিভিন্ন ক্লাসে ভিন্ন ভিন্নভাবে কাজ করে।

উদাহরণ ৫: পলিমরফিজম
php
<?php
// ইন্টারফেস
interface Shape {
    public function calculateArea();
    public function draw();
}

class Circle implements Shape {
    private $radius;
    
    public function __construct($radius) {
        $this->radius = $radius;
    }
    
    public function calculateArea() {
        return pi() * $this->radius * $this->radius;
    }
    
    public function draw() {
        return "⭕ বৃত্ত আঁকা হচ্ছে (ব্যাসার্ধ: $this->radius)";
    }
}

class Rectangle implements Shape {
    private $length;
    private $width;
    
    public function __construct($length, $width) {
        $this->length = $length;
        $this->width = $width;
    }
    
    public function calculateArea() {
        return $this->length * $this->width;
    }
    
    public function draw() {
        return "⬜ আয়তক্ষেত্র আঁকা হচ্ছে (দৈর্ঘ্য: $this->length, প্রস্থ: $this->width)";
    }
}

// পলিমরফিক ফাংশন
function displayShapeInfo(Shape $shape) {
    echo $shape->draw() . "\n";
    echo "ক্ষেত্রফল: " . $shape->calculateArea() . "\n";
}

$circle = new Circle(5);
$rectangle = new Rectangle(4, 6);

displayShapeInfo($circle);     // একই ফাংশন ভিন্ন ভাবে কাজ করছে
displayShapeInfo($rectangle);  // পলিমরফিজমের উদাহরণ
?>
৬. এনক্যাপসুলেশন (Encapsulation)
ডাটা লুকিয়ে রাখা এবং নির্দিষ্ট মেথডের মাধ্যমে এক্সেস দেওয়া।

উদাহরণ ৬: এনক্যাপসুলেশন
php
<?php
class Employee {
    private $name;
    private $salary;
    private $employeeId;
    private static $totalEmployees = 0;
    
    public function __construct($name, $salary) {
        $this->setName($name);
        $this->setSalary($salary);
        $this->employeeId = $this->generateEmployeeId();
        self::$totalEmployees++;
    }
    
    // Getter
    public function getName() {
        return $this->name;
    }
    
    // Setter with validation
    public function setName($name) {
        if(strlen($name) < 2) {
            throw new Exception("নাম খুব ছোট");
        }
        $this->name = $name;
    }
    
    public function getSalary() {
        return $this->salary;
    }
    
    public function setSalary($salary) {
        if($salary < 0) {
            throw new Exception("বেতন ঋণাত্মক হতে পারে না");
        }
        $this->salary = $salary;
    }
    
    private function generateEmployeeId() {
        return "EMP" . rand(1000, 9999);
    }
    
    public function getEmployeeId() {
        return $this->employeeId;
    }
    
    public static function getTotalEmployees() {
        return self::$totalEmployees;
    }
    
    public function giveRaise($percentage) {
        if($percentage > 0 && $percentage <= 50) {
            $this->salary += $this->salary * ($percentage / 100);
            return "বেতন $percentage% বাড়ানো হয়েছে";
        }
        return "ভুল পার্সেন্টেজ";
    }
}

try {
    $emp1 = new Employee("রহিম", 30000);
    $emp2 = new Employee("করিম", 35000);
    
    echo $emp1->getName() . " এর আইডি: " . $emp1->getEmployeeId() . "\n";
    echo $emp1->giveRaise(10) . "\n";
    echo "নতুন বেতন: " . $emp1->getSalary() . "\n";
    echo "মোট কর্মচারী: " . Employee::getTotalEmployees() . "\n";
    
    // $emp1->salary = 50000; // Error: private property
    // $emp1->setSalary(-1000); // Error: validation
    
} catch(Exception $e) {
    echo "Error: " . $e->getMessage();
}
?>
৭. অ্যাবস্ট্রাক্ট ক্লাস (Abstract Class)
অ্যাবস্ট্রাক্ট ক্লাস সরাসরি ইনস্ট্যান্সিয়েট করা যায় না। এটি শুধুমাত্র ইনহেরিট করার জন্য।

উদাহরণ ৭: অ্যাবস্ট্রাক্ট ক্লাস
php
<?php
abstract class Database {
    protected $connection;
    protected $host;
    protected $username;
    protected $password;
    
    public function __construct($host, $username, $password) {
        $this->host = $host;
        $this->username = $username;
        $this->password = $password;
    }
    
    // অ্যাবস্ট্রাক্ট মেথড (বাধ্যতামূলক)
    abstract public function connect();
    abstract public function query($sql);
    abstract public function disconnect();
    
    // কংক্রিট মেথড (অপশনাল)
    public function getConnectionInfo() {
        return "Host: $this->host, User: $this->username";
    }
}

class MySQLDatabase extends Database {
    public function connect() {
        $this->connection = mysqli_connect(
            $this->host, 
            $this->username, 
            $this->password
        );
        echo "MySQL সংযোগ সফল\n";
    }
    
    public function query($sql) {
        echo "MySQL query executed: $sql\n";
        return "result";
    }
    
    public function disconnect() {
        mysqli_close($this->connection);
        echo "MySQL সংযোগ বন্ধ\n";
    }
}

class PostgreSQLDatabase extends Database {
    public function connect() {
        // PostgreSQL সংযোগ কোড
        echo "PostgreSQL সংযোগ সফল\n";
    }
    
    public function query($sql) {
        echo "PostgreSQL query executed: $sql\n";
        return "result";
    }
    
    public function disconnect() {
        echo "PostgreSQL সংযোগ বন্ধ\n";
    }
}

// $db = new Database(); // Error: abstract class
$mysql = new MySQLDatabase("localhost", "root", "");
$mysql->connect();
$mysql->query("SELECT * FROM users");
$mysql->disconnect();

$pgsql = new PostgreSQLDatabase("localhost", "postgres", "");
$pgsql->connect();
?>
৮. ইন্টারফেস (Interface)
ইন্টারফেসে শুধু মেথডের সিগনেচার থাকে, ইমপ্লিমেন্টেশন থাকে না।

উদাহরণ ৮: ইন্টারফেস
php
<?php
// Payment Gateway Interface
interface PaymentGateway {
    public function processPayment($amount);
    public function refundPayment($transactionId);
    public function getStatus($transactionId);
}

// Multiple interface implement
interface FraudCheck {
    public function verifyTransaction($transactionId);
}

class BkashPayment implements PaymentGateway, FraudCheck {
    private $bkashNumber;
    
    public function __construct($bkashNumber) {
        $this->bkashNumber = $bkashNumber;
    }
    
    public function processPayment($amount) {
        // bKash API call
        return [
            'status' => 'success',
            'transaction_id' => 'BKS' . rand(10000, 99999),
            'amount' => $amount,
            'method' => 'bKash'
        ];
    }
    
    public function refundPayment($transactionId) {
        return "Transaction $transactionId refunded to bKash";
    }
    
    public function getStatus($transactionId) {
        return "bKash transaction status: Completed";
    }
    
    public function verifyTransaction($transactionId) {
        // Fraud verification logic
        return true;
    }
}

class NagadPayment implements PaymentGateway {
    public function processPayment($amount) {
        return [
            'status' => 'success',
            'transaction_id' => 'NGD' . rand(10000, 99999),
            'amount' => $amount,
            'method' => 'Nagad'
        ];
    }
    
    public function refundPayment($transactionId) {
        return "Transaction $transactionId refunded to Nagad";
    }
    
    public function getStatus($transactionId) {
        return "Nagad transaction status: Pending";
    }
}

// Type hinting with interface
function makePayment(PaymentGateway $gateway, $amount) {
    $result = $gateway->processPayment($amount);
    echo "পেমেন্ট সফল: " . $result['transaction_id'] . "\n";
    return $result;
}

$bkash = new BkashPayment("017xxxxxxxx");
$nagad = new NagadPayment();

makePayment($bkash, 1000);
makePayment($nagad, 500);
?>
৯. ট্রেইট (Trait)
ট্রেইট ব্যবহার করে একাধিক ক্লাসে একই কোড রিইউজ করা যায়।

উদাহরণ ৯: ট্রেইট
php
<?php
// ট্রেইট ডিফাইন
trait Logger {
    public function log($message) {
        echo "[" . date('Y-m-d H:i:s') . "] " . $message . "\n";
    }
    
    public function logError($error) {
        $this->log("ERROR: " . $error);
    }
}

trait Timestampable {
    public $createdAt;
    public $updatedAt;
    
    public function setTimestamps() {
        $this->createdAt = date('Y-m-d H:i:s');
        $this->updatedAt = date('Y-m-d H:i:s');
    }
    
    public function updateTimestamp() {
        $this->updatedAt = date('Y-m-d H:i:s');
    }
}

// একাধিক ট্রেইট ব্যবহার
class User {
    use Logger, Timestampable;
    
    private $name;
    private $email;
    
    public function __construct($name, $email) {
        $this->name = $name;
        $this->email = $email;
        $this->setTimestamps();
        $this->log("নতুন ইউজার তৈরি: $name");
    }
    
    public function updateEmail($newEmail) {
        $oldEmail = $this->email;
        $this->email = $newEmail;
        $this->updateTimestamp();
        $this->log("ইমেইল আপডেট: $oldEmail -> $newEmail");
    }
}

class Product {
    use Logger;
    
    private $name;
    private $price;
    
    public function __construct($name, $price) {
        $this->name = $name;
        $this->price = $price;
        $this->log("নতুন প্রোডাক্ট: $name");
    }
    
    public function updatePrice($newPrice) {
        $oldPrice = $this->price;
        $this->price = $newPrice;
        $this->log("প্রাইস আপডেট: $oldPrice -> $newPrice");
    }
}

// ব্যবহার
$user = new User("রহিম", "rahim@email.com");
$user->updateEmail("rahim@newemail.com");

$product = new Product("ল্যাপটপ", 50000);
$product->updatePrice(45000);
?>
১০. স্ট্যাটিক মেথড ও প্রপার্টি (Static Methods & Properties)
স্ট্যাটিক মেম্বার ক্লাস লেভেলে থাকে, অবজেক্ট লেভেলে নয়।

উদাহরণ ১০: স্ট্যাটিক মেম্বার
php
<?php
class MathUtility {
    public static $pi = 3.14159;
    private static $calculationCount = 0;
    
    public static function add($a, $b) {
        self::$calculationCount++;
        return $a + $b;
    }
    
    public static function multiply($a, $b) {
        self::$calculationCount++;
        return $a * $b;
    }
    
    public static function getCircleArea($radius) {
        self::$calculationCount++;
        return self::$pi * $radius * $radius;
    }
    
    public static function getCalculationCount() {
        return self::$calculationCount;
    }
    
    public static function resetCount() {
        self::$calculationCount = 0;
    }
}

// স্ট্যাটিক মেথড কল (অবজেক্ট ছাড়াই)
echo MathUtility::add(10, 20) . "\n"; // 30
echo MathUtility::$pi . "\n"; // 3.14159
echo MathUtility::getCircleArea(5) . "\n"; // 78.53975

// কাউন্ট ট্র্যাকিং
echo "মোট ক্যালকুলেশন: " . MathUtility::getCalculationCount() . "\n";
MathUtility::resetCount();

// স্ট্যাটিক প্রপার্টি এবং মেথড ইনহেরিটেন্স
class AdvancedMath extends MathUtility {
    public static function power($base, $exponent) {
        return pow($base, $exponent);
    }
}

echo AdvancedMath::power(2, 3) . "\n"; // 8
echo AdvancedMath::$pi . "\n"; // 3.14159
?>
১১. ম্যাজিক মেথড (Magic Methods)
PHP-র কিছু বিশেষ মেথড যা নির্দিষ্ট সময়ে অটো কল হয়।

উদাহরণ ১১: ম্যাজিক মেথড
php
<?php
class MagicClass {
    private $data = [];
    
    // __get - অ্যাক্সেস না করা প্রপার্টি রিড করতে চাইলে
    public function __get($name) {
        echo "প্রপার্টি '$name' পড়ার চেষ্টা করা হচ্ছে\n";
        return isset($this->data[$name]) ? $this->data[$name] : null;
    }
    
    // __set - অ্যাক্সেস না করা প্রপার্টি সেট করতে চাইলে
    public function __set($name, $value) {
        echo "প্রপার্টি '$name' = '$value' সেট করা হচ্ছে\n";
        $this->data[$name] = $value;
    }
    
    // __call - অনির্ধারিত মেথড কল করলে
    public function __call($name, $arguments) {
        echo "মেথড '$name' কল করা হয়েছে আর্গুমেন্ট সহ: " . implode(', ', $arguments) . "\n";
    }
    
    // __toString - অবজেক্টকে স্ট্রিং হিসেবে ব্যবহার করলে
    public function __toString() {
        return "এটি একটি ম্যাজিক ক্লাস অবজেক্ট";
    }
    
    // __invoke - অবজেক্টকে ফাংশনের মত কল করলে
    public function __invoke($x) {
        echo "অবজেক্টকে ফাংশনের মত কল করা হয়েছে: $x\n";
    }
    
    // __isset - isset() চেক করলে
    public function __isset($name) {
        echo "isset() চেক করা হচ্ছে '$name' এর জন্য\n";
        return isset($this->data[$name]);
    }
    
    // __unset - unset() কল করলে
    public function __unset($name) {
        echo "unset() কল করা হচ্ছে '$name' এর জন্য\n";
        unset($this->data[$name]);
    }
}

$obj = new MagicClass();

$obj->name = "রহিম";        // __set কল হবে
echo $obj->name . "\n";     // __get কল হবে
echo $obj->nonExistent . "\n"; // __get কল হবে

$obj->unknownMethod(1, 2, 3); // __call কল হবে

echo $obj . "\n";           // __toString কল হবে

$obj(100);                  // __invoke কল হবে

isset($obj->name);          // __isset কল হবে
unset($obj->name);          // __unset কল হবে
?>
১২. ডিপেন্ডেন্সি ইনজেকশন (Dependency Injection)
একটি ক্লাসের প্রয়োজনীয় ডিপেন্ডেন্সি বাইরে থেকে সরবরাহ করা।

উদাহরণ ১২: ডিপেন্ডেন্সি ইনজেকশন
php
<?php
// Mailer Service
interface Mailer {
    public function send($to, $subject, $message);
}

class SmtpMailer implements Mailer {
    private $host;
    private $port;
    
    public function __construct($host, $port) {
        $this->host = $host;
        $this->port = $port;
    }
    
    public function send($to, $subject, $message) {
        echo "SMTP Mail sent to $to\n";
        echo "Host: $this->host, Port: $this->port\n";
        return true;
    }
}

class SendGridMailer implements Mailer {
    private $apiKey;
    
    public function __construct($apiKey) {
        $this->apiKey = $apiKey;
    }
    
    public function send($to, $subject, $message) {
        echo "SendGrid Mail sent to $to using API\n";
        return true;
    }
}

// UserService which depends on Mailer
class UserService {
    private $mailer;
    private $database;
    
    // Constructor Injection
    public function __construct(Mailer $mailer, Database $database) {
        $this->mailer = $mailer;
        $this->database = $database;
    }
    
    public function registerUser($email, $name) {
        // Save user to database
        $this->database->saveUser($email, $name);
        
        // Send welcome email
        $this->mailer->send(
            $email,
            "স্বাগতম",
            "প্রিয় $name, আমাদের প্ল্যাটফর্মে আপনাকে স্বাগতম!"
        );
        
        return "User registered successfully";
    }
}

class Database {
    public function saveUser($email, $name) {
        echo "User saved to database: $name ($email)\n";
    }
}

// Usage
$smtpMailer = new SmtpMailer("smtp.gmail.com", 587);
$database = new Database();

// Inject dependencies
$userService = new UserService($smtpMailer, $database);
$userService->registerUser("rahim@email.com", "রহিম");

// Easily switch to different mailer
$sendGridMailer = new SendGridMailer("api_key_123");
$userService2 = new UserService($sendGridMailer, $database);
$userService2->registerUser("karim@email.com", "করিম");
?>
১৩. নামস্পেস (Namespace)
কোড সংগঠিত করতে এবং একই নামের ক্লাস আলাদা করতে নামস্পেস ব্যবহার করা হয়।

উদাহরণ ১৩: নামস্পেস
php
<?php
// File: Models/User.php
namespace Models;

class User {
    public function __construct() {
        echo "Models\User তৈরি হয়েছে\n";
    }
    
    public function save() {
        echo "User সংরক্ষণ করা হয়েছে\n";
    }
}

// File: Controllers/User.php
namespace Controllers;

class User {
    public function __construct() {
        echo "Controllers\User তৈরি হয়েছে\n";
    }
    
    public function index() {
        echo "User কন্ট্রোলার এক্সিকিউট হচ্ছে\n";
    }
}

// File: Services/AuthService.php
namespace Services;

use Models\User as UserModel;
use Controllers\User as UserController;

class AuthService {
    private $userModel;
    private $userController;
    
    public function __construct() {
        // আলাদা নামস্পেসের ক্লাস ব্যবহার
        $this->userModel = new UserModel();
        $this->userController = new UserController();
    }
    
    public function login($email, $password) {
        $this->userModel->save();
        $this->userController->index();
        echo "লগইন প্রসেস সম্পন্ন\n";
    }
}

// File: index.php
namespace Main;

use Models\User;
use Controllers\User as UserCtrl;
use Services\AuthService;

// একাধিক ক্লাস ইম্পোর্ট
$user1 = new User();  // Models\User
$user2 = new UserCtrl();  // Controllers\User

$auth = new AuthService();
$auth->login("test@email.com", "password");

// ব্যাকস্ল্যাশ দিয়ে সরাসরি ব্যবহার
$user3 = new \Models\User();
$user4 = new \Controllers\User();
?>
১৪. টাইপ হিন্টিং (Type Hinting)
মেথডের প্যারামিটার ও রিটার্ন টাইপ নির্ধারণ করে দেওয়া।

উদাহরণ ১৪: টাইপ হিন্টিং
php
<?php
declare(strict_types=1);

class Calculator {
    // Scalar type hinting
    public function add(int $a, int $b): int {
        return $a + $b;
    }
    
    public function divide(float $a, float $b): float {
        if($b == 0) {
            throw new InvalidArgumentException("Division by zero");
        }
        return $a / $b;
    }
    
    // Array type hinting
    public function sumArray(array $numbers): float {
        return array_sum($numbers);
    }
    
    // Nullable type
    public function formatValue(?string $value): string {
        return $value ?? "No value provided";
    }
    
    // Union types (PHP 8+)
    public function processInput(int|string $input): string {
        return "Processing: " . $input;
    }
    
    // Object type hinting
    public function processUser(User $user): string {
        return "User: " . $user->getName();
    }
    
    // Self/Return type
    public function createInstance(): self {
        return new self();
    }
}

class User {
    private string $name;
    private int $age;
    
    public function __construct(string $name, int $age) {
        $this->name = $name;
        $this->age = $age;
    }
    
    public function getName(): string {
        return $this->name;
    }
    
    public function getAge(): int {
        return $this->age;
    }
    
    // Mixed type (any type)
    public function setData(mixed $data): void {
        var_dump($data);
    }
}

$calc = new Calculator();
echo $calc->add(10, 20) . "\n"; // 30
// echo $calc->add("10", 20); // TypeError (strict_types)

$user = new User("রহিম", 25);
echo $calc->processUser($user) . "\n";

$calc->processInput(100);
$calc->processInput("test");
?>
১৫. এক্সেপশন হ্যান্ডলিং (Exception Handling)
এরর হ্যান্ডলিং এর জন্য ট্রাই-ক্যাচ ব্লক ব্যবহার।

উদাহরণ ১৫: কাস্টম এক্সেপশন
php
<?php
// Custom Exception Class
class InsufficientBalanceException extends Exception {
    protected $message = "অপর্যাপ্ত ব্যালেন্স";
    protected $code = 1001;
    
    public function errorMessage() {
        return "Error [$this->code]: $this->message\n";
    }
}

class InvalidAmountException extends Exception {
    public function __construct($amount) {
        $this->message = "অবৈধ পরিমাণ: $amount (০ এর বেশি হতে হবে)";
        $this->code = 1002;
    }
}

class AccountNotFoundException extends Exception {
    public function __construct($accountNumber) {
        parent::__construct(
            "একাউন্ট নম্বর $accountNumber পাওয়া যায়নি",
            1003
        );
    }
}

class BankingSystem {
    private $accounts = [];
    
    public function addAccount($number, $balance) {
        $this->accounts[$number] = $balance;
    }
    
    public function withdraw($accountNumber, $amount) {
        try {
            // Validate amount
            if($amount <= 0) {
                throw new InvalidAmountException($amount);
            }
            
            // Check if account exists
            if(!isset($this->accounts[$accountNumber])) {
                throw new AccountNotFoundException($accountNumber);
            }
            
            // Check balance
            if($this->accounts[$accountNumber] < $amount) {
                throw new InsufficientBalanceException();
            }
            
            // Process withdrawal
            $this->accounts[$accountNumber] -= $amount;
            echo "সফলভাবে $amount টাকা উত্তোলন করা হয়েছে\n";
            echo "বর্তমান ব্যালেন্স: " . $this->accounts[$accountNumber] . "\n";
            
        } catch (InsufficientBalanceException $e) {
            echo $e->errorMessage();
            echo "আপনার ব্যালেন্স: " . $this->accounts[$accountNumber] . "\n";
        } catch (InvalidAmountException $e) {
            echo "Error: " . $e->getMessage() . "\n";
        } catch (AccountNotFoundException $e) {
            echo "Error: " . $e->getMessage() . "\n";
        } catch (Exception $e) {
            // Generic exception
            echo "অজানা ত্রুটি: " . $e->getMessage() . "\n";
        } finally {
            echo "এই ব্লক সবসময় execute হবে\n";
        }
    }
    
    public function getBalance($accountNumber) {
        if(!isset($this->accounts[$accountNumber])) {
            throw new AccountNotFoundException($accountNumber);
        }
        return $this->accounts[$accountNumber];
    }
}

// Usage
$bank = new BankingSystem();
$bank->addAccount("ACC123", 5000);

$bank->withdraw("ACC123", 1000);   // Success
$bank->withdraw("ACC123", -500);   // Invalid amount
$bank->withdraw("ACC123", 10000);  // Insufficient balance
$bank->withdraw("ACC456", 1000);   // Account not found

// Multiple exceptions in one catch (PHP 7.1+)
try {
    $balance = $bank->getBalance("INVALID");
} catch (AccountNotFoundException | Exception $e) {
    echo "Caught: " . $e->getMessage() . "\n";
}
?>
১৬. বাস্তব প্রজেক্ট: ই-কমার্স সিস্টেম
উদাহরণ ১৬: সম্পূর্ণ OOP প্রজেক্ট
php
<?php
// Interfaces
interface Discountable {
    public function applyDiscount($percentage);
    public function getDiscountedPrice();
}

interface Taxable {
    public function calculateTax();
}

// Abstract Product Class
abstract class Product implements Discountable, Taxable {
    protected $id;
    protected $name;
    protected $price;
    protected $discount = 0;
    const TAX_RATE = 0.15;
    
    public function __construct($id, $name, $price) {
        $this->id = $id;
        $this->name = $name;
        $this->setPrice($price);
    }
    
    // Encapsulation with getter/setter
    public function getId() { return $this->id; }
    public function getName() { return $this->name; }
    
    public function getPrice() { 
        return $this->price; 
    }
    
    public function setPrice($price) {
        if($price <= 0) {
            throw new InvalidArgumentException("Price must be positive");
        }
        $this->price = $price;
    }
    
    // Discountable implementation
    public function applyDiscount($percentage) {
        if($percentage < 0 || $percentage > 100) {
            throw new InvalidArgumentException("Invalid discount percentage");
        }
        $this->discount = $percentage;
    }
    
    public function getDiscountedPrice() {
        return $this->price * (1 - $this->discount / 100);
    }
    
    // Taxable implementation
    public function calculateTax() {
        return $this->getDiscountedPrice() * self::TAX_RATE;
    }
    
    // Abstract method
    abstract public function getProductType();
    
    public function getFinalPrice() {
        return $this->getDiscountedPrice() + $this->calculateTax();
    }
    
    public function __toString() {
        return sprintf(
            "%s [%s]: মূল্য: %.2f, ডিসকাউন্ট: %d%%, কর: %.2f, সর্বমোট: %.2f",
            $this->name,
            $this->getProductType(),
            $this->price,
            $this->discount,
            $this->calculateTax(),
            $this->getFinalPrice()
        );
    }
}

// Concrete Product Classes
class Electronics extends Product {
    private $warrantyMonths;
    
    public function __construct($id, $name, $price, $warrantyMonths) {
        parent::__construct($id, $name, $price);
        $this->warrantyMonths = $warrantyMonths;
    }
    
    public function getProductType() {
        return "ইলেকট্রনিক্স";
    }
    
    public function getWarrantyInfo() {
        return "$this->warrantyMonths মাস ওয়ারেন্টি";
    }
}

class Clothing extends Product {
    private $size;
    private $material;
    
    public function __construct($id, $name, $price, $size, $material) {
        parent::__construct($id, $name, $price);
        $this->size = $size;
        $this->material = $material;
    }
    
    public function getProductType() {
        return "পোশাক";
    }
    
    public function getSize() { return $this->size; }
    public function getMaterial() { return $this->material; }
}

class Book extends Product {
    private $author;
    private $isbn;
    
    public function __construct($id, $name, $price, $author, $isbn) {
        parent::__construct($id, $name, $price);
        $this->author = $author;
        $this->isbn = $isbn;
    }
    
    public function getProductType() {
        return "বই";
    }
    
    // Override tax calculation for books (different rate)
    public function calculateTax() {
        return $this->getDiscountedPrice() * 0.05; // 5% tax for books
    }
}

// Cart Item Class
class CartItem {
    private $product;
    private $quantity;
    
    public function __construct(Product $product, $quantity = 1) {
        $this->product = $product;
        $this->setQuantity($quantity);
    }
    
    public function getProduct() { return $this->product; }
    
    public function getQuantity() { return $this->quantity; }
    
    public function setQuantity($quantity) {
        if($quantity < 1) {
            throw new InvalidArgumentException("Quantity must be at least 1");
        }
        $this->quantity = $quantity;
    }
    
    public function getTotalPrice() {
        return $this->product->getFinalPrice() * $this->quantity;
    }
    
    public function __toString() {
        return sprintf(
            "%s x %d = %.2f টাকা",
            $this->product->getName(),
            $this->quantity,
            $this->getTotalPrice()
        );
    }
}

// Shopping Cart Class
class ShoppingCart {
    use Logger; // Using trait from previous example
    
    private $items = [];
    private $customerName;
    private $createdAt;
    
    public function __construct($customerName) {
        $this->customerName = $customerName;
        $this->createdAt = date('Y-m-d H:i:s');
        $this->log("নতুন কার্ট তৈরি: $customerName");
    }
    
    public function addItem(Product $product, $quantity = 1) {
        $productId = $product->getId();
        
        if(isset($this->items[$productId])) {
            // Update quantity if product already in cart
            $currentQty = $this->items[$productId]->getQuantity();
            $this->items[$productId]->setQuantity($currentQty + $quantity);
            $this->log("পরিমাণ আপডেট: {$product->getName()} +$quantity");
        } else {
            // Add new item
            $this->items[$productId] = new CartItem($product, $quantity);
            $this->log("নতুন আইটেম যোগ: {$product->getName()}");
        }
    }
    
    public function removeItem($productId) {
        if(isset($this->items[$productId])) {
            $productName = $this->items[$productId]->getProduct()->getName();
            unset($this->items[$productId]);
            $this->log("আইটেম রিমুভ: $productName");
        }
    }
    
    public function updateQuantity($productId, $quantity) {
        if(isset($this->items[$productId])) {
            $this->items[$productId]->setQuantity($quantity);
            $this->log("পরিমাণ আপডেট: আইডি $productId = $quantity");
        }
    }
    
    public function getSubtotal() {
        $total = 0;
        foreach($this->items as $item) {
            $total += $item->getTotalPrice();
        }
        return $total;
    }
    
    public function getItemCount() {
        $count = 0;
        foreach($this->items as $item) {
            $count += $item->getQuantity();
        }
        return $count;
    }
    
    public function getItems() {
        return $this->items;
    }
    
    public function checkout() {
        if(empty($this->items)) {
            throw new Exception("কার্ট খালি!");
        }
        
        echo "\n=== চেকআউট ===\n";
        echo "ক্রেতা: $this->customerName\n";
        echo "সময়: $this->createdAt\n";
        echo "----------------\n";
        
        foreach($this->items as $item) {
            echo $item . "\n";
        }
        
        echo "----------------\n";
        echo "মোট আইটেম: " . $this->getItemCount() . "\n";
        echo "সর্বমোট মূল্য: " . $this->getSubtotal() . " টাকা\n";
        
        $this->log("চেকআউট সম্পন্ন: " . $this->getSubtotal() . " টাকা");
        
        // Process payment
        return $this->processPayment();
    }
    
    private function processPayment() {
        // Payment processing logic
        return [
            'status' => 'success',
            'transaction_id' => 'TXN' . rand(10000, 99999),
            'amount' => $this->getSubtotal(),
            'date' => date('Y-m-d H:i:s')
        ];
    }
}

// Order Class
class Order {
    private $orderId;
    private $cart;
    private $status;
    private $orderDate;
    private $paymentInfo;
    
    const STATUS_PENDING = 'pending';
    const STATUS_PROCESSING = 'processing';
    const STATUS_COMPLETED = 'completed';
    const STATUS_CANCELLED = 'cancelled';
    
    public function __construct(ShoppingCart $cart, $paymentInfo) {
        $this->orderId = 'ORD' . date('Ymd') . rand(1000, 9999);
        $this->cart = $cart;
        $this->paymentInfo = $paymentInfo;
        $this->status = self::STATUS_PENDING;
        $this->orderDate = date('Y-m-d H:i:s');
    }
    
    public function getOrderId() { return $this->orderId; }
    public function getStatus() { return $this->status; }
    
    public function updateStatus($status) {
        $validStatuses = [self::STATUS_PENDING, self::STATUS_PROCESSING, 
                         self::STATUS_COMPLETED, self::STATUS_CANCELLED];
        
        if(in_array($status, $validStatuses)) {
            $this->status = $status;
            return true;
        }
        return false;
    }
    
    public function getOrderSummary() {
        return [
            'order_id' => $this->orderId,
            'date' => $this->orderDate,
            'status' => $this->status,
            'total' => $this->cart->getSubtotal(),
            'payment' => $this->paymentInfo
        ];
    }
    
    public function __toString() {
        return sprintf(
            "অর্ডার #%s [%s] - মোট: %.2f টাকা - তারিখ: %s",
            $this->orderId,
            $this->status,
            $this->cart->getSubtotal(),
            $this->orderDate
        );
    }
}

// Logger Trait (reused)
trait Logger {
    public function log($message) {
        echo "[LOG] " . date('H:i:s') . " - $message\n";
    }
}

// Usage Example
try {
    // Create products
    $laptop = new Electronics("P001", "ল্যাপটপ", 50000, 24);
    $tshirt = new Clothing("P002", "টি-শার্ট", 800, "L", "কটন");
    $book = new Book("P003", "PHP Programming", 500, "রহিম", "ISBN123");
    
    // Apply discounts
    $laptop->applyDiscount(10); // 10% discount
    $book->applyDiscount(5);    // 5% discount
    
    // Create shopping cart
    $cart = new ShoppingCart("করিম");
    
    // Add items to cart
    $cart->addItem($laptop, 1);
    $cart->addItem($tshirt, 2);
    $cart->addItem($book, 3);
    
    // Update quantity
    $cart->updateQuantity("P002", 3); // Change t-shirt quantity to 3
    
    // Display cart items
    echo "\n=== শপিং কার্ট ===\n";
    foreach($cart->getItems() as $item) {
        echo $item . "\n";
    }
    
    echo "\nকার্ট সারাংশ:\n";
    echo "মোট আইটেম: " . $cart->getItemCount() . "\n";
    echo "সর্বমোট: " . $cart->getSubtotal() . " টাকা\n";
    
    // Checkout
    $paymentInfo = $cart->checkout();
    
    // Create order
    $order = new Order($cart, $paymentInfo);
    echo "\n" . $order . "\n";
    
    // Update order status
    $order->updateStatus(Order::STATUS_PROCESSING);
    echo "আপডেটেড স্ট্যাটাস: " . $order->getStatus() . "\n";
    
    // Product information
    echo "\n" . $laptop . "\n";
    echo "ওয়ারেন্টি: " . $laptop->getWarrantyInfo() . "\n";
    
    echo $book . "\n";
    
} catch (Exception $e) {
    echo "Error: " . $e->getMessage() . "\n";
}
?>
OOP-র সুবিধাসমূহ
কোড রিইউজ: ইনহেরিটেন্সের মাধ্যমে একই কোড বারবার ব্যবহার

মডুলারিটি: প্রতিটি ক্লাস আলাদা মডিউল হিসেবে কাজ করে

মেইনটেইনেবিলিটি: কোড সহজে মডিফাই ও আপডেট করা যায়

সিকিউরিটি: এনক্যাপসুলেশনের মাধ্যমে ডাটা প্রোটেক্ট

ফ্লেক্সিবিলিটি: পলিমরফিজমের মাধ্যমে কোড ফ্লেক্সিবল

OOP বনাম প্রোসিডিউরাল প্রোগ্রামিং
বিষয়	OOP	প্রোসিডিউরাল
অ্যাপ্রোচ	অবজেক্ট-ভিত্তিক	ফাংশন-ভিত্তিক
ডাটা সিকিউরিটি	বেশি (এনক্যাপসুলেশন)	কম
কোড রিইউজ	বেশি (ইনহেরিটেন্স)	সীমিত
কমপ্লেক্সিটি	বড় প্রজেক্টের জন্য ভাল	ছোট প্রজেক্টের জন্য ভাল
মেইনটেনেন্স	সহজ	কঠিন
OOP প্র্যাকটিসের জন্য টিপস
SOLID প্রিন্সিপল ফলো করুন: OOP ডিজাইনের ৫টি মৌলিক নীতি

DRY (Don't Repeat Yourself): একই কোড বারবার লিখবেন না

KISS (Keep It Simple, Stupid): সহজ ও ক্লিন কোড লিখুন

কম্পোজিশনকে প্রাধান্য দিন: ইনহেরিটেন্সের চেয়ে কম্পোজিশন ভাল

ইন্টারফেস ব্যবহার করুন: লুজ কাপলিং এর জন্য

এই গাইড ফলো করলে আপনি PHP OOP-তে দক্ষ হয়ে উঠবেন। প্রতিটি কনসেপ্ট প্র্যাকটিস করুন এবং নিজের প্রজেক্ট তৈরি করুন।



<!-- OOP-এর সুবিধাসমূহ -->
https://chat.deepseek.com/share/5j55jiy2itv41s4i7c