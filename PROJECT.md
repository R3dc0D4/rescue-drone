# Otopilot Drone Projesi — Arama Kurtarma

**Oluşturulma:** 28.06.2026  
**Güncelleme:** 28.06.2026  
**Durum:** Parça temini  
**Sorumlu:** Ünal TANRISEVER  
**Amaç:** Doğada kayıp kişi arama-kurtarma drone'u — arama-kurtarma faaliyeti yürüten gönüllü gruplar ve STK'lar için uygun fiyatlı kurtarma drone'una sahip olabilmesi amacıyla tasarlanmıştır. Ticari değil, gönüllülük amaçlıdır.

**Niyet:** Deniz dibi çöp toplama + su akıntısı ile karşı adaya giden çöp toplama + arama-kurtarma

## Proje Özeti

Doğada kayıp kişileri tespit etmek için otopilot uçuş yapabilen bir İHA. Pixhawk uçuş kontrol kartı tabanlı, termal/kamera ile donatılmış arama-kurtarma sistemi. Kumanda yok — tam otopilot uçuş, telemetri ile yer istasyonu kontrolü.

**NOT:** DJI Neo 2 ayrı bir proje — çöp toplama ve selfie drone'u. Bu proje sadece arama-kurtarma.

## Elde Mevcut Parçalar

| Parça | Adet | Kaynak | Not |
|-------|------|--------|-----|
| Flysky FS-CT6B Kumanda + FS-R6B Alıcı | 1 | Elinde var | 6 kanal, AFHDS, acil müdahale için |
| Emax CF2822 1200KV Fırçasız Motor | 4 | Siparişte | motorobit.com |
| 30A ESC Fırçasız Motor Sürücü | 4 | Siparişte | direnc.net, Topacc |
| F450 PCB Kartlı Quadcopter Gövde Kiti | 1 | Siparişte | robotistan.com, 450mm, 280g |
| KK2.15 Ekranlı Uçuş Kontrol Kartı | 1 | Elinde var | ⚠️ Sadece stabilizasyon, otopilot yok |
| KK Multiicopter v5.5 Uçuş Kontrol Kartı | 1 | Elinde var | ⚠️ Sadece stabilizasyon, otopilot yok |
| DJI Neo 2 | 1 | Siparişte | ❌ Ayrı proje — selfie/çöp drone |

## Sipariş Bekleyen Parçalar

| Parça | Adet | Kaynak | Tahmini Fiyat | Not |
|-------|------|--------|----------------|-----|
| Pixhawk 32Bit Standart Paket | 1 | robotistan.com | ~12.317 TL | GPS + Buzzer + OSD + LED + Kablolar dahil |
| 3DR V5 433MHz 1000mW Telemetri Seti | 1 çift | robotistan.com | ~7.148 TL | 1000mW, ~2-5km menzil, Pixhawk uyumlu |

## Alınması Gereken Ekstra Parçalar

| Parça | Adet | Tahmini Fiyat | Not |
|-------|------|----------------|-----|
| Telemetri | — | — | V5 1000mW Robotistan'dan alınacak (aynı sipariş) |
| PDB (Güç Dağıtım Boardu) | — | Elinde var | F450 PCB board + yedek |
| F450 PCB Kartlı Quadcopter Gövde Kiti | — | Elinde var | 450mm, kırmızı/beyaz |
| Pervane (10x4.5 veya 10x5) | — | Elinde var | CF2822 için uyumlu |
| LiPo Şarj Aleti | — | Elinde var | |
| 3S LiPo Batarya (3000-4000mAh) | 2 | ~1.600-2.400 TL | CF2822 3S öneriyor |
| **Aksiyon Kamera (arama-kurtarma)** | 1 | ~1.500-3.000 TL | Aşağıda detaylar |

### Aksiyon Kamera Seçenekleri (Arama-Kurtarma)

Arama-kurtarma için kamera kritik — kayıp kişiyi tespit etmek için:

| Seçenek | Fiyat | Artı | Eksi |
|---------|-------|------|------|
| **Runcam Split 3 Nano** | ~800-1.200 TL | Hafif (20g), 4K kayıt, FPV çıkışı | Gece görüşü yok |
| **Caddx Ratel 2** | ~1.500-2.000 TL | Yıldız ışığı sensör, gece görüşü | Ağır değil ama termal yok |
| **Walksnail Moonlight Kit** | ~10.800 TL | 1080p, geniş FOV, iyi düşük ışık | Pahalı |
| **Termal kamera (ht301 vb.)** | ~8.000-15.000 TL | ✅ Isı tespiti — arama-kurtarma için en iyi | Çok pahalı, ağır |

