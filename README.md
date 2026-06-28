# 🚁 AKUT Arama-Kurtarma Drone Projesi

> **Uygun fiyatlı, açık kaynaklı, otopilot arama-kurtarma drone'u**
> 
> AKUT gönüllüsü olarak, tüm ekiplerin uygun fiyatlı kurtarma drone'una sahip olabilmesi için tasarlanmıştır.

## 🎯 Proje Amacı

Bu proje ticari değil, **gönüllülük amaçlıdır**. AKUT (Arama Kurtarma Derneği) gönüllüleri için:

- 🌊 Deniz dibi çöp toplama
- 🌊 Su akıntısı ile karşı adaya giden çöp toplama  
- 🔍 Doğada kayıp kişi arama-kurtarma

Hedef: Tüm AKUT ekiplerinin kopyalayabileceği, düşük maliyetli, tekrarlanabilir bir kurtarma drone sistemi.

## ⚙️ Donanım

| Parça | Model | Tahmini Fiyat | Not |
|-------|-------|---------------|-----|
| Uçuş Kontrol | Pixhawk 32Bit Standart Paket | ~12.317 TL | robotistan.com |
| Telemetri | 3DR V5 433MHz 1000mW | ~7.148 TL | robotistan.com |
| Motor | Emax CF2822 1200KV x4 | ~1.500 TL | direnc.net |
| ESC | 30A Fırçasız Motor Sürücü x4 | ~1.080 TL | direnc.net |
| Gövde | F450 PCB Kartlı Quadcopter | ~500-800 TL | robotistan.com |
| Kumanda | Flysky FS-CT6B + FS-R6B | Elinde var | Acil müdahale |
| Batarya | 3S LiPo 3000-4000mAh x2 | ~1.600-2.400 TL | |
| Termal Kamera | (Faz 4) | ~8.000-15.000 TL | Gece arama |
| **Toplam (Faz 1-3)** | | **~25.000-27.000 TL** | |

> ⚠️ Fiyatlar Haziran 2026 itibarıyladır. AKUT gönüllüleri için toplu alım indirimleri araştırılmalıdır.

## 🏗️ Proje Fazları

### Faz 1: Temel Uçuş (2-3 hafta)
- Pixhawk kurulumu ve kalibrasyon
- RC kalibrasyonu (Flysky FS-CT6B)
- Quadcopter montajı
- İlk uçuş (STABILIZE modu)

### Faz 2: Otopilot Uçuş (1-2 hafta)
- GPS kalibrasyonu
- ALT_HOLD, LOITER, AUTO modları
- Waypoint görevi (grid tarama pattern)
- RTL acil durum prosedürü

### Faz 3: Arama-Kurtarma Entegrasyonu (2-4 hafta)
- Aksiyon kamera montajı
- FPV verici ile canlı görüntü
- Grid tarama görevi oluşturma
- Mission Planner ile arama pattern'leri

### Faz 4: Gelişmiş Arama-Kurtarma (4-8 hafta)
- Termal kamera entegrasyonu
- Companion Computer (RPi 4B)
- OpenCV ile kişi tespiti
- Otomatik iniş (precision landing)

## 🔧 Yazılım

- **Uçuş Yazılımı:** [ArduPilot Copter 4.x](https://ardupilot.org/)
- **Yer İstasyonu:** [Mission Planner](https://ardupilot.org/planner/)
- **Otopilot Programlama:** [DroneKit Python](https://dronekit-python.readthedocs.io/)
- **Görüntü İşleme:** [OpenCV](https://opencv.org/)

## 📋 Uçuş Modları

| Mod | Açıklama | Kullanım |
|-----|----------|----------|
| STABILIZE | Manuel + stabilizasyon | Test |
| ALT_HOLD | Yükseklik tutma | Arama |
| LOITER | GPS ile konum tutma | Gözlem |
| AUTO | Waypoint görevi | Grid tarama |
| RTL | Return to Launch | Güvenlik |
| GUIDED | Yer istasyonu kontrollü | Hedef takip |

## ⚠️ Güvenlik ve Yasal

- **TR'de İHA:** SHGM onayı gerekli, e-Devlet kaydı zorunlu
- **Sivil İHA limiti:** 25kg altı, 120m yükseklik, VLOS
- **Arama-kurtarma:** AFAD/UMKE koordinasyonu gerekli
- **Sigorta:** Üçüncü şahıs sorumluluk sigortası zorunlu
- **İlk uçuş:** Açık alan, kumanda hazır bulundurulmalı
- **RTL:** Her uçuşta testli ve aktif olmalı
- **Batarya:** %20 altına düşmeden iniş yapılmalı

## 🤝 Katkıda Bulunma

Bu proje AKUT gönüllüleri içindir. Katkıda bulunmak için:

1. Fork yapın
2. Feature branch oluşturun (`git checkout -b feature/yenilik`)
3. Commit yapın (`git commit -m 'Yenilik eklendi'`)
4. Push yapın (`git push origin feature/yenilik`)
5. Pull Request açın

## 📄 Lisans

MIT License — ticari olmayan, gönüllülük amaçlı kullanım için serbesttir.

## 🙏 Teşekkürler

- [ArduPilot](https://ardupilot.org/) — açık kaynak otopilot yazılımı
- [Robotistan](https://www.robotistan.com/) — Türkiye'de drone parçaları
- AKUT — arama-kurtarma gönüllüleri

---

**🚁 Her ekip bir kurtarma drone'una sahip olabilmeli.**