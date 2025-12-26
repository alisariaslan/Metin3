
---

# ⚔️ Metin2 Projesi: Modern Mimari ve Teknik Dökümantasyon

Bu proje, nostaljik Metin2 deneyimini **Uçtan Uca C# (Full-Stack C#)** felsefesiyle, 2025 yılının en güncel teknolojilerini kullanarak modernize eder.

---

## 🏗️ 1. Sistem Mimarisi ve Veri Akışı

Oyunun temelinde **"Single Source of Truth" (Tek Doğruluk Kaynağı)** prensibi yatar. `M3.Shared` kütüphanesi sayesinde, oyuncu verileri (PlayerSession, Inventory, Stats) her platformda aynı şekilde işlenir.

### **Veri Katmanları (Hybrid DB Strategy)**

| Katman | Teknoloji | Görev | Neden Bu Seçim? |
| --- | --- | --- | --- |
| **Kalıcı (Persistent)** | **PostgreSQL 18.1.2** | Hesap, Karakter, Envanter | Veri bütünlüğü (ACID) ve güvenli ticaret. |
| **Önbellek (Cache)** | **Redis 5.0.14.1** | Pozisyon, Session, Ranking | Milisaniyelik gecikme ile anlık senkronizasyon. |
| **Büyük Veri (Big Data)** | **ClickHouse** | Oyun İçi Loglar, GM İşlemleri | Saniyede milyonlarca log analizi ve hile tespiti. |
| **API / Gatekeeper** | **ASP.NET Core 9** | Auth, Server List, Web Shop | Veritabanı ile Oyun Sunucusu arasındaki tampon. |

---

## 🛠️ 2. Yazılım ve Geliştirme Ekosistemi

### **Oyun Motoru: Unity 6 (6.0.0.3.2f1)**

* **Render Pipeline:** **URP** (Mobil ve PC arası optimizasyon).
* **Scripting Backend:**
* *Development:* **Mono** (Hızlı derleme ve debug).
* *Production:* **IL2CPP** (C++ performansı ve Reverse Engineering koruması).


* **Networking:** **Mirror** + **Telepathy Transport** (TCP tabanlı stabil iletişim).

### **Varlık (Asset) İş Akışı**

1. **Meshroom:** Fotoğraflardan gerçekçi 3D objelerin (kaya, bina, zırh) üretilmesi.
2. **Blender 3.6:** Retopology ve Low-Poly optimizasyonu.
3. **Mixamo & Unity Animator:** Senkronize saldırı ve beceri animasyonları.

---

## 🌐 3. Sunucu Yapılandırması (Hierarchy)

Proje, yükü dengelemek için üç katmanlı bir dağıtım modeline sahiptir:

1. **Level 1: Hub (Login Server):**
* **Teknik:** ASP.NET Core Web API.
* **Görevi:** Karakter seçimi, sunucu listesi sunumu, şifre doğrulama.


2. **Level 2: World (Master Server):**
* **Teknik:** Unity Dedicated Server.
* **Görevi:** "Anadolu", "Rumeli" gibi ana sunucu mantığını yönetir.


3. **Level 3: Channel (CH):**
* **Teknik:** Çoklu Server Instance (Farklı Portlarda).
* **Görevi:** Kalabalık bölgelerdeki yükü (Slotlar, Bosslar) bölüştürür.



---

## ⚙️ 4. Komut Satırı ve Otomasyon (CLI)

Build edilen uygulamaları yönetmek için geliştirilen parametre yapısı:

| Parametre | Açıklama | Varsayılan Değer |
| --- | --- | --- |
| **`-redisConn`** | Redis bağlantı stringi. | `127.0.0.1:6379,abortConnect=false` |
| **`-api`** | Server List API adresi. | `https://localhost:7266/api/server/list` |

**Post-Build Script:**

```batch
copy /Y "$(TargetPath)" "C:\Projects\Metin3\Assets\"

```

*Geliştirme sırasında Shared kütüphanesini otomatik olarak Unity projesine aktarır.*

---

## 🛡️ 5. Güvenlik ve Kararlılık (Fixes)

* **Redis Windows Fix:** Redis'in servis olarak çalışırken portu dinlememesi sorunu, konfigürasyondaki `dir` yolunun `C:/Redis` olarak güncellenmesi ve `NETWORK SERVICE` izinlerinin verilmesiyle çözülmüştür.
* **Pathing Fix:** Konfigürasyon dosyalarındaki ters bölü (`\`) hataları, kaçış karakteri sorunlarını önlemek için çift ters bölü (`\\`) veya düz bölü (`/`) ile stabilize edilmiştir.
* **Async/Await:** Tüm veritabanı ve ağ istekleri, Unity Main Thread'i dondurmayacak şekilde asenkron yapılmıştır.

---

## 🎯 6. Web & Mobil Entegrasyonu (Blazor & Flutter)

* **Blazor Web App:** Oyun sunucusuyla aynı `M3.Shared` kütüphanesini kullanır. Bu sayede oyuncu web sitesinden bir item satın aldığında, item özellikleri sunucuyla %100 uyumlu olur.
* **Flutter Mobile:** Oyuncuların dışarıdayken pazarlarını kontrol etmesine ve karakter istatistiklerini görmesine olanak tanır.

---

### **Geliştirici Özet Görünümü**

> **Dil:** Tek Dil (C#)
> **Güvenlik:** Server-Authoritative
> **Performans:** Redis Cache & IL2CPP
> **Esneklik:** CLI & API Driven

---
