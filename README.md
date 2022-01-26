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
      - [3.2.2.1. Standart çıktıyı sout.txt'ye gönderir ve standart hatayı serr.txt'ye gönderir.](#3221-standart-çıktıyı-souttxtye-gönderir-ve-standart-hatayı serrtxtye-gönderir.)
      - [3.2.2.2. Send standard output and standard error streams to the same file sone.txt](#3222-send-standard-output-and-standard-error-streams-to-the-same-file-sonetxt)
      - [3.2.2.3. Hem standart girdiyi hem de çıktıyı görmezden gelir.](#3223-hem-standart-girdiyi-hem-de-çıktıyı-görmezden-gelir)
  - [3.3. Pipe](#33-pipe)
  - [3.4. xargs](#34-xargs)
  - [3.5. tee](#35-tee)
- [4. Dosya Adı Genişletme](#4-dosya-adı-genişletme)
- [5. İş Kontrolü](#5-job-control)
- [6. Süreç Yönetimi](#6-süreç-yönetimi)
  - [6.1. ```ps``` ve ```jobs``` Arasındaki Farklar](#61--ps-ve-jobs-arasındaki-farklar)
- [7. Alıntılar](#7-quoting)
- [8. Temel Dosya Yönetimi](#8-temel-dosya-yönetimi)
  - [8.1. Dizin Listeleme```ls```](#81-dizin-listeleme)
  - [8.2. Dosya İçeriğini Gösterme](#82-dosya-içeriğini-gösterme)
  - [8.3. Dosya Yönetimi(#83-dosya-yönetimi)
    - [8.3.1. Kopyalama](#831-kopyalama)
    - [8.3.2. Taşıma ve Yeniden Adlandırma](#832-taşıma-ve-yeniden-adlandırma)
    - [8.3.3. Silme](#833-silme)
    - [8.3.4. Dosya Bağantısı](#834-dosya-bağlantısı)
    - [8.3.5. Dizin Değiştir (CD)](#835-dizin-değiştir)
- [9. ```grep```](#9-grep)
  - [9.1. Kullanışlı ```grep``` seçenekleri](#91-kullanışlı-grep-seçenekleri)
    - [9.1.1. Örnekler](#911-örnekler)
  - [9.2. Grep'te Düzenli İfadeler (Regex)](#92-grepte-düzenli-ifadeler-regex)
  - [9.3. Örnekler](#93-örnekler)
- [10. ```find```](#10-find)
  - [10.1. Örnekler](#101-örnekler)
- [11. ```sed``` Metni filtrele ve dönüştür(çevir)](#11-metni-filtrele-ve-dönüştür)
  - [11.1. Genel Bakış](#111-genel-bakış)
  - [11.2. Örnekler](#112-örnekler)
  - [11.3. Gruplama](#113-gruplama)
    - [11.3.1. Gruplama Örnekleri:](#1131-gruplama-örnekleri)
  - [11.4. Hold Buffer](#114-hold-buffer)
    - [11.4.1. Örnekler](#1141-örnekler)
- [12. Değişme Tarihi](#24-değişme-tarihi)


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



## 11.4. Hold Buffer
- sed metni okuduğunda, her satır geçici bir alana yerleştirilir.
- Yeni bir satır okunduğunda, geçici boşlukta eski metin yeni satırla değiştirilir.
- Bu geçici alana kalıp alanı denir.
- Hold Buffer uzun süreli bir depolama gibidir. metin, desen alanına ve desen alanından kopyalanabilir.

Komut | Tanım
--- | ---
x | Değişim tutma alanı ve desen alanı.
h | Desen arabelleğini bekleme alanına kopyalar.
H | Tutma alanına desen arabelleği ekler.
g | Tutma alanını desen alanına kopyalar.
G | Bekletme arabelleğini desen arabelleğine ekler.

### 11.4.1. Örnek
- kalıp eşleşmesinden önce ve sonra bir satır yazdırır:<br>```sed -n '/999/ !{x;d};/999/ {x;p;x;p;n;p}' file.txt ```
- her satırdan sonra boşluk ekler:<br>```sed 'G' file.txt```
- <br>```sed '/start/ {x;p;x}' file.txt``` kalıbıyla eşleşen her satırın üstüne boş satır ekler.
- Kalıpla eşleşen her satırdan sonra boş satır ekleyin<br>```sed '/start/ {G}' file.txt```
- <br>```sed '/start/ {x;p;x;G}' file.txt``` kalıbıyla eşleşen her satırın önüne ve arkasına boş satır ekleyin.
-

# 12. Değişme Tarihi
- Ters kronolojik yolda, yani en son yardım en üsttedir.

İsim | Tarih | Açıklamayı Değiştir
---- | ---- | ---
Utsav Barmen | 25 Ocak 2022 | Bekleme, globbing, grep -o eklendi; sabit yazım hataları
