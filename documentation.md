The obvious public functions:

```
EmailParser::__construct(string $emailString)
EmailParser::getText()
EmailParser::getHtml()
EmailParser::getAttachments()
```

Other public functions

```php
String EmailParser::getHeader(string $key)

Search the email header with the key and return the value.
Use smallcaps. All header keys are converted to smallcaps

example:
$parser->getHeader('from');

returns:
someDude <some.dude@email.com>
```

```php
Array EmailParser::searchHeader(string $key, string $value)

Search the email header with the key-value pair
use regex string.

example: check if subject contains "[foo-(anything)]"
$parser->searchHeader('/subject/', '/\[foo-[^\]]+\]/');

returns:
array("key"=>"subject", "value"=>"[foo-barsoap]")
```

```php
EmailParser::getParsed()

Get the recursively parsed email.

```

```php
EmailParser::searchByHeader(String $key, String $value, [ String $body = false ])

Get the header and body, from a section of multipart/* email.
Use regex strings

example: find all attachments.
EmailParser::searchByHeader('/content-disposition/', '/attachment/');

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

```
