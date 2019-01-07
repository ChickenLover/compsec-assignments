## Code snippet 1.

```
<?php
 if (isset($_GET['redirect'])) {
     header('Location: '.$_GET['redirect']);
 }
 header('Set-Cookie: _afUserId='. $_GET['userId']);
 header('Set-Cookie: _afGroupId='. $_GET['groupId']);
 ?>
 <html>
 <head>
     <meta http-equiv="refresh" content="5;url=<?=$_GET['url']?>"></meta>
 </head>
 <body>
       <?php
           $roleId = explode(":", base64_decode($_COOKIE['roleId']))[0];
           if ($roleId == 'admin') {
               include 'admin_interface.php';
           }
           elseif ($roleId == 'user') {
               include 'user_interface.php'
           }
           else {
               echo '<h2>Unknown role '.$roleId.'\n</h2>';
           }
       ?>

 </body>
 </html>
```

1. roleId просто достается из Cookie, любой может вставить себе base64('admin') и получить доступ к admin_inreface.php (Это недостаток)
2. конкатенация пользовательского ввода в header. Возможна инъекция в raw http от сервера

## Code snippet 2.

```
private static bool IsValidSignature(string data, string signature) {
  var bytes = Encoding.ASCII.GetBytes("eCTR4rhYQVNwn78j" + data);
  var hash = MD5.Create().ComputeHash(bytes);
  return BitConverter.ToString(hash) == signature;
}
...
if (IsValidSignature(Request["data"], Request["signature"])) {
  var decryptor = Aes.Create() { 
     BlockSize = 128;
     Key = Encoding.ASCII.GetBytes("YtGDn6mvAHbp5X7C");
     IV = Encoding.ASCII.GetBytes("mHMUYSjiVxo4wp9R");
   }.CreateDecryptor();
}
```

