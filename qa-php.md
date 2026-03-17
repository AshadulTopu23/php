২০০টি PHP প্রশ্ন ও উত্তর (বাংলায়)
PHP বেসিক (প্রশ্ন ১-৩০)
প্রশ্ন ১: PHP এর পূর্ণরূপ কি?
উত্তর: PHP এর পূর্ণরূপ Hypertext Preprocessor। আগে এর নাম ছিল Personal Home Page।

প্রশ্ন ২: PHP স্ক্রিপ্ট কিভাবে শুরু এবং শেষ হয়?
উত্তর: PHP স্ক্রিপ্ট <?php দিয়ে শুরু হয় এবং ?> দিয়ে শেষ হয়।

প্রশ্ন ৩: PHP তে variable ডিক্লেয়ার করার নিয়ম কি?
উত্তর: PHP তে variable সবসময় $ চিহ্ন দিয়ে শুরু হয়, যেমন: $name = "Rahim";

প্রশ্ন ৪: PHP তে comment লেখার কয়টি পদ্ধতি আছে?
উত্তর: তিনটি পদ্ধতি:

// single line comment

single line comment
/* multi line comment */

প্রশ্ন ৫: echo এবং print এর মধ্যে পার্থক্য কি?
উত্তর: echo একসাথে একাধিক argument নিতে পারে এবং এর কোনো return value নেই। print শুধু একটি argument নেয় এবং সবসময় 1 return করে।

প্রশ্ন ৬: PHP তে variable naming rules কি কি?
উত্তর:

$ দিয়ে শুরু হতে হবে

letter বা underscore দিয়ে শুরু করতে হবে

number দিয়ে শুরু করা যাবে না

শুধু alpha-numeric character এবং underscore ব্যবহার করা যায়

case-sensitive ( $name এবং $Name আলাদা)

প্রশ্ন ৭: PHP এর ডাটা টাইপগুলো কি কি?
উত্তর:

String

Integer

Float (Double)

Boolean

Array

Object

NULL

Resource

প্রশ্ন ৮: var_dump() ফাংশনের কাজ কি?
উত্তর: var_dump() ফাংশন variable সম্পর্কে বিস্তারিত তথ্য দেখায় যেমন type এবং value।

প্রশ্ন ৯: PHP তে constants কিভাবে ডিফাইন করে?
উত্তর: define() ফাংশন দিয়ে: define("SITE_NAME", "MyWebsite"); অথবা const keyword দিয়ে: const PI = 3.1416;

প্রশ্ন ১০: PHP তে . (dot) operator এর কাজ কি?
উত্তর: এটি string concatenation operator, দুই বা ততোধিক string কে যুক্ত করে।

প্রশ্ন ১১: isset() এবং empty() এর মধ্যে পার্থক্য কি?
উত্তর: isset() চেক করে variable set আছে কিনা এবং NULL নয় কিনা। empty() চেক করে variable খালি কিনা (0, "", NULL, false, [])।

প্রশ্ন ১২: PHP তে variable scope কত প্রকার?
উত্তর: তিন প্রকার: local, global, static

প্রশ্ন ১৩: global variable কে function এর ভিতর এক্সেস করার উপায় কি?
উত্তর: global keyword ব্যবহার করে অথবা $GLOBALS array ব্যবহার করে।

প্রশ্ন ১৪: static variable কি?
উত্তর: static variable function এর execution শেষ হওয়ার পরও তার value ধরে রাখে।

প্রশ্ন ১৫: PHP তে array কত প্রকার?
উত্তর: তিন প্রকার: Indexed array, Associative array, Multidimensional array

প্রশ্ন ১৬: count() ফাংশনের কাজ কি?
উত্তর: array এর element সংখ্যা গণনা করে।

প্রশ্ন ১৭: PHP তে Superglobals গুলো কি কি?
উত্তর: $GLOBALS, $_SERVER, $_REQUEST, $_POST, $_GET, $_FILES, $_ENV, $_COOKIE, $_SESSION

প্রশ্ন ১৮: $_SERVER['PHP_SELF'] কি?
উত্তর: এটি current script file এর path এবং filename দেখায়।

প্রশ্ন ১৯: include এবং require এর মধ্যে পার্থক্য কি?
উত্তর: include ব্যর্থ হলে warning দেয় এবং script চলতে থাকে। require ব্যর্থ হলে fatal error দেয় এবং script বন্ধ হয়ে যায়।

প্রশ্ন ২০: include_once এবং require_once কেন ব্যবহার করা হয়?
উত্তর: একই file বারবার include হওয়া থেকে বাঁচাতে।

