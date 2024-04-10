# University PHP Coding Lecture Notes

### What's PHP ?
Betik bir programlama dilidir.
Web tabanlı yazılım geliştirme yanı güçlüdür ve genellikle bu amaçla kullanılır.

```plain text
Author: Rasmus Lerdorf
First Version: 1995
```

Kaynak kodu açık ve ücretsizdir. Server side çalışır. HTML ile birlikte çalışabilir. Geniş işletim sistemi, web sunucu ve veritabanı yazılım desteğine sahiptir.

> Step-By-Step Working Process

1. Yazılan kod sunucu tarafında yorumlanır.
2. Çıktı HTML web sunucusuna yönlendirilir.
3. Web sunucusu çıktıyı tarayıcıya yönlendirir.

> What can be done with PHP?

1. Database apps
2. E-commerce sites
3. Surver, Discussion forums, Search engines, CMS
(...)

## PHP Usage

"echo, print, printf" commands print text on the screen.

### Comments blocks:
> ```php
>   <?php
>       // This is the comment line.
>       echo("PHP Hello World!");
>       /*
>       * Test line 1
>       * Test line 2
>       */
>       echo "PHP Hello World!";
>   ?>
> ```

### Escape characters:
> ```php
>   <?php
>    echo (“\”PHP\” dünyası merhaba”); // çıktısı “PHP” dünyası merhaba
>    // \n New line, \t Tab, \r Return
>   ?>
>```

