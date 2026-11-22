# ComboBox Erişilebilirlik Testleri

Aranabilir ve bağımlı il–ilçe alanlarını iOS VoiceOver ve Android TalkBack ile karşılaştırmak için hazırlanmış statik HTML test reposu.

## Başlatma

VS Code ile klasörü açın; Live Server üzerinden `index.html` dosyasını çalıştırın. Alternatif: `python -m http.server 5500` ve `http://localhost:5500`.

## Dosyalar

| Dosya | Kütüphane | Önceki iPhone VoiceOver gözlemi |
| --- | --- | --- |
| `kendo.html` | Kendo UI Core | Çalıştı; `popup.appendTo` ile popup ilgili alanın yanında |
| `govuk.html` | GOV.UK Accessible Autocomplete | Çalıştı; ComboBox'lar bir kez oluşturuluyor, ilçe `source` fonksiyonuyla değişiyor |
| `selectize.html` | Selectize.js | Sonuç ayrıca doğrulanmalı |
| `aria.html` | aria-autocomplete | Liste açılıyor, seçenekler VoiceOver tarafından okunmadı |
| `trevor.html` | Trevor Eyre Autocomplete | Liste açılıyor, seçenekler VoiceOver tarafından okunmadı |

Bu gözlemler belirli test oturumlarına aittir; evrensel uyumluluk veya WCAG uygunluğu kanıtı değildir.

## Test senaryosu

1. Ekran okuyucuyu açın; il alanının adını ve rolünü dinleyin.
2. Listeyi açın; sağa/sola kaydırarak seçeneklerin okunup okunmadığını test edin.
3. Ankara → Çankaya seçin.
4. İl seçimini İstanbul olarak değiştirin; önceki ilçenin temizlendiğini doğrulayın.
5. İstanbul → Şişli seçin. Türkçe karakterlerle aramayı deneyin.
6. Klavye, odak, geri/ileri gezinme, liste kapanması ve sonuç bildirimini kontrol edin.

## Kayıt şablonu

| Tarih | Cihaz / OS | Tarayıcı | Ekran okuyucu | Kütüphane | Seçenekler okunuyor mu? | Bağımlılık doğru mu? | Not |
| --- | --- | --- | --- | --- | --- | --- | --- |
| | | | | | | | |

## Teknik notlar

- Dış CDN bağlantısı gerekir; test öncesi ağ erişimini kontrol edin.
- Kendo testinde jQuery 3.7.1 kullanılır.
- GOV.UK testinde React/jQuery gerekmez.
- İl/ilçe verileri demo amaçlıdır, Türkiye'nin tüm idari birimlerini kapsamaz.
- `govuk.html` önceki başarılı örneğin mantığını korur; ilçe input'una `input` olayı göndererek temizleme davranışı ayrıca test edilmelidir.
- Kütüphanelerin lisansları ve sürüm uygunluğu üretim öncesinde ayrıca kontrol edilmelidir.
