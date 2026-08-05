<p align="center">
  <img src="assets/redrivrr-logo.png" alt="RedRiveRR GPS Spoofer" width="144">
</p>

<h1 align="center">RedRiveRR GPS Spoofer</h1>

<p align="center">
  <a href="https://github.com/RedRiveRR/RedRiveRR-GPS-Spoofer/releases/tag/v1.1.0-rc.3"><img alt="Sürüm" src="https://img.shields.io/badge/release-v1.1.0--rc.3-black?style=for-the-badge"></a>
  <img alt="Lisans" src="https://img.shields.io/badge/lisans-kapal%C4%B1%20kaynak-black?style=for-the-badge">
  <img alt="macOS" src="https://img.shields.io/badge/macOS-12.7%2B-black?style=for-the-badge&logo=apple">
  <img alt="Mimariler" src="https://img.shields.io/badge/Universal-Intel%20%2B%20Apple%20Silicon-black?style=for-the-badge">
</p>

> RedRiveRR GPS Spoofer tescilli, kapalı kaynak bir yazılımdır. Bu repo resmi binary dağıtım sayfasıdır; kaynak kod sunmaz ve lisansta açıkça izin verilen durumlar dışında yazılımı kopyalama, değiştirme, tersine mühendislik veya yeniden dağıtma izni vermez.

[English](README.en.md) · [Sürüm notları](CHANGELOG.md) · [Güvenlik](SECURITY.md) · [Lisans](LICENSE)

## Güncel Sürüm

`1.1.0-rc.3`, Intel ve Apple Silicon Mac'ler için bir ön sürüm release candidate paketidir. Kararlı sürüm değildir.

- [Universal DMG dosyasını indir](https://github.com/RedRiveRR/RedRiveRR-GPS-Spoofer/releases/download/v1.1.0-rc.3/RedRiveRR-GPS-Spoofer-1.1.0-rc.3-universal.dmg)
- [SHA-256 doğrulama dosyasını indir](https://github.com/RedRiveRR/RedRiveRR-GPS-Spoofer/releases/download/v1.1.0-rc.3/RedRiveRR-GPS-Spoofer-1.1.0-rc.3-universal.dmg.sha256)

Yayımlanan SHA-256:

```text
146f0edb94a482e62d953fd9982f5d6f2a0b98c6ce7a9b35fabee1f84be38ffa
```

## Gereksinimler

| Bileşen | Gereksinim |
| --- | --- |
| macOS | 12.7 veya sonrası |
| Mac | Intel veya Apple Silicon |
| iPhone | Developer Mode açık olmalı |
| Bağlantı | Kilidi açık, güvenilmiş USB bağlantısı önerilir |
| iOS | iOS 17.4 ve sonrası userspace desteği; iOS 17.0-17.3.x desteklenmez |
| Runtime | Sağlıklı app-managed runtime yoksa uyumlu Python 3 gerekir |

Jailbreak, root erişimi, `sudo`, yönetici AppleScript'i veya kalıcı kernel tunnel gerekmez.

## Kurulum

1. DMG ve doğrulama dosyasını Release sayfasından indirin.
2. Terminal'de checksum değerini doğrulayın:

   ```bash
   shasum -a 256 RedRiveRR-GPS-Spoofer-1.1.0-rc.3-universal.dmg
   ```

3. DMG dosyasını açın ve **RedRiveRR GPS Spoofer** uygulamasını **Applications** klasörüne sürükleyin.
4. Uygulamayı açın, iPhone'u bağlayıp güvenin ve hedef cihazı uygulamada açıkça seçin.

RC3 imzasızdır ve Apple notarization işlemi yapılmamıştır. Son Apple dağıtım kimlik bilgileri ve fiziksel UI doğrulaması tamamlanırken değerlendirme amacıyla sunulur.

## macOS Gatekeeper Uyarısı

RC3, Apple tarafından verilmiş bir Developer ID sertifikasıyla imzalanmamıştır ve Apple notarization işleminden geçmemiştir. Bu nedenle güncel DMG açılırken macOS geliştiricinin doğrulanamadığını veya uygulamanın kötü amaçlı yazılım içerip içermediğinin denetlenemediğini söyleyen uyarıyı gösterir. Bu uyarı, Gatekeeper'ın uygulama için kullanılabilir bir imza veya notarization bileti bulamadığı anlamına gelir; macOS'un uygulamayı kötü amaçlı yazılıma karşı denetleyip onayladığı anlamına gelmez.

Yalnızca DMG dosyasını resmi RedRiveRR GitHub Release sayfasından indirdiyseniz ve SHA-256 değeri yukarıda yayımlanan değerle eşleşiyorsa devam edin.

Güncel RC sürümünü Apple'ın desteklediği güvenlik istisnası akışıyla açmak için:

1. Uyarı penceresinde **Vazgeç** veya **Bitti** seçeneğini seçin. Uygulamayı Çöp Sepeti'ne taşımayın.
2. macOS Ventura 13 veya sonrasında **Sistem Ayarları → Gizlilik ve Güvenlik** bölümünü açın. macOS Monterey 12'de **Sistem Tercihleri → Güvenlik ve Gizlilik → Genel** bölümünü açın ve istenirse kilit simgesini açın.
3. RedRiveRR GPS Spoofer için **Yine de Aç** seçeneğine basın.
4. İstendiğinde Mac giriş parolanız veya Touch ID ile doğrulama yapın.
5. Uyarı yeniden gösterildiğinde **Aç** seçeneğini seçin.

Apple'a göre **Yine de Aç** seçeneği engellenen açma denemesinden sonra yaklaşık bir saat kullanılabilir. Seçenek görünmüyorsa uygulamayı bir kez daha açmayı deneyip Gizlilik ve Güvenlik sayfasına geri dönün. Şirket veya okul tarafından yönetilen Mac'lerde bu istisna engellenebilir.

Gatekeeper'ı kapatmayın ve Terminal komutlarıyla quarantine niteliğini kaldırmayın. Bu genel yöntemler macOS korumasını zayıflatır ve desteklenen kurulum sürecinin parçası değildir. Apple'ın [Mac'inizde uygulamaları güvenle açma](https://support.apple.com/en-gb/102445) yönergesine bakabilirsiniz.

Kalıcı yayıncı çözümü; Apple Developer Program erişimi edinmek, yeni sürümü Apple **Developer ID Application** sertifikası, Hardened Runtime ve güvenli timestamp ile imzalamak, Apple notary servisine göndermek ve notarization biletini DMG'ye staple etmektir. Sürüm yayımlanmadan önce `codesign`, `stapler` ve Gatekeeper kontrollerinden geçmelidir. Apple bu dağıtım modelini [Developer ID sertifikaları](https://developer.apple.com/help/account/certificates/create-developer-id-certificates) ve [notarization sorunlarını çözme](https://developer.apple.com/documentation/security/resolving-common-notarization-issues) belgelerinde açıklar. Doğru şekilde imzalanıp notarize edilmiş yeni bir paket, bu doğrulanamayan geliştirici uyarısı olmadan normal macOS onay akışıyla açılmalıdır.

## Runtime Kurulumu

Uygulama kendi `pymobiledevice3` ortamını kurar ancak Python'ı kendisi kurmaz.

Uyumlu Python 3 zaten varsa uygulama:

- `~/Library/Application Support/RedRiveRR GPS Spoofer/Runtime/venv` içinde izole bir virtual environment oluşturabilir;
- bu ortama `pymobiledevice3==10.3.0`, `urllib3<2`, `cryptography<47` ve bağımlılıklarını kurabilir;
- macOS socket-buffer uyumluluk düzeltmesini uygulayıp doğrulayabilir ve bundled konum oturumu helper'ını doğrulayabilir;
- kurulumu root, `sudo`, yönetici yetkisi, Homebrew değişikliği, global pip kurulumu veya user-site paket değişikliği olmadan tamamlayabilir.

Bu davranış uyumlu Xcode Python 3.9.6 bulunan Intel bir Mac'te doğrulandı. App-managed runtime bulunmadan yapılan açılışta uygulama sıfırdan ortam oluşturdu, sabitlenmiş paketi kurdu, 7 MiB socket-buffer fallback uyguladı ve yaklaşık 2 dakika 16 saniyede `ready` durumuna ulaştı. Kurulum süresi Mac'e ve ağ/cache durumuna göre değişir.

### İlk Runtime Kurulumu

1. Mac'i internete bağlı tutun ve uygulamayı açın.
2. **Environment Setup** Python'ı kontrol edip managed runtime oluştururken uygulamayı açık bırakın. Bu işlem birkaç dakika sürebilir.
3. Kurulum başlamazsa veya durum sağlıklı hale gelmezse **Install Managed Runtime** seçeneğine basın. Yarım kalmış ya da uyumsuz kurulum için **Repair Runtime** kullanın.
4. Durumun `ready`, `pymobiledevice3 10.3.0`, doğru Mac mimarisi ve başarılı userspace DVT/socket-buffer kontrollerini göstermesini bekleyin.
5. Runtime hazır olduktan sonra iPhone'u bağlayın, cihaz listesini yenileyin ve hedef cihazı açıkça seçin.

Elle `pip install pymobiledevice3` çalıştırmayın, paketi global olarak kurmayın ve `sudo` kullanmayın. Eski bir kullanıcı kurulumu uyumsuz olabilirken uygulamanın yönettiği runtime düzgün çalışabilir.

### Python Bulunmayan Mac

Güncel DMG bağımsız bir Python runtime içermez. Uyumlu Python 3 bulunmayan gerçekten temiz bir Mac'te otomatik bağımlılık kurulumu başlayamaz. Önce uyumlu bir Python 3 dağıtımı kurun, uygulamayı yeniden açın, **Check Again** seçeneğine basın ve uygulamanın managed runtime oluşturmasına izin verin. Bu durum release candidate sınırlaması olmaya devam eder; gelecekte tamamen bağımsız DMG için imzalanmış bundled Python runtime veya derlenmiş native helper gerekir.

### Temiz Yeniden Kurulum Testi

Sistem araçlarını değiştirmeden managed installer'ı yeniden test etmek için:

1. Aktif konum oturumunu durdurun ve RedRiveRR GPS Spoofer uygulamasını normal şekilde kapatın.
2. Yalnızca `~/Library/Application Support/RedRiveRR GPS Spoofer/Runtime` klasörünü Çöp Sepeti'ne taşıyın.
3. `/usr/bin/python3`, Xcode Python, Homebrew Python, RedRiveRR Application Support klasörünün tamamı, Keychain öğeleri, geçmiş veya favorileri silmeyin.
4. Uygulamayı yeniden açın ve yukarıdaki **İlk Runtime Kurulumu** adımlarını izleyin.

Runtime klasörünü kaldırmak uygulamanın yönettiği Python paketlerini siler. Uygulamayı kaldırmaz; kayıtlı geçmişi ve favorileri silmez.

## Kullanım Ve Güvenlik

- Apply, açıkça seçilmiş cihaz için userspace konum oturumu başlatır.
- Koordinat güncellemeleri oturum çalışırken uygulamanın yönettiği aynı oturumu kullanır.
- Stop, Clear komutunu gönderir ve uygulamanın yönettiği oturumu kapatır.
- Clear, Stop ve güvenlik temizliği lisans durumundan bağımsız olarak kullanılabilir kalır.
- Clear komutunun tamamlanması iPhone'un fiziksel GPS durumunu bağımsız olarak kanıtlamaz. Gerçek konumun döndüğünü Apple Maps veya Compass üzerinden doğrulayın.

## Ağ Ve Gizlilik

- Konum komutları seçilen cihaza yerel olarak gönderilir.
- Apple MapKit harita verisi indirebilir.
- Runtime kurulumu sabitlenmiş paketleri ve bağımlılıkları indirebilir.
- Güncelleme kontrolü public GitHub sürüm bilgisini sorgulayabilir.
- Bu release candidate içinde production ödeme ve lisanslama aktif değildir.

## Destek

Tekrarlanabilir ürün sorunları için [GitHub Issues](https://github.com/RedRiveRR/RedRiveRR-GPS-Spoofer/issues) sayfasını kullanın. Lisans anahtarı, cihaz kimliği, kişisel konum verisi, secret içeren log veya başka özel bilgiler paylaşmayın. Güvenlik sorunlarını [SECURITY.md](SECURITY.md) içindeki özel bildirim yöntemiyle iletin.

## Lisans

Copyright © 2024-2026 RedRiveRR. Tüm hakları saklıdır. Bu yazılım tescilli ve kapalı kaynaktır. Ayrıntılar için [LICENSE](LICENSE) dosyasına bakın.
