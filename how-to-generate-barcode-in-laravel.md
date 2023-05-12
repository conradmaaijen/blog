How to generate BarCode in Laravel

In this post, we will use a laravel barcode generator example. You will learn how to save generate bar code in laravel. Here, i will create a very basic example of picqer/php-barcode-generator laravel php.

So you can easily generate any barcode by using laravel 8, 9, any version easily. picqer/php-barcode-generator is a very composer package for generate barcode in our laravel 8 application. I can simply generate any svg, png, jpg and html image of barcode.

---

![How to generate BarCode in Laravel](/images/generate-barcodes.webp)

Here are the steps to generate bar code in Laravel:

## Step 1: Install Laravel

In first step, if you haven’t done already, install a fresh Laravel project.

	composer create-project --prefer-dist laravel/laravel projectname

## Step 2: Install picqer/php-barcode-generator package

Now we have to install a package. picqer/php-barcode-generator package is best for barcode generator, that way we can use it’s method. So, open your terminal and run below command.

	composer require picqer/php-barcode-generator

## Step 3: Create Route

Now In this step, i will create one route for testing our example project. So, let’s add a new route on the file: routes/web.php

	Route::view('barcode', 'barcode');

Step 4: Create a Blade file

Now create barcode.blade.php for displaying the barcode output.

	<!DOCTYPE html>
	<html>
	<head>
    	  <title>Generate BarCode in Laravel</title>
	</head>
	<body>

	<h1>Generate BarCode in Laravel?</h1>

	<h3>Product: 00012456732636</h3>
	@php
      	  $generator = new Picqer\Barcode\BarcodeGeneratorHTML();
	@endphp

	{!! $generator->getBarcode('00012456732636', $generator::TYPE_CODE_128) !!}

	<h3>Product 2: 00012456732636</h3>
	@php
    	  $generatorPNG = new Picqer\Barcode\BarcodeGeneratorPNG();
	@endphp

	<img src​="data:image/png;base64,{!! base64_encode($generatorPNG->getBarcode('00012456732636', $generatorPNG::TYPE_CODE_128)) !!}">
	</body>
	</html>

What’s your output ?


Tags: laravel
