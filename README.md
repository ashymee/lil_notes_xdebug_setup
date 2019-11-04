# lil_notes_xdebug_setup
> catatan kecil : setting xdebug PHP 7.3.11 (Manjaro)

### Step
1. Kunjungi link ini https://xdebug.org/wizard
2. Buat file index.php
```php
<?php

echo phpinfo();
```
3. Copy semua laman tampil di layar, paste ke dalam kolom kosong di https://xdebug.org/wizard
4. Download ***xdebug-2.8.0.tgz***
5. Ekstrak file ***xdebug-2.8.0.tgz*** dengan perintah
```bash
tar -xvzf xdebug-2.8.0.tgz
```
6. Masuk ke folder
```bash
cd xdebug-2.8.0
```
7. Jalankan perintah 
```bash
phpize
```
output:
```bash
Configuring for:
PHP Api Version:         20180731
Zend Module Api No:      20180731
Zend Extension Api No:   320180731
```
8. Jalankan perintah:
```bash
./configure
```
9. Selanjutnya :
```bash
make
```
10. Kemudian: 
```bash
cp modules/xdebug.so /usr/lib/php/modules
```
11. Edit file php.ini pada direktori /etc/php/php.ini, tambahkan pada baris terakhir
```bash
[XDebug]
zend_extension = /usr/lib/php/modules/xdebug.so
xdebug.remote_autostart = 1
xdebug.profiler_append = 0
xdebug.profiler_enable = 0
xdebug.profiler_enable_trigger = 0
xdebug.remote_enable = 1
xdebug.remote_handler = "dbgp"
xdebug.remote_host = "127.0.0.1"
xdebug.remote_port = 9000
xdebug.remote_cookie_expire_time = 36000
```
12. Restart apache
```bash
sudo systemctl restart httpd.service
```
