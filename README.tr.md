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

Güncel DMG bağımsız bir Python runtime içermez. Uyumlu Python 3 bulunmayan temiz bir Mac'te önce Python 3 kurun, uygulamayı yeniden açın ve managed-runtime kurulum ya da onarım akışını kullanın. Uygulamanın yönettiği ortam `pymobiledevice3==10.3.0` sürümünü kullanır ve yönetici yetkisi gerektirmez.

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
