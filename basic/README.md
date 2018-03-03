# Arduino & Sensors

![](https://www.arduino.cc/en/uploads/Trademark/ArduinoCommunityLogo.png)


### Software Requirements
		1. [arduino IDE](https://www.arduino.cc/en/Main/Software)
		
### Hardware Requirements
		1. Arduino Uno
		2. LED
		3. DHT 11 (Sensor Suhu)
		4. LDR (Sensor cahaya)
		5. HC-SR04 (Sensor Jarak)
		6. PIR (Sensor Gerakan)
		7. IR Receiver
		8. Servo
		
## A. Dasar Teori
### 1. Arduino

![](assets/arduino.jpg)

Arduino adalah sebuah mikrokontroller board tunggal yang memiliki sifat terbuka (open source) yang diturunkan dari platform berbasis Wiring. Pengendali ini dirancang untuk mempermudah penggunaan dalam berbagai bidang elektronik. Hardware arduino mengandung prosesor jenis Atmel AVR, dan memiliki bahasa pemrograman tersendiri (mirip bahasa C). 

### 2. LED

![](assets/led.jpg)

Light Emitting Diode atau sering disingkat dengan LED adalah komponen elektronika yang dapat memancarkan cahaya monokromatik ketika diberikan tegangan DC. LED merupakan keluarga Dioda yang terbuat dari bahan semikonduktor. Warna-warna Cahaya yang dipancarkan oleh LED tergantung pada jenis bahan semikonduktor yang dipergunakannya. 

### 3. DHT 11 (Sensor Suhu)

![](assets/dht11.jpg)

DHT11 adalah salah satu sensor yang dapat mengukur dua parameter lingkungan sekaligus, yakni suhu dan kelembaban udara (humidity). Dalam sensor ini terdapat sebuah thermistor tipe NTC (Negative Temperature Coefficient) untuk mengukur suhu, sebuah sensor kelembaban tipe resisitif dan sebuah mikrokontroller 8-bit yang mengolah kedua sensor tersebut dan mengirim hasilnya ke pin output dengan format single-wire bi-directional (kabel tunggal dua arah).

### 4. LDR (Sensor cahaya)

![](assets/ldr.jpg)

Light Dependent Resistor atau disingkat dengan LDR adalah jenis Resistor yang nilai hambatan atau nilai resistansinya tergantung pada intensitas cahaya yang diterimanya. Nilai Hambatan LDR akan menurun pada saat cahaya terang dan nilai Hambatannya akan menjadi tinggi jika dalam kondisi gelap. Dengan kata lain, fungsi LDR (Light Dependent Resistor) adalah untuk menghantarkan arus listrik jika menerima sejumlah intensitas cahaya (Kondisi Terang) dan menghambat arus listrik dalam kondisi gelap.

### 5. HC-SR04 (Sensor Jarak)

![](assets/ping.jpg)

HC-SR04 adalah sensor pengukur jarak berbasis gelombang ultrasonik. Prinsip kerja sesnsor ini pirip dengan radar ultrasonik. Gelombang ultrasonik di pancarkan kemudian di terima balik oleh receiver ultrasonik. Jarak antara waktu pancar dan waktu terima adalah representasi dari jarak objek. Sensor ini cocok untuk aplikasi elektronik yang memerlukan deteksi jarak termasuk untuk sensor pada robot.

### 6. PIR (Sensor Gerakan)

![](assets/PIR.jpg)

PIR (Passive Infrared Receiver) merupakan sebuah sensor berbasiskan infrared. Akan tetapi, tidak seperti sensor infrared kebanyakan yang terdiri dari IR LED dan fototransistor. PIR tidak memancarkan apapun seperti IR LED. Sesuai dengan namanya ‘Passive’, sensor ini hanya merespon energi dari pancaran sinar inframerah pasif yang dimiliki oleh setiap benda yang terdeteksi olehnya. Benda yang bisa dideteksi oleh sensor ini biasanya adalah tubuh manusia.

### 7. IR Sensor

![](assets/IR.jpg)


Infra red (IR) detektor atau sensor infra merah adalah komponen elektronika yang dapat mengidentifikasi cahaya infra merah (infra red, IR). Sensor infra merah atau detektor infra merah saat ini ada yang dibuat khusus dalam satu modul dan dinamakan sebagai IR Detector Photomodules. IR Detector Photomodules merupakan sebuah chip detektor inframerah digital yang di dalamnya terdapat fotodiode dan penguat (amplifier).


### 8. Servo

![](assets/servo.jpg)

Motor servo adalah sebuah motor DC dengan sistem umpan balik tertutup di mana posisi rotor-nya akan diinformasikan kembali ke rangkaian kontrol yang ada di dalam motor servo. Motor ini terdiri dari sebuah motor DC, serangkaian gear, potensiometer, dan rangkaian kontrol. Potensiometer berfungsi untuk menentukan batas sudut dari putaran servo. Sedangkan sudut dari sumbu motor servo diatur berdasarkan lebar pulsa yang dikirim melalui kaki sinyal dari kabel motor servo.


## B. Instalasi

### 1. Instalasi Virtualbox
Debian Based : `apt-get install virtualbox`

Mac Os : via Official Web dan jalankan file .dmg. [Download](https://www.virtualbox.org/wiki/Downloads)
### 2. Instalasi Vagrant
Debian Based : `apt-get install vagrant`

Mac Os : via official web


### C. Membuat Virtualisasi
Setelah berhasil menginstall vagrant, selanjutnya kita akan mencoba membuat virtualisasi baru menggunakan provider virtualbox. Langkah-langkah pembuatan virtualisasi baru dijelaskan sebagai berikut:

1. Buat folder baru untuk meletakkan konfigurasi.

	`mkdir vagrant-example`
2. Masuk ke dalam folder yang telah di buat.

	`cd vagrant-example`
3. Inisialisasi projek vagrant

	`vagrant init`

	Setelah menjalankan perintah diatas akan dibuat file baru bernama **Vagrantfile**
5. Isi dari **Vagrantfile**
	
		# -*- mode: ruby -*-
		# vi: set ft=ruby :

		# All Vagrant configuration is done below. The "2" in Vagrant.configure
		# configures the configuration version (we support older styles for
		# backwards compatibility). Please don't change it unless you know what
		# you're doing.
		Vagrant.configure("2") do |config|
		  # The most common configuration options are documented and commented below.
		  # For a complete reference, please see the online documentation at
		  # https://docs.vagrantup.com.

		  # Every Vagrant development environment requires a box. You can search for
		  # boxes at https://vagrantcloud.com/search.
		  config.vm.box = "base"

		  # Disable automatic box update checking. If you disable this, then
		  # boxes will only be checked for updates when the user runs
		  # `vagrant box outdated`. This is not recommended.
		  # config.vm.box_check_update = false

		  # Create a forwarded port mapping which allows access to a specific port
		  # within the machine from a port on the host machine. In the example below,
		  # accessing "localhost:8080" will access port 80 on the guest machine.
		  # NOTE: This will enable public access to the opened port
		  # config.vm.network "forwarded_port", guest: 80, host: 8080

		  # Create a forwarded port mapping which allows access to a specific port
		  # within the machine from a port on the host machine and only allow access
		  # via 127.0.0.1 to disable public access
		  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

		  # Create a private network, which allows host-only access to the machine
		  # using a specific IP.
		  # config.vm.network "private_network", ip: "192.168.33.10"

		  # Create a public network, which generally matched to bridged network.
		  # Bridged networks make the machine appear as another physical device on
		  # your network.
		  # config.vm.network "public_network"

		  # Share an additional folder to the guest VM. The first argument is
		  # the path on the host to the actual folder. The second argument is
		  # the path on the guest to mount the folder. And the optional third
		  # argument is a set of non-required options.
		  # config.vm.synced_folder "../data", "/vagrant_data"

		  # Provider-specific configuration so you can fine-tune various
		  # backing providers for Vagrant. These expose provider-specific options.
		  # Example for VirtualBox:
		  #
		  # config.vm.provider "virtualbox" do |vb|
		  #   # Display the VirtualBox GUI when booting the machine
		  #   vb.gui = true
		  #
		  #   # Customize the amount of memory on the VM:
		  #   vb.memory = "1024"
		  # end
		  #
		  # View the documentation for the provider you are using for more
		  # information on available options.

		  # Enable provisioning with a shell script. Additional provisioners such as
		  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
		  # documentation for more information about their specific syntax and use.
		  # config.vm.provision "shell", inline: <<-SHELL
		  #   apt-get update
		  #   apt-get install -y apache2
		  # SHELL
		end

4. Pada contoh kasus ini kita ingin menggunakan os Ubuntu (12.04) Precise 64 bit. Maka dari itu kita perlu download **Vagrant Box** terlebih dahulu. Dengan cara:

	`vagrant box add hashicorp/precise64`

5. Kemudian jika box mendukung lebih dari satu provider akan ditanyakan provider yang akan digunakan. Pilih provider **virtualbox**.
6. Setting box pada Vagrant file dengan cara ganti vm.box yang awalnya **base** menjadi **hashicorp/precise64**

		config.vm.box = "base"
	menjadi

		config.vm.box = "hashicorp/precise64"
7. Simpan file Vagrantfile

### D. Konfigurasi Resource Virtual Machine
Layaknya komputer fisik, virtual machine terdapat memory dan core cpu. Pada **Vagrant**, resource core dan memory virtual machine diatur pada **Vagrantfile**. Untuk mengatur resource virtual machine dapat dilakukan dengan langkah berikut:

1. Uncomment konfigurasi

		config.vm.provider "virtualbox" do |vb|
		   # Display the VirtualBox GUI when booting the machine
		   # vb.gui = true
		
		   # Customize the amount of memory on the VM:
			vb.memory = "1024"
		end
2. Untuk menentukan resource memory yang diperlukan ganti value 

	`vb.memory`
3. Untuk mengatur core cpu, tambahkan baris sebelum **end**.

		config.vm.provider "virtualbox" do |vb|
		   # Display the VirtualBox GUI when booting the machine
		   # vb.gui = true
		
		   # Customize the amount of memory on the VM:
			vb.memory = "1024"
			vb.cpus = 2 
		end

4. Untuk storage tidak dapat diatur oleh vagrant. Mungkin bisa diatur melalui Hypervisor yang digunakan.

### E. Cara Bermain
1. Menjalankan vagrant : `vagrant up`
2. Untuk masuk ke virtual machine : `vagrant ssh`
3. Untuk mematikan virtual machine : `vagrant halt`
4. Untuk menghapus virtual machine : `vagrant destroy`
5. Untuk merestart virtual machine dan akan memuat ulang konfigurasi **Vagrantfile** : `vagrant reload`
6. Untuk menjalankan provisioning : `vagrant provision`

### F. Konfigurasi Internet Pada Virtual Machine
Pada vagrant terdapat 3 jenis konfigurasi agar virtual machine dapat diakses dari host maupun dari luar host.

1. Port Forwarders

	Pada linkungan produksi, aplikasi yang berjalan di virtualisasi harus dapat diakses melalui komputer hostnya. Akses ini dilakukan dengan mekanisme port forwarders . Port forwarders bekerja dengan cara meneruskan akses dari port komputer host menuju port tertentu pada virtualisasi. Port forwarders dapat diilustrasikan dengan gambar berikut. 

	![](assets/port_forwarder.png)


	Klien mengakses port 8080/8443 pada komputer host, kemudian akan diteruskan menuju port 80/443 pada virtualisasi vagrant. Untuk mengaktifkan port forwarders, terdapat step-step sebagai berikut:

	1. Uncomment baris agar port 80 VM dapat diakses melalui port 8080 host

			config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
		dan hapus 

			host_ip: "127.0.0.1"
		agar bisa diakses dari luar host. Sehingga menjadi

			config.vm.network "forwarded_port", guest: 80, host: 8080
	2. Tambahkan baris

			config.vm.network "forwarded_port", guest: 443, host: 8443
		agar port 443 pada virtual machine dapat diakses melalui port 8443
2. Static Local IP

	Ketika banyak virtualisasi yang dijalankan, kita membutuhkan alamat IP lokal agar antar virtualisasi dapat saling berkomunikasi. IP lokal hanya dapat diakses oleh komputer host dan virtualisasi pada komputer host yang sama. Untuk menentukan alamat IP pada virtualisasi lakukan step-step berikut:

	1. Uncomment baris :

			config.vm.network "private_network", ip: "192.168.33.10"
		Virtual machine dapat kita akses melalui ip **192.168.33.10**

		Untuk pemilihan IP, pilihlah ip dengan angka belakang 2-254, karena ip dengan angka belakang 1 sudah digunakan oleh komputer host sebagai router antar virtualisasi. Alamat IP lokal antar virtualisasi tidak perlu harus dalam subnet yang sama. Alamat IP pada subnet yang berbeda tetap bisa berkomunikasi, karena mekanisme routing telah diatur oleh vagrant.
3. Bridged IP

	Pada kondisi tertentu dibutuhkan virtualisasi yang dapat di akses dari luar, contohnya pada layanan cloud vps(virtual private server). Untuk membuat virtualisasi dapat diakses dari luar, dibutuhkan mekanisme yang disebut bridging . Mekanisme bridging ini telah ditangani oleh vagrant. Untuk mengaktifkan fungsi bridged ikuti langkah-langkah berikut:

	* Untuk DHCP: 
		1. Uncomment baris:

				config.vm.network "public_network"

	* Untuk konfigurasi IP static pada virtualiasasi gunakan konfigurasi berikut

			config.vm.network "public_network", ip: "10.151.36.225"

		Ip tergantung subnet dari host

### G. Sinkronisasi folder
Adakalanya kita ingin mendevelop aplikasi menggunakan editor favorit kita seperti sublimetext, netbeans dan lain sebagainya, tetapi kita ingin agar kode-kode aplikasi kita tersebut berada di dalam virtualisasi sehingga ketika terjadi perubahan kode maka kode tersebut langsung dipindahkan ke dalam virtualisasi atau kita ingin folder di dalam virtualisasi dapat diakses melalui komputer host untuk keperluan backup/audit. Hal seperti ini dapat dilakukan menggunakan fitur sinkronisasi pada vagrant. Folder yang di sinkronisasi dapat diakses melalui komputer host atau virtual dengan kondisi tersinkronisasi, sehingga ketika terjadi perubahan melalui komputer host atau melalui virtualisasi data-data dalam folder tersebut tetap sama. Untuk mengaktifkan sinkronisasi folder lakukan langkah-langkah berikut:

1. Buka file Vagrantfile ubah baris berikut.

		# config.vm.synced_folder "../data", "/vagrant_data"
	menjadi

		config.vm.synced_folder "src/", "/var/www"
2. Simpan file Vagrantfile. **src/** adalah folder pada komputer host, sedangkan **/var/www** adalah folder pada virtual machine.

3. Buat folder src di dalam folder projek vagrant example kemudian tambahkan file index.html

		mkdir src
		echo "hello world" >> src/index.html
4. Jalankan virtualisasi.

		vagrant up

5. Masuk ke dalam virtualisasi.

		vagrant ssh

6. Lakukan perubahan pada file src/index.html di komputer host, kemudian cek file index.html yang berada pada folder /var/www di virtual machine. Kedua file akan berisi data yang sama, karena telah tersinkronisasi.

### H.Provisioning aplikasi pada virtual machine
Kita menginginkan komputer virtual yang kita gunakan telah terinstall aplikasi aplikasi yang kita butuhkan. Tahapan instalasi dan konfigurasi tersebut sering dikenal dengan sebutan provisioning. Pada vagrant, provisioning dapat dilakukan dengan mudah. Kita dapat membuat script menggunakan bash scripting untuk melakukan provisioning. Langkah-langkah untuk melakukan provisioning adalah sebagai berikut:

* Menggunakan File bootstrap

	1. Buat bash script dengan nama bootsrap.sh pada folder yang sama dengan vagrant file.
	2. Untuk menginstall apache tuliskan baris berikut pada file bootsrap.sh.

			#!/usr/bin/env bash
			apt-get update
			apt-get install -y apache2
	3. Pada file Vagrantfile diatas **end** terakhir, tambahkan baris  

			config.vm.provision :shell, path: "bootstrap.sh".

		Sehingga menjadi
		
				config.vm.provision "shell", path: "bootstrap.sh"
			end

	4. Simpan file Vagrantfile kemudian nyalakan virtualisasi.

			vagrant up

	5. Jika virtualisasi sudah dibuat dan sedang menyala maka jalankan fungsi reload dengan menambahkan flag **--provision** untuk memaksa vagrant merestart virtualisasi dan menjalankan script provisioning ketika mesin virtual sedang aktif.

			vagrant reload --provision

		atau tanpa merestart ulang virtual machine

			vagrant provision

	6. Cek apakah provisioning berhasil dengan masuk kedalam virtualisasi menggunakan ssh.

			vagrant ssh
	7. Cek apakah apache telah berhasil terinstall

			service apache2 status
* atau dengan Menambahkan command pada **Vagrantfile**
	1. Uncomment baris:

			config.vm.provision "shell", inline: <<-SHELL
			  	apt-get update
			  	apt-get install -y apache2
			SHELL


Proses provisioning dapat juga menggunakan configuration management seperti ansible, chef, atau puppet. Proses provisioning otomatis menjalankan menggunakan superuser. Jika ingin mematikan superuser dapat menambahkan opsi

	privileged:false

Contoh:

	config.vm.provision "shell", path: "bootstrap.sh",  privileged:false



### I. Referensi
1. Modul Komputasi Awan 2017 oleh Thiar Hasbiya S.Kom, M.Kom
2. Pengalaman

### J. Soal Latihan
1. Buat vagrant virtualbox dan install nginx. Nginx dapat diakses pada port 9000 host.

### K. Tugas
1. Buat vagrant virtualbox dan buat user 'awan' dengan password 'buayakecil'.
2. Buat vagrant virtualbox dan lakukan provisioning install Phoenix Web Framework
3. Buat vagrant virtualbox dan lakukan provisioning install:
	1. php
	2. mysql
	3. composer
	4. nginx
	
	setelah melakukan provioning, clone https://github.com/fathoniadi/pelatihan-laravel.git pada folder yang sama dengan vagrantfile di komputer host. Setelah itu sinkronisasi folder pelatihan-laravel host ke vagrant ke **/var/www/web** dan jangan lupa install vendor laravel agar dapat dijalankan. Setelah itu setting root document nginx ke **/var/www/web**. webserver VM harus dapat diakses pada port 8080 komputer host dan mysql pada vm dapat diakses pada port 6969 komputer host
4. Buat vagrant virtualbox dan lakukan provisioning install:
	1. Squid proxy
	2. Bind9

### J. Soal Latihan
1. Buat vagrant virtualbox dan install nginx. Nginx dapat diakses pada port 9000 host.
