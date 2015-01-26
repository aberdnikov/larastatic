# How To Use

## ����������� ����������:
� 
~~~
../app/config/app.php
~~~
������� � ������ �����������
~~~
'providers'       => [
	'Illuminate\Foundation\Providers\ArtisanServiceProvider',
	'Illuminate\Auth\AuthServiceProvider',
	... 
	'Larakit\Larastatic\LarastaticServiceProvider',
],
~~~

## ������������ ����� � ������� ������� � ��������� ����, ��� ����� � 
~~~
../app/start/global.php
~~~
� ����� ����� ������� ������:
~~~
require app_path() . '/staticfiles.php';
~~~
## �������� ���� 
~~~
../app/staticfiles.php
~~~
� �������� ��� ������������ �� ����������� JS/CSS
~~~
<?php
\Larakit\Larastatic\Css::instance()
   ->add('http://fonts.googleapis.com/css?family=Open+Sans:300&subset=cyrillic')
   ->add('http://fonts.googleapis.com/css?family=Oswald:400,700,300')
   ->add('/packages/components/font-awesome/css/font-awesome.css')
   ->add('/packages/components/animate.css/animate.css')
   ->add('/packages/components/jquery-pace/jquery-pace.js')
   ->add('/packages/components/jquery-notific8/jquery.notific8.min.css')
;
\Larakit\Larastatic\Js::instance()
  ->add('/!/build/bootstrap.min.js')
  ->add('/!/static/js/main.js')
;
~~~

## ���, ������ ����� ����������� ����� � ������� ���������� �� ��� �������� ����� ���� � ����� ������������� ��������� �����
~~~
<html>
    <head>
        <title>title</title>
        {{ \Larakit\Larastatic\Css::instance()->__toString(); }}
    </head>
    <body>
		{{ \Larakit\Larastatic\Js::instance()->__toString(); }}
    </body>
</html>
~~~

## ���� � ��� ��������� ������������ Twig ����� ������ "rcrowe/twigbridge", �� 
1) ����������� � app ������ ������
~~~
php artisan config:publish rcrowe/twigbridge
~~~
2) ��������� � 
~~~
../app/config/packages/rcrowe/twigbridge/extensions.php 
~~~
3) ������� � ������ enabled
~~~
return [

    /*
    |--------------------------------------------------------------------------
    | Extensions
    |--------------------------------------------------------------------------
    |
    | Enabled extensions.
    |
    | `Twig_Extension_Debug` is enabled automatically if twig.debug is TRUE.
    |
    */
    'enabled'   => [
        'TwigBridge\Extension\Loader\Facades',
        'TwigBridge\Extension\Loader\Filters',
        'TwigBridge\Extension\Loader\Functions',
		...
		'Larakit\Larastatic\Twig'
~~~
4) ������ � ����� �������� ������ �������� ������� css & js

~~~ 
<html>
    <head>
        <title>title</title>
        {{ css() }}
    </head>
    <body>
		{{ js() }}
    </body>
</html>
~~~ 
