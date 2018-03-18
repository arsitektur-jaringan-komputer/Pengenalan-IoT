# Arduino & Sensors

<img src="assets/header.png" alt="Arduino">

### Software Requirements
1. [Arduino IDE](https://www.arduino.cc/en/Main/Software)
2. [XAMPP](https://www.apachefriends.org/download.html)
3. Browser
		
### Hardware Requirements
1. Arduino Uno
2. Laptop (linux OS)
3. Smartphone (optional)

## A. Dasar Teori
### 1. Serial Communication

Komunikasi serial adalah komunikasi yang pengiriman datanya per-bit secara berurutan dan bergantian. Komunikasi ini mempunyai suatu kelebihan yaitu hanya membutuhkan satu jalur dan kabel yang sedikit dibandingkan dengan komunikasi paralel. Pada prinsipnya komunikasi serial merupakan komunikasi dimana pengiriman data dilakukan per bit sehingga lebih lambat dibandingkan komunikasi parallel, atau dengan kata lain komunikasi serial merupakan salah satu metode komunikasi data di mana hanya satu bit data yang dikirimkan melalui seuntai kabel pada suatu waktu tertentu.

### 2. PHP

Bahasa Pemrograman PHP adalah bahasa pemrograman script server-side yang didesain untuk pengembangan web. Selain itu, PHP juga bisa digunakan sebagai bahasa pemrograman umum (wikipedia). Pertama kali di kembangkan oleh Rasmust Lerdorf pada tahun 1995, dan sekarang php dikembangkan oleh The PHP Group.

### 3. Web Server

Web server adalah sebuah software yang memberikan layanan berbasis data dan berfungsi menerima permintaan dari HTTP atau HTTPS pada klien yang dikenal dan biasanya kita kenal dengan nama web browser (Mozilla Firefox, Google Chrome) dan untuk mengirimkan kembali yang hasilnya dalam bentuk beberapa halaman web dan pada umumnya akan berbentuk dokumen HTML.

## B. Cara Bermain

### 1. Config Arduino

Sketch Arduino:

```C

/*

  Used with the PHP code
  http://localhost/arduino.php
 */

void setup() {                

  Serial.begin(9600); // initialize serial communication:

  // initialize the digital pin as an output.
  // Pin 13 has an LED connected on most Arduino boards:
  pinMode(13, OUTPUT);     
}

void loop() {

// read the serial port:

if (Serial.available() > 0) {
int inByte = Serial.read();

switch (inByte) {
case 'a':
  digitalWrite(13, HIGH);   // set the LED on
  Serial.println("HIGH");
  
break;

case 'b':
  digitalWrite(13, LOW);   // set the LED off
  Serial.
  println("LOW");

break;
}

}

}
}
```


### 2. Config Server

Index.php

```PHP<?php

$port="/dev/ttyACM0";

exec('mode $port: baud=9600 data=8 stop=1 parity=n xon=no');

$switch1 = "";

/* Serial script for pan/tilt Camera with servos */
/* Script by Aneal Khimani, 2-12-10 */

//check the GET action SuperGlobal var to see if an
//action is to be performed

if (isset($_GET['action'])) {

$switch1 = $_GET['action'];

//Action required

switch ($switch1) {
case "on":
$fp = fopen( $port, "w");
fwrite($fp, chr(97));
fclose($fp);
break;

case "off":
$fp = fopen( $port, "w");
fwrite($fp, chr(98));
fclose($fp);
break;


}
}

?>

<html>
<body>
<center>

<p>
<font size="4">Flick Switch</font><br />
<table width="30">
<tr><td><a href="<?=$_SERVER['PHP_SELF'] . "?action=on" ?>">On</a></td><td><?php if($switch1 == 'on'){echo "<b>ON</b>";} ?></td></tr>
<tr><td><a href="<?=$_SERVER['PHP_SELF'] . "?action=off" ?>">Off</a></td><td><?php if($switch1 == 'off'){echo "<b>OFF</b>";} ?></td></tr>
</table>
</p>

</center>
</body>
</html>

```