প্রশ্ন ২১: PHP তে for এবং foreach loop এর মধ্যে পার্থক্য কি?
উত্তর: for loop সাধারণ counter-based loop, foreach বিশেষ করে array এর জন্য ব্যবহার করা হয়।

প্রশ্ন ২২: break এবং continue statement এর কাজ কি?
উত্তর: break loop থেকে বের হয়ে যায়, continue current iteration শেষ করে next iteration এ চলে যায়।

প্রশ্ন ২৩: PHP তে function ডিফাইন করার নিয়ম কি?
উত্তর: function functionName() { code }

প্রশ্ন ২৪: function থেকে value return করার উপায় কি?
উত্তর: return statement ব্যবহার করে।

প্রশ্ন ২৫: default argument value সহ function কিভাবে লেখে?
উত্তর: function greet($name = "Guest") { echo "Hello $name"; }

প্রশ্ন ২৬: PHP তে variable function কি?
উত্তর: যদি variable এর শেষে () যোগ করা হয়, তাহলে PHP ঐ variable এর নামে function খোঁজে।

প্রশ্ন ২৭: PHP version চেক করার উপায় কি?
উত্তর: phpversion() function অথবা PHP_VERSION constant ব্যবহার করে।

প্রশ্ন ২৮: phpinfo() ফাংশনের কাজ কি?
উত্তর: PHP configuration সম্পর্কিত বিস্তারিত তথ্য দেখায়।

প্রশ্ন ২৯: date() ফাংশন দিয়ে কিভাবে বর্তমান তারিখ দেখায়?
উত্তর: echo date('Y-m-d');

প্রশ্ন ৩০: time() ফাংশন কি রিটার্ন করে?
উত্তর: Unix timestamp (January 1 1970 থেকে current time পর্যন্ত সেকেন্ড) রিটার্ন করে।

PHP স্ট্রিং হ্যান্ডলিং (প্রশ্ন ৩১-৫০)
প্রশ্ন ৩১: strlen() ফাংশনের কাজ কি?
উত্তর: string এর length (ক্যারেক্টার সংখ্যা) রিটার্ন করে।

প্রশ্ন ৩২: str_word_count() ফাংশন কি করে?
উত্তর: string এ কয়টি word আছে তা গণনা করে।

প্রশ্ন ৩৩: strrev() ফাংশনের কাজ কি?
উত্তর: string কে reverse করে।

প্রশ্ন ৩৪: strpos() ফাংশন কিভাবে কাজ করে?
উত্তর: string এর মধ্যে কোনো text এর প্রথম occurrence এর position খুঁজে বের করে।

প্রশ্ন ৩৫: str_replace() ফাংশনের কাজ কি?
উত্তর: string এর কিছু character কে অন্য character দিয়ে replace করে।

প্রশ্ন ৩৬: strtolower() এবং strtoupper() এর কাজ কি?
উত্তর: strtolower() string কে lowercase করে, strtoupper() uppercase করে।

প্রশ্ন ৩৭: ucfirst() ফাংশন কি করে?
উত্তর: string এর প্রথম character কে uppercase করে।

প্রশ্ন ৩৮: lcfirst() ফাংশন কি করে?
উত্তর: string এর প্রথম character কে lowercase করে।

প্রশ্ন ৩৯: trim() ফাংশনের কাজ কি?
উত্তর: string এর শুরু এবং শেষের whitespace দূর করে।

প্রশ্ন ৪০: ltrim() এবং rtrim() এর কাজ কি?
উত্তর: ltrim() শুরু থেকে whitespace দূর করে, rtrim() শেষ থেকে whitespace দূর করে।

প্রশ্ন ৪১: explode() ফাংশন কি করে?
উত্তর: string কে নির্দিষ্ট delimiter দিয়ে ভাগ করে array বানায়।

প্রশ্ন ৪২: implode() ফাংশন কি করে?
উত্তর: array এর element গুলোকে string এ জোড়া দেয়।

প্রশ্ন ৪৩: substr() ফাংশনের কাজ কি?
উত্তর: string থেকে নির্দিষ্ট অংশ কেটে বের করে।

প্রশ্ন ৪৪: str_split() ফাংশন কি করে?
উত্তর: string কে array তে ভাগ করে, প্রতিটি element এ নির্দিষ্ট সংখ্যক character থাকে।

প্রশ্ন ৪৫: str_repeat() ফাংশন কি করে?
উত্তর: string কে নির্দিষ্ট সংখ্যক বার repeat করে।

প্রশ্ন ৪৬: strcmp() ফাংশন কিভাবে কাজ করে?
উত্তর: দুইটি string তুলনা করে। সমান হলে 0, প্রথমটি বড় হলে positive, দ্বিতীয়টি বড় হলে negative রিটার্ন করে।

প্রশ্ন ৪৭: strcasecmp() এবং strcmp() এর পার্থক্য কি?
উত্তর: strcasecmp() case-insensitive comparison করে, strcmp() case-sensitive করে।

প্রশ্ন ৪৮: nl2br() ফাংশন কি করে?
উত্তর: string এর নতুন লাইন (\n) গুলোকে
ট্যাগে রূপান্তর করে।

প্রশ্ন ৪৯: number_format() ফাংশনের কাজ কি?
উত্তর: number কে thousands grouped format এ রূপান্তর করে।

প্রশ্ন ৫০: htmlspecialchars() ফাংশন কেন ব্যবহার করা হয়?
উত্তর: XSS attack প্রতিরোধ করতে HTML entities তে convert করার জন্য।

PHP অ্যারে ফাংশন (প্রশ্ন ৫১-৭০)
প্রশ্ন ৫১: array_merge() ফাংশন কি করে?
উত্তর: দুই বা ততোধিক array কে একত্রিত করে।

প্রশ্ন ৫২: array_diff() ফাংশনের কাজ কি?
উত্তর: দুইটি array এর মধ্যে পার্থক্য বের করে।

প্রশ্ন ৫৩: array_intersect() ফাংশন কি করে?
উত্তর: দুইটি array এর সাধারণ (intersect) value গুলো বের করে।

প্রশ্ন ৫৪: array_push() ফাংশন কি করে?
উত্তর: array এর শেষে এক বা একাধিক element যোগ করে।

প্রশ্ন ৫৫: array_pop() ফাংশন কি করে?
উত্তর: array এর শেষ element সরিয়ে দেয় এবং তা রিটার্ন করে।

প্রশ্ন ৫৬: array_shift() ফাংশন কি করে?
উত্তর: array এর প্রথম element সরিয়ে দেয় এবং তা রিটার্ন করে।

প্রশ্ন ৫৭: array_unshift() ফাংশন কি করে?
উত্তর: array এর শুরুতে এক বা একাধিক element যোগ করে।

প্রশ্ন ৫৮: array_search() ফাংশন কি করে?
উত্তর: array তে নির্দিষ্ট value খুঁজে তার key রিটার্ন করে।

প্রশ্ন ৫৯: in_array() ফাংশন কি করে?
উত্তর: চেক করে নির্দিষ্ট value array তে আছে কিনা।

প্রশ্ন ৬০: array_key_exists() ফাংশন কি করে?
উত্তর: চেক করে নির্দিষ্ট key array তে আছে কিনা।

প্রশ্ন ৬১: array_keys() ফাংশন কি রিটার্ন করে?
উত্তর: array এর সব keys নিয়ে একটি নতুন array রিটার্ন করে।

প্রশ্ন ৬২: array_values() ফাংশন কি রিটার্ন করে?
উত্তর: array এর সব values নিয়ে একটি নতুন array রিটার্ন করে।

প্রশ্ন ৬৩: sort() এবং rsort() এর পার্থক্য কি?
উত্তর: sort() ascending order এ সাজায়, rsort() descending order এ সাজায়।

প্রশ্ন ৬৪: asort() এবং arsort() এর কাজ কি?
উত্তর: asort() associative array কে value অনুযায়ী ascending order এ সাজায়, arsort() descending order এ সাজায়।

প্রশ্ন ৬৫: ksort() এবং krsort() এর কাজ কি?
উত্তর: ksort() associative array কে key অনুযায়ী ascending order এ সাজায়, krsort() descending order এ সাজায়।

প্রশ্ন ৬৬: array_reverse() ফাংশন কি করে?
উত্তর: array কে reverse order এ সাজায়।

প্রশ্ন ৬৭: array_sum() ফাংশন কি করে?
উত্তর: array এর সব value এর যোগফল বের করে।

প্রশ্ন ৬৮: array_product() ফাংশন কি করে?
উত্তর: array এর সব value এর গুণফল বের করে।

প্রশ্ন ৬৯: array_unique() ফাংশন কি করে?
উত্তর: array থেকে duplicate value দূর করে।

প্রশ্ন ৭০: array_map() ফাংশন কিভাবে কাজ করে?
উত্তর: array এর প্রতিটি element এ একটি নির্দিষ্ট function প্রয়োগ করে নতুন array বানায়।

PHP ম্যাথ ফাংশন (প্রশ্ন ৭১-৮০)
প্রশ্ন ৭১: abs() ফাংশন কি করে?
উত্তর: সংখ্যার absolute (positive) মান রিটার্ন করে।

প্রশ্ন ৭২: round() ফাংশন কিভাবে কাজ করে?
উত্তর: সংখ্যাকে নিকটতম integer এ round করে।

প্রশ্ন ৭৩: ceil() ফাংশন কি করে?
উত্তর: সংখ্যাকে উপরের দিকে নিকটতম integer এ round করে।

প্রশ্ন ৭৪: floor() ফাংশন কি করে?
উত্তর: সংখ্যাকে নিচের দিকে নিকটতম integer এ round করে।

প্রশ্ন ৭৫: max() এবং min() ফাংশন কি করে?
উত্তর: max() array বা সংখ্যার মধ্যে সবচেয়ে বড় মান বের করে, min() সবচেয়ে ছোট মান বের করে।

প্রশ্ন ৭৬: rand() ফাংশন কিভাবে কাজ করে?
উত্তর: random integer জেনারেট করে।

প্রশ্ন ৭৭: sqrt() ফাংশন কি করে?
উত্তর: সংখ্যার square root বের করে।

প্রশ্ন ৭৮: pow() ফাংশন কি করে?
উত্তর: সংখ্যার power বের করে (যেমন: pow(2,3) = 8)।

প্রশ্ন ৭৯: pi() ফাংশন কি রিটার্ন করে?
উত্তর: PI এর মান (3.1415926535898) রিটার্ন করে।

প্রশ্ন ৮০: is_numeric() ফাংশন কি চেক করে?
উত্তর: variable numeric value কিনা তা চেক করে।

PHP ফাইল সিস্টেম (প্রশ্ন ৮১-১০০)
প্রশ্ন ৮১: fopen() ফাংশন দিয়ে file খোলার নিয়ম কি?
উত্তর: $file = fopen("filename.txt", "r"); // r for read, w for write, a for append

প্রশ্ন ৮২: fread() ফাংশন কি করে?
উত্তর: খোলা file থেকে data পড়ে।

প্রশ্ন ৮৩: fwrite() ফাংশন কি করে?
উত্তর: খোলা file এ data লেখে।

প্রশ্ন ৮৪: fclose() ফাংশন কেন প্রয়োজন?
উত্তর: খোলা file বন্ধ করতে, system resources ফ্রি করতে।

প্রশ্ন ৮৫: file_get_contents() ফাংশন কি করে?
উত্তর: সম্পূর্ণ file একটি string এ পড়ে।

প্রশ্ন ৮৬: file_put_contents() ফাংশন কি করে?
উত্তর: file এ data লেখে (fopen+fwrite+fclose একসাথে)।

প্রশ্ন ৮৭: file_exists() ফাংশন কি চেক করে?
উত্তর: file বা directory আছে কিনা চেক করে।

প্রশ্ন ৮৮: filesize() ফাংশন কি রিটার্ন করে?
উত্তর: file এর size bytes এ রিটার্ন করে।

প্রশ্ন ৮৯: unlink() ফাংশন কি করে?
উত্তর: file delete করে।

প্রশ্ন ৯০: mkdir() ফাংশন কি করে?
উত্তর: নতুন directory তৈরি করে।

প্রশ্ন ৯১: rmdir() ফাংশন কি করে?
উত্তর: directory delete করে।

প্রশ্ন ৯২: is_dir() ফাংশন কি চেক করে?
উত্তর: path টি directory কিনা চেক করে।

প্রশ্ন ৯৩: is_file() ফাংশন কি চেক করে?
উত্তর: path টি file কিনা চেক করে।

প্রশ্ন ৯৪: copy() ফাংশন কি করে?
উত্তর: file copy করে।

প্রশ্ন ৯৫: rename() ফাংশন কি করে?
উত্তর: file বা directory rename করে।

প্রশ্ন ৯৬: basename() ফাংশন কি করে?
উত্তর: path থেকে filename অংশ বের করে।

প্রশ্ন ৯৭: dirname() ফাংশন কি করে?
উত্তর: path থেকে directory নাম বের করে।

প্রশ্ন ৯৮: pathinfo() ফাংশন কি রিটার্ন করে?
উত্তর: file path সম্পর্কে বিস্তারিত তথ্য (dirname, basename, extension, filename) array আকারে রিটার্ন করে।

প্রশ্ন ৯৯: feof() ফাংশন কি চেক করে?
উত্তর: file এর end-of-file এ পৌঁছেছে কিনা চেক করে।

প্রশ্ন ১০০: fgets() ফাংশন কি করে?
উত্তর: file থেকে একটি লাইন পড়ে।

PHP ফর্ম হ্যান্ডলিং (প্রশ্ন ১০১-১২০)
প্রশ্ন ১০১: GET এবং POST method এর মধ্যে পার্থক্য কি?
উত্তর: GET ডেটা URL এ visible, সীমিত size। POST ডেটা URL এ visible নয়, বড় size, নিরাপদ।

প্রশ্ন ১০২: $_GET এবং $_POST কি?
উত্তর: Superglobal arrays যা form data ধারণ করে।

প্রশ্ন ১০৩: $_REQUEST সুপারগ্লোবাল কি করে?
উত্তর: $_GET, $_POST, এবং $_COOKIE এর ডেটা ধারণ করে।

প্রশ্ন ১০৪: form data validate করার উপায় কি?
উত্তর: filter_input() বা filter_var() ফাংশন দিয়ে, অথবা নিয়মিত expression দিয়ে।

প্রশ্ন ১০৫: htmlspecialchars() দিয়ে form data sanitize কেন করা হয়?
উত্তর: XSS attack প্রতিরোধ করতে।

প্রশ্ন ১০৬: required field চেক করার নিয়ম কি?
উত্তর: empty() ফাংশন দিয়ে চেক করে।

প্রশ্ন ১০৭: email validate করার PHP ফাংশন কোনটি?
উত্তর: filter_var($email, FILTER_VALIDATE_EMAIL)

প্রশ্ন ১০৮: URL validate করার PHP ফাংশন কোনটি?
উত্তর: filter_var($url, FILTER_VALIDATE_URL)

প্রশ্ন ১০৯: file upload এ MAX_FILE_SIZE hidden field কেন ব্যবহার করা হয়?
উত্তর: ক্লায়েন্ট সাইডে maximum file size limit সেট করতে।

প্রশ্ন ১১০: $_FILES array কি ধারণ করে?
উত্তর: uploaded file সম্পর্কিত তথ্য (name, type, tmp_name, error, size)।

প্রশ্ন ১১১: move_uploaded_file() ফাংশন কেন ব্যবহার করা হয়?
উত্তর: uploaded temporary file কে desired location এ move করতে।

প্রশ্ন ১১২: multiple checkbox এর value কিভাবে পেতে হয়?
উত্তর: name="hobbies[]" দিয়ে array আকারে পাঠাতে হয়।

প্রশ্ন ১১৩: form এ enctype="multipart/form-data" কখন ব্যবহার করতে হয়?
উত্তর: file upload এর সময়।

প্রশ্ন ১১৪: form token কি এবং কেন ব্যবহার করা হয়?
উত্তর: CSRF attack প্রতিরোধ করতে hidden field এ unique token ব্যবহার করা হয়।

প্রশ্ন ১১৫: $_SERVER['REQUEST_METHOD'] কিভাবে ব্যবহার করা হয়?
উত্তর: form GET নাকি POST method এ submit হয়েছে তা চেক করতে।

প্রশ্ন ১১৬: form data trim() করে নেওয়া কেন ভালো অভ্যাস?
উত্তর: অপ্রয়োজনীয় whitespace দূর করতে।

প্রশ্ন ১১৭: stripslashes() ফাংশন কখন ব্যবহার করা হয়?
উত্তর: added slashes কে remove করতে।

প্রশ্ন ১১৮: form validation এ preg_match() কেন ব্যবহার করা হয়?
উত্তর: regular expression দিয়ে pattern matching এর জন্য।

প্রশ্ন ১১৯: form পুনরায় submit ঠেকানোর উপায় কি?
উত্তর: PRG (Post/Redirect/Get) pattern ব্যবহার করে।

প্রশ্ন ১২০: form এর error message কোথায় রাখা ভালো?
উত্তর: ফর্মের উপরে অথবা specific field এর পাশে।

PHP সেশন ও কুকি (প্রশ্ন ১২১-১৩৫)
প্রশ্ন ১২১: সেশন কি?
উত্তর: সেশন সার্ভারে ডেটা সংরক্ষণ করার একটি পদ্ধতি যা multiple pages এ user-specific data ধরে রাখে।

প্রশ্ন ১২২: সেশন start করার ফাংশন কোনটি?
উত্তর: session_start()

প্রশ্ন ১২৩: সেশন variable সেট করার নিয়ম কি?
উত্তর: $_SESSION['username'] = 'Rahim';

প্রশ্ন ১২৪: সেশন destroy করার নিয়ম কি?
উত্তর: session_destroy()

প্রশ্ন ১২৫: সেশন variable unset করার নিয়ম কি?
উত্তর: unset($_SESSION['username'])

প্রশ্ন ১২৬: কুকি কি?
উত্তর: কুকি ছোট text file যা user এর browser এ সংরক্ষণ করা হয়।

প্রশ্ন ১২৭: কুকি সেট করার ফাংশন কোনটি?
উত্তর: setcookie(name, value, expire, path, domain, secure, httponly)

প্রশ্ন ১২৮: কুকি ডিলিট করার নিয়ম কি?
উত্তর: expire time past date এ সেট করতে হবে: setcookie('user', '', time() - 3600)

প্রশ্ন ১২৯: session এবং cookie এর মধ্যে পার্থক্য কি?
উত্তর: session ডেটা সার্ভারে থাকে, cookie ডেটা ক্লায়েন্টের browser এ থাকে। session বেশি নিরাপদ।

প্রশ্ন ১৩০: session_start() কোথায় কল করতে হয়?
উত্তর: HTML output পাঠানোর আগে, script এর শুরুতে।

প্রশ্ন ১৩১: session_id() ফাংশন কি করে?
উত্তর: current session id রিটার্ন বা সেট করে।

প্রশ্ন ১৩২: session_regenerate_id() কেন ব্যবহার করা হয়?
উত্তর: security এর জন্য নতুন session id জেনারেট করতে (যেমন login এর পরে)।

প্রশ্ন ১৩৩: cookie তে array store করার উপায় কি?
উত্তর: serialize() বা json_encode() দিয়ে তারপর setcookie()।

প্রশ্ন ১৩৪: session timeout কিভাবে implement করা যায়?
উত্তর: $_SESSION['last_activity'] store করে এবং প্রতিবার request এ চেক করে।

প্রশ্ন ১৩৫: HTTP Only cookie কি?
উত্তর: যে cookie JavaScript এক্সেস করতে পারে না, XSS attack প্রতিরোধে সাহায্য করে।

PHP ডেটাবেজ (প্রশ্ন ১৩৬-১৫৫)
প্রশ্ন ১৩৬: MySQLi এবং PDO এর মধ্যে পার্থক্য কি?
উত্তর: MySQLi শুধু MySQL support করে, PDO ১২ টি database system support করে। PDO বেশি flexible।

প্রশ্ন ১৩৭: MySQLi দিয়ে connection তৈরি করার নিয়ম কি?
উত্তর: $conn = new mysqli($servername, $username, $password, $dbname);

প্রশ্ন ১৩৮: PDO দিয়ে connection তৈরি করার নিয়ম কি?
উত্তর: $pdo = new PDO("mysql:host=$host;dbname=$dbname", $username, $password);

প্রশ্ন ১৩৯: MySQL query execute করার নিয়ম কি?
উত্তর: $result = $conn->query($sql);

প্রশ্ন ১৪০: fetch_assoc() এবং fetch_array() এর পার্থক্য কি?
উত্তর: fetch_assoc() associative array রিটার্ন করে, fetch_array() both associative and numeric array রিটার্ন করে।

প্রশ্ন ১৪১: prepared statement কি?
উত্তর: SQL injection প্রতিরোধের জন্য SQL query template যা পরে parameter দিয়ে execute করা হয়।

প্রশ্ন ১৪২: bind_param() এ "sss" এর অর্থ কি?
উত্তর: তিনটি parameter সবগুলো string type। s=string, i=integer, d=double, b=blob।

প্রশ্ন ১৪৩: affected rows কাউন্ট করার পদ্ধতি কি?
উত্তর: MySQLi তে $conn->affected_rows, PDO তে $stmt->rowCount()

প্রশ্ন ১৪৪: last inserted ID পাওয়ার উপায় কি?
উত্তর: $conn->insert_id অথবা $pdo->lastInsertId()

প্রশ্ন ১৪৫: SQL injection কি?
উত্তর: একটি attack যেখানে harmful SQL code form input দিয়ে database query এ প্রবেশ করানো হয়।

প্রশ্ন ১৪৬: SQL injection প্রতিরোধের উপায় কি?
উত্তর: prepared statement ব্যবহার, input validation, escaping।

প্রশ্ন ১৪৭: transaction কি?
উত্তর: একাধিক database operation এর একটি গ্রুপ যা all-or-nothing ভাবে execute হয়।

প্রশ্ন ১৪৮: begin_transaction(), commit(), rollback() এর কাজ কি?
উত্তর: transaction শুরু, সফল হলে confirm, ব্যর্থ হলে cancel করে।

প্রশ্ন ১৪৯: database connection close করার নিয়ম কি?
উত্তর: $conn->close() অথবা $pdo = null

প্রশ্ন ১৫০: MySQL এ table create করার SQL statement কি?
উত্তর: CREATE TABLE table_name (column1 datatype, column2 datatype)

প্রশ্ন ১৫১: SELECT query এ LIMIT clause কেন ব্যবহার করা হয়?
উত্তর: নির্দিষ্ট সংখ্যক row রিটার্ন করতে।

প্রশ্ন ১৫২: ORDER BY clause এর কাজ কি?
উত্তর: result set সাজাতে (ASC বা DESC)।

প্রশ্ন ১৫৩: GROUP BY clause এর কাজ কি?
উত্তর: একই value গুলো group করতে।

প্রশ্ন ১৫৪: JOIN কত প্রকার?
উত্তর: INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL JOIN।

প্রশ্ন ১৫৫: Index কি এবং কেন ব্যবহার করা হয়?
উত্তর: database query এর performance বাড়াতে।

PHP OOP (প্রশ্ন ১৫৬-১৭৫)
প্রশ্ন ১৫৬: ক্লাস কি?
উত্তর: ক্লাস হচ্ছে object এর একটি blueprint বা template।

প্রশ্ন ১৫৭: অবজেক্ট কি?
উত্তর: ক্লাসের instance বা বাস্তব রূপ।

প্রশ্ন ১৫৮: constructor কি?
উত্তর: __construct() magic method যা object তৈরি হলে automatically call হয়।

প্রশ্ন ১৫৯: destructor কি?
উত্তর: __destruct() magic method যা object destroy হলে automatically call হয়।

প্রশ্ন ১৬০: access modifiers কত প্রকার?
উত্তর: তিন প্রকার: public, private, protected।

প্রশ্ন ১৬১: public, private, protected এর পার্থক্য কি?
উত্তর: public সব জায়গা থেকে accessible, private শুধু নিজ class এ, protected নিজ class ও child class এ।

প্রশ্ন ১৬২: inheritance কি?
উত্তর: একটি class আরেকটি class এর property এবং method inherit করতে পারে extends keyword দিয়ে।

প্রশ্ন ১৬৩: parent keyword এর কাজ কি?
উত্তর: parent class এর method বা constructor call করতে।

প্রশ্ন ১৬৪: polymorphism কি?
উত্তর: একই method বিভিন্ন class এ ভিন্ন ভাবে কাজ করে।

প্রশ্ন ১৬৫: encapsulation কি?
উত্তর: data লুকিয়ে রাখা এবং নির্দিষ্ট method এর মাধ্যমে access দেওয়া।

প্রশ্ন ১৬৬: abstraction কি?
উত্তর: গুরুত্বপূর্ণ information দেখানো এবং অপ্রয়োজনীয় detail লুকানো।

প্রশ্ন ১৬৭: interface এবং abstract class এর পার্থক্য কি?
উত্তর: interface এ method declaration only, implement করতে হবে। abstract class এ method implement ও করা যায়।

প্রশ্ন ১৬৮: trait কি?
উত্তর: multiple inheritance এর বিকল্প, একাধিক class এ code reuse করার উপায়।

প্রশ্ন ১৬৯: static method এবং property কি?
উত্তর: object তৈরি না করেই class name দিয়ে access করা যায়।

প্রশ্ন ১৭০: final keyword এর কাজ কি?
উত্তর: class inherit করা বা method override করা বন্ধ করে।

প্রশ্ন ১৭১: $this এবং self এর পার্থক্য কি?
উত্তর: $this current object reference, self current class reference।

প্রশ্ন ১৭২: instanceof operator এর কাজ কি?
উত্তর: object নির্দিষ্ট class এর instance কিনা check করে।

প্রশ্ন ১৭৩: __construct() এবং __destruct() magic method কখন call হয়?
উত্তর: __construct() object create এ, __destruct() object destroy এ।

প্রশ্ন ১৭৪: __get() এবং __set() magic method এর কাজ কি?
উত্তর: inaccessible property read/write করতে।

প্রশ্ন ১৭৫: __call() এবং __callStatic() magic method এর কাজ কি?
উত্তর: inaccessible method call handle করতে।

PHP অ্যাডভান্সড (প্রশ্ন ১৭৬-২০০)
প্রশ্ন ১৭৬: namespace কেন ব্যবহার করা হয়?
উত্তর: class নামের conflict এড়াতে এবং code organize করতে।

প্রশ্ন ১৭৭: use keyword এর কাজ কি?
উত্তর: namespace import করতে।

প্রশ্ন ১৭৮: autoloading কি?
উত্তর: class প্রয়োজন হলে automatically file include করা।

প্রশ্ন ১৭৯: Composer কি?
উত্তর: PHP dependency manager।

প্রশ্ন ১৮০: PSR (PHP Standard Recommendation) কি?
উত্তর: PHP coding standards এবং best practices।

প্রশ্ন ১৮১: exception handling এর নিয়ম কি?
উত্তর: try, catch, throw, finally block ব্যবহার করে।

প্রশ্ন ১৮২: custom exception কিভাবে তৈরি করে?
উত্তর: Exception class extends করে।

প্রশ্ন ১৮৩: finally block কখন execute হয়?
উত্তর: exception catch হোক বা না হোক, সবসময় execute হয়।

প্রশ্ন ১৮৪: error এবং exception এর মধ্যে পার্থক্য কি?
উত্তর: error সাধারণত PHP system error, exception programmer-defined।

প্রশ্ন ১৮৫: Dependency Injection কি?
উত্তর: class এর dependency বাইরে থেকে inject করা।

প্রশ্ন ১৮৬: MVC pattern কি?
উত্তর: Model-View-Controller, application architecture pattern।

প্রশ্ন ১৮৭: RESTful API কি?
উত্তর: HTTP protocol ব্যবহার করে web service তৈরি করার পদ্ধতি।

প্রশ্ন ১৮৮: JSON encode এবং decode করার ফাংশন কি?
উত্তর: json_encode() এবং json_decode()

প্রশ্ন ১৮৯: AJAX কি এবং PHP এর সাথে কিভাবে ব্যবহার করে?
উত্তর: Asynchronous JavaScript and XML, background এ server request করে।

প্রশ্ন ১৯০: Web shell কি?
উত্তর: malicious script যা server এ remote access দেয়।

প্রশ্ন ১৯১: CSRF attack কি?
উত্তর: Cross-Site Request Forgery, user এর অজান্তে request পাঠানো।

প্রশ্ন ১৯২: XSS attack প্রতিরোধের উপায় কি?
উত্তর: htmlspecialchars(), content security policy।

প্রশ্ন ১৯৩: password_hash() এবং password_verify() ফাংশন কিভাবে কাজ করে?
উত্তর: secure password hashing এবং verification এর জন্য।

প্রশ্ন ১৯৪: PHP-FPM কি?
উত্তর: PHP FastCGI Process Manager, performance বৃদ্ধি করে।

প্রশ্ন ১৯৫: OPcache কি?
উত্তর: compiled PHP script cache করে performance বাড়ায়।

প্রশ্ন ১৯৬: PHPUnit কি?
উত্তর: PHP testing framework।

প্রশ্ন ১৯৭: Xdebug কি?
উত্তর: PHP debugging এবং profiling tool।

প্রশ্ন ১৯৮: PHP artisan কি?
উত্তর: Laravel framework এর command line tool।

প্রশ্ন ১৯৯: PHP 8 এ নতুন কি কি feature এসেছে?
উত্তর: JIT compilation, match expression, named arguments, constructor property promotion, attributes ইত্যাদি।

প্রশ্ন ২০০: PHP developer হিসেবে ক্যারিয়ার গড়ার উপায় কি?
উত্তর:

PHP এবং OOP ভালোভাবে শেখা

Laravel/Symfony ফ্রেমওয়ার্ক শেখা

MySQL এবং অন্যান্য database শেখা

JavaScript, HTML, CSS শেখা

RESTful API তৈরি শেখা

Git ব্যবহার শেখা

প্রকৃত প্রজেক্ট তৈরি করা

কমিউনিটিতে active থাকা

নিয়মিত নতুন technology শেখা

লার্নিং কখনো বন্ধ না রাখা

এই ২০০টি প্রশ্ন ও উত্তর PHP শেখার জন্য একটি সম্পূর্ণ গাইড। প্রতিটি প্রশ্ন বারবার পড়ুন, নিজে নিজে উত্তর দেওয়ার চেষ্টা করুন, এবং কোড লিখে প্র্যাকটিস করুন। শুভ কামনা! 🚀

This response is AI-generated, for reference only.