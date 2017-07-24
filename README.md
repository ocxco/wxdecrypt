# wxdecrypt

微信小程序服务端解密api，每次使用都需要去官方下载，总是不太方便
 
同时官方示例中PHP代码版本过老，还在使用与类名同名的构造函数，不能直接使用，因此修改并迁移官方示例至composer

composer引入方式: 

```
    "require": {
        "ocxco/wxdecrypt": "dev-master",
    },
```

详细使用方式见包内demo.php
```
<?php

include_once "vendor/autoload.php";

$appid = 'wx4f4bc4dec97d474b';
$sessionKey = 'tiihtNczf5v6AKRyjwEUhQ==';

$encryptedData="CiyLU1Aw2KjvrjMdj8YKliAjtP4gsMZMQmRzooG2xrDcvSnxIMXFufNstNGTyaGS9uT5geRa0W4oTOb1WT7fJlAC+oNPdbB+3hVbJSRgv+4lGOETKUQz6OYStslQ142dNCuabNPGBzlooOmB231qMM85d2/fV6ChevvXvQP8Hkue1poOFtnEtpyxVLW1zAo6/1Xx1COxFvrc2d7UL/lmHInNlxuacJXwu0fjpXfz/YqYzBIBzD6WUfTIF9GRHpOn/Hz7saL8xz+W//FRAUid1OksQaQx4CMs8LOddcQhULW4ucetDf96JcR3g0gfRK4PC7E/r7Z6xNrXd2UIeorGj5Ef7b1pJAYB6Y5anaHqZ9J6nKEBvB4DnNLIVWSgARns/8wR2SiRS7MNACwTyrGvt9ts8p12PKFdlqYTopNHR1Vf7XjfhQlVsAJdNiKdYmYVoKlaRv85IfVunYzO0IKXsyl7JCUjCpoG20f0a04COwfneQAGGwd5oa+T8yO5hzuyDb/XcxxmK01EpqOyuxINew==";

$iv = 'r7BXXKkLb8qrSNn05n0qiA==';

$pc = new \WxDecrypt\WxBizDataCrypt($appid, $sessionKey);
$errCode = $pc->decryptData($encryptedData, $iv, $data );

if ($errCode == 0) {
    print($data . "\n");
} else {
    print($errCode . "\n");
}

```
