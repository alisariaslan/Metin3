İşte tüm stratejileri, teknik detayları ve modern mimariyi kapsayan, profesyonelce hazırlanmış güncel **README.md** içeriği. Bunu kopyalayıp direkt projenin ana dizinine yapıştırabilirsin.

---

# 🎮 Metin2 Oyun Projesi – Unity ile Modernleştirilmiş Hal

Bu proje, klasik Metin2 oyununun **Unity 6** altyapısı üzerinde geliştirilmiş, modern yazılım mimarileriyle desteklenen versiyonudur. Proje sadece bir görsel yenileme değil; veritabanı tutarlılığı, ölçeklenebilir backend ve modern ağ protokollerini içeren tam kapsamlı bir MMORPG altyapısıdır.

---

## 🏗️ Veri Yönetimi ve Backend Stratejisi

Oyunun ekonomisini korumak ve performansı maksimize etmek için **Hybrid (Hibrit) Veri Tabanı** mimarisi benimsenmiştir.

| Veri Tipi | Teknoloji | Amaç ve Avantaj |
| --- | --- | --- |
| **Oyuncu Hesapları & Itemler** | **PostgreSQL** | ACID uyumluluğu ile %100 veri tutarlılığı. Item kopyalama (dupe) riskini engeller. |
| **Ekonomi & Ticaret Logları** | **PostgreSQL** | İlişkisel veri yapısı ile güvenli ticaret ve detaylı raporlama. |
| **Anlık Konum & Session** | **Redis** | Milisaniyelik hız, düşük gecikme. Sunucu RAM yükünü optimize eder. |
| **Büyük Log Verileri** | **ClickHouse** | Milyonlarca satırlık oyun içi aksiyonu analiz etmek için yüksek sıkıştırmalı depolama. |
| **Karakter Sıralaması** | **Redis (Cache)** | DB'yi yormadan anlık sıralama (Ranking) verisi sunar. |
| **Nesne Market (Shop)** | **Transactional DB** | Kritik ekonomi işlemleri için güvenli ve loglanabilir yapı. |
| **Mobile Companion** | **Flutter + API** | Oyuncuların dışarıdayken pazarlarını kontrol edebilmesi için API entegrasyonu. |

---

## 🛠️ Kullanılan Teknolojiler ve Sürümler

### 🎮 Oyun Motoru & Grafik

* **Unity:** `6.0.0.3.2f1`
* **Grafik Motoru:** **URP (Universal Render Pipeline)**
* *Neden?* Performans dostudur, Metin2'nin klasik atmosferini modern ışıklandırma ile birleştirir ve düşük donanımlarda bile akıcı çalışır.


* **Modelleme:** **Blender 3.6** & **Meshroom** (Photogrammetry ile gerçekçi nesne tarama).
* **Animasyonlar:** Mixamo üzerinden optimize edilmiş ve Unity Animator ile yapılandırılmış setler.

### 🌐 Ağ ve API Altyapısı (Networking)

* **Ağ Sistemi:** **Mirror** (High-level networking API).
* **Ağ Transport:** **Telepathy Transport**
* *Özellikler:* TCP tabanlı, stabil ve güvenli mesaj iletimi sağlar.


* **Web API:** **ASP.NET Core (C#)**
* Oyun sunucusu, Web sitesi ve Mobil uygulama arasındaki merkezi köprüdür.



### 🧠 Kod Çalıştırma ve Dağıtım

* **Geliştirme (Mono):** Hızlı build ve kolay hata ayıklama (Debugging) için tercih edilir.
* **Dağıtım (IL2CPP):** * Kodun makine diline çevrilmesiyle yüksek performans sağlar.
* Tersine mühendisliği zorlaştırarak hile (cheat) güvenliğini artırır.



---

## 🧱 Varlık (Asset) ve Modelleme Yol Haritası

Oyun varlıkları oluşturulurken modern bir "Asset Pipeline" izlenir:

1. **Tarama:** Meshroom kullanılarak gerçek dünyadaki nesnelerden fotoğraflar üzerinden 3D modeller üretilir.
2. **Düzenleme:** Ham modeller Blender'a aktarılır.
3. **Optimizasyon:** `Decimate Modifier` ile poligon sayısı düşürülür (Retopology), UV mapleri hazırlanır.
4. **Entegrasyon:** Hazırlanan `.fbx` dosyaları URP uyumlu shaderlar ile Unity içine dahil edilir.
5. **Hareket:** Mixamo üzerinde riglenen modeller, Unity'de `Mirror` üzerinden senkronize bir şekilde canlandırılır.

---

## 🛡️ Güvenlik ve Anti-Cheat Modeli

* **Server-Side Authority:** Tüm hareketler ve hasar hesaplamaları sunucu tarafında doğrulanır.
* **Rate Limiting:** Web API tarafında brute-force ve bot saldırılarına karşı istek sınırlaması uygulanır.
* **Anti-Cheat Dashboard:** Log analizi API uçları ile şüpheli oyuncu hareketleri anlık olarak yönetim paneline düşer.

---

## 📌 Geliştirici Notları

* Karakter animasyonları, Mixamo platformundan alınmış ve Unity üzerinde uyumlu şekilde düzenlenmiştir.
* Veritabanı işlemleri için asenkron (async/await) yapı kullanılarak sunucu kilitlenmeleri önlenmiştir.
* Web sitesi ve mobil uygulama, aynı merkezi **Web API** üzerinden PostgreSQL ve Redis verilerine erişir.

---

**Sence bu README'ye bir de "Gelecek Planları (Roadmap)" başlığı ekleyelim mi? (Örneğin: At binme sistemi, Lonca savaşları vb.)**
