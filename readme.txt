sub: How to configure Apache 2.x to evaluate PHP rather than serve it as HTML?

Hello SOF,

I want to serve php files using this tech-combo:

 - ubuntu 14.04 LTS
 - apache 2.4.18
 - php 7.0.3


I installed both apache and php from source using shell commands configure and make.

Installation went smoothly.

I make-installed apache here:

    ~/apache/

I make-installed php here:

    ~/php/

The php install placed a shared library in the apache tree:

    -rwxr-xr-x  1 dan dan 29175263 Feb 18 01:14 libphp7.so

The above file is in this folder:

    ~/apache/modules/

Also the php install edited:

    ~/apache/conf/httpd.conf

I see this entry in there:

    LoadModule php7_module        modules/libphp7.so

I edited httpd.conf to listen at

    0.0.0.0:3080

I brought up the apache server using

    ~/apache/bin/apachectl start

It can serve html files no problem.

I tried the first demo at php.net:

    <html>
     <head>
      <title>PHP Test</title>
     </head>
     <body>
     <?php echo '<p>Hello World</p>'; ?> 
     </body>
    </html>

I placed the syntax in:

    ~/apache/htdocs/php10.php

When I GET php10.php with curl I see this:

    dan@nia111:~ $ 
    dan@nia111:~ $ curl 0.0.0.0:3080/php10.php
    <html>
     <head>
      <title>PHP Test</title>
     </head>
     <body>
     <?php echo '<p>Hello World</p>'; ?> 
     </body>
    </html>
    dan@nia111:~ $ 
    dan@nia111:~ $ 

This is an obvious malfunction.

I should see this:

    <html>
     <head>
      <title>PHP Test</title>
     </head>
     <body>
     <p>Hello World</p>
     </body>
    </html>

Question:

How to debug my tech-combo so Apache evaluates the php-syntax in my php file instead of serving it as plain HTML?




