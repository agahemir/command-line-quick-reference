- [1. Giriş](#1-giriş)
  - [1.1. İzlenim](#11-izlenim)
- [2. Temeller](#2-temeller)
  - [2.1. Yaygın Kullanılan Komutlar](#21-yaygın-kullanılan-komutlar)
  - [2.2. Kısayollar](#22-kısayollar)
    - [2.2.1. Gezinti](#221-gezinti)
    - [2.2.2. Düzenleme](#222-düzenleme)
    - [2.2.3. Geçmişten Geri Çağırma](#223-geçmişten-geri-çağırma)
- [3. Stream'lar, Pipe'lar ve Yönlendirmeler](#3-streams-pipes-and-redirects)
  - [3.1. Stream'lar](#31-stream)
  - [3.2. Yeniden Yönlendirmeler](#32-yeniden-yönlendirmeler)
    - [3.2.1. Biçimler](#321-biçimler)
    - [3.2.2. Ek Örnekler](#322-ek-örnekler)
      - [3.2.2.1. Send standard output to sout.txt and standard error to serr.txt](#3221-send-standard-output-to-souttxt-and-standard-error-to-serrtxt)
      - [3.2.2.2. Send standard output and standard error streams to the same file sone.txt](#3222-send-standard-output-and-standard-error-streams-to-the-same-file-sonetxt)
      - [3.2.2.3. Ignore both standard input and output](#3223-ignore-both-standard-input-and-output)
  - [3.3. Pipe](#33-pipe)
  - [3.4. xargs](#34-xargs)
  - [3.5. tee](#35-tee)
- [4. Dosya Adı Genişletme](#4-filename-expansion)
- [5. İş Kontrolü](#5-job-control)
- [6. Process handling](#6-process-handling)
  - [6.1. difference between ```ps``` and ```jobs```](#61-difference-between-ps-and-jobs)
- [7. Quoting](#7-quoting)
- [8. Basic file management](#8-basic-file-management)
  - [8.1. list directory ```ls```](#81-list-directory-ls)
  - [8.2. show file contents](#82-show-file-contents)
  - [8.3. file handling](#83-file-handling)
    - [8.3.1. copy](#831-copy)
    - [8.3.2. move or rename](#832-move-or-rename)
    - [8.3.3. delete](#833-delete)
    - [8.3.4. file linking](#834-file-linking)
    - [8.3.5. change directory](#835-change-directory)
- [9. ```grep```](#9-grep)
  - [9.1. Useful ```grep``` options](#91-useful-grep-options)
    - [9.1.1. Examples](#911-examples)
  - [9.2. Regular expression in grep](#92-regular-expression-in-grep)
  - [9.3. Examples](#93-examples)
- [10. ```find```](#10-find)
  - [10.1. Examples](#101-examples)
- [11. ```sed``` filter and transform text](#11-sed-filter-and-transform-text)
  - [11.1. Overview](#111-overview)
  - [11.2. Examples](#112-examples)
  - [11.3. Grouping](#113-grouping)
    - [11.3.1. Grouping Examples:](#1131-grouping-examples)
  - [11.4. Hold Buffer](#114-hold-buffer)
    - [11.4.1. Example](#1141-example)
- [12. ```awk```](#12-awk)
  - [12.1. Actions](#121-actions)
  - [12.2. Special variables](#122-special-variables)
  - [12.3. Examples](#123-examples)
- [13. Command substitution](#13-command-substitution)
  - [13.1. Examples](#131-examples)
- [14. Process substitution](#14-process-substitution)
  - [14.1. Examples:](#141-examples)
- [15. Subshell](#15-subshell)
- [16. ssh](#16-ssh)
- [17. Text editing with ```cut```, ```paste``` and ```join```](#17-text-editing-with-cut-paste-and-join)
  - [17.1. ```cut```](#171-cut)
    - [17.1.1. Examples](#1711-examples)
  - [17.2. ```paste```](#172-paste)
    - [17.2.1. Examples](#1721-examples)
  - [17.3. ```join```](#173-join)
    - [17.3.1. Examples](#1731-examples)
- [18. Aliases](#18-aliases)
  - [18.1. useful aliases](#181-useful-aliases)
- [19. Functions](#19-functions)
  - [19.1. useful functions](#191-useful-functions)
- [20. sort](#20-sort)
- [21. uniq](#21-uniq)
- [22. Conditions](#22-conditions)
  - [22.1. If else](#221-if-else)
  - [22.2. Short circuiting](#222-short-circuiting)
    - [22.2.1. example](#2221-example)
- [23. Loops](#23-loops)
  - [23.1. while loops](#231-while-loops)
    - [23.1.1. example](#2311-example)
  - [23.2. for loops](#232-for-loops)
    - [23.2.1. example](#2321-example)
- [24. One liners](#24-one-liners)
- [25. Further reading](#25-further-reading)
- [26. Change History](#26-change-history)


# 1. Giriş
## 1.1. İzlenim
- Bu belge, genellikle komut satırında yapılan şeylere odaklanacaktır.
- Odak noktası, tek seferlik geçici görevler için araçlar ve tekniklerdir. 
- Belgedeki çoğu şey kabuk komut dosyasına uygulanabilir. Ancak, bu belgede tamamen odaklanılan şey kabuk programlama değildir.
- Bu belge Linux/UNIX içindir.
- Bu belge benim tarafımdan "Türkçe" diline uyarlanmıştır. Çeviriler %100 doğru değildir, eklediğim ve çıkardığım kısımlar mevcut.
# 2. Temeller
## 2.1. Yaygın Kullanılan Komutlar

komut     | açıklama
--          | --
```man```   | Komutlar hakkında bilgi verir. örneğin: <br>```man date```
```date```  | Tarih ve zamanı çıktı verir.
```cal```   | Takvimi çıktı verir.
```ls```    | Bulunduğunuz dizinde hangi dosyaların bulunduğunu söyler <br>*-l* seçeneği ile kullanıldığında, komut, sahibini, boyutunu, dosyanın tarihini, izinlerini, vb. döndürecektir.
```cat```   | Dosyanın içindekilerini gösterir.
```cp```    | Dosya kopyalar.
```mv```    | Dosya taşır.
```diff```  | İki dosyanın farklılıklarını gösterir.
```rm```    | Dosya siler.
```grep```  | Bir veya daha fazla dosyadaki dizelerin içindekileri bulur.
```pwd```   | Mevcut çalışma dizininin adını yazdırır.
```cd```    | Mevcut dizini değiştirir.

## 2.2. Kısayollar

### 2.2.1. Gezinti
klavye kısayolu | açıklama
---               |---
Ctrl+A | İmleci satırın başlangıcına taşır.
Ctrl+E | İmleci satırın sonuna taşır.
Alt+F | İmleci tek sözcük ileriye taşır.
Ctrl+F | İmleci bir karakter ileriye taşır.
Alt+B | İmleci tek sözcükle geriye taşır.
Ctrl+B | İmleci bir arayla geriye taşır.
Ctrl+XX | İmlecin konumunu geçerli konumla önceki konum arasında değiştirir.
 
### 2.2.2. Düzenleme
klavye kısayolu | açıklama
---              |---
Ctrl+U | İmlecin sol tarafında kalan tüm karakterleri keser.
Ctrl+K | İmlecin sağ tarafında kalan tüm karakterleri keser.
Ctrl+W | İmlecin solundaki bir sözcüğü keser.
Ctrl+H | İmlecin solundaki bir karakteri keser.
Alt+D | İmlecin sağındaki bir sözcüğü keser.
Ctrl+D | İmlecin sağındaki bir karakteri keser.
Ctrl+Y | Kesilen karakterleri yapıştırır.
Ctrl+_ | Son silmeyi geri alır.
Tab | Komut dizgelerini tamamlar ya da kullanılabilir tüm komutları listeler.

### 2.2.3. Geçmişten Geri Çağırma
Klavye Kısayolu | Açıklama
---               |---
Crtl+R            | Komut geçmişini arar.
Ctrl+G            | Komut geçmişi seçkesini iptal eder.
Ctrl+P/YUKARI         | Geçmişte kullandığınız bir önceki komutu gösterir.
Ctrl+N/AŞAĞI       | Geçmişte kullandığınız bir ileriki komutu gösterir.

# 3. Stream'lar, Pipe'lar ve Yönlendirmeler
## 3.1. Stream'lar
Linux kabuğunun giriş ve çıkışları "Stream" adı verilen karakter dizileridir. Üç adet standart I/O (giriş-çıkış) akışı bulunur:

Adı  | Açıklama                   |Dosya Tanımlayıcısı
---   |---                             |---
stdout| Komutlardan çıktıyı görüntüler.  | 1
stderr| Komutlardan hatayı görüntüler   | 2
stdin | Komutlara giriş sağlar    | 0
 
## 3.2. Yeniden Yönlendirmeler

### 3.2.1. Biçimler
Giriş ve çıkış yeniden yönlendirmeleri büyüktür ve küçüktür işareti kullanılarak yapılır (<>)

Bracket type   | description
---            | ---
\>             | dosyaya Stream gönderir. Örneğin: <br> ```ls a > o.txt```
\>>            | dosyaya Stream ekleme. Örneğin: <br> ```ls b >> o.txt```
\>&            | Stream'ın içine yazar. Örneğin: <br> ```ls c > o2.txt 2>&1```
<              | Dosyadan Stream alır. Örneğin: <br> ```wc < o.txt```
<<             | Betik içindeki bir komuta beslenecek metni gömer. <br> Örneğin: <br> ```cat << EOF > output.txt``` <br> ```line 1```  <br> ```line 2``` <br> ```line 3``` <br> ```EOF``` <br> ```echo tamamlandı```

### 3.2.2. Ek Örnekler
#### 3.2.2.1. Standart çıktıyı sout.txt'ye gönderir ve standart hatayı serr.txt'ye gönderir.
```komut1 > sout.txt 2> serr.txt```
#### 3.2.2.2. Standart çıktı ve standart hata akışlarını aynı "sone.txt dosyasına gönderir.
```komut1 > sone.txt 2>&1```

Veya

```command1 &> sone.txt```

#### 3.2.2.3. Hem standart girdiyi hem de çıktıyı görmezden gelir.
```command1 &> /dev/null```

***/dev/null** boş bir aygıt dosyasıdır. Bu, kendisine yazılan her şeyi atacak ve okuma sırasında EOF döndürecektir.*

## 3.3. Pipe
Pipe, bir komutun standart çıktısını başka bir komutun girişine yeniden yönlendirebilir.

```command1 | command2 paramater1 | command3 parameter1 parameter2 | command4```

Örnekler:

- Dosya içeriğini yalnızca bir kez yazdırır. Tekrar eden kayıtları kaldırır:<br> ```sort file1 | uniq```

- En sık kullanılan 5 komutu yazdırır: <br>
```history | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn  | head -5```

- Dosya türlerini ve sıklığını yazdırır: <br> ```ls | rev | cut -f1 -d'.' | rev | sort | uniq -c | sort -n```
  
## 3.4. xargs
- Genişletilmiş argümanların kısaltmasıdır.
- Bazı komutlar hem standart girişten hem de komut satırı bağımsız değişkenleri olarak bağımsız değişkenler alabilir.
- Ancak, standart girişten giriş alamayan bazı komutlar vardır. Yalnızca bağımsız değişkenlerden gelen girdileri kabul ederler. Bu komutlar için args kullanmamız gerekir.
- xargs, Standart girişten bağımsız değişkenlere girişi bir komuta dönüştürür.
- Bağımsız değişkenleri izin verilen bir sayıya böler ve komutu her bağımsız değişken grubu üzerinde art arda çalıştırır.
- -n seçeneği kullanılarak, komut başına bağımsız değişken sayısı belirtilebilir. 
   ```find . | xargs -n1 basename```
-  Std girişini bir yer tutucuya atamak için, ```-I{}```. Yer tutucu genellikle std girişini bir komutun ortasına yerleştirmek istediğimizde kullanılır.<br>
   ```ls | xargs -I{} echo {} dosya bulundu```

Örnekler:
- Dizindeki dosyalardaki kod satırlarının sayılarını/sözcükleri/karakterleri yazdırır. <br>
  ```ls | wc```
- Dosya türlerini ve frekanslarını yazdırır. <br>
  ```find . -type f | xargs basename -a | grep "\." | rev | cut -f1 -d'.' | rev | sort | uniq -c | sort -n```
- Dizindeki tüm dosyaları yeniden adlandırır. <br>
  ```ls | xargs -I{} mv {} {}.bkp```

## 3.5. tee
- Komut standart girişten okur ve standart bir çıktıya ve bir veya daha fazla dosyaya yazar
- Bu, hem ekranda bir komutun çıktısını görmek istediğimizde hem de çıktıyı daha sonra analiz için bir dosyaya kaydetmek istediğimizde yararlıdır.

Örnek:
- ```ls | tee fileList.txt```

# 4. Dosya adı genişletme
- Joker karakter, dosya adı veya klasör adında bir veya daha fazla karakteri temsil etmek için kullanılan bir karakterdir.
- Dosya küreleme, bu joker karakterleri tanıyan ve genişletmeyi yapan işlemdir. 

Joker karakter | Açıklama                                                        | örnek      | eşleşenler                           | eşleşmeyenler
---      | ---                                                                | ---          | ---                               | ---
\*       | 0 ve daha fazla karakter ile eşleşir.                                      | ls to*       | to, tom, ton, tow, tommy, tommie  | tata, tea
?        | 1 karakter ile eşleşir.                                                | ls to?       | tom, tow, ton                     | to, tommy, tommie, tata, tea
[abc]    | Parantez içindeki karakterlerden herhangi biriyle eşleşir.                  | ls [bc]at    | bat, cat                          | Bat, Cat, rat
[a-z]    | Parantez içindeki aralıktaki karakterlerden herhangi biriyle eşleşir. | ls day[1-9]  | day1, day2 upto day9              | day11, day
[!abc]   | Parantez içinde olmayan herhangi bir karakterle eşleşir.              | ls [!r]at    | bat, cat, Bat, Cat, Rat           | rat
[!a-z]   | Parantez içindeki aralıkta olmayan herhangi bir karakterle eşleşir. | ls day[!1-9] | day0, days                        | day1 upto day9


# 5. İş Kontrolü
- Komut satırı, bir işlemin yürütülmesini durdurma/askıya alma ve askıya alınmış bir işlemi daha sonraki bir zamanda devam ettirme yeteneği sağlar.
- Çalışan her programa iş denir (Buradaki "iş" bir kabuğun bir süreç grubunu temsil eder).
- Her işe benzersiz bir kimlik atanır.

Komut        | Açıklama
---            | ---
```jobs```     | Geçerli kabuğun çalışan ve askıya alınan tüm işlerini listeler.
```fg```       | İşi ön plana çıkarır.
```bg```       | İşi arkaplana çıkarır.
```kill```     | İşi sonlandırır.
```stop```     | İşi durdurur.
Ctrl+c         | İşi sonlandırır.
Ctrl+z         | İşi askıya alır.

Örnekler:
- İşi önplana çıkarmak için:<br>```fg %2 # burada 2 iş numarasıdır```
- Bir işi askıya almak için:<br>```stop %2 # burada 2 iş numarasıdır```
- Bir işi arka planda sürdürmek için.<br>```bg %2 # burada 2 iş numarasıdır```
- Bir işi sonlandırmak için:<br>```kill %2 # burada 2 iş numarasıdır```

# 6. Süreç Yönetimi

- Birlikte çalışan işlemlerin anlık görüntüsünü almak için ```ps``` komutu kullanılır.
- Bir komutun işlem kimliğini almak için: ```ps -ef | grep command```
- Bir işlemin bitmesini beklemek için: ```bash wait <process id>```
- Bir işlemi öldürmek için:``` kill <process id>```
- Tüm alt işlemlerin tamamlanmasını beklemek için:<br>```wait```
- Belirli bir işlemin tamamlanmasını beklemek için:<br>```wait 1234 # burada 1234 işlem kimliğidir```


## 6.1. ```ps``` ve ```jobs``` Arasındaki Farklar
- ```jobs``` Geçerli kabuğun yönettiği işlerin listesini bildirir.
- ```ps``` Sistemde çalışan bütün işlemlerin listesini bildirir.


# 7. Alıntılar
- Alıntılar, karakterlerden veya kelimelerden özel anlamları çıkarmak için kullanılır.
- Tek tırnak işareti kullanıldığında(''), tırnak içindeki her karakter korunur ve değerlendirilmez.
- Çift tırnak işareti kullanıldığında ("") dolar işareti, ters tırnak ve ters taksim işareti değerlendirilir ve yorumlanır.
- \ (ters taksim) ise karakterin gerçek değerini korumak için kullanılır.
 

Örnekler: 
Örnek          | Komut            | Çıktı
---               | ---                | ---
Alıntı olmadan          | ```echo $HOME```   | /home/user1/
Kaçış dizisi ile  | ```echo \$HOME```  | $HOME
Tek tırnak ile      | ```echo '$HOME'``` | $HOME
Çift tırnak ile      | ```echo "$HOME"``` | /home/user1/

# 8. Temel Dosya Yönetimi

## 8.1. Dizin Listeleme ```ls```
Komut                     | Açıklama
---                         | ---
```ls```                    | Geçerli dizinin içindekileri listeler.
```ls *```                  | Geçerli dizinin içindekileri alt-dizinler ile birlikte listeler.
```ls -l```                 | Geçerli dizinin içindekileri dosya sahibi, izinler, tarih ve boyutu ile listeler.
```ls -a```                 | Gizli dosyaları listeler.
```ls -t```                 | Dosyaları son değiştirilme tarihine göre azalan sırada listeler.
```ls -rt```                | Dosyaları son değiştirilme tarihine göre artan sırada listeler.
```ls -R```                 | Geçerli dizinin ve alt dizinin dosyalarını son alt dizine özyinelemeli olarak listeler.
```ls /path/to/dirextory``` | Belirtilen dizindeki dosyaları listeler.


## 8.2. Dosya İçeriğini Gösterme
Komut                           | Açıklama
---                               | ---
```cat demo.txt```                | Dosyanın içindekilerini çıktı verir. Nispeten küçük dosyalarda kullanılır.
```head demo.txt```               | Show the first part of the file Dosyanın ilk bölümünü gösterir.
```tail demo.txt```               | Show the last part of the file Dosyanın son bölümünü gösterir.
```tail -f demo.txt```            | Dosya büyüdükçe dosyaya eklenen metni gösterir.
```less demo.txt```               | Dosyanın içeriğini bir ekranda bir seferde gösterir.
```less -p "regular" demo.txt```  | Dizgenin eşleştiği ilk satırdaki dosyanın içeriğini gösterir.
```strings -a binaryfile```       | Dosyadaki tüm yazdırılabilir karakterlerin sırasını yazdırır.
```diff file1 file2```            | İki dosya arasındaki farkları gösterir.

## 8.3. Dosya Yönetimi

### 8.3.1. Kopyalama
Komut                           | Açıklama
---                               | ---
```cp dosya1 dosya2```              | dosya1'den dosya2'ye kopyalama
```cp dosya1 dosya2 dizin1```   | dosya1 ve dosya2'yi dizin1'e kopyalama
```cp -R dizin1 dizin2``` | dizin1'deki içerikleri dizin2'ye kopyalama
```cp *.txt dizin1```         | Sonu .txt olan bütün dosyaları dizin1'e kopyalama

### 8.3.2. Taşıma ve Yeniden Adlandırma
Komut                           | Açıklama
---                               | ---
```mv dosya1 dosya2```              | dosya1'i dosya2 olarak yeniden adlandırma
```mv dosya1 dizin1/```        | dosya1'i dizin1'e taşıma
```mv *.jpg dizin1/```        | Sonu .jpg olan bütün dosyaları dizin1'e taşıma

### 8.3.3. Silme
command                           | description
---                               | ---
```rm dosya1```                    | dosya1'i siler.
```rm file1 file2```              | dosya1 ve dosya2'yi siler.
```rm *.png```                    | Sonu .png olan bütün dosyaları siler.
```rm -d emptyDirectory```        | Remove an empty directory Boş bir dizini siler.
```rm -r directory1```            | Tüm dosyaları, alt dizinleri ve dizin1 dizinini silme.

### 8.3.4. Dosya Bağlantısı
- Sembolik bağlantı, başka bir dosyaya veya dizine işaret eden bir dosyadır.
- Dosya bağlantılarının 2 adet biçimi bulunur.
  - **Sabit Bağlantı** -> Mevcut dosya için ek bir addır. Her dosya benzersiz bir numara ile ilişkilendirilir. Bu benzersiz numaraya inode denir. Sabit Bağlantı, 2 veya daha fazla dosya adını aynı inode ve sırayla aynı dosyayla ilişkilendirir. Orijinal dosya kaldırılırsa, içeriğe sabit bağlantı yoluyla erişilebilir.
  - **Yumuşak Bağlantı** -> Bir dosya veya dizine dolaylı bir işaretçidir. İçeriğine değil, yalnızca orijinal dosyanın yoluna sahiptir.

Komut                           | Açıklama
---                               | ---
```ln dosya1 bağlantu1```              | dosya1'e sabit bağlantı oluşturun (bağlantı1) ile.
```ln -s dosya1 bağlantı1```           | dosya1'e yumuşak bağlantı oluşturun (bağlantı1) ile.

### 8.3.5. Dizin Değiştir (CD)

command                           | description
---                               | ---
```cd```                          | Ev dizinine değiştirir. (Uçbirimde şuan olduğunuz dizini)
```cd ~```                        | Ev dizinine değiştirir. (Uçbirimde şuan olduğunuz dizini)
```cd -```                        | Önceki dizine döner. (Uçbirimde şuan olduğunuz dizini)
```cd ..```                       | Üst dizine değiştirir. (Uçbirimde şuan olduğunuz dizini)
```cd \```                        | Kök dizini değiştirir. (Uçbirimde şuan olduğunuz dizini)
```cd ~/dir1/dir2```              | Ana dizine göre dizine geçer.


# 9. ```grep```
- Dosyalarda kalıp arar ve giriş kalıbıyla eşleşen her satırı çıktı verir.
Kullanımı: ```grep -<options> <pattern> <filenames>``` bu şekildedir.
- Grep, tek bir dosyada veya birden çok dosyada arama yapmak için kullanılabilir.

## 9.1. Kullanışlı ```grep``` seçenekleri

option  | description
---     | ---
-i      | Durumu göz ardı eder.
-n      | Satır numaralarını satırlarla birlikte gösterir.
-v      | Desen(istenen kalıba)'e uymayan satırları gösterir.
-c      | Eşleşen satırların sayısını gösterir.
-l      | Eşleşen desene sahip dosyanın dosya adını gösterir.
-o      | Yanlızca eşleşen dizeyi yazdırır, yani eşleşen dizeye sahip bütün satırlar yazdırılmaz.
-A\<n>  | Eşleşmeden sonrasına n satırını dahil et.
-B\<n>  | Eşleşmeden öncesine n satırını dahil et.
-C\<n>  | Eşleşmeden sonrasına ve öncesine n satırını dahil et.

### 9.1.1. Örnekler
- diyelim ki bir demo dosyası(demo.txt) aşağıdaki içeriğe sahip

> BU BÜYÜK HARFLİ<br>
> bu küçük harfli<br>
> Bu normal çizgili<br>
> Bu satır da normal<br>
> Satır sayısı 4<br>
> Satır #5<br>
> son satır

- Bir dosyada bir dize arar.<br>
  ```grep "bu" demo.txt```

- Dosyada büyük/küçük harf eşleşmesi olmadan bir dize arar.<br>
  ```grep -i "bu" demo.txt```

- Bir dosyada bir dize arayın ve hem satır numarasını hem de çıktıyı alır.<br>
  ```grep -n "bu" demo.txt```

- Aranan dizeyle eşleşen satır sayısını alır.<br>
  ```grep -c "bu" demo.txt```

- Aranan dizenin bulunduğu dosya adını alır.<br>
  ```grep -l "bu" demo.txt```

- Eşleşen satırdan sonra 2 satır alır.<br>
  ```grep -A2 "Bu" demo.txt```

- Eşleşen satırdan önce 2 satır alır.<br>
  ```grep -B2 "Bu" demo.txt```

- Eşleşen satırdan önce ve sonra 2 satır alır.<br>
  ```grep -C2 "Bu" demo.txt```
 
## 9.2. Grep'te Düzenli İfadeler (Regex)
- Düzenli ifadeler, metindeki arama düzenini belirten karakter dizileridir.
- Düzenli ifadelerde, farklı karakterlerin farklı anlamları vardır.

Karakter | Açıklama
---       | ---
[abc]     | matches any one of the characters in the square brackets
[a-d]     | matches any one of the characters in the range specified in the square brackets
^start    | matches the pattern only if the pattern is at the start of the line 
end$      | matches the pattern only if the pattern is at the end of the line
[^abc]    | matches any one character that is NOT present in the square brackets
[^a-d]    | matches any one character that is NOT present in the range
.         | matches any one character
\*        | mathces 0 or more occurences of the preceding character
.*        | matches zero or more of any character

## 9.3. Examples

- Match any one character<br>
  ```grep "[Tt]his" demo.txt```

- Search for line starting with the search pattern<br>
  ```grep "^last" demo.txt```

- Search for line ending with the search patter<br>
  ```grep "regular$" demo.txt```

- Search for line with a character in specified range<br>
  ```grep "[0-9]" demo.txt```

- Search for line without a character in specified range<br>
  ```grep "[^0-9]" demo.txt```

- Search for a line where the middle characters are not known<br>
  ```grep "line.*regular" demo.txt```

**Note:** grep can have regular expressions in the search pattern part, and can have wildcards in the files to search section.

# 10. ```find```
- the ```find``` command is used to search and locate the list of files and directories
- the list returned will satisfy the conditions used in find command.
- syntax is ``` find [starting point] [expression] ```
- ```-exec [command]``` can be used to run command on the files located by ```find```

## 10.1. Examples
- find files with specific name<br> ```find . -name demo.txt```
- find files with a specific pattern<br> ``` find ./Codes -name *.cpp```
- find directories with specific name<br> ```find . -name Codes -type d```
- find files with permission as 777 and change permissions to 644<br> ```find . -type f -perm 0777 -print -exec chmod 644 {} \;```
- find and remove files<br>```find . -type f -name "*.bkp" -exec rm -f {};```

# 11. ```sed``` filter and transform text
## 11.1. Overview
- looks for pattern and edits them
- works on both files and stdin
- original files is not updated
- results are put into standard output
- syntax is ``` sed 'instructions' file```
- instruction is of format ``` '[address]command/regex/replace/modifier' ``` 
  - example - '5,15s/abc/ABC/g' -> this will substitute abc with ABC in lines 5 to 15. 
    - modifier g specifies that all occurences of abc in line will be replaced with ABC
- when address is used, the lines belonging to the address are examined/modified. -> ```sed '1,100 s/A/a/' file.txt```. this restricts substition to first 100 lines.
- By default all the lines are printed. When '-n' flag is used, this behavior is suppressed. Nothing will be printed unless an explicit request to print is found.
- A pattern can be used as a address -> ```sed -n '/start/,/stop/ p' file.txt```
- When '!' is used, the command is run outside of the address -> ```sed -n '/match/ !p' file.txt```

command | description
---     | ---
d       | delete
p       | print
s       | substitute
q       | quit
a       | insert a line after pattern
i       | insert a line before pattern
c       | change a line
y       | transform

## 11.2. Examples
- remove blank lines<br>``` sed '/^$/d' file.txt```
- remove all lines with search string<br>```sed '/Search/d' file.txt```
- remove all instances of search string<br>```sed 's/Search//g' file.txt```
- print lines with the search string<br>```sed '/Search/ p' file.txt```
- substitue a string with another<br>```sed 's/oldString/newString/g' file.txt```
- remove trailing spaces<br>```sed 's/ *$//' file.txt```
- remove leading spaces<br>```sed `s/^ *//' file.txt```
- add spaces to start of everyline<br>```sed 's/^/    /' file.txt```
- print the first 10 line<br>```sed '10 q' file.txt```<br>```sed -n '1,10 p' file.txt```
- append line after a pattern<br>```sed '/pattern/ a add line here' file.txt```
- insert line before a pattern<br>```sed '/pattern/ i add line here' file.txt```
- change a line with a pattern<br>```sed '/pattern/ c line changed here' file.txt```
- change a->p, b->q, c->r<br>```sed 'y/abc/pqr/' file.txt```
  
## 11.3. Grouping
- sed allows capturing specific parts of text into groups.
- these groups can be manipulated
- group is enclosed within parentheses expression "\(" and "\)" in the search string
- each group is assigned a number. The first group is assigned \1 and so on.
- \1 can be both in pattern string and replacement string

### 11.3.1. Grouping Examples:
- switch first and second columns<br>```sed 's/\([a-z]*\) \([a-z]*\)/\2 \1/' file.txt```
- print lines which have consecutive duplicate words<br>```sed -n '/\([a-z][a-z]*\) \1/p' file.txt```
- remove consecutive duplicate words in a line<br>```sed 's/\([a-z][a-z]*\) \1/\1/' file.txt```

## 11.4. Hold Buffer
- When sed read text, each line is placed into a temporary space.
- When a new line is read, the old text is replaced by the new line in the temporary space.
- This temporary space is called pattern space.
- Hold buffer is like a long term storage. text can be copied to and from pattern space.

command | description
---     | ---
x       | exchange hold space and pattern space
h       | copy pattern buffer into hold space
H       | append pattern buffer into hold space
g       | copy hold space to pattern space
G       | append hold buffer into pattern buffer

### 11.4.1. Example
- print one line after and before the pattern match<br>```sed -n '/999/ !{x;d};/999/ {x;p;x;p;n;p}' file.txt```
- add space after every line<br>```sed 'G' file.txt```
- insert blank line above every line which matches pattern<br>```sed '/start/ {x;p;x}' file.txt```
- Insert blank line after every line which matches pattern<br>```sed '/start/ {G}' file.txt```
- Insert blank line before and after every line which matches pattern<br>```sed '/start/ {x;p;x;G}' file.txt```

# 12. ```awk```
- command line utility to find, process and transform text files
- the basic syntax is ```pattern { action }```
  - the pattern is compared with every input line. pattern can be any regular expression
  - when the pattern matches, the action is performed
  - when no pattern is provided, the action is applied to every line
  - example -> ```/^HTTP/ {print}```
    - every line starting with HTTP is printed
  - there are 2 other important patterns
    - BEGIN - specifies actions to be performed, before any line is read
    - END   - specifies actions to be performed, after all lines are read
    - Example -> ```awk 'BEGIN{print "start"} {print} END{print "end"}' file.txt```
      - first *start* is printed, then all lines of file.txt are printed and then *end* is printed
- awk interprets each line as a record of fields
- one or more consecutive spaces or tabs are considered as a single delimiter between fields
- $1, $2, etc. represents the first field, second field, and so on.
- $0 represents the entire input line
- awk has 2 data types - strings and integers
- awk internally converts variable according to context
- awk supports associative arrays. example ```var[key] = value```
- on integers, basic arithmatic operations (+-*/%) are supported. autoincrement(++) and decrement(--) is also supported.

## 12.1. Actions
- following are few actions that can be performed

action                                                                      | description
---                                                                         | ---
{ print $0; }                                                               | print records
{ exit; }                                                                   | ends program
{ next; }                                                                   | skips current line
{a=$1; b="X"}                                                               | variable assignment
{ c[$1] = $2 }                                                              | array varaible assignment
{if (condition) { action } else if (condition) { action } else { action }}  | if else conditions
{ for (i=1; i < x; i++) { action } }                                        | for loop
{ for (item in c) { action } }                                              | for loop iterating over a list

## 12.2. Special variables

variable    | desc
---         | ---
FS          | Input field separator. can be modified
RS          | Input record separator. default value is newline. can be modified by user
OFS         | Output field separator. can be modified
ORS         | Output record separator. default value is newline. can be modified by user
NF          | Number of fields in the current line (record). cannot be updated by user
NR          | Number of lines processed so far. cannot be updated by user

*Note: -F option can be used to update the input field separator -> ```awk -F":"'{ print $1 }' file.txt```*

## 12.3. Examples
- split up “,” (comma) separated fields and print the third field ($3)<br>```awk -F"," '{print $2}' file.txt```
- print the 3rd field of a csv if the second field ($2) exists and is not empty<br>```awk -F"," '{if ($2)print $3}' file.txt```
- print the last field in each line<br>```awk -F"," '{ print $NF }' file.txt```
- print the line after the line matching search pattern<br>```awk '/pattern/ { i=1; next; } {if(i) {i--; print;}}' file.txt```
- print the line and the 2 lines after the line matching search pattern<br>```awk '/regexp/ {i=3;} { if(i) {i--; print;}}' file.txt```
- print the lines from a file starting at the line matching *start* until the line matching *stop*<br>```awk '/start/,/stop/' file.txt```
- count lines (wc -l)<br>```awk 'END{print NR}' file.txt```
- print matching lines (grep)<br>```awk '/pattern/'```
- print non matching lines (grep -v)<br>```awk '!/pattern/'```
- remove duplicate consecutive lines (uniq)<br>```awk 'a !~ $0 {print}; {a=$0}' file.txt```
- print first 10 lines of file (head)<br>```awk 'NR < 11' file.txt```
- print last 10 lines of file (tail)<br>```awk '{vect[NR]=$0;} END{for(i=NR-9;i<=NR;i++) {print vect[i];}}' file.txt```
- print the total number of bytes used by files<br>```ls -l | awk '{ x += $5 } END { print "Total bytes: " x }'```

# 13. Command substitution
- In command substitution, the output of a command replaces the command
- the output of a command can be used an argument to another command
- syntax is ``` `command` ```

## 13.1. Examples
- assign the output of a command to a variable<br> ``` DATE=`date` ```
- use the output of command as a parameter of another command<br> ``` vi `grep -l 123 *` ```

# 14. Process substitution
- the input or output of a command can appear as a file. This is known as process substitution
- this technique is useful when we want to use the output of multiple commands as the input to a command
- process substitution can also be used to capture output and redirect it to the input of a process
- template - ```<(command)``` and ```>(command)```

## 14.1. Examples:
- sort and compare two files<br>
  ```diff <(sort file1) <(sort file2)```

- compare 2 folders<br>
  ```diff <(ls $first_directory) <(ls $second_directory)```

# 15. Subshell
- a subshell is a child process launched by a shell
- whenever a shell script is run, a subshell is created and the script is run in the subshell
- variables defined in parent shell can be accessed if ```export``` is used while defining the variable
- subshells can also be created using parentheses<br>
  ```(command1; command2; command3)```
- subshells are a convenient way to group commands. 
- can be used to temporarily move to a different directory
```bash
#do something in current directory
(cd some/other/directory; other-command)
#back in the original directory
```
- to run a command or script in the current shell, without creating a subshell, use '.' as in ```. script.sh```


# 16. ssh
- ssh (SSH client) is a program for logging into a remote machine and for executing commands on a remote machine
- syntax ```ssh user@host```
- running a single command on remote server<br>```ssh user@host command_to_run```
- logging into server with different port<br>```ssh -p portnum user@host```
- ssh connection using host in the middle```ssh -t reachable_host ssh unreachable_host```


# 17. Text editing with ```cut```, ```paste``` and ```join```

## 17.1. ```cut```
- ```cut``` command cuts out sections from each line and writes result to standard output
- syntax is ```cut OPTION [FILE]```

option  | description
---     | ---
-c      | character range which will be selected
-d      | delimiter which will separate each fields in line in file
-f      | fields which will be printed

when -c option is used, ranges can be specified. Each range can be one of:
range type  | description
---         | ---
N           | Nth character
N-          | fron Nth character to end of line
N-M         | from Nth character to Mth character
-M          | from first to Mth character

### 17.1.1. Examples
- print the first and third columns of a csv file<br>```cut -f1,3 -d"," file.txt```
- print the first 3 characters of each line<br>```cut -c -3 file.txt```

## 17.2. ```paste```
- merges lines of files
- by default, the lines from each files are delimited by tab
- when '-' is used instead of filename, the command reads from standard input
- syntax ```paste [OPTION] [FILE] [FILE]```
  
option  | description
---     | ---
-d      | used to specify the delimiter
-s      | paste one file at a time

### 17.2.1. Examples
lets take 2 files - number.txt and name.txt
> cat number.txt
> 1<br>
> 2<br>
> 3<br>
> 4<br>

> cat name.txt
> Alice<br>
> Bob<br>
> Charlie<br>
> David<br>

- merge 2 files, first file will give the first column and second file will give the second column<br>```paste number.txt name.txt```
- merge 2 files, delimited by ','<br>```paste -d"," number.txt name.txt```
- merge 2 files, sequentially, i.e first only first file is printed and then only the second file<br>```paste -s number.txt name.txt```

## 17.3. ```join```
- join lines of two files on a common field
- syntax ```join [OPTIONS] FILE1 FILE2```

### 17.3.1. Examples
lets take 2 files - number.txt and name.txt
> cat number.txt
> 1 100<br>
> 2 101<br>
> 3 102<br>
> 4 103<br>
> 5 104<br>

> cat name.txt
> 1 Alice<br>
> 2 Bob<br>
> 3 Charlie<br>
> 4 David<br>

- join 2 files based on the first column<br>```join number.txt name.txt```

# 18. Aliases
- aliases are short names for long commands
- when we need to execute long commands multiple times, it is advisable to create aliases
- syntax - ```alias [-p] [name[=value]]```
- we can create permanent alias by storing them in configuration files
- to temporarily bypass an alias, use \ -> ```\ll```

- creating a alias<br>```alias name='values'```
- removing alias<br>```unalias name```
- print all defined alias<br>```alias -p```

## 18.1. useful aliases
```bash
alias gh='history|grep'
alias c=clear
alias cx='chmod +x'
alias ..='cd ..'
alias sl=ls
alias left='ls -t -1'
alias count='find . -type f | wc -l'
alias f='find . |grep '
```

# 19. Functions
- set of commands that accomplish a specific task
- can be used numerous times
- helps avoid writing the same code repeatedly
- can use loops and conditions within them
- arguments can be passed to functions
- by using ```export -f functionname```, we can make the functions available to shell scripts
  - export can be added to configuration files like *.bashrc*
  - To keep things modular, create a new file called ~/.bash_functions and then have your .bashrc load it
- syntax<br> 
```bash
function_name () {
  commands
}
```

```bash
function_name () { commands; }
```

## 19.1. useful functions
```bash
mcd() { mkdir -p "$1"; cd "$1";}
cdl() { cd "$1"; ls;}
```

# 20. sort
- sort lines text files

option  | description
---     | ---
-r      | sort in reverse order
-n      | sort in numberical order
-k <n>  | sort based on nth column
-u      | sort and remove duplicates

# 21. uniq
- report or omit repeated lines
- the input file must be sorted

option  | description
---     | ---
-c      | show how many times a line is repeated
-d      | prints only the repeated lines only once
-u      | prints only the unique lines
-i      | case insensitive comparison


# 22. Conditions
## 22.1. If else
- if-then-else is supported in command line
- Syntax
```bash
if [ condition1 ]; then command1;
elif [ condition2 ]; then command2;
else command3; fi
```

```bash
if [ condition1 ]; then command1; elif [ condition2 ]; then command2; else command3; fi
```
- there are different types of conditions
  1. file based condiitons

conditions  | description
---         | ---
-a          | check if file exists
-r          | check if file exists and is readable
-w          | check if file exists and is writable
-d          | check if file exists and is a directory

  2. string based conditions

conditions  | description
---         | ---
==          | check if both the strings are equal
!=          | check if both the strings are not equal
\>          | check if the first string is lexicographically greater than the second
<           | check if the first string is lexicographically smaller than the second
-n          | check if the string has a length more than 0
-z          | check if the string is an empty string

  3. number based conditions

conditions  | descr>iption
---         | ---
-eq         | check if the numbers are equal
-ne         | check if the numbers are not equal
-gt         | check if the first number is greater than the second
-ge         | check if the first number is greater than or equal to the second
-lt         | check if the first number is less than the second
-le         | check if the first number is less than or equal to the second


- 0 is considered true and numbers greater than 0 are considered false. 
  - this is because in Unix/Linix, when a process ends successfuly, it returns 0

## 22.2. Short circuiting
- an alternative way of using conditions is by using logical AND (&&) and logical OR(||)
- evaluation of a logical expression is stopped, as soon as the outcome has been determined. This is known as short-circuiting.
- in case of Logical AND, as soon as sub-expression becomes false, the whole expression evaluates to false
  - in case of *expr1 && expr2*, if expr1 evaluates to false, then the whole expression will evaluate to false. So, expr2 is not evaluated at all.
  - && can be used to ensure that command2 is run only if command1 ends successfully. example ->```command1 && command2``` 
- in case of Logical OR, as soon as sub-expression becomes true, the whole expression evaluates to true
  - in case of *expr1 || expr2*, if expr1 evaluates to true, then the whole expression will evaluate to true. So, expr2 is not evaluated at all.
  - || can be used to ensure that command2 is run only if command1 fails. example -> ```command1 || command2```

### 22.2.1. example
- create folder if it does not exist  
```bash
  [ -d ./some/path/folder ] || mkdir /some/path/folder
```

- create create file only if folder exists
```bash
  cd /some/path/folder && touch file.txt
```

# 23. Loops
## 23.1. while loops
- the loop runs as long as the given condition is true
- syntax 
  ```bash 
  while [ condition ]; do commands; done
  ```
### 23.1.1. example
- print all the folders with .c files<br>
```bash
find . -name *.c | {while read filename; do dirname $filename; done;} | sort | uniq # dirname returns the directory name
```


## 23.2. for loops
- the loop iterates over a list of values or preset number of times
- syntax 
  ```bash
  for <variable name> in <a list of items>;do <some command> $<variable name>;done;
  ```
### 23.2.1. example
- copy files from one folder to another
```bash
for i in ./code/*.txt; do cp $i /home/code/backup; done
```
# 24. One liners

- print the files and directories in tree structure<br>```find . | sed -e "s/[^-][^\/]*\// |/g" -e "s/|\([^ ]\)/|-\1/"```
- print the directories in tree structure<br>```find . -type d   | sed -e "s/[^-][^\/]*\// |/g" -e "s/|\([^ ]\)/| - \1/"```
- quick access to ascii table<br>```man ascii```
- find common lines in 2 files<br>```cat file1 file2 | uniq -d```
- find lines in file1 that is not present in file2<br>```cat file1 file2 file2 | uniq -u```
- find most frequently used commands<br>```history | cut -c8- | sort | uniq -c | sort -rn | head```
- recursively remove only directories with no files<br>```find . -depth -type d -exec rmdir {} \;```

# 25. Further reading
- 

# 26. Change History
- presented in reversed chronological order i.e. the latest change is at the top

Name                 | Date         | Change Description
----                 | ----         | ---
Utsav Barman         | 25 Jan 2022  | Added wait, globbing, grep -o; fixed typos
Utsav Barman         | 24 Jan 2022  | Initial draft