**Öneri (aşamalı):**
1. **Faz 1:** Runcam Split 3 Nano veya Caddx Ratel 2 — düşük maliyetle başla
2. **Faz 2:** Termal kamera modülü ekle (gece/vizual tespit için)

## Donanım Detayları

### Uçuş Kontrol: Pixhawk 32Bit Standart Paket İçeriği
- 1x Pixhawk 32Bit Uçuş Kontrol Kartı (Cortex M4 ARM)
- 1x Dahili Pusulalı GPS Modülü
- 1x Buzzer
- 1x LED Güvenlik Butonu
- 1x Telemetri Kablo
- 1x Micro SD Adaptör
- 1x GPS Tutucu
- 1x Servo Kablo
- 1x Amortisör
- 1x Drone OSD
- 1x Güç Kaynağı Kablosu

**Ekstra alınacaklar:**
- SiK Telemetry V3 (433MHz) → Rx-Dynamic ~8.490 TL veya daha uygun alternatif aranıyor

### Kumanda: Flysky FS-CT6B + FS-R6B
- 6 kanal, AFHDS protokol
- Sadece acil durum/arming için
- Otopilot modunda kumanda kullanılmayacak

### Motor: Emax CF2822 1200KV
- 4x fırçasız motor
- 3S LiPo, 10" pervane ile 710g thrust/motor
- Toplam ~2840g thrust (quadcopter)

### ESC: 30A Fırçasız Motor Sürücü
- 4x ESC (Topacc marka)
- CF2822 16A max akım için yeterli

### KK2.15 ve KK v5.5 Kartları
- ⚠️ Bu kartlar SADECE stabilizasyon yapar, otopilot DEĞİLDİR
- GPS, waypoint, RTL özellikleri YOK
- Pixhawk gelene kadar manuel uçuş testi için kullanılabilir
- Arama-kurtarma projesi için Pixhawk şart

### Arama-Kurtarma Özellikleri (Hedef)

| Özellik | Açıklama | Faz |
|---------|----------|-----|
| Waypoint tarama | Belirlenen alanda grid tarama | Faz 2 |
| RTL | Otomatik dönüş ve iniş | Faz 2 |
| Telemetri izleme | Yer istasyonundan canlı konum/veri | Faz 2 |
| Kamera kayıt | Aksiyon kamera ile video kayıt | Faz 3 |
| Canlı video | FPV verici ile gerçek zamanlı görüntü | Faz 3 |
| Termal tespit | Isı kaynağı tespiti (gece arama) | Faz 4 |
| AI kişi tespiti | Companion computer ile otomatik tespit | Faz 4 |

## CF2822 Motor Hesaplamaları

**Quadcopter (4 motor) tahmini:**
- Toplam thrust: ~2.840g (4x 710g @ 3S 10x5)
- Önerilen uçuş ağırlığı: ~700-1000g (%35-50 thrust-to-weight ratio)
- Frame + elektronik ağırlık tahmini: ~400-500g
- Batarya (3S 4000mAh): ~350g
- Kamera + verici: ~50-100g
- Net payload kapasitesi: ~150-300g

**Uçuş süresi tahmini (3S 4000mAh, 800g toplam):**
- Ortalama akım: ~22-28A (4 motor hover + kamera)
- Uçuş süresi: ~7-10 dakika

## Yazılım

### Uçuş Yazılımı: ArduPilot
- **ArduPilot Copter 4.x** — quadcopter otopilot
- MAVLink protokolü ile yer istasyonu iletişimi
- Mission Planner (Windows) ile konfigürasyon

### Arama-Kurtarma Yazılımı (ileri seviye)
- **DroneKit Python** — otopilot görev programlama
- **OpenCV** — kişi tespiti, hareket algılama
- **MAVProxy** — headless yer istasyonu
- **Grid tarama pattern** — belirlenen alanda otomatik arama

### Otopilot Uçuş Modları
| Mod | Açıklama | Kullanım |
|-----|----------|----------|
| STABILIZE | Manuel + stabilizasyon | Test |
| ALT_HOLD | Yükseklik tutma | Arama |
| LOITER | GPS ile konum tutma | Gözlem |
| AUTO | Waypoint görevi | Grid tarama |
| RTL | Return to Launch | Güvenlik |
| GUIDED | Yer istasyonu kontrollü | Hedef takip |

## Proje Fazları

### Faz 1: Temel Uçuş (2-3 hafta)
- [ ] Pixhawk Standart Paket temini — siparişte
- [x] Motor + ESC temini (CF2822 x4, 30A ESC x4) ✅ Siparişte
- [x] F450 gövde kiti ✅ Siparişte
- [x] Kumanda mevcut (Flysky FS-CT6B) ✅ Elinde var
- [ ] 3DR V5 1000mW Telemetri — robotistan.com'dan alınacak (aynı sipariş)
- [ ] PDB satın al
- [ ] Pervane + 3S LiPo batarya satın al
- [ ] Aksiyon kamera satın al
- [ ] ArduPilot Copter 4.x flash ve kalibrasyon
- [ ] RC kalibrasyonu (FS-CT6B → Pixhawk PWM)
- [ ] Quadcopter montajı
- [ ] İlk uçuş (STABILIZE modu)
- [ ] Telemetri bağlantısı testi

### Faz 2: Otopilot Uçuş (1-2 hafta)
- [ ] GPS kalibrasyonu
- [ ] ALT_HOLD, LOITER modu testleri
- [ ] Waypoint görevi (AUTO modu) — grid tarama pattern
- [ ] RTL acil durum prosedürü testi
- [ ] Batarya monitörü ve alarm

### Faz 3: Arama-Kurtarma Entegrasyonu (2-4 hafta)
- [ ] Aksiyon kamera montajı ve kayıt
- [ ] FPV verici ile canlı görüntü (opsiyonel)
- [ ] Grid tarama görevi oluşturma (belirlenen alan otomatik tarama)
- [ ] Mission Planner ile arama pattern'leri
- [ ] Gerçek zamanlı telemetri dashboard

### Faz 4: Gelişmiş Arama-Kurtarma (4-8 hafta)
- [ ] Termal kamera modülü entegrasyonu
- [ ] Companion Computer (RPi 4B) montajı
- [ ] OpenCV ile kişi tespiti
- [ ] Otomatik iniş (precision landing)
- [ ] Web tabanlı arama koordinasyon arayüzü

## Bütçe Tahmini

| Kategori | Bütçe (TL) |
|----------|------------|
| Pixhawk Standart Paket | ~12.317 |
| 3DR V5 1000mW Telemetri | ~7.148 |
| PDB (Güç Dağıtım) | ~200 |
| F450 PCB Kartlı Gövde | ~500-800 |
| Motor + ESC (CF2822 x4 + 30A ESC x4) | ~1.500-2.000 |
| Pervane + Yedek | ~100-200 |
| 3S LiPo Batarya (2 adet) | ~1.600-2.400 |
| Aksiyon Kamera (Runcam/Caddx) | ~1.000-2.000 |
| Diğer (kablo, konektör, vs.) | ~200-300 |
| **Toplam** | **~25.700-29.500 TL** |

**İleri fazlar:**
- Termal kamera modülü: +8.000-15.000 TL
- Companion Computer (RPi 4B): +2.000-3.000 TL
- FPV verici sistemi: +2.000-4.000 TL

## Güvenlik ve Yasal

- **TR'de İHA:** SHGM onayı gerekli, e-Devlet kaydı zorunlu
- **Sivil İHA limiti:** 25kg altı, 120m yükseklik, VLOS
- **Arama-kurtarma:** AFAD/UMKE koordinasyonu gerekli
- **Sigorta:** Üçüncü şahıs sorumluluk sigortası zorunlu
- **İlk uçuş:** Açık alan, kumanda hazır bulundurulmalı
- **RTL:** Her uçuşta testli ve aktif olmalı
- **Batarya:** %20 altına düşmeden iniş yapılmalı

## Kaynaklar

- [ArduPilot Dokümantasyonu](https://ardupilot.org/)
- [Pixhawk Dokümantasyonu](https://docs.px4.io/)
- [DroneKit Python](https://dronekit-python.readthedocs.io/)
- [MAVLink Protokolü](https://mavlink.io/)
- [Mission Planner](https://ardupilot.org/planner/)
- [Emax CF2822 Motor Spec](https://www.motorobit.com/emax-cf2822-1200kv-fircasiz-drone-motoru)

## Notlar

- Bu proje **arama-kurtarma** amaçlıdır — DJI Neo 2 ayrı bir proje (selfie/çöp drone)
- İlk uçuşlarda Flysky FS-CT6B kumanda ile el kontrolü hazır bulundurulacak
- Kumanda sadece arming ve acil müdahale için
- SiK Telemetry V3 ile yer istasyonundan tam kontrol sağlanacak
- Arama-kurtarma için termal kamera en değerli eklenti (Faz 4)
- KK2.15 ve KK v5.5 kartları otopilot için uygun değil, sadece öğrenme amaçlı
- CF2822 + 3S LiPo + 10" pervane + F450 frame kombinasyonu bu proje için ideal