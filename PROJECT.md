# Rescue Drone — Arama Kurtarma İHA Projesi

**Oluşturulma:** 28.06.2026  
**Son güncelleme:** 22.10.2026  
**Durum:** V1 temel uçuş platformunu tamamlama  
**Sorumlu:** Ünal TANRISEVER  
**Amaç:** Doğada kayıp kişi arama-kurtarma faaliyetlerinde kullanılabilecek, uygun maliyetli, açık kaynak tabanlı ve geliştirilebilir bir İHA prototipi oluşturmak.

> Bu repo yalnızca arama-kurtarma drone projesine aittir. DJI Neo 2 ve diğer drone projeleri bu kapsamın dışındadır.

---

## 1. V1 Başarı Kriteri

V1 tamamlanmış sayılabilmesi için aşağıdaki zincirin güvenilir şekilde çalışması gerekir:

- [ ] Pixhawk fiziksel montajı ve elektrik bağlantıları doğrulandı
- [ ] ArduPilot Copter güncel stable sürüm kuruldu
- [ ] Frame Type = Quad X doğrulandı
- [ ] Accelerometer kalibrasyonu tamamlandı
- [ ] Compass kalibrasyonu tamamlandı
- [ ] RC kalibrasyonu tamamlandı
- [ ] Battery monitor / power module kalibre edildi
- [ ] Radio failsafe yapılandırıldı ve test edildi
- [ ] Battery failsafe yapılandırıldı ve test edildi
- [ ] Motor sıralaması pervaneler sökülüyken doğrulandı
- [ ] Motor dönüş yönleri doğrulandı
- [ ] STABILIZE uçuşu güvenilir
- [ ] ALT_HOLD uçuşu güvenilir
- [ ] LOITER uçuşu güvenilir
- [ ] RTL sahada test edildi
- [ ] Küçük AUTO waypoint/grid görevi başarıyla tamamlandı
- [ ] Telemetri ve uçuş logları kaydedildi

**V1 tamamlanmadan kamera, termal kamera, companion computer veya AI entegrasyonu uçuş platformuna eklenmeyecek.**

---

## 2. Mevcut Donanım

| Parça | Adet | Durum | Not |
|---|---:|---|---|
| F450 PCB Quadcopter Gövde | 1 | ✅ Mevcut | 450 mm |
| Emax CF2822 1200KV Motor | 4 | ✅ Mevcut | 3S kullanım |
| 30A ESC | 4 | ✅ Mevcut | Topacc |
| Pixhawk 32Bit Standart Paket | 1 | ✅ Mevcut | GPS, buzzer, safety switch vb. |
| GPS + Compass | 1 | ✅ Mevcut | Pixhawk paketi |
| MAVLink2 Wi-Fi Telemetri | 1 | ✅ Mevcut | Kısa menzilli bench/konfigürasyon için |
| Flysky FS-CT6B + FS-R6B | 1 | ✅ Mevcut | Acil müdahale / manuel kontrol |
| Sony/Murata US18650VTC6 | 6 | ✅ Mevcut | 3S2P planlanmış |
| PDB | 1 | ✅ Mevcut | F450 PCB |
| Pervaneler | Set | ✅ Mevcut | Uygun çap/pitch uçuş öncesi tekrar doğrulanacak |
| 433 MHz uzun menzil telemetri | 1 çift | ⏳ Plan | V1 için zorunlu değil |
| 3S LiPo | 1–2 | ⏳ Önerilen | İlk saha testlerinde tercih edilebilir |
| Power module / akım-voltaj sensörü | 1 | ⚠️ Doğrulanacak | Battery failsafe için kritik |

### Önceki bench notları

01.07.2026 tarihli proje notlarında aşağıdakiler çalışmış olarak kayıtlıdır:

- Motor yön testi: ✅
- Wi-Fi telemetri testi: ✅
- Pixhawk, motor, ESC ve gövde temini: ✅

**Bu maddeler ilk saha uçuşundan önce yeniden doğrulanacaktır.**

---

## 3. Kritik Düzeltme — ArduPilot Quad X Motor Sıralaması

Önceki PROJECT.md sürümünde Motor 2 ve Motor 4 konumları hatalı yazılmıştı.

ArduPilot'un varsayılan Quad X motor fonksiyon sırası:

| Motor | Varsayılan çıkış | Konum |
|---|---|---|
| Motor 1 | MAIN OUT 1 | Ön Sağ (Front Right) |
| Motor 2 | MAIN OUT 2 | Arka Sol (Back Left) |
| Motor 3 | MAIN OUT 3 | Ön Sol (Front Left) |
| Motor 4 | MAIN OUT 4 | Arka Sağ (Back Right) |

```text
                 ÖN
          M3             M1
       (Ön Sol)       (Ön Sağ)

              [ PIXHAWK ]

          M2             M4
      (Arka Sol)      (Arka Sağ)
                ARKA
```

> Motor numarası ile Mission Planner Motor Test ekranındaki A/B/C/D harfleri aynı şey değildir.

Mission Planner Motor Test, Quad X için **ön sağdan başlayıp saat yönünde** test eder. Test mutlaka **pervaneler sökülüyken** yapılacaktır.

Motor dönüş yönü yalnızca dokümana bakılarak varsayılmayacak; Mission Planner motor diagramı ve fiziksel pervane tipi birlikte doğrulanacaktır.

---

## 4. Güç Mimarisi

Önerilen güç akışı:

```text
Batarya
   │
   ▼
Power Module / Voltage-Current Monitor
   │
   ├────────────► Pixhawk POWER
   │
   ▼
F450 PDB
   ├── ESC 1 ──► Motor 1
   ├── ESC 2 ──► Motor 2
   ├── ESC 3 ──► Motor 3
   └── ESC 4 ──► Motor 4
```

Power module yalnızca Pixhawk'ı beslemek için değil, aşağıdakiler için de gereklidir:

- Gerçek zamanlı batarya voltajı
- Akım ölçümü
- Tüketilen mAh takibi
- Low Battery failsafe
- Critical Battery failsafe
- Uçuş loglarında güç analizi

### Batarya yaklaşımı

Mevcut 3S2P VTC6 paket geliştirme amacıyla kullanılabilir; ancak ilk saha testlerinde:

- hazır ve güvenilir bir 3S LiPo,
- düzgün bir power module,
- kalibre edilmiş voltage/current monitor

tercih edilir.

Batarya failsafe değerleri hücre kimyasına ve yük altındaki gerçek voltaj düşümüne göre sahada ölçülerek ayarlanacaktır; sabit bir voltaj değeri kopyalanmayacaktır.

---

## 5. Uçuş Kontrol Bağlantıları

```text
Pixhawk
├── POWER      ← Power Module
├── GPS        ← GPS
├── I2C/CAN*   ← Compass (modüle göre)
├── RC IN      ← Flysky receiver
├── TELEM      ← MAVLink Wi-Fi / ileride SiK telemetri
├── MAIN OUT 1 → Motor 1 / Ön Sağ
├── MAIN OUT 2 → Motor 2 / Arka Sol
├── MAIN OUT 3 → Motor 3 / Ön Sol
└── MAIN OUT 4 → Motor 4 / Arka Sağ
```

`* GPS/Compass paketinin bağlantı tipine göre.`

---

## 6. V1 Fazları ve Geçiş Kriterleri

### Faz 1 — Mekanik ve Elektrik

- [ ] F450 gövde sıkılık kontrolü
- [ ] Pixhawk titreşim azaltıcı pad üzerinde ve yönü doğru
- [ ] GPS/compass motor güç kablolarından mümkün olduğunca uzak
- [ ] PDB lehimleri ve XT60 bağlantısı kontrol edildi
- [ ] ESC güç bağlantıları kontrol edildi
- [ ] ESC sinyal/GND bağlantıları kontrol edildi
- [ ] Power module mevcut ve doğru bağlı
- [ ] Receiver bağlı
- [ ] Telemetri bağlı

**Geçiş kriteri:** Kısa devre yok; Pixhawk güvenilir açılıyor; tüm çevre birimleri algılanıyor.

### Faz 2 — Firmware ve Kalibrasyon

- [ ] ArduPilot Copter stable firmware
- [ ] Frame = Quad X
- [ ] Accelerometer calibration
- [ ] Compass calibration
- [ ] Radio calibration
- [ ] Flight modes atandı
- [ ] Battery monitor calibration
- [ ] Radio failsafe
- [ ] Battery failsafe
- [ ] Arming checks açık

**Geçiş kriteri:** Pre-arm hata vermiyor veya her uyarının nedeni bilinçli olarak çözülmüş.

### Faz 3 — Pervanesiz Motor Testi

- [ ] Pervaneler tamamen söküldü
- [ ] Mission Planner Motor Test A/B/C/D konumları doğrulandı
- [ ] Motor 1–4 fiziksel konumları doğrulandı
- [ ] Dönüş yönleri doğrulandı
- [ ] ESC'ler tutarlı şekilde başlıyor
- [ ] Anormal titreşim/ses yok

**Geçiş kriteri:** Her komut yalnızca beklenen motoru çalıştırıyor.

### Faz 4 — İlk Uçuş

Test sırası:

1. STABILIZE
2. ALT_HOLD
3. LOITER
4. RTL
5. AUTO

Her aşamadan sonra log incelenecek; bir önceki mod güvenilir değilse sonraki aşamaya geçilmeyecek.

**İlk saha testi hedefi:** sadece kısa hover ve kontrollü iniş.

### Faz 5 — Otonom Grid

- [ ] Mission Planner'da küçük test alanı
- [ ] Düşük hız
- [ ] Güvenli irtifa
- [ ] RTL yüksekliği doğrulandı
- [ ] Geofence değerlendirildi
- [ ] AUTO görevi
- [ ] Görev sonunda RTL/LAND davranışı doğrulandı

**Geçiş kriteri:** Küçük grid görevi tekrarlanabilir biçimde tamamlanıyor.

---

## 7. Arama-Kurtarma V2 Mimarisi

V1 uçuş platformu tamamlandıktan sonra:

```text
RGB Kamera ───────┐
                  │
Termal Kamera ───►│ Companion Computer
                  │ Raspberry Pi 5 / benzeri
                  │
                  ├── Person Detection
                  ├── Thermal Hotspot Detection
                  ├── Frame Timestamp
                  └── Hedef piksel koordinatı
                         │
                         ▼
                     MAVLink
                         │
                         ▼
                     Pixhawk
                         │
                  GPS / Altitude / Yaw
                         │
                         ▼
                Tahmini hedef koordinatı
                         │
                         ▼
              Yer istasyonunda işaretleme
```

### V2 hedefleri

- [ ] RGB canlı görüntü
- [ ] Görüntü kaydı
- [ ] Termal kamera
- [ ] Companion computer
- [ ] AI kişi tespiti
- [ ] Tespitin zaman damgası ile uçuş logunu eşleştirme
- [ ] Hedef koordinatı tahmini
- [ ] Yer istasyonunda pin/olay kaydı
- [ ] Aynı hedefin tekrar tekrar raporlanmasını engelleyen takip mantığı

**FPGA şu aşamada gerekli değildir.** İhtiyaç daha sonra düşük gecikmeli görüntü ön işleme nedeniyle oluşursa ayrıca değerlendirilecektir.

---

## 8. Yazılım

### Uçuş

- ArduPilot Copter
- Mission Planner
- MAVLink

### Companion Computer — V2

- Python
- OpenCV
- MAVSDK veya pymavlink
- AI inference runtime
- İleride web tabanlı görev/olay arayüzü

> Yeni geliştirmede DroneKit'e bağımlı mimari kurmak yerine MAVSDK/pymavlink öncelikli değerlendirilecektir.

---

## 9. İlk Çalışma Oturumu — Yapılacaklar

Bir sonraki fiziksel çalışma oturumunun sırası:

- [ ] Drone'un üstten ve alttan güncel fotoğrafını çek
- [ ] Pixhawk model/etiketini doğrula
- [ ] Power module'un fiziksel olarak mevcut olup olmadığını doğrula
- [ ] GPS/compass kablolarını doğrula
- [ ] Receiver bağlantısını doğrula
- [ ] ESC → MAIN OUT sırasını kablo kablo doğrula
- [ ] Pervaneleri çıkar
- [ ] Mission Planner bağlantısı kur
- [ ] Mevcut firmware sürümünü kaydet
- [ ] Parametre yedeği al
- [ ] Motor Test A/B/C/D sonuçlarını kaydet

Bu işlem tamamlanınca ilk uçuş öncesi eksik parça listesi kesinleşecektir.

---

## 10. Güvenlik

- Motor testleri pervaneler sökülüyken yapılır.
- İlk uçuş geniş, boş ve insanlardan uzak bir alanda yapılır.
- Manuel müdahale için RC bağlantısı aktif tutulur.
- Arming checks sırf uçuşu mümkün kılmak için kapatılmaz.
- GPS tabanlı modlar yeterli konum çözümü olmadan denenmez.
- LOITER güvenilir olmadan RTL denenmez.
- RTL güvenilir olmadan AUTO göreve geçilmez.
- Her saha testinden sonra DataFlash logu saklanır ve incelenir.
- Uçuş öncesinde yürürlükteki SHGM kayıt, uçuş sahası ve operasyon kuralları ayrıca doğrulanır.

---

## 11. Resmî Teknik Kaynaklar

- [ArduPilot — First Time Setup](https://ardupilot.org/copter/docs/initial-setup.html)
- [ArduPilot — Connect ESCs and Motors](https://ardupilot.org/copter/docs/connect-escs-and-motors.html)
- [ArduPilot — Autopilot Output Functions](https://ardupilot.org/copter/docs/common-rcoutput-mapping.html)
- [ArduPilot — Pre-Flight Checklist](https://ardupilot.org/copter/docs/checklist.html)
- [ArduPilot — Battery Failsafe](https://ardupilot.org/copter/docs/failsafe-battery.html)
- [ArduPilot — Power Modules](https://ardupilot.org/copter/docs/common-powermodule-landingpage.html)
- [Mission Planner](https://ardupilot.org/planner/)
- [MAVLink](https://mavlink.io/)

---

## 12. Proje Durum Özeti

**Şu anki hedef:** Kamera/AI satın almak değil; F450 + Pixhawk platformunu güvenilir şekilde uçurmak.

**Bir sonraki kilometre taşı:**

> Pervanesiz bağlantı ve motor doğrulaması → firmware/kalibrasyon → kısa STABILIZE hover.

Bundan sonra ALT_HOLD, LOITER, RTL ve AUTO grid görevleri sırayla kapatılacaktır.
