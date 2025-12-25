🎮 Metin2 Oyun Projesi – Unity ile Modernleştirilmiş Hal
Bu proje, klasik Metin2 oyununun Unity altyapısı üzerinde geliştirilmiş modern versiyonudur. Oyun, hem grafiksel olarak hem de teknik olarak güncel bir yapıya sahiptir.

🛠️ Kullanılan Teknolojiler ve Sürümler
Unity: 6.0.0.3.2f1
Blender: 3.6
Visual Studio: 22
Animasyonlar: Mixamo’dan alınmıştır
🎨 Grafik Motoru: URP (Universal Render Pipeline)
URP, oyunun görsel rendering şeklini belirler.

“Oyun ne kadar süslü, ne kadar hızlı çalışacak?”

Neden URP?
Hafif ve performanslıdır
Metin2 tarzı sade grafikler için idealdir
Düşük sistemlerde bile sorunsuz çalışır
Alternatifler:
Built-in ❌ (eski ve yavaş)
HDRP ❌ (aşırı ağır, gereksiz)
👉 URP = doğru seçim

🌐 Ağ Sistemi: Mirror (GitHub)
Oyunun online hale gelmesini sağlar.

“Oyuncular birbirini nasıl görecek, kim server’a bağlanacak?”

Mirror ile sağlanan özellikler:
Client ↔ Server iletişimi
Oyuncu spawn işlemleri
Sync (pozisyon, animasyon vs.)
Dedicated server desteği
Mirror, Unity’in eski UNET sistemine benzer şekilde modernleştirilmiş bir yapıdır.

🔌 Ağ Transport: Telepathy Transport
Mirror’ın internet üzerinden veri göndermesini sağlayan motorudur.

“Mirror mesajları hangi yoldan yolluyor?”

Özellikler:
TCP tabanlı
Stabil ve güvenli
Küçük MMO’lar için ideal
Alternatifler:
KCP (UDP) → hızlı ama karmaşık
WebSocket → tarayıcı desteği için
👉 Telepathy = en sorunsuz başlangıç

🧠 Kod Çalıştırma Motoru: Mono (Development)
C# kodlarının nasıl çalıştırılacağını belirler.

“Kodları çalıştıran motor”

Neden Development ortamında Mono?
Hızlı build işlemleri
Hata ayıklama kolaylığı
Online testler için ideal
🚀 Dağıtım Motoru: IL2CPP (Release)
Oyunun son kullanıcıya dağıtıldığı aşamadır.

“Oyunu makine diline çevirir”

Avantajları:
Daha hızlı çalışır
Daha güvenli (hile zor)
Server + client için ideal
Dezavantajı:
Build süresi uzun
🧱 Unity İçin Pratik Modelleme Yol Haritası
Meshroom ile fotoğraflardan 3D model oluştur
Modeli Blender’a aktar
Poligon sayısını azalt (Decimate modifier)
Temizlenmiş modeli Unity’ye .fbx formatında aktar
Animasyonlar: Mixamo üzerinden alınan karakter animasyonları entegre edilir
📌 Notlar:
Karakter animasyonları, Mixamo platformundan alınmış ve Unity üzerinde uyumlu şekilde düzenlenmiştir.
Blender 3.6 kullanılarak model optimizasyonu yapılmıştır.
