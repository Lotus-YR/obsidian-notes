### Chapter 1 : getting to know HTML
HyperText Markup Language, or HTML for short. So, get ready for some language
lessons. After this chapter, not only are you going to understand some basic
elements of HTML, but you’ll also be able to speak HTML with a little style. Heck,
by the end of this book you’ll be talking HTML like you grew up in Webville.

index.html
```html
<html>
    <head>
        <title>Starbuzz Coffee</title>
        <style type="text/css">       
	        body {
		        background-color: #d2b48c;
		        margin-left:20%;
		        margin-right:20%;
		        border:1px dotted gray;
		        padding:10px 10px 10px 10px;
		        font-family:sans-serif;
	        }
		</style>
    </head>
    
    <body>
        <h1>Starbuzz Coffee Beverages</h1>
        <h2>House Blend, $1.49</h2>
        <p>A smooth, mild blend of coffees from Mexico, Bolivia and Guatemala. </p>
        <h2>Mocha Cafe Latte, $2.35</h2>
        <p>Espresso, steamed milk and chocolate syrup.</p>
        <h2>Cappuccino, $1.89</h2>
        <p>A mixture of espresso, steamed milk and foam.</p>
        <h2>Chai Tea, $1.85</h2>
        <p>A spicy drink made with black tea, spices, milk and honey.</p>
    </body>
</html>
```

miss.html
```html
<html>
	<head>
		<title>Starbuzz Coffee's Mission</title>
		<style type="text/css">       
	        body {
		        background-color: #d2b48c;
		        margin-left:20%;
		        margin-right:20%;
		        border:1px dotted gray;
		        padding:10px 10px 10px 10px;
		        font-family:sans-serif;
	        }
		</style>
	</head>

	<body>
		<h1>Starbuzz Coffee's Mission</h1>
		<p>To provide all the caffeine that you need tp power your life.</p>
		<p>Just drink it.</p>
	</body>

</html>
```

### Chapter 2 : going further, with hypertext
In Chapter 1 we kicked the tires of HTML and found it to be a nice markup
language (the ‘ML’ in HTML) for describing the structure of Web pages. Now we’re
going to check out the ‘HT’ in HTML, hypertext, which will let us break free of a single
page and link to other pages. Along the way we’re going to meet a powerful new
element, the $<a>$ element, and learn how being “relative” is a groovy thing. So, fasten
your seat belts – you’re about to learn some hypertext.

```html
<a href = " .. /xxxx.html">XXXXXX</a>
<a href = "images/xxxx.jpg">XXXX</a>
```

organize your Web site files

### Chapter 3 : building blocks
In this chapter we’re going to ramp up construction: you’re going to take a Web page from conception
to blueprint, pour the foundation, build it, and even put on some finishing touches. All you need is your hard hat and your tool belt, as we’ll be adding some new tools and giving you some insider knowledge that would make Tim “The Toolman” Taylor proud.

```html
<q>inline element</q>
<blockquote>all block element</blockquote>

<p>
<ol>
	<li>first list iterm</li>
	<li>second list iterm</li>
</ol>
</p>

<p>This is a linebraker<br>
which is an empty element</p>

<p>Use entities for special characters in your HTML content, such as &gt; and &lt; for < and > </p>
```

### Chapter 4 : getting connected