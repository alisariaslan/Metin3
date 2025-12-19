# Metin3
Metin2 oyun projesinin Unity ile yazılıp modernleştirilmiş halidir. 

Unity 6.3 LTS,
URP,
Mirror (GitHub),
Telepathy Transport,
Mono (dev),
IL2CPP (release),

🎨 URP (Universal Render Pipeline)
Grafiğin nasıl çizileceğini belirler.
“Oyun ne kadar süslü, ne kadar hızlı çalışacak?”
Neden URP?
Hafif
Performanslı
Metin2 tarzı sade grafik için ideal
Düşük sistemlerde bile akar
Alternatifler:
Built-in ❌ (eski)
HDRP ❌ (aşırı ağır)
👉 URP = doğru seçim

🌐 Mirror (GitHub)
Oyunu online yapar.
“Oyuncular birbirini nasıl görecek, kim server’a bağlanacak?”
Mirror şunları sağlar:
Client ↔ Server iletişimi
Oyuncu spawn
Sync (pozisyon, animasyon vs.)
Dedicated server
Unity’nin kendi eski UNET sisteminin modern hâli gibi.

🔌 Telepathy Transport
Mirror’un internet üzerinden veri gönderen motoru.
“Mirror mesajları hangi yoldan yolluyor?”
TCP tabanlı
Stabil
Küçük MMO’lar için ideal
Alternatifler:
KCP (UDP) → hızlı ama karmaşık
WebSocket → tarayıcı için
👉 Telepathy = en sorunsuz başlangıç

🧠 Mono (dev)
C# kodlarının nasıl çalıştırılacağını belirler.
“Kodları çalıştıran motor”
Neden development’ta Mono?
Çok hızlı build alır
Hata ayıklama kolay
Online test yaparken ideal

🚀 IL2CPP (release)
Oyunu son kullanıcıya dağıtmak için kullanılır.
“Oyunu makine diline çevirir”
Avantajları:
Daha hızlı
Daha güvenli (hile zor)
Server + client için ideal
Dezavantajı:
Build süresi uzun

Unity İçin Pratik Modelleme Yol Haritası
Meshroom ile fotoğraflardan 3D modeli oluşturun.
Modeli Blender'a atıp poligon sayısını düşürün (Decimate modifier).
Temizlenmiş modeli Unity'ye .fbx olarak aktarın.
