MailParser.php
==============

Repository for a PHP email parse class

for more information on public functions, read the documentation.

Usage:
```php
$parser = new EmailParser( file_get_contents('the/email/file') );
    
$text = $parser->getText();
$html = $parser->getHtml();
$attachments = $parser->getAttachments();
    

print "the text\n"
print_r($text);
print "=================================\n\n"
    
print "the html\n"
print_r($html);
print "=================================\n\n"
    
print "the attachment(s)\n"
print_r(attachments);

```

Result:

    the text
    Array
      (
        [header] => Array
          (
            [content-type] => text/plain; charset=windows-1252
            [content-transfer-encoding] => quoted-printable
          )
        [body] => some content
      )
    =================================
    
    the html
    Array
      (
        [header] => Array
          (
            [content-type] => text/html; charset=windows-1252
            [content-transfer-encoding] => quoted-printable
          )
        [body] => <html><body><p>some <b>content</b></p></body></html>
      )
    =================================
    
    the attachment(s)
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
            
