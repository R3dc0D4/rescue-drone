# V1 İlk Uçuş Kontrol Listesi

Bu dosya Rescue Drone V1'in fiziksel kurulum ve ilk saha uçuşu sırasında kullanılacak operasyon kontrol listesidir.

## A. Çalışmaya Başlamadan Önce

- [ ] Çalışma masasında pervaneler söküldü
- [ ] Batarya fiziksel hasar / şişme açısından kontrol edildi
- [ ] XT60 ve PDB bağlantıları kontrol edildi
- [ ] Pixhawk yön oku gövdenin önü ile uyumlu
- [ ] Pixhawk titreşim azaltıcı pad üzerinde
- [ ] GPS/compass sağlam ve uygun konumda
- [ ] Receiver sağlam
- [ ] Telemetri sağlam
- [ ] SD kart takılı

## B. Bağlantı Kaydı

| Kontrol | Sonuç | Not |
|---|---|---|
| Power Module → Pixhawk POWER | ⬜ | |
| GPS → Pixhawk | ⬜ | |
| Compass → Pixhawk | ⬜ | |
| Receiver → RC IN | ⬜ | |
| Telemetry → TELEM | ⬜ | |
| MAIN OUT 1 → Ön Sağ | ⬜ | |
| MAIN OUT 2 → Arka Sol | ⬜ | |
| MAIN OUT 3 → Ön Sol | ⬜ | |
| MAIN OUT 4 → Arka Sağ | ⬜ | |

## C. Mission Planner

- [ ] Bağlantı kuruldu
- [ ] Firmware sürümü not edildi
- [ ] Parametre yedeği alındı
- [ ] Frame = Quad X
- [ ] Accelerometer calibration tamam
- [ ] Compass calibration tamam
- [ ] Radio calibration tamam
- [ ] Battery monitor voltajı multimetre ile karşılaştırıldı
- [ ] Current monitor doğrulandı
- [ ] Flight modes doğrulandı
- [ ] Radio failsafe doğrulandı
- [ ] Battery failsafe doğrulandı
- [ ] Pre-arm kontroller temiz

## D. Motor Test — Pervaneler Sökülü

Mission Planner Motor Test harf sırası motor numaraları ile karıştırılmamalıdır.

- [ ] Test A doğru fiziksel motoru çalıştırdı
- [ ] Test B doğru fiziksel motoru çalıştırdı
- [ ] Test C doğru fiziksel motoru çalıştırdı
- [ ] Test D doğru fiziksel motoru çalıştırdı
- [ ] Motor 1 = Ön Sağ
- [ ] Motor 2 = Arka Sol
- [ ] Motor 3 = Ön Sol
- [ ] Motor 4 = Arka Sağ
- [ ] Dönüş yönleri Mission Planner diagramı ile uyumlu
- [ ] ESC/motor başlangıçları tutarlı

## E. Pervane Montajı

- [ ] Doğru CW/CCW pervane doğru motorda
- [ ] Pervaneler çatlak/hasarsız
- [ ] Somunlar güvenli
- [ ] Kablolar pervane alanından uzak

## F. Saha Öncesi

- [ ] Açık ve boş alan
- [ ] İnsan/araç yok
- [ ] Rüzgâr kabul edilebilir
- [ ] GPS 3D fix yeterli
- [ ] Home position doğru
- [ ] RC kontrolü aktif
- [ ] Telemetri aktif
- [ ] Batarya tam ve dengeli şarj
- [ ] Battery voltage Mission Planner'da doğru
- [ ] RTL altitude kontrol edildi

## G. İlk Uçuş Sırası

### 1 — STABILIZE

- [ ] Arm
- [ ] Kısa hover
- [ ] Roll/pitch/yaw tepkileri normal
- [ ] Anormal titreşim yok
- [ ] Kontrollü iniş
- [ ] Log indirildi

### 2 — ALT_HOLD

- [ ] STABILIZE güvenilir
- [ ] ALT_HOLD kısa test
- [ ] Yükseklik davranışı normal
- [ ] Log indirildi

### 3 — LOITER

- [ ] ALT_HOLD güvenilir
- [ ] GPS/compass davranışı normal
- [ ] LOITER konum tutuyor
- [ ] Log indirildi

### 4 — RTL

- [ ] LOITER güvenilir
- [ ] Home doğru
- [ ] RTL altitude güvenli
- [ ] Kısa mesafeden RTL test
- [ ] Dönüş davranışı normal
- [ ] Log indirildi

### 5 — AUTO

- [ ] RTL güvenilir
- [ ] Küçük test görevi
- [ ] Düşük hız
- [ ] Güvenli irtifa
- [ ] Az sayıda waypoint
- [ ] Görev tamamlandı
- [ ] Log indirildi

## H. Test Sonrası Kaydedilecek Veriler

- Tarih:
- Konum:
- Hava/rüzgâr:
- Batarya tipi:
- Kalkış voltajı:
- İniş voltajı:
- Uçuş süresi:
- Maksimum akım:
- Maksimum irtifa:
- Kullanılan modlar:
- Sorunlar:
- DataFlash log dosyası:
- Sonraki aksiyon:
