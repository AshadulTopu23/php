পিএইচপি (PHP) বেসিক কনসেপ্ট সম্পূর্ণ গাইড
পরিচিতি
PHP (Hypertext Preprocessor) একটি সার্ভার-সাইড স্ক্রিপ্টিং ভাষা যা ওয়েব ডেভেলপমেন্টে ব্যবহৃত হয়। এটি HTML এর সাথে এম্বেড করা যায় এবং ডাইনামিক ওয়েব পেজ তৈরি করতে সাহায্য করে।

১. পিএইচপি সিনট্যাক্স ও বেসিক স্ট্রাকচার
উদাহরণ ১: প্রথম PHP প্রোগ্রাম
php
<?php
    echo "Hello World!";
    echo "<h1>আমার প্রথম PHP প্রোগ্রাম</h1>";
?>
ব্যবহার
PHP কোড সবসময় <?php দিয়ে শুরু হয় এবং ?> দিয়ে শেষ হয়। প্রতিটি স্টেটমেন্ট সেমিকোলন (;) দিয়ে শেষ করতে হয়।

২. ভেরিয়েবল (Variables)
উদাহরণ ২: বিভিন্ন ধরণের ভেরিয়েবল
php
<?php
    $name = "রহিম";           // String
    $age = 25;                 // Integer
    $price = 99.99;            // Float
    $isStudent = true;         // Boolean
    
    echo "নাম: " . $name . "<br>";
    echo "বয়স: " . $age . "<br>";
    echo "মূল্য: $" . $price . "<br>";
?>
ব্যবহার
PHP-তে ভেরিয়েবল সবসময় $ চিহ্ন দিয়ে শুরু হয়। টাইপ ডিক্লেয়ার করার প্রয়োজন নেই।

৩. ডাটা টাইপস (Data Types)
উদাহরণ ৩: বিভিন্ন ডাটা টাইপ
php
<?php
    // String
    $text = "Hello PHP";
    
    // Integer
    $number = 100;
    
    // Float
    $decimal = 10.5;
    
    // Boolean
    $bool = true;
    
    // Array
    $fruits = array("আপেল", "কলা", "কমলা");
    
    // Null
    $empty = null;
    
    var_dump($text);
    var_dump($number);
    var_dump($fruits);
?>
৪. অপারেটর (Operators)
উদাহরণ ৪: বিভিন্ন অপারেটর
php
<?php
    $a = 10;
    $b = 5;
    
    // Arithmetic Operators
    echo $a + $b; // যোগ: 15
    echo $a - $b; // বিয়োগ: 5
    echo $a * $b; // গুণ: 50
    echo $a / $b; // ভাগ: 2
    
    // Comparison Operators
    var_dump($a == $b);   // false
    var_dump($a > $b);    // true
    var_dump($a != $b);   // true
    
    // Logical Operators
    var_dump($a > 5 && $b < 10); // true
    var_dump($a > 15 || $b < 10); // true
?>
৫. কন্ডিশনাল স্টেটমেন্ট (Conditional Statements)
উদাহরণ ৫: if-else
php
<?php
    $age = 18;
    
    if ($age >= 18) {
        echo "আপনি ভোট দিতে পারবেন";
    } else {
        echo "আপনি ভোট দিতে পারবেন না";
    }
    
    // Switch Statement
    $day = "সোমবার";
    switch($day) {
        case "শুক্রবার":
            echo "আজ ছুটির দিন";
            break;
        case "শনিবার":
            echo "আজ সাপ্তাহিক ছুটি";
            break;
        default:
            echo "আজ কাজের দিন";
    }
?>
৬. লুপ (Loops)
উদাহরণ ৬: বিভিন্ন লুপ
php
<?php
    // For Loop
    echo "For Loop:<br>";
    for($i = 1; $i <= 5; $i++) {
        echo "সংখ্যা: $i <br>";
    }
    
    // While Loop
    echo "<br>While Loop:<br>";
    $j = 1;
    while($j <= 5) {
        echo "সংখ্যা: $j <br>";
        $j++;
    }
    
    // Foreach Loop (Array এর জন্য)
    echo "<br>Foreach Loop:<br>";
    $colors = array("লাল", "নীল", "সবুজ");
    foreach($colors as $color) {
        echo "রং: $color <br>";
    }
?>
৭. ফাংশন (Functions)
উদাহরণ ৭: ফাংশন তৈরি ও ব্যবহার
php
<?php
    // Simple Function
    function sayHello($name) {
        return "হ্যালো, $name!";
    }
    
    echo sayHello("রহিম");
    
    // Function with multiple parameters
    function addNumbers($x, $y) {
        $sum = $x + $y;
        return $sum;
    }
    
    $result = addNumbers(10, 20);
    echo "যোগফল: " . $result;
    
    // Function with default value
    function greet($name = "অতিথি") {
        echo "স্বাগতম $name";
    }
    
    greet(); // স্বাগতম অতিথি
    greet("করিম"); // স্বাগতম করিম
?>
৮. অ্যারে (Arrays)
উদাহরণ ৮: অ্যারে অপারেশন
php
<?php
    // Indexed Array
    $students = array("রহিম", "করিম", "ফাতেমা");
    echo $students[0]; // রহিম
    
    // Associative Array
    $person = array(
        "name" => "রহিম",
        "age" => 25,
        "city" => "ঢাকা"
    );
    echo $person["name"]; // রহিম
    
    // Multidimensional Array
    $employees = array(
        array("রহিম", "ম্যানেজার", 50000),
        array("করিম", "ডেভেলপার", 40000)
    );
    
    // Array Functions
    echo count($students); // অ্যারের সাইজ
    array_push($students, "নাসিম"); // নতুন এলিমেন্ট যোগ
    print_r($students);
?>
৯. সুপারগ্লোবাল ভেরিয়েবল (Superglobals)
উদাহরণ ৯: $_POST এবং $_GET
php
<?php
    // HTML Form (form.html)
    /*
    <form method="POST" action="process.php">
        <input type="text" name="username">
        <input type="submit" value="Submit">
    </form>
    */
    
    // process.php
    if($_SERVER["REQUEST_METHOD"] == "POST") {
        $name = $_POST['username'];
        echo "হ্যালো, " . $name;
    }
    
    // $_GET Example
    // URL: page.php?name=Rahim
    $name = $_GET['name'] ?? 'অতিথি';
    echo "হ্যালো, " . $name;
?>
১০. ফাইল হ্যান্ডলিং (File Handling)
উদাহরণ ১০: ফাইল read/write
php
<?php
    // File Write
    $file = fopen("test.txt", "w");
    fwrite($file, "হ্যালো ওয়ার্ল্ড");
    fclose($file);
    
    // File Read
    $file = fopen("test.txt", "r");
    echo fread($file, filesize("test.txt"));
    fclose($file);
    
    // Simpler way
    file_put_contents("test.txt", "নতুন কন্টেন্ট");
    echo file_get_contents("test.txt");
?>
১১. সেশন ও কুকি (Session & Cookie)
উদাহরণ ১১: Session ব্যবহার
php
<?php
    // Start Session
    session_start();
    
    // Set Session
    $_SESSION['username'] = "rahim123";
    $_SESSION['email'] = "rahim@email.com";
    
    // Get Session
    echo "স্বাগতম " . $_SESSION['username'];
    
    // Destroy Session
    // session_destroy();
    
    // Cookie Example
    setcookie("user", "Rahim", time() + 3600, "/");
    
    if(isset($_COOKIE['user'])) {
        echo "হ্যালো " . $_COOKIE['user'];
    }
?>
১২. ডেটাবেস কানেকশন (MySQLi)
উদাহরণ ১২: MySQL ডেটাবেস সংযোগ
php
<?php
    // Database Connection
    $servername = "localhost";
    $username = "root";
    $password = "";
    $dbname = "test_db";
    
    // Create connection
    $conn = new mysqli($servername, $username, $password, $dbname);
    
    // Check connection
    if ($conn->connect_error) {
        die("সংযোগ ব্যর্থ: " . $conn->connect_error);
    }
    echo "সংযোগ সফল";
    
    // Insert Data
    $sql = "INSERT INTO users (name, email) VALUES ('রহিম', 'rahim@email.com')";
    
    if ($conn->query($sql) === TRUE) {
        echo "নতুন রেকর্ড সফলভাবে যোগ করা হয়েছে";
    }
    
    // Select Data
    $sql = "SELECT id, name, email FROM users";
    $result = $conn->query($sql);
    
    if ($result->num_rows > 0) {
        while($row = $result->fetch_assoc()) {
            echo "ID: " . $row["id"] . " - নাম: " . $row["name"] . "<br>";
        }
    }
    
    $conn->close();
?>
১৩. OOP (Object Oriented Programming)
উদাহরণ ১৩: ক্লাস ও অবজেক্ট
php
<?php
    // Class Definition
    class Student {
        // Properties
        public $name;
        public $roll;
        private $grade;
        
        // Constructor
        function __construct($name, $roll) {
            $this->name = $name;
            $this->roll = $roll;
        }
        
        // Method
        function getInfo() {
            return "নাম: " . $this->name . ", রোল: " . $this->roll;
        }
        
        // Setter
        function setGrade($grade) {
            $this->grade = $grade;
        }
        
        // Getter
        function getGrade() {
            return $this->grade;
        }
    }
    
    // Create Object
    $student1 = new Student("রহিম", 101);
    echo $student1->getInfo();
    $student1->setGrade("A");
    echo "গ্রেড: " . $student1->getGrade();
?>
১৪. এরর হ্যান্ডলিং (Error Handling)
উদাহরণ ১৪: try-catch
php
<?php
    // Error Handling
    function divide($a, $b) {
        if($b == 0) {
            throw new Exception("শূন্য দিয়ে ভাগ করা যাবে না");
        }
        return $a / $b;
    }
    
    try {
        echo divide(10, 0);
    } catch(Exception $e) {
        echo "এরর: " . $e->getMessage();
    } finally {
        echo "<br>এই ব্লক সবসময় execute হবে";
    }
    
    // Custom Error Handler
    function customError($errno, $errstr) {
        echo "এরর [$errno]: $errstr";
    }
    
    set_error_handler("customError");
    echo $undefinedVariable;
?>
১৫. JSON ও API
উদাহরণ ১৫: JSON encode/decode
php
<?php
    // Array to JSON
    $data = array(
        "name" => "রহিম",
        "age" => 25,
        "city" => "ঢাকা"
    );
    
    $jsonData = json_encode($data);
    echo $jsonData;
    
    // JSON to Array
    $jsonString = '{"name":"করিম","age":30,"city":"চট্টগ্রাম"}';
    $phpArray = json_decode($jsonString, true);
    echo $phpArray['name'];
    
    // Simple API Call
    $api_url = "https://api.example.com/data";
    $response = file_get_contents($api_url);
    $data = json_decode($response, true);
?>
১৬. প্র্যাকটিক্যাল প্রজেক্ট: সিম্পল কন্টাক্ট ফর্ম
উদাহরণ ১৬: সম্পূর্ণ কন্টাক্ট ফর্ম
php
<?php
// contact.php
session_start();
$message = '';

if($_SERVER["REQUEST_METHOD"] == "POST") {
    $name = trim($_POST['name']);
    $email = trim($_POST['email']);
    $message_text = trim($_POST['message']);
    
    // Validation
    $errors = [];
    
    if(empty($name)) {
        $errors[] = "নাম দেওয়া বাধ্যতামূলক";
    }
    
    if(empty($email)) {
        $errors[] = "ইমেইল দেওয়া বাধ্যতামূলক";
    } elseif(!filter_var($email, FILTER_VALIDATE_EMAIL)) {
        $errors[] = "সঠিক ইমেইল দিন";
    }
    
    if(empty($message_text)) {
        $errors[] = "মেসেজ দেওয়া বাধ্যতামূলক";
    }
    
    if(empty($errors)) {
        // Save to database or send email
        $_SESSION['success'] = "মেসেজ সফলভাবে পাঠানো হয়েছে";
        header("Location: " . $_SERVER['PHP_SELF']);
        exit();
    } else {
        $message = '<div class="error"><ul>';
        foreach($errors as $error) {
            $message .= "<li>$error</li>";
        }
        $message .= '</ul></div>';
    }
}
?>

<!DOCTYPE html>
<html>
<head>
    <title>কন্টাক্ট ফর্ম</title>
    <style>
        .form-group { margin: 10px 0; }
        input, textarea { width: 300px; padding: 5px; }
        .error { color: red; }
        .success { color: green; }
    </style>
</head>
<body>
    <h2>যোগাযোগ ফর্ম</h2>
    
    <?php echo $message; ?>
    
    <?php if(isset($_SESSION['success'])): ?>
        <div class="success"><?php echo $_SESSION['success']; unset($_SESSION['success']); ?></div>
    <?php endif; ?>
    
    <form method="POST" action="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">
        <div class="form-group">
            <label>নাম:</label><br>
            <input type="text" name="name" value="<?php echo isset($_POST['name']) ? htmlspecialchars($_POST['name']) : ''; ?>">
        </div>
        
        <div class="form-group">
            <label>ইমেইল:</label><br>
            <input type="email" name="email" value="<?php echo isset($_POST['email']) ? htmlspecialchars($_POST['email']) : ''; ?>">
        </div>
        
        <div class="form-group">
            <label>মেসেজ:</label><br>
            <textarea name="message" rows="5"><?php echo isset($_POST['message']) ? htmlspecialchars($_POST['message']) : ''; ?></textarea>
        </div>
        
        <button type="submit">পাঠান</button>
    </form>
</body>
</html>
PHP-র ব্যবহারক্ষেত্র
ওয়েবসাইট ডেভেলপমেন্ট: ই-কমার্স সাইট, ব্লগ, নিউজ পোর্টাল

কন্টেন্ট ম্যানেজমেন্ট সিস্টেম: WordPress, Joomla, Drupal

API ডেভেলপমেন্ট: RESTful API তৈরি

ডাটাবেজ ম্যানেজমেন্ট: MySQL, PostgreSQL এর সাথে ইন্টারঅ্যাকশন

ফাইল ম্যানেজমেন্ট সিস্টেম: ফাইল আপলোড, ডাউনলোড, ম্যানিপুলেশন

টিপস ও ট্রিক্স
এরর রিপোর্টিং চালু রাখুন:

php
ini_set('display_errors', 1);
error_reporting(E_ALL);
পাসওয়ার্ড এনক্রিপ্ট করুন:

php
$hashed_password = password_hash($password, PASSWORD_DEFAULT);
if(password_verify($input_password, $hashed_password)) {
    // Correct password
}
SQL Injection থেকে বাঁচুন:

php
$stmt = $conn->prepare("INSERT INTO users (name, email) VALUES (?, ?)");
$stmt->bind_param("ss", $name, $email);
PDF বানানোর নির্দেশনা
এই কন্টেন্ট থেকে PDF বানাতে:

পুরো কন্টেন্ট সিলেক্ট করে কপি করুন (Ctrl+A, Ctrl+C)

Microsoft Word বা Google Docs-এ পেস্ট করুন (Ctrl+V)

ফরম্যাট ঠিক করে নিন

File → Download → PDF Document সিলেক্ট করুন

লোকাল ড্রাইভে সেভ করুন

অথবা কোনো অনলাইন HTML to PDF কনভার্টার ব্যবহার করতে পারেন।

অনুশীলনীর জন্য পরামর্শ
প্রতিটি কনসেপ্ট নিজে নিজে প্র্যাকটিস করুন

ছোট ছোট প্রজেক্ট তৈরি করুন (ক্যালকুলেটর, টো-ডু লিস্ট)

PHP ডকুমেন্টেশন নিয়মিত পড়ুন

কমিউনিটিতে যুক্ত হন (Stack Overflow, Facebook PHP Groups)

এই গাইড অনুসরণ করলে আপনি PHP-র বেসিক কনসেপ্টগুলো খুব ভালোভাবে আয়ত্ত করতে পারবেন। কোনো প্রশ্ন থাকলে জানাতে পারেন। শুভ কামনা!


<!--  -->
https://chat.deepseek.com/share/5j55jiy2itv41s4i7c