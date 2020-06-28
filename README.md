  
 # Asenkron Programlama
 
 Asenkron çalışma prensibi, yürütülen süreçlerin uzun sürmesinden dolayı, yürütülmesi gereken diğer süreçlerin beklemeden çalışmasına devam edebilmesi için geliştirilmiştir. Bazen wab ortamındaki bir kaynağa erişip istekte bulunmak ve cevap almak uzun sürebilmektedir. Senkron çalışma prensibinde örneğin bir web kaynağından cevap gelene kadar sıradaki işlem yürütülmez.  Ancak asenkron süreçlerde uzun sürebilecek işlemler farklı bir görev olarak tanımlanarak çalıştırılır ve sıradaki işleme geçilir. Böylece uzun süren işlemler arka planda farklı görevler olarak çalışmaya devam eder.
 
 ### Async/Await anahtar kelimelerinin kullanımı
 
 “async” anahtar kelimesi, kullanıldığı metod içerisinde “await” anahtar kelimesinin etkinleştirilmesi  için kullanılır. “async” anahtar kelimesinin kullnaılmadığı metodlarda “await” anahtar kelimesi çalışmaz. Yani “async” anahtar kelimesinin kullanıldığı metodu asenkron hale çeviren bir sihiri yoktur.

Async kullanılan metodlar tıpkı diğer metodlar gibi çalıştırılır. Her hangi bir farkı yoktur. Ta ki derleyici “await” ile karşılaşana kadar işlemler senkron olarak işletilir. İşlemler Thread pool içerisinde bir thread ile yürütülür. “async” ve “await” kelimelerinin kullanımı aşağıdaki gibidir.


```
private async void download(string url)
{
    var down = await Downloader.DownloadString(url);
}
```

 

 ## Task Nedir?
 
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

## Thread Nedir?

Threadler iş parçacıkları olup, çoklu tasklerde senkranizasyon sağlamak için kullanılır. 
Threadler sayesinde ayrı metodları aynı anda çalıştırabiliriz. İşletim sistemi her thread'e çalışması için belli bir **zaman aralığı** verir. Bu zaman aralığı dolduğunda çalışan Thread'den çıkılıp, program içerisindeki diğer bir metoda veya başka bir thread'e girilir. Bir metod içerisinde yapılan iş ne kadar uzun sürüyorsa o metodun bağlı olduğu thread'de o kadar fazla zaman harcanır. Bazen bu süre o kadar fazla olurki, process içerisindeki başka bir thread'e çalışması için çok az zaman kalır. Başlatılan threadlerin aynı anda senkron bir şekilde çalışabilmesi için .NET te senkronizasyon teknikleri kullanılır.

```
	static void Main(string[] args) {  
	    Thread thread = new Thread(new ThreadStart(getMyName));  
	    thread.Start();  
	}  
	public void getMyName() {}
```

## Process Nedir?

Process, kendisine ait kaynakları olan işlem birimidir. Her process kendisine ait hafıza alanına sahiptir. Process bir işletim sistemi üzerinde herhangi bir dil ile kodlanmış ve bir derleyici ile derlenmiş ve daha sonra hafızaya yüklerek işlemcide çalıştırılan programlara verilen isimdir.

![blog4](https://user-images.githubusercontent.com/58445606/85931302-0bdb9300-b8cc-11ea-83f6-8b07e64bbf28.png)

## Thread ve Process ortak özellikleri

* Paralel çalışabilirler, etkileşebilirler ve haberleşebilirler.
* Dış dünya ile haberleşebilirler.
* Ardışık işlemler yapılabilir.
* Threadlerde processler gibi durum değiştiribilirler. Hazır, askıda, çalışıyor durumlarda olabilir.

## Thread ve Process farkları

Threadler process içinde bulunurlar ve aynı adres uzayını paylaşırlar. Bir process içerisinde birden fazla iş yürütülebilir.
Threadler processler gibi birbirinden bağımsız değildir. Kendi aralarında kaynakları ve bazı verileri birbirleriyle paylaşırlar. 

Tek bir process bile birden fazla işlem yapılabilir. Böylece işlemcide daha az context değiştirme olayı gerçekleşir. Her işlemde proses kontrol bloğu yeniden güncellenmez. İşletim sistemi işlemleri gerçekleştirirken zaman kaybı yaşamaz.

Çok işlemcili sistemlerde faydalıdır. Threadlerin bazıları işlemciye yönelik işlemler yaparken bazıları giriş -çıkış işlemleri yapıyorsa yapılan iş için daha iyi performans elde edilir.
Proseslerin kaynakları vardır. İşletim sisteminde yer işgal ederler. Ne kadar çok proses olursa RAM'de o kadar çok yer işgal edilir. İpliklerin ise kaynakları yoktur. Mevcut prosesin sahip olduğu kaynağı kullanırlar. Fazladan yer işgal etmezler. Yaratılmaları ve yok edilmeleri proseslere göre daha kolaydır.

Kısacası;

İşler birbirinden tamamen bağımsız ise: PROCESS

İşler birbirine bağlı ve birlikte yürütülüyorsa: THREAD

# Extension Nedir?

Extension method, kelime anlamı ile genişletilebilir metod anlamına gelmektedir. Extension method bize .NET içerisinde bulunan sınıflara yeni metodlar eklememizi sağlamaktadır. Extension methodlar static class içerisinde static olarak tanımlanmaktadır. 

Kısacası özetlemek gerekirse bir tip üzerinde herhangi bir değişikliğe uğratmadan genişletilebilir olmasını sağlayabiliriz. 

Örnek vermek gerekirse decimal bir değişkenimiz bulunmakta ve bu değişkende de para birimi tutuluyor. Biz bu değişkenin değerini ekranda ya da herhangi bir yerde gösterirken formatlayarak göstermek istiyoruz. Bu gibi durumlarda bir extension method oluşturabilir ve istediğimiz format ile gösterimini sağlayabiliriz. Extension methodlar belirlenen tip için oluşturulabilir

Projenizde herhangi bir tip için sık kullanacağınız ve tüm proje boyunca her yerde o veri tipi üzerinden kolayca ulaşabileceğiniz yetenekler geliştirmek için Extension Method’lar kullanılabilir.

**Kural 1:** Oluşturulan sınıf ‘static’ olmalıdır. Static bir sınıf içine static metot olarak tanımlanmalıdır.

**Kural 2:** Bu sınıf içerisinde genişletilmiş method olarak planlanan tüm methodlar parametrelerini ‘this’ anahtar sözcüğüyle almalıdır. 

Extension metotta, genişletilecek sınıfın türü **this** anahtar sözcüğü ile parametre olarak alınmalıdır. Bu sınıf türü, **this** ile ele alınmazsa hiç bir zaman çağrılmayacaktır. Aynı zamanda bir metodu, kendi ismiyle genişletirseniz, yazılan extension metot yerine yine kendisi çağrılır.

**Extensions create**

Extension metodları kullacağınız kaynak koda, using anahtar kelimesini kullanarak eklediğinizde bu metodlarınızı kullanabilirsiniz. Extension metod eklemenin ilk adımı normal bir class ekler gibi projemize class ekliyoruz. Ben extension metodlarımı saklamak için kullanacağım classa dExtensions adını vereceğim.

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace FvrNews.Library.CustomModels.Extensions {
    public static class dExtensions {

        public static int ToInt32(this string s) {
            return Convert.ToInt32(s);
        }
    }
}
```
Yukarıdaki kodu inceleyecek olursak, bahsettiğim gibi dExtensions adında bir class oluşturdum. Dikkat ederseniz classım statik. Daha sonra bu metodun string tipindeki değerler üzerinde kullanılacağını belirttim, metoda verdiğim parametrenin önüne this anahtar kelimesini getirerek(this string s). Geri dönüş tipi olarak ta int olduğunu belirttim.
Bu metodu yazarak her defasında string bir değeri int değere çevirmek için kod yazmakla uğraşmayacağım. String nesne üzerinden ToInt32 metodunu kullanarak direkt geri dönen değeri alabileceğim. Aşağıda da metodun kullanım biçimini görebilirsiniz.
```
using System.Linq;
using System.Web.Mvc;
using FvrNews.Library.CustomModels.Extensions; //Extension metodumun bulunduğu namespace
using FvrNews.Library.Services;

namespace TheLira.Controllers {
    public class PageController : Controller {
        public ActionResult GetPage(string pageSefLink,string[] idArray) {

            //String nesne üzerinden çağırdığım ToInt32 metodu
            int firstId = idArray.First().ToInt32();
            
            return View(new PageService().GetPageByID(firstId));
        }
    }
}
```
