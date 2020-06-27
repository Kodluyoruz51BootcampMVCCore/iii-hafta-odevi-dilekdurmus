  
 # Asenkron Programlama
 
 Asenkron çalışma prensibi, yürütülen süreçlerin uzun sürmesinden dolayı, yürütülmesi gereken diğer süreçlerin beklemeden çalışmasına devam edebilmesi için geliştirilmiştir. Bazen wab ortamındaki bir kaynağa erişip istekte bulunmak ve cevap almak uzun sürebilmektedir. Senkron çalışma prensibinde örneğin bir web kaynağından cevap gelene kadar sıradaki işlem yürütülmez.  Ancak asenkron süreçlerde uzun sürebilecek işlemler farklı bir görev olarak tanımlanarak çalıştırılır ve sıradaki işleme geçilir. Böylece uzun süren işlemler arka planda farklı görevler olarak çalışmaya devam eder.
 ## Async/Await anahtar kelimelerinin kullanımı
 
 “async” anahtar kelimesi, kullanıldığı metod içerisinde “await” anahtar kelimesinin etkinleştirilmesi  için kullanılır. “async” anahtar kelimesinin kullnaılmadığı metodlarda “await” anahtar kelimesi çalışmaz. Yani “async” anahtar kelimesinin kullanıldığı metodu asenkron hale çeviren bir sihiri yoktur.

Async kullanılan metodlar tıpkı diğer metodlar gibi çalıştırılır. Her hangi bir farkı yoktur. Ta ki derleyici “await” ile karşılaşana kadar işlemler senkron olarak işletilir. İşlemler Thread pool içerisinde bir thread ile yürütülür. “async” ve “await” kelimelerinin kullanımı aşağıdaki gibidir.


```
private async void download(string url)
{
    var down = await Downloader.DownloadString(url);
}
```

 

 # Task Nedir?
 
.Net frameworkde threading sağlar. Task sınıfı, bir değer döndürmeyen ve genllikle zaman uyumsuz olarak yürütülen tek bir işlemi temsil eder. Task, yapılması gereken bazı işleri temsil eden bir nesnedir.
.NET framework, task oluşturmamıza ve bunları asenkron olarak çalıştırmamıza olanak tanıyan **Threading.Task** sınıfını sağlar.

Task, işlemin tamamlanıp tamamlanmadığını ve işlemin bir sonuç döndürdüğünü söyleyebilir, task sonucu verir. 

Task Create
```
	static void Main(string[] args) {  
	    Task < string > hitask = Task.Run(() => (  
	        return“ Hello”));  
	    Console.WriteLine(hitask.result);  
	} 
```

![task](https://user-images.githubusercontent.com/58445606/85930585-5bb75b80-b8c6-11ea-9d99-71c56212dafa.png)

# Thread Nedir?

Threadler iş parçacıkları olup, çoklu tasklerde senkranizasyon sağlamak için kullanılır. 
Threadler sayesinde ayrı metodları aynı anda çalıştırabiliriz. İşletim sistemi her thread'e çalışması için belli bir **zaman aralığı** verir. Bu zaman aralığı dolduğunda çalışan Thread'den çıkılıp, program içerisindeki diğer bir metoda veya başka bir thread'e girilir. Bir metod içerisinde yapılan iş ne kadar uzun sürüyorsa o metodun bağlı olduğu thread'de o kadar fazla zaman harcanır. Bazen bu süre o kadar fazla olurki, process içerisindeki başka bir thread'e çalışması için çok az zaman kalır. Başlatılan threadlerin aynı anda senkron bir şekilde çalışabilmesi için .NET te senkronizasyon teknikleri kullanılır.

# Process Nedir?

Process, kendisine ait kaynakları olan işlem birimidir. Her process kendisine ait hafıza alanına sahiptir. Process bir işletim sistemi üzerinde herhangi bir dil ile kodlanmış ve bir derleyici ile derlenmiş ve daha sonra hafızaya yüklerek işlemcide çalıştırılan programlara verilen isimdir.



![blog4](https://user-images.githubusercontent.com/58445606/85931302-0bdb9300-b8cc-11ea-83f6-8b07e64bbf28.png)
