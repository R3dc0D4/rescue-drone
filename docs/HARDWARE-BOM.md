# Rescue Drone — Donanım / BOM ve Güncel Maliyetler

**Fiyat kontrol tarihi:** 22.10.2026  
**Para birimi:** TL, KDV dahil fiyatlar esas alınmıştır.  
**Not:** Bu rakamlar geçmişte ödenen satın alma fiyatları değil, 22.10.2026 itibarıyla Türkiye'de görülen **ikame / yeniden satın alma maliyetleridir**. Stok ve fiyatlar değişebilir.

---

## 1. V1 — Mevcut Donanım ve Güncel İkame Değeri

| Parça | Adet | Durum | Güncel birim fiyat | Toplam / aralık | Kaynak / not |
|---|---:|---|---:|---:|---|
| F450 PCB Quadcopter gövde | 1 | ✅ Mevcut | ~684–841 | ~684–841 | Robotistan kırmızı/beyaz: 683,98 TL; kırmızı/siyah: 841,10 TL |
| Emax CF2822 1200KV motor | 4 | ✅ Mevcut | ~1.080–1.394 | ~4.320–5.575 | Robotzade 1.080 TL; Motorobit liste fiyatı daha yüksek |
| 30A ESC | 4 | ✅ Mevcut | ~401 | ~1.604 | Direnc.net 30A ESC: 401,01 TL |
| Pixhawk 32Bit Standart Paket | 1 | ✅ Mevcut | ~9.204–13.377 | ~9.204–13.377 | Robotistan ürün sayfası ve kategori listesinde fiyat farkı var; ürün stok durumu değişken |
| GPS + compass | 1 | ✅ Pixhawk paketinde | dahil | — | Ayrı satın alma gerekmiyor |
| Safety switch / buzzer / kablolar | set | ✅ Pixhawk paketinde | dahil | — | Ayrı satın alma gerekmiyor |
| MAVLink2 Wi-Fi telemetri | 1 | ✅ Mevcut | ~780 | ~780 | Orbi Elektronik |
| FlySky FS-CT6B + FS-R6B | 1 | ✅ Mevcut | ~2.940–3.968 | ~2.940–3.968 | F1Depo / Robolinkmarket |
| Murata/Sony US18650VTC6 | 6 | ✅ Mevcut | ~568 | ~3.409 | Akakçe en düşük görülen fiyat |
| 10x4.5 CW/CCW pervaneler | set | ✅ Mevcut | ~150–550 / set | ~150–550 | Marka ve paket adedine göre büyük fiyat farkı var |
| PDB | 1 | ✅ F450 PCB içinde | dahil | — | Ayrı kart gerekmiyor |
| LiPo balans şarj cihazı | 1 | ✅ Eski proje notunda mevcut | ~2.243–3.300 | ~2.243–3.300 | iMAX B6AC sınıfı; fiziksel cihaz/model tekrar doğrulanacak |

### Mevcut sistemin bugünkü yaklaşık ikame değeri

**Yaklaşık 25.700 – 33.400 TL**

Bu değer, elimizde olduğu kayıtlı parçaların bugün yeniden satın alınması halinde oluşabilecek maliyettir. Aşağıdaki V1 eksikleri bu toplama dahil değildir.

---

## 2. V1 — Satın Alınacak / Fiziksel Olarak Doğrulanacak Kritik Parçalar

| Öncelik | Parça | Adet | Durum | Güncel maliyet | Karar |
|---|---|---:|---|---:|---|
| 🔴 P0 | Pixhawk Power Module, 30V/90A, XT60 | 1 | ⚠️ Fiziksel varlığı doğrulanacak | ~502 TL | **Yoksa alınacak** |
| 🔴 P0 | 3S LiPo 2800–3300mAh, min. 40C | 1 | ⏳ Alınacak | ~1.919–2.263 TL | İlk uçuş için önerilen ana batarya |
| 🟠 P1 | İkinci 3S LiPo 2800–3300mAh, min. 40C | 1 | ⏳ Önerilen | ~1.919–2.263 TL | Saha testinde ikinci batarya |
| 🔴 P0 | Pixhawk PPM Encoder | 1 | ⚠️ Büyük olasılıkla gerekli | ~299–606 TL | FS-R6B'nin bireysel PWM kanallarını Pixhawk RC IN'e toplamak için |
| 🟠 P1 | Yedek 10x4.5 CW/CCW pervane | 1–2 set | ⏳ Önerilen | ~150–550 TL | İlk saha uçuşunda mutlaka yedek olsun |
| 🟠 P1 | XT60, silikon güç kablosu, makaron, kablo bağı | set | ⚠️ Stok kontrol | ~300–600 TL bütçe | Sarf malzemesi bütçesi |
| 🟡 P2 | microSD kart | 1 | ⚠️ Pixhawk içinde kart var mı kontrol | ~300–500 TL bütçe | DataFlash log için |
| 🟡 P2 | 433 MHz SiK/Holybro telemetri | 1 çift | ⏳ Opsiyonel | ~8.466 TL | V1 ilk yakın saha uçuşu için zorunlu değil |

### V1 için muhtemel ek nakit ihtiyacı

**Tek uçuş bataryası ile:** yaklaşık **3.600 – 4.500 TL**  
**İki uçuş bataryası ile:** yaklaşık **5.900 – 6.800 TL**

Bu hesap; power module, olası PPM encoder, batarya, pervane ve temel sarf malzemelerini içerir.  
**433 MHz uzun menzil telemetri dahil değildir.**

433 MHz telemetri de alınırsa V1 ek bütçesi yaklaşık **14.400 – 15.300 TL** seviyesine çıkar.

> LiPo şarj cihazının gerçekten elde olduğu doğrulanırsa yeni şarj cihazı alınmayacak. Yoksa iMAX B6AC sınıfı balanslı şarj için ayrıca yaklaşık **2.250–3.300 TL** gerekir.

---

## 3. Kritik Teknik Uyum Kontrolü

### Motor + ESC

CF2822 1200KV motor için 3S + 10x4.5 test verisinde yaklaşık **14,5A/motor** görülebiliyor. Dört motor için teorik üst sınır yaklaşık:

```text
14,5 A × 4 = 58 A
```

Bu nedenle:

- 30A ESC / motor → yeterli marj sağlar.
- 90A power module → V1 için yeterli sınıftadır.
- Güç kablosu, XT60 ve PDB bağlantıları 60A sınıfı toplam akımı güvenli taşıyacak durumda olmalıdır.

### VTC6 3S2P paketi neden ilk tercih değil?

Murata, US18650VTC6 için **30A hücre başına sürekli maksimum deşarj** değeri listeliyor. 3S2P teorik olarak:

```text
30 A × 2 paralel = 60 A
```

Motorların 10x4.5 pervane ile teorik tam yükü ise yaklaşık **58A** olabilir.

Yani 3S2P VTC6 paketinde tam gaz bölgesinde elektriksel rezerv çok küçüktür. Ayrıca hücre, bağlantı şeridi, kaynak, sıcaklık ve yaşlanma bu rezervi daha da azaltır.

**Karar:** VTC6 paketi bench/deney amaçlı tutulabilir; ilk gerçek uçuş ve güvenilir V1 için **3S LiPo 2800–3300mAh / 40C veya üstü** kullanmak daha uygundur.

> 18650 hücrelerle paket yapılacaksa yaylı holder kullanılmamalı; yüksek akım için uygun hücre bağlantısı ve profesyonel punta kaynak tercih edilmelidir.

---

## 4. RC Bağlantısında Muhtemel Eksik Parça

FS-CT6B ile kullanılan FS-R6B eski AFHDS alıcı, kanalları ayrı PWM servo çıkışları üzerinden verir. Pixhawk tarafında RC IN için toplu PPM/SBUS tipi sinyal kullanmak en temiz yöntemdir.

Bu nedenle mevcut kumanda korunacaksa:

```text
FS-R6B
CH1 ─┐
CH2 ─┤
CH3 ─┤
CH4 ─┤──► PPM Encoder ─► Pixhawk RC IN
CH5 ─┤
CH6 ─┘
```

**PPM encoder fiyatı:** yaklaşık **299–606 TL**.

Bu parça fiziksel sistemde zaten bulunuyorsa yeniden alınmayacaktır.

Alternatif olarak ileride daha yeni bir kumanda/alıcı sistemine (SBUS/iBUS/CRSF vb.) geçilebilir; fakat V1'i tamamlamak için kumanda sistemini değiştirmek şart değildir.

---

## 5. V1 Satın Alma Sırası

1. **Power module var mı?** Fiziksel kontrol.
2. **PPM encoder var mı / FS-R6B Pixhawk'a nasıl bağlı?** Fiziksel kontrol.
3. **Bir adet 3S 2800–3300mAh 40C LiPo** al.
4. Mevcut şarj cihazının modelini ve balanslı 3S desteğini doğrula.
5. Pervane sayısı ve doğru CW/CCW çiftlerini say.
6. XT60 / güç kablosu / lehim / makaron stoklarını tamamla.
7. İlk hover başarıyla bitince ikinci LiPo al.
8. LOITER/RTL/AUTO güvenilir hale gelince 433MHz telemetri ihtiyacını tekrar değerlendir.

Bu sıra, gereksiz harcamadan önce uçan platformu tamamlamaya yöneliktir.

---

## 6. V2 — Kamera / AI / Termal Donanım Bütçesi

V1 uçmadan bu parçalar alınmayacak; aşağıdaki rakamlar gelecek faz bütçe planı içindir.

| Parça | Yaklaşık 22.10.2026 fiyatı | Not |
|---|---:|---|
| Raspberry Pi 5 8GB | ~11.800–12.550 TL | Companion computer |
| Raspberry Pi Active Cooler | ~490 TL | Uçuşta zorunluya yakın |
| 5V/5A UBEC / DC-DC | ~235–760 TL | Pi'yi ana bataryadan beslemek için |
| Raspberry Pi Camera Module 3 | ~2.290–2.724 TL | RGB görüntü |
| Raspberry Pi AI Camera (IMX500) | ~5.370 TL | Kamera üzerinde AI; HAT ihtiyacını ilk prototipte azaltabilir |
| Raspberry Pi AI HAT+ 26 TOPS | ~6.000–8.333 TL | Daha ağır AI modelleri için |
| MLX90640 32x24 termal modül | ~4.020–8.390 TL | Ucuz termal prototip; düşük çözünürlük |
| FLIR Lepton 3.5 160x120 modül | ~57.000 TL | Gerçek saha termal görüntü için çok daha anlamlı ama pahalı |

### V2 için iki mantıklı yol

**Ekonomik prototip:**

- Pi 5
- Camera Module 3 veya AI Camera
- MLX90640
- 5V/5A regülatör

Yaklaşık **18.000 – 27.000 TL** ek donanım.

**Daha gerçek arama-kurtarma odaklı termal sistem:**

- Pi 5
- RGB kamera
- AI hızlandırıcı
- FLIR Lepton 3.5
- uygun regülatör / montaj

Yaklaşık **78.000 – 82.000 TL+** ek donanım.

> MLX90640 sadece 32x24 piksel olduğu için yüksek irtifadan insan bulmak için nihai sensör olarak düşünülmemelidir. Öncelikle yazılım, sensör füzyonu ve termal iş akışını geliştirmek için ekonomik prototip sensörüdür.

---

## 7. Fiyat Kaynakları — 22.10.2026

- Robotistan — F450 kırmızı/beyaz: https://www.robotistan.com/f450-govde-kiti-kirmizi-beyaz
- Robotistan — F450 kırmızı/siyah: https://www.robotistan.com/f450-govde-kiti-kirmizi-siyah
- Robotzade — Emax CF2822: https://www.robotzade.com/urun/emax-cf2822-1200kv-fircasiz-drone-motoru
- Direnc.net — ESC listesi: https://www.direnc.net/drone-motor-suruculeri
- Robotistan — Pixhawk Standart Paket: https://www.robotistan.com/ucus-kontrol-karti-elektronik-seti-otopilot
- Robotistan — Power Module listesi: https://www.robotistan.com/drone-guc-modulleri
- Orbi Elektronik — MAVLink2 Wi-Fi: https://www.orbielektronik.com/urun/pixhawk-mavlink2-antenli-kablosuz-wi-fi-telemetri-modulu
- F1Depo — FlySky CT6B/R6B: https://www.f1depo.com/urun/flysky-fs-ct6b-2-4ghz-6-kanal-rc-kumanda-seti-fs-r6b-alici-dahil
- Akakçe — Murata VTC6: https://www.akakce.com/pil/en-ucuz-sony-murata-us18650vtc6-3-7v-3120-mah-li-ion-sarjli-30a-fiyati,863186563.html
- Robotistan — 3S LiPo listesi: https://www.robotistan.com/li-po-pil
- Robocombo — Pixhawk PPM Encoder: https://robocombo.com/pixhawk-ppm-encoder-4632
- Motorobit — PPM Encoder + kablo: https://www.motorobit.com/pixhawk-ppm-encoder-modulu-enkoder-kablo-seti
- Flyonic — Holybro SiK V3: https://flyonic.com.tr/urun-etiket/433mhz-telemetri/
- Robotzade — iMAX B6AC: https://www.robotzade.com/urun/imax-b6ac-adaptorlu-profesyonel-lipo-sarj-aleti
- Murata — US18650VTC6 datasheet: https://www.murata.com/-/media/webrenewal/products/batteries/cylindrical/datasheet/us18650vtc6-product-datasheet.ashx
- Devresel — Raspberry Pi / kamera / AI: https://www.devresel.com.tr/marka/raspberry-pi
- Kompent — MLX90640: https://www.kompent.com/adafruit-mlx90640-ir-termal-kamera-karti-55-derece-1721
- SingTown/OpenMV — FLIR Lepton 3.5: https://singtown.com/tr/store/flir-lepton-module

---

## 8. Sonuç

**V1'i bitirmek için yeni bir Pixhawk, yeni motor veya yeni ESC almamız gerekmiyor.**

Önce fiziksel olarak şu üç maddeyi doğrulamalıyız:

- Power module var mı?
- PPM encoder var mı?
- LiPo balans şarj cihazının tam modeli nedir?

Bunlar doğrulandıktan sonra gerçek satın alma listesi birkaç kaleme düşecektir.
