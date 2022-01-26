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
Klavye Kısayolu | Açıklama
---               |---
Ctrl+A | İmleci satırın başlangıcına taşır.
Ctrl+E | İmleci satırın sonuna taşır.
Alt+F | İmleci tek sözcük ileriye taşır.
Ctrl+F | İmleci bir karakter ileriye taşır.
Alt+B | İmleci tek sözcükle geriye taşır.
Ctrl+B | İmleci bir arayla geriye taşır.
Ctrl+XX | İmlecin konumunu geçerli konumla önceki konum arasında değiştirir.
 
### 2.2.2. Düzenleme
Klavye Kısayolu | açıklama
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
[abc]     | Köşeli parantez içindeki karakterlerden herhangi biriyle eşleşir.
[a-d]     | Köşeli parantez içinde belirtilen aralıktaki karakterlerden herhangi biriyle eşleşir.
^start    | Yalnızca desen satırın başındaysa desenle eşleşir.
end$      | Yalnızca desen satırın sonundaysa desenle eşleşir.
[^abc] | Köşeli parantez içinde OLMAYAN herhangi bir karakterle eşleşir.
[^a-d] | Aralıkta OLMAYAN herhangi bir karakterle eşleşir.
. | Herhangi bir karakterle eşleşir.
\* | Önceki karakterin 0 veya daha fazla tekrarını hesaplar.
.* | Herhangi bir karakterin sıfır veya daha fazlasıyla eşleşir.

## 9.3. Örnekler

- Herhangi bir karakterle eşleşme:<br>
  ```grep "[Tt]his" demo.txt```

- Arama düzeniyle başlayan satırı arayın: <br>
  ```grep "^last" demo.txt```

- Arama modeliyle biten satırı arayın:<br>
  ```grep "regular$" demo.txt```

- Belirtilen aralıkta bir karaktere sahip satırı arayın:<br>
  ```grep "[0-9]" demo.txt```

- Belirtilen aralıkta karakter içermeyen satırı arayın: <br>
  ```grep "[^0-9]" demo.txt```

- Ortadaki karakterlerin bilinmediği bir satır arayın<br>
  ```grep "line.*regular" demo.txt```

**Not:** grep, arama deseni bölümünde normal ifadelere sahip olabilir ve aranacak dosyalar bölümünde joker karakterlere sahip olabilir.

# 10. ```find```
- ```find``` komutu dosya ve dizin listesini aramak ve bulmak için kullanılır.
- Döndürülen liste, find komutunda kullanılan koşulları karşılayacaktır.
- Sözdizimi bu şekildedir. ``` find [starting point] [expression] ```
- ```-exec [command]``` , ```find``` tarafından bulunan dosyalarda komut çalıştırmak için kulanılabilir.

## 10.1. Örnekler
- Belirli bir isime sahip dosyaları bulmak için:<br> ```find . -name demo.txt```
- Belirli bir kalıba sahip dosyaları bulmak için:<br> ``` find ./Codes -name *.cpp```
- Belirli ada sahip dizinleri bulmak için:<br> ```find . -name Codes -type d```
- İzini 777 olrak ayarlanmış dosyaları bul ve onların izinlerini 644 olarak değiştir:<br> ```find . -type f -perm 0777 -print -exec chmod 644 {} \;```
- Bul ve dosyaları sil:<br>```find . -type f -name "*.bkp" -exec rm -f {};```

# 11. ```sed``` Metni filtrele ve dönüştür(çevir)
## 11.1. Genel Bakış
- Kalıp arar ve kalıbı düzenler
- Hem dosyalarda hem de stdin'de çalışır
- Orijinal dosyalar güncellenmez
- Sonuçlar standart çıktıya atanır.
- Sözdizimi bu şekildedir: ``` sed 'instructions' file```
- Komutun biçimi şu şekildedir. ``` '[adres]komut/düzenli_ifade/değiştir/değiştirici' ``` 
  - Örneğin: '5,15s/abc/ABC/g' -> 5 ila 15 satırlarında abc'yi ABC ile değiştirecektir.
    - Buradaki g değiştiricisi, satırdaki tüm abc oluşumlarının ABC ile değiştirileceğini belirtir.
- Adres kullanıldığında adrese ait satırlar incelenir/değiştirilir. -> ```sed '1,100 s/A/a/' file.txt```. Örneğin bu komut, değiştirmeyi ilk 100 satırla sınırlar.
- Varsayılan olarak tüm satırlar yazdırılır. '-n' bayrağı kullanıldığında bu davranış bastırılır. Açık bir yazdırma isteği bulunmadıkça hiçbir şey yazdırılmayacaktır.
- Adres olarak bir kalıp kullanılabilir-> ```sed -n '/start/,/stop/ p' file.txt```
- '!' kullanıldığı zaman, komut adresin dışında çalıştırılır. -> ```sed -n '/match/ !p' file.txt```

Komut | Açıklama
---     | ---
d       | Siler.
p       | Çıktı verir (yazdırır).
s       | Yerine geçirir.
q       | Çık.
a       | Satırdan sonra bir kalıp ekle.
i       | Satırdan önce bir kalıp ekle.
c       | Satırı değiştirir.
y       | Değiştirir.

## 11.2. Örnekler
- Boş satırları kaldırır: <br>``` sed '/^$/d' file.txt```
- Arama dizesini içeren bütün satırları kaldırır:<br>```sed '/Search/d' file.txt```
- Arama dizesinin tüm kopyalarını kaldırır: <br>```sed 's/Search//g' file.txt```
- Arama dizesi içeren satırları çıktı verir:<br>```sed '/Search/ p' file.txt```
- Bir dizeyi başka bir dizeyle değiştirir: <br>```sed 's/oldString/newString/g' file.txt```
- Sondaki boşlukları kaldırır:<br>```sed 's/ *$//' file.txt```
- Baştaki boşlukları kaldırır: <br>```sed `s/^ *//' file.txt```
- Her satırın başına boşluk ekler: <br>```sed 's/^/    /' file.txt```
- İlk 10 satırı yazdırır<br>```sed '10 q' file.txt```<br>```sed -n '1,10 p' file.txt```
- Bir kalıptan sonra satır ekler<br>```sed '/pattern/ a add line here' file.txt```
- Bir kalıptan önce satır ekler<br>```sed '/pattern/ i add line here' file.txt```
- Bir kalıpla bir satırı değiştirir:<br>```sed '/pattern/ c line changed here' file.txt```
- Değiştir a->p, b->q, c->r<br>```sed 'y/abc/pqr/' file.txt```
  
## 11.3. Gruplama
- Sed metnin belirli bölümlerini gruplara ayırmaya izin verir.
- Bu gruplar manipüle edilebilir.
- Grup, arama dizesinde parantez içindeki ("\" ve "\)" ifadesinin içine alınır.
- Her gruba bir numara atanır. İlk gruba \1 atanır vb.
- \1 hem kalıp dizesinde hem de değiştirme dizesinde olabilir.

### 11.3.1. Gruplama Örnekleri:
- Birinci ve ikinci sütunları değiştir<br>```sed 's/\([a-z]*\) \([a-z]*\)/\2 \1/' file.txt```
- print lines which have consecutive duplicate words<br>```sed -n '/\([a-z][a-z]*\) \1/p' file.txt```
- remove consecutive duplicate words in a line<br>```sed 's/\([a-z][a-z]*\) \1/\1/' file.txt```



## 11.4. Tampon tutun
- sed metni okuduğunda, her satır geçici bir alana yerleştirilir.
- Yeni bir satır okunduğunda, geçici boşlukta eski metin yeni satırla değiştirilir.
- Bu geçici alana kalıp alanı denir.
- Tutma arabelleği uzun süreli bir depolama gibidir. metin, desen alanına ve desen alanından kopyalanabilir.

komut | tanım
--- | ---
x | değişim tutma alanı ve desen alanı
h | desen arabelleğini bekleme alanına kopyala
H | tutma alanına desen arabelleği ekle
g | tutma alanını desen alanına kopyala
G | bekletme arabelleğini desen arabelleğine ekle

### 11.4.1. Örnek
- kalıp eşleşmesinden önce ve sonra bir satır yazdır<br>```sed -n '/999/ !{x;d};/999/ {x;p;x;p;n;p}' file.txt ```
- her satırdan sonra boşluk ekleyin<br>```sed 'G' file.txt```
- <br>```sed '/start/ {x;p;x}' file.txt``` kalıbıyla eşleşen her satırın üstüne boş satır ekleyin
- Kalıpla eşleşen her satırdan sonra boş satır ekleyin<br>```sed '/start/ {G}' file.txt```
- <br>```sed '/start/ {x;p;x;G}' file.txt``` kalıbıyla eşleşen her satırın önüne ve arkasına boş satır ekleyin

# 12. ```awk```
- metin dosyalarını bulmak, işlemek ve dönüştürmek için komut satırı yardımcı programı
- temel sözdizimi ```pattern { action }```
  - desen her giriş satırıyla karşılaştırılır. desen herhangi bir normal ifade olabilir
  - desen eşleştiğinde eylem gerçekleştirilir
  - desen sağlanmadığında, eylem her satıra uygulanır
  - örnek -> ```/^HTTP/ {print}```
    - HTTP ile başlayan her satır yazdırılır
  - 2 önemli model daha var
    - BAŞLA - herhangi bir satır okunmadan önce gerçekleştirilecek eylemleri belirtir
    - END - tüm satırlar okunduktan sonra gerçekleştirilecek eylemleri belirtir
    - Örnek -> ```awk 'BEGIN{print "start"} {print} END{print "end"}' file.txt```
      - önce *start* yazdırılır, ardından file.txt'nin tüm satırları yazdırılır ve ardından *end* yazdırılır
- awk, her satırı alanların kaydı olarak yorumlar
- bir veya daha fazla ardışık boşluk veya sekme, alanlar arasında tek bir sınırlayıcı olarak kabul edilir
- $1, $2, vb. birinci alanı, ikinci alanı vb. temsil eder.
- $0 tüm giriş satırını temsil eder
- awk'nin 2 veri türü vardır - dizeler ve tamsayılar
- awk, değişkeni bağlama göre dahili olarak dönüştürür
- awk ilişkisel dizileri destekler. örnek ```var[anahtar] = değer```
- tamsayılarda temel aritmatik işlemler (+-*/%) desteklenir. otomatik artırma(++) ve azaltma(--) da desteklenir.

## 12.1. Hareketler
- aşağıdakiler gerçekleştirilebilecek birkaç eylemdir

eylem | tanım
--- | ---
{ $0 yazdır; } | kayıtları yazdır
{ çıkış; } | programı sonlandırır
{ sonraki; } | geçerli satırı atlar
{a=$1; b="X"} | değişken atama
{ c[$1] = $2 } | dizi değişken ataması
{if (koşul) { eylem } else if (koşul) { eylem } başka { eylem }} | aksi takdirde koşullar
{ for (i=1; i < x; i++) { eylem } } | döngü için
{ for (c'deki öğe) { action } } | bir liste üzerinde yinelenen döngü için

## 12.2. Özel değişkenler

değişken | azalan
--- | ---
FS | Giriş alanı ayırıcı. değiştirilebilir
RS | Giriş kayıt ayırıcı. varsayılan değer yeni satırdır. kullanıcı tarafından değiştirilebilir
OFS | Çıkış alanı ayırıcı. değiştirilebilir
ORS | Çıkış kayıt ayırıcı. varsayılan değer yeni satırdır. kullanıcı tarafından değiştirilebilir
NF | Geçerli satırdaki (kayıttaki) alan sayısı. kullanıcı tarafından güncellenemez
NR | Şu ana kadar işlenen satır sayısı. kullanıcı tarafından güncellenemez

*Not: -F seçeneği, giriş alanı ayırıcısını güncellemek için kullanılabilir -> ```awk -F":"'{ print $1 }' file.txt```*

## 12.3. Örnekler
- “,” (virgülle) ayrılmış alanları bölün ve üçüncü alanı (3 $) yazdırın<br>```awk -F"," '{print $2}' file.txt```
- ikinci alan ($2) varsa ve boş değilse, csv'nin 3. alanını yazdırın<br>```awk -F"," '{if ($2)yazdır $3}' file.txt```
- her satırdaki son alanı yazdır<br>```awk -F"," '{ print $NF }' file.txt```
- arama modeliyle eşleşen satırdan sonraki satırı yazdır<br>```awk '/pattern/ { i=1; sonraki; } {if(i) {i--; print;}}' file.txt```
- arama modeliyle eşleşen satırdan sonraki satırı ve 2 satırı yazdır<br>```awk '/regexp/ {i=3;} { if(i) {i--; print;}}' file.txt```
- *start* ile eşleşen satırdan başlayarak *stop*<br>```awk '/start/,/stop/' file.txt``` ile eşleşen satıra kadar bir dosyadan satırları yazdırın
- satırları say (wc -l)<br>```awk 'END{print NR}' file.txt```
- eşleşen satırları yazdır (grep)<br>```awk '/pattern/'```
- eşleşmeyen satırları yazdır (grep -v)<br>```awk '!/pattern/'```
- yinelenen ardışık satırları kaldırın (uniq)<br>```awk 'a !~ $0 {print}; {a=$0}' dosya.txt```
- - dosyanın ilk 10 satırını yazdır (head)<br>```awk 'NR < 11' file.txt```
- dosyanın son 10 satırını yazdır (kuyruk)<br>```awk '{vect[NR]=$0;} END{for(i=NR-9;i<=NR;i++) {vect[i] yazdır ;}}' dosya.txt```
- dosyalar tarafından kullanılan toplam bayt sayısını yazdır<br>```ls -l | awk '{ x += $5 } END { print "Toplam bayt: " x }'```

# 13. Komut ikamesi
- Komut ikamesinde, komutun çıktısı komutun yerini alır
- bir komutun çıktısı başka bir komutun argümanı olarak kullanılabilir
- sözdizimi ``` `komut` ```

## 13.1. Örnekler
- bir komutun çıktısını bir değişkene atayın<br> ``` DATE=`date` ```
- komutun çıktısını başka bir komutun parametresi olarak kullan<br> ``` vi `grep -l 123 *` ```

# 14. Süreç ikamesi
- bir komutun girdisi veya çıktısı bir dosya olarak görünebilir. Bu süreç ikamesi olarak bilinir
- bu teknik, bir komutun girdisi olarak birden çok komutun çıktısını kullanmak istediğimizde kullanışlıdır.
- süreç ikamesi, çıktıyı yakalamak ve onu bir sürecin girdisine yönlendirmek için de kullanılabilir.
- şablon - ```<(komut)``` ve ```>(komut)```

## 14.1. Örnekler:
- iki dosyayı sıralayın ve karşılaştırın<br>
  ```fark <(dosya1 sırala <(dosya2 sırala)```

- 2 klasörü karşılaştırın<br>
  ```fark <(ls $ilk_dizin) <(ls $ikinci_dizin)```

# 15. Alt Kabuk
- bir alt kabuk, bir kabuk tarafından başlatılan bir alt işlemdir
- bir kabuk komut dosyası çalıştırıldığında, bir alt kabuk oluşturulur ve komut dosyası alt kabukta çalıştırılır
- ana kabukta tanımlanan değişkenlere, değişken tanımlanırken ```export``` kullanılırsa erişilebilir
- parantezler kullanılarak alt kabuklar da oluşturulabilir<br>
  ```(komut1; komut2; komut3)```
- alt kabuklar, komutları gruplandırmanın uygun bir yoludur.
- geçici olarak farklı bir dizine geçmek için kullanılabilir
```bash
#geçerli dizinde bir şeyler yap
(cd bazı/diğer/dizin; diğer komut)
#orijinal dizine geri dön
```
- geçerli kabukta bir alt kabuk oluşturmadan bir komut veya komut dosyası çalıştırmak için '.' kullanın. ``` da olduğu gibi. script.sh```


# 16. ssh
- ssh (SSH istemcisi), uzak bir makinede oturum açmak ve uzak bir makinede komutları yürütmek için bir programdır.
- sözdizimi ```ssh user@host```
- uzak sunucuda tek bir komut çalıştırma<br>```ssh user@host command_to_run```
- sunucuya farklı bağlantı noktasıyla oturum açma<br>```ssh -p portnum user@host```
- ortadaki ana bilgisayar kullanılarak ssh bağlantısı ''ssh -t ulaşılabilir_konakçı ssh erişilemez_konakçı'''


# 17. "Kes", "Yapıştır" ve "Birleştir" ile metin düzenleme

## 17.1. '''kes'''
- ```cut``` komutu her satırdan bölümleri keser ve sonucu standart çıktıya yazar
- sözdizimi ```cut OPTION [DOSYA]```

seçenek | tanım
--- | ---
-c | seçilecek karakter aralığı
-d | dosyadaki satırdaki her alanı ayıracak sınırlayıcı
-f | yazdırılacak alanlar

-c seçeneği kullanıldığında aralıklar belirtilebilir. Her aralık şunlardan biri olabilir:
aralık tipi | tanım
--- | ---
N | N. karakter
N- | Nth karakterinden satırın sonuna kadar
N-M | N. karakterden M. karaktere
-M | ilk karakterden Mth karakterine

### 17.1.1. Örnekler
- bir csv dosyasının birinci ve üçüncü sütunlarını yazdırın<br>```cut -f1,3 -d"," file.txt```
- her satırın ilk 3 karakterini yazdır<br>```cut -c -3 file.txt```

## 17.2. '''yapıştır'''
- dosya satırlarını birleştirir
- varsayılan olarak, her dosyadan gelen satırlar sekme ile sınırlandırılır
- dosya adı yerine '-' kullanıldığında, komut standart girdiden okunur
- sözdizimi ```yapıştır [SEÇENEK] [DOSYA] [DOSYA]```
  
seçenek | tanım
--- | ---
-d | sınırlayıcıyı belirtmek için kullanılır
-s | bir seferde bir dosya yapıştırın

### 17.2.1. Örnekler
2 dosya alalım - number.txt ve name.txt
> kedi numarası.txt
> 1<br>
> 2<br>
> 3<br>
> 4<br>

> kedi adı.txt
> Alice<br>
> Bob<br>
> Charlie<br>
> Davut<br>

- 2 dosyayı birleştir, ilk dosya ilk sütunu verecek ve ikinci dosya ikinci sütunu verecek<br>```numarayı.txt adını yapıştırın.txt```
- ','<br>```paste -d"," number.txt name.txt``` ile sınırlandırılmış 2 dosyayı birleştir
- 2 dosyayı sırayla birleştirin, yani ilk önce yalnızca ilk dosya yazdırılır ve ardından yalnızca ikinci dosya<br>```paste -s number.txt name.txt```

## 17.3. '' katıl '''
- ortak bir alanda iki dosyanın satırlarını birleştirin
- sözdizimi ```katıl [SEÇENEKLER] DOSYA1 DOSYA2```

### 17.3.1. Örnekler
2 dosya alalım - number.txt ve name.txt
> kedi numarası.txt
> 1 100<br>
> 2 101<br>
> 3 102<br>
> 4 103<br>
> 5 104<br>

> kedi adı.txt
> 1 Alice<br>
> 2 Bob<br>
> 3 Charlie<br>
> 4 Davut<br>

- ilk sütuna göre 2 dosyayı birleştirin<br>```numara.txt adını birleştirin.txt```

# 18. Takma Adlar
- takma adlar, uzun komutlar için kısa adlardır
- uzun komutları birden çok kez çalıştırmamız gerektiğinde, takma adlar oluşturmanız önerilir
- sözdizimi - ```takma ad [-p] [ad[=değer]]```
- bunları yapılandırma dosyalarında saklayarak kalıcı takma ad oluşturabiliriz
- bir takma adı geçici olarak atlamak için \ -> ```\ll``` kullanın

- takma ad oluşturma<br>```takma ad='değerler'```
- takma adı <br>```unalias name``` kaldırılıyor
- tanımlanmış tüm takma adları yazdır<br>```takma ad -p```

## 18.1. faydalı takma adlar
```bash
takma ad gh='geçmiş|grep'
takma ad cx='chmod +x'
takma ad ..='cd ..'
takma ad sl=ls
takma ad sol='ls -t -1'
takma ad sayısı='bul . -tip f | wc -l'
takma ad f='bul . |grep'
```

# 19. Fonksiyonlar
- belirli bir görevi yerine getiren komutlar seti
- defalarca kullanılabilir
- aynı kodu tekrar tekrar yazmaktan kaçınmaya yardımcı olur
- döngüleri ve içlerindeki koşulları kullanabilir
- işlevlere argümanlar iletilebilir
- ``export -f functionname``` kullanarak, fonksiyonları kabuk betiklerinde kullanılabilir hale getirebiliriz.
  - *.bashrc* gibi yapılandırma dosyalarına dışa aktarma eklenebilir
  - İşleri modüler tutmak için ~/.bash_functions adında yeni bir dosya oluşturun ve ardından .bashrc'nizin onu yüklemesini sağlayın
- sözdizimi<br>
```bash
fonksiyon adı () {
  komutlar
}
```

```bash
işlev_adı () { komutlar; }
```

## 19.1. faydalı fonksiyonlar
```bash
mcd() { mkdir -p "$1"; cd "$1";}
cdl() { cd "$1"; ls;}
```

# 20. sıralama
- satır metin dosyalarını sırala

seçenek | tanım
--- | ---
-r | ters sırada sıralama
-n | numara sırasına göre sırala
-k <n> | n. sütuna göre sırala
-u | kopyaları sırala ve kaldır

# 21. benzersiz
- tekrarlanan satırları rapor edin veya atlayın
- giriş dosyası sıralanmalıdır

seçenek | tanım
--- | ---
-c | bir satırın kaç kez tekrarlandığını göster
-d | yalnızca tekrarlanan satırları yalnızca bir kez yazdırır
-u | yalnızca benzersiz satırları yazdırır
-i | büyük/küçük harfe duyarsız karşılaştırma


# 22. Koşullar
## 22.1. eğer başka
- if-then-else komut satırında desteklenir
- Sözdizimi
```bash
eğer [ koşul1 ]; sonra komut1;
elif [ koşul2 ]; sonra komut2;
başka komut3; fi
```

```bash
eğer [ koşul1 ]; sonra komut1; elif [ koşul2 ]; sonra komut2; başka komut3; fi
```
- farklı koşullar var
  1. dosya tabanlı koşullar

koşullar | tanım
--- | ---
-a | dosyanın var olup olmadığını kontrol edin
-r | dosyanın var olup olmadığını ve okunabilir olup olmadığını kontrol edin
-w | dosyanın var olup olmadığını ve yazılabilir olup olmadığını kontrol edin
-d | dosyanın var olup olmadığını ve bir dizin olup olmadığını kontrol edin

  2. dize tabanlı koşullar

koşullar | tanım
--- | ---
== | her iki dizenin de eşit olup olmadığını kontrol edin
!= | her iki dizenin de eşit olup olmadığını kontrol edin
\> | ilk dizenin sözlükbilimsel olarak ikinciden daha büyük olup olmadığını kontrol edin
< | ilk dizenin sözlükbilimsel olarak ikinciden daha küçük olup olmadığını kontrol edin
-n | dizenin 0'dan fazla olup olmadığını kontrol edin
-z | dizenin boş bir dize olup olmadığını kontrol edin

  3. sayıya dayalı koşullar

koşullar | açıklama
--- | ---
-eq | sayıların eşit olup olmadığını kontrol edin
-ne | sayıların eşit olup olmadığını kontrol edin
-gt | ilk sayının ikinciden büyük olup olmadığını kontrol edin
-ge | ilk sayının ikinciden büyük veya ona eşit olup olmadığını kontrol edin
-lt | ilk sayının ikinciden küçük olup olmadığını kontrol edin
-le | ilk sayının ikinciden küçük veya ona eşit olup olmadığını kontrol edin


- 0 doğru olarak kabul edilir ve 0'dan büyük sayılar yanlış olarak kabul edilir.
  - bunun nedeni Unix/Linix'te bir işlem başarıyla sona erdiğinde 0 döndürmesidir.

## 22.2. kısa devre
- koşulları kullanmanın alternatif bir yolu, mantıksal VE (&&) ve mantıksal VEYA(||) kullanmaktır.
- sonuç belirlenir belirlenmez mantıksal bir ifadenin değerlendirilmesi durdurulur. Bu kısa devre olarak bilinir.
- Mantıksal VE durumunda, alt ifade yanlış olur olmaz, ifadenin tamamı yanlış olarak değerlendirilir
  - *ifade1 && ifade2* durumunda, ifade1 yanlış olarak değerlendirilirse, tüm ifade false olarak değerlendirilir. Yani, ifade2 hiç değerlendirilmez.
  - &&, komut2'nin yalnızca komut1 başarıyla sona ererse çalıştırılmasını sağlamak için kullanılabilir. örnek ->```komut1 && komut2```
- Mantıksal VEYA durumunda, alt ifade doğru olur olmaz tüm ifade doğru olarak değerlendirilir
  - *ifade1 durumunda || ifade2*, ifade1 doğru olarak değerlendirilirse, tüm ifade doğru olarak değerlendirilir. Yani, ifade2 hiç değerlendirilmez.
  - || komut2'nin yalnızca komut1 başarısız olursa çalıştırılmasını sağlamak için kullanılabilir. örnek -> ```komut1 || komut2```

### 22.2.1. örnek
- yoksa klasör oluştur
```bash
  [ -d ./some/path/folder ] || mkdir /bazı/yol/klasör
```

- yalnızca klasör varsa dosya oluştur
```bash
  cd /some/path/klasör && file.txt'e dokunun
```

# 23. Döngüler
## 23.1. döngüler sırasında
- döngü verilen koşul doğru olduğu sürece çalışır
- sözdizimi
  ```bash
  while [ koşul ]; komutları yapmak; tamamlamak
  ```
### 23.1.1. örnek
- tüm klasörleri .c dosyalarıyla yazdırın<br>
```bash
bulmak . -isim *.c | {dosya adını okurken; dirname $dosyaadı yapın; bitti;} | sıralama | uniq # dirname dizin adını döndürür
```


## 23.2. döngüler için
- döngü, bir değerler listesi veya önceden ayarlanmış sayıda yinelenir
- sözdizimi
  ```bash
  <bir öğe listesi> içindeki <değişken adı> için;do <bir komut> $<değişken adı>;done;
  ```
### 23.2.1. örnek
- dosyaları bir klasörden diğerine kopyalayın
```bash
./code/*.txt içindeki i için; cp $i /home/code/yedekleme yapın; tamamlamak
```
# 24. Bir gömlek

- ağaç yapısındaki dosyaları ve dizinleri yazdırın<br>```find . | sed -e "s/[^-][^\/]*\// |/g" -e "s/|\([^ ]\)/|-\1/"```
- dizinleri ağaç yapısında yazdırın<br>```find . -tip d | sed -e "s/[^-][^\/]*\// |/g" -e "s/|\([^ ]\)/| - \1/"```
- ascii tablosuna hızlı erişim<br>```man ascii```
- 2 dosyada ortak satırları bulun<br>```cat dosya1 dosya2 | uniq -d```
- dosya1'de dosya2'de bulunmayan satırları bulun<br>```cat dosya1 dosya2 dosya2 | benzersiz -u```
- en sık kullanılan komutları bulun<br>```geçmiş | kesme -c8- | sıralama | tek -c | sırala -rn | kafa```
- yalnızca dosya içermeyen dizinleri tekrar tekrar kaldırın<br>```find . -derinlik -type d -exec rmdir {} \;```
# 25. Daha fazla okuma
-

# 26. Değişen Tarihi
- Ters kronolojik yolda, yani en son yardım en üsttedir.

İsim | Tarih | Açıklamayı Değiştir
---- | ---- | ---
Utsav Barmen | 25 Ocak 2022 | Bekleme, globbing, grep -o eklendi; sabit yazım hataları
