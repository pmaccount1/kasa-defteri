# Kasa Defteri

Şahsi ön muhasebe: müşteri ve firma carileri, stok kartları, satış/alış (sipariş) kayıtları, TL/USD/EUR kasa ve banka, cari ekstre, vade ve kritik stok takibi. Aynı kod hem Android uygulaması (APK) hem masaüstü (tarayıcıda, kurulabilir uygulama) olarak çalışır.

## APK'yi almanın en kolay yolu (bilgisayara bir şey kurmadan)

1. github.com'da yeni, boş bir depo açın (örn. `kasa-defteri`).
2. Bu klasördeki her şeyi (gizli `.github` klasörü dahil) depoya yükleyin. En kolayı: depo sayfasında **Add file → Upload files**, sonra klasörün içeriğini sürükleyip bırakın. `.github` klasörü sürüklemede görünmezse GitHub Desktop kullanın.
3. **Settings → Pages → Build and deployment → Source: GitHub Actions** seçin (masaüstü sürümü için).
4. **Actions** sekmesinde "APK ve masaustu surumu" iş akışı otomatik başlar (başlamazsa **Run workflow**). 5–8 dakika sürer.
5. Bitince **Releases** bölümünde `KasaDefteri.apk` çıkar. Telefondan indirip kurun ("Bilinmeyen kaynaklara izin ver" onayı istenir).

Kodu her değiştirip yüklediğinizde yeni bir APK kendiliğinden üretilir.

## Masaüstünde kullanım

- **GitHub Pages ile:** Adım 3'ü yaptıysanız uygulama `https://KULLANICIADI.github.io/kasa-defteri/` adresinde yayında olur. Chrome veya Edge'de açıp adres çubuğundaki **Uygulamayı yükle** simgesine basın; masaüstünde kendi penceresinde, internetsiz de açılır.
- **Hiç kurulum olmadan:** `www/index.html` dosyasına çift tıklayın, tarayıcıda açılır.

Not: Veriler her cihazın kendi içinde saklanır. Telefon ile bilgisayar arasında taşımak için **Yedek** sekmesinden yedek alıp diğerinde geri yükleyin.

## Kendi bilgisayarında derlemek (isteğe bağlı)

Node.js 22+, JDK 21 ve Android Studio gerekir.

```
npm install
npm run apk
```

APK: `android/app/build/outputs/apk/debug/app-debug.apk`. Android Studio ile açmak için: `npx cap open android`.

## Uygulamayı değiştirmek

Tüm uygulama `www/index.html` içindedir. Değiştirdikten sonra `npx cap sync android` (ya da GitHub'a yükleyin, iş akışı kendisi yapar).

## Play Store'a koymak isterseniz

Buradaki APK "debug" imzalıdır; kendi telefonunuzda ve dağıtımda sorunsuz çalışır ama Play Store imzalı "release" derleme ister. Android Studio'da **Build → Generate Signed Bundle** ile yapılır.
