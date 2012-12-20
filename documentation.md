The obvious public functions
---
```
EmailParser::__construct(string $emailString)
EmailParser::getText()
EmailParser::getHtml()
EmailParser::getAttachments()
```
<br />
Other public functions
---
<br />

<b>EmailParser::getHeader($key)</b>
> Search the email header with the key and return the value.<br />
> Use smallcaps. All header keys are converted to smallcaps
> 
> 
> example:
```php
print $parser->getHeader('from');
>
// someDude <some.dude@email.com>
```

<br />
<b>EmailParser::searchHeader(string $key, string $value)</b>
> Search the email header with the key-value pair.<br />
> Use regex string.
> 
> 
> example: check if subject contains "[foo-(anything)]"
```php
print_r( $parser->searchHeader('/subject/', '/\[foo-[^\]]+\]/') );
> 
// array(key=>subject, value=>[foo-barsoap])
```

<br />
<b>EmailParser::getParsed()</b>

> Get the recursively parsed email.
> Returns an array.


<br />
<b>EmailParser::searchByHeader(String $key, String $value, [ String $body = false ])</b>

> Get the header and body, from a section of multipart/* email.
> Use regex strings
> 
> 
> example: find all attachments.
```php
EmailParser::searchByHeader('/content-disposition/', '/attachment/');
> 
>	/*
	Array
      (
        [0] => Array
          (
            [header] => Array
              (
                [content-type] => image/jpeg; name="erika.jpg"
                [content-disposition] => attachment; filename="erika.jpg"
                [content-transfer-encoding] => base64
                [x-attachment-id] => f_hawb57bx5
              )
            [body] => /9j/4AAQSkZJRgABAQEASABIAAD/2wBDAAgGBgcGBQgHBwcJCQgKDBQNDAsLDBkSEw8UHRofHh0a
    HBwgJC4nICIsIxwcKDcpLDAxNDQ0Hyc5PTgyPC4zNDL/2wBDAQkJCQwLDBgNDRgyIRwhMjIyMjIy
          )
        [1] => Array
          (
            [header] => Array
              (
                [content-type] => image/jpeg; name="erika2.jpg"
                [content-disposition] => attachment; filename="erika2.jpg"
                [content-transfer-encoding] => base64
                [x-attachment-id] => g_asdf7878
              )
            [body] => VEqnRHzUS4AWVkgXDcqskT9k4lAukY2VNRx5ppqqYyZVTnjaZAKYUlx9MTzVL6kCdygmZzibBIAT
      2K8d454fT05Fai3hBNwEY5eVXpzKdTibcqyo4FoW7OIhoN02sNx0/NK3Qk29t7OeGP01A1q88VWD      
          )
        )
      )
      */
> 
```
