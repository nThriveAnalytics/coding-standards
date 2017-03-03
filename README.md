# nThrive Analytics Coding Standards

Coding standards for nThrive Analytics.

These coding standards are set by the engineering team to help build a more stable platform. They are meant to be "living" and may change as necessary to new languages or methods. Please adhere to these standards as much as possible.

* [PHP Coding Standards](#php)
* [Javascript Coding Standards](#javascript)
* [HTML Coding Standards](#html)
* [CSS Coding Standards](#css)
* [Importing into PHP Storm](#importing into php storm)

## PHP


### Quotes and Spaces

Use single and double quotes when appropriate. If you're not evaluating anything in the string, use single quotes.

Always use a single space after parentheses and never space in front of statements or within parentheses.

```php
// Bad Code
if ( $a === false ){ ...

// Good Code
if($a === false) { ...
```

### Indentation

* Use tabs for indentation.
* Align multiple relative variables or values along their operator.

```php
$var_development = 'value1';
$var_staging     = 'value1';
$var_live        = 'value1';
```

Align array values for function parameters on new lines where the parameter count is greater than three. As a guiding principal, if a function requires greater than three parameters it may make sense to split the function into smaller methods. 

```php
function newFunction($parameter_one,$parameter_two,$parameter_three) {
  ...
}

function anotherFunction(
  $paramOne,
  $paramTwo,
  $paramThree,
  $paramFour
) {
  ...
}
```

### Brace Style
Braces shall be used for all blocks in the style shown here.

```php
// Bad Code
if( condition )
{
action1();
}

// Do not break statements to new lines
else {
  action2();
}

// Good Code
if(condition) {
  action1();
  action2();
} elseif(condition2 && condition3) {
  action3();
  action4();
} else {
  defaultaction();
}
```

Furthermore, if you have a really long block, consider whether it can be broken into two or more shorter blocks or functions.

### SQL Statements

* Always capitals the SQL parts of the statement like UPDATE or WHERE.
* Always use parametrized statements for MySQL.

```php
$slct = $conn->prepare('SELECT * FROM clients WHERE cube_identifier = :cube');
$slct->bindParam(':cube', $cube_identifier, PDO::PARAM_INT);
$slct->execute();
```

### Naming Conventions

* Class names should be the same as the file name and have capitalization on first letter of word.
* Files follow camel case naming convention, excluding URL facing files which use a hyphen, lowercase convention and classes as covered above.
* Variable and function names should be camel case.

```php
new ClassName {
  public function getFunction($firstParam) {
    return $firstParam;
  }
}
```

### Best Practices

Never use shorthand PHP start tags. Always use full PHP tags.


## Javascript

* Structure
* Naming Conventions
* Commenting
* Equality
* Strings
* Best Practices

### Structure

Use tabs for indentation and line breaks for statements.

```javascript
(function( $ ) {
  // Expressions indented
  function doSomething() {
    // Expressions indented
  }
})(jQuery);
```

if, else, for, while, and try blocks should always use braces, and always go on multiple lines. The opening brace should be on the same line as the function definition, the conditional, or the loop. The closing brace should be on the line directly following the last statement of the block.

```javascript
var a, b, c;
if(myFunction()) {
  // Expressions
} else if((a && b) || c) {
  // Expressions
} else {
  // Expressions
}
```

Objects can be structured inline for three or less declarations. Any more declarations should reside on their own line.

```javascript
// Preferred
var map = {
  ready: 9,
  when: 4,
  'you are': 15
};

// Acceptable for small objects
var map = {ready: 9, when: 4, 'you are': 15};
// Bad
var map = { ready: 9,
  when: 4, 'you are': 15 };
```
### Naming Conventions

Variable and function names should be full words, using camel case with a lowercase first letter.

### Commenting

Comments come before the code to which they refer, and should always be preceded by a blank line. Capitalize the first letter of the comment, and include a period at the end when writing full sentences. There must be a single space between the comment token (//) and the comment text.

Single line comments:

```javascript
someStatement();
// Explanation of something complex on the next line
$('p').doSomething();
```

Multi-line comments should be used for long comments:

```javascript
/*
This is a comment that is long enough to warrant being stretched
over the span of multiple lines.
*/
```

### Equality

Strict equality checks (===) must be used in favor of abstract equality checks (==). The only exception is when checking for both undefined and null by way of null.

```javascript
// Check for both undefined and null values, for some important reason.
if(undefOrNull == null) {
  // Expressions
}
```

### Strings
Use single quotes for string literals. When a string contains single quotes, they need to be escaped with a backslash (\):

```javascript
var myStr = 'strings should be contained in single quotes';
// Escape single quotes within strings:
var myStr = 'Note the backslash before the \'single quotes\'';
```

### Best Practices

Creating arrays in JavaScript should be done using the shorthand [] constructor rather than the new Array() notation.

```javascript
var $array = [];
```

There are many ways to create objects in JavaScript. Object literal notation, {}, is both the most performant, and also the easiest to read.

```javascript
var $object = {};
```

## HTML

* Syntax
* HTML5 doctype
* Attribute Order
* Best Practices

### Syntax

* Indent all nested elements using a single tab.
* Always use double quotes, never single quotes, on attributes.
* Never omit optional closing tags. (eg. or )

### HTML5 doctype

Enforce standards mode and more consistent rendering in every browser possible with this simple doctype at the beginning of every HTML page.

```
<!DOCTYPE html>
```

### Attribute Order

HTML attributes should come in this particular order for easier reading of code:

* lass
* id, name
* data-*
* src, for, type, href, value
* title, alt
* aria-*, role

Classes make for great reusable components, so they come first. Ids are more specific and should be used sparingly (e.g., for in-page bookmarks), so they come second.

```
<a class="..." id="..." data-modal="toggle" href="#">
  Example link
</a>
<input class="form-control" type="text">
<img src="..." alt="...">
```
### Best Practices

Reduce markup. Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML. Take the following example:

```
<!-- Not so great -->
<span class="avatar">
  <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```


## CSS

* Structure
* Selectors
* Commenting
* Best Practices

### Structure

* Use tabs for indentation.
* When grouping selectors, keep individual selectors to a single line.
* Include one space before the opening brace of declaration blocks.
* Place closing braces of declaration blocks on a new line.
* Include one space after : for each declaration.
* Each declaration should appear on its own line.
* End all declarations with a semi-colon.
* Comma-separated property values should include a space after each comma (e.g., box-shadow).
* Lowercase all hex values.
* Quote attribute values in selectors, e.g., input[type="text"].
* Avoid specifying units for zero values, e.g., margin: 0; instead of margin: 0px;.
* Don't include spaces after commas within rgb(), rgba(), hsl(), hsla(), or rect() values.
* Add two blank lines between sections and one blank line between blocks in a section.
* 0 values should not have units unless necessary, such as with transition-duration.

```
/* Bad CSS */
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}

/* Good CSS */
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin: 0 0 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

### Selectors

Exercise your best judgement when it comes to selectors. Being overly simple can cause conflict and being too specific can cause code bloat.

* Use lowercase and separate words with hyphens. Avoid camel case and underscores.
* Avoid over-qualifying selectors. (eg. div.container can simply be .container)
* Use easy to understand names, don't use shorthand for sake of simplicity.
* Use classes over generic element tag for optimum rendering performance.

```
/* Bad CSS */
div.metricContainer,
#chart_container,
.chrt-x {
  padding:15px;   
}

/* Good CSS */
.metric-container {
  padding: 15px;
}
```

### Commenting

Code is written and maintained by people. Ensure your code is descriptive, well commented, and approachable by others.

```
/* Bad example */
/* Modal header */
.modal-header {
  float: left;
}

/* Good example */
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  float: left;
  margin: 0; /* This is an inline comment */
}
```

### Best Practices

* Avoid using inline styling.
* If you are attempting to fix an issue, attempt to remove code before adding more.
* Avoid using declarations on a one-off basis or quick fixes.
* Avoid using the !important tag if possible.

# Importing into PHP Storm
* Download the file PHPStorm-CodeStandards.xml for PHP Storm
* In PHP Storm go to "Preferences" -> "Editor" -> "Code Style"
* Next to "Scheme:" click the "Manage" button
* Click "Import" then select "Intellij IDEA code style XML" and click OK
* Select the file you downloaded and import

If you find that something is incorrect in this code style file, please update it, export a new XML file and commit that change to this repo. Try not to replace the entire file, and only replace the change.
