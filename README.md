
---

# 🎮 Metin2 Oyun Projesi – Unity ile Modernleştirilmiş Hal

Bu proje, klasik Metin2 oyununun **Unity 6** altyapısı üzerinde geliştirilmiş, modern yazılım mimarileriyle desteklenen versiyonudur. Proje; güvenli veritabanı yapısı, C# uçtan uca (End-to-End) geliştirme ekosistemi ve performanslı bir ağ altyapısını birleştirir.

---

## 🏗️ Veri Yönetimi ve Backend Stratejisi

Oyunun ekonomisini korumak ve performansı maksimize etmek için **Hybrid (Hibrit) Veri Tabanı** mimarisi benimsenmiştir.

| Veri Tipi | Teknoloji | Amaç ve Avantaj |
| --- | --- | --- |
| **Hesaplar & Envanter** | **PostgreSQL** | ACID uyumluluğu ile %100 veri tutarlılığı. Dupe riskini engeller. |
| **Ekonomi & Ticaret** | **PostgreSQL** | İlişkisel veri yapısı ile güvenli ticaret ve detaylı raporlama. |
| **Anlık Konum & Session** | **Redis** | Milisaniyelik hız. Sunucu RAM yükünü optimize eder. |
| **Büyük Log Verileri** | **ClickHouse** | Milyonlarca satırlık oyun içi logu analiz etmek için. |
| **Karakter Sıralaması** | **Redis (Cache)** | DB'yi yormadan anlık sıralama (Ranking) verisi sunar. |
| **Nesne Market & Admin** | **Blazor Web App** | C# ile geliştirilmiş, Web API ile tam uyumlu modern web arayüzü. |

---

## 🛠️ Kullanılan Teknolojiler ve Sürümler

### 🎮 Oyun Motoru & Grafik

* **Unity:** `6.0.0.3.2f1`
* **Grafik Motoru:** **URP (Universal Render Pipeline)**
* **Modelleme:** **Blender 3.6** & **Meshroom** (Photogrammetry).
* **Animasyonlar:** Mixamo üzerinden optimize edilmiş setler.

### 🌐 Web & API Ekosistemi (Uçtan Uca C#)

* **Web API:** **ASP.NET Core 9+** (Merkezi veri köprüsü).
* **Web Sitesi:** **Blazor WebAssembly / Interactive Server**
* *Neden?* Oyun sunucusuyla aynı C# sınıflarını (Item, Player, Skill) kullanarak kod tekrarını önler.
* *Avantaj:* JS ihtiyacını minimize eder, yüksek güvenlikli oyuncu panelleri sunar.


* **Mobile Companion:** **Flutter** (API üzerinden anlık pazar takibi).

### 🌐 Ağ Altyapısı (Networking)

* **Ağ Sistemi:** **Mirror** (High-level networking).
* **Ağ Transport:** **Telepathy Transport** (TCP tabanlı stabil iletişim).

---

## 🚀 Derleme ve Dağıtım (Build Pipeline)

* **Geliştirme (Mono):** Hızlı prototipleme ve kolay Debugging.
* **Dağıtım (IL2CPP):** * **Performans:** C# kodunu C++'a çevirerek işlemci verimliliğini artırır.
* **Güvenlik:** Kodun decompile edilmesini zorlaştırarak hilelere karşı koruma sağlar.



---

## 🧱 Varlık (Asset) İş Akışı

1. **Tarama:** Meshroom ile gerçek nesnelerin fotoğraflarından model üretimi.
2. **Optimizasyon:** Blender `Decimate` ve `Retopology` ile düşük poligonlu oyun modellerine dönüştürme.
3. **Entegrasyon:** `.fbx` modellerin URP shaderları ve Unity Animator ile canlandırılması.

---

## 🛡️ Güvenlik ve Anti-Cheat Modeli

* **Server-Side Authority:** Tüm fizik ve hasar hesaplamaları sunucuda doğrulanır.
* **Shared Logic:** Blazor web paneli ve oyun sunucusu, aynı doğrulama mantığını (Validation Logic) paylaşır.
* **Anti-Cheat Dashboard:** Blazor admin paneli üzerinden anlık log analizi ve oyuncu banlama işlemleri.

---

## 📌 Geliştirici Notları

* Proje, C# ekosisteminin gücünü kullanarak (Unity + .NET API + Blazor) tek bir dil ile tüm platformlara hitap eder.
* Veritabanı işlemleri asenkron yapıdadır.
* **Blazor** arayüzü, oyuncuların oyun dışındayken nesne marketi kullanmasına ve karakterlerini yönetmesine olanak tanır.

* Redis for Windows 5.0.14.1 (Port: 6379)
* StackExchange.Redis 2.10.1

---

