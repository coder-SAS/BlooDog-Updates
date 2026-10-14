# BlooDog — Releases

Bu depo **yalnızca dağıtım verisi** içerir. Kaynak kod burada değildir.

İçerik:

| Dosya | Ne |
|---|---|
| `status.json` | Güncel sürümün sürüm numarası, indirme adresi, SHA-256 karması ve boyutu |

## Nedir bu

BlooDog, Counter-Strike 2 için **harici** bir görüntü katmanı (ESP) uygulamasıdır.
Oyun sürecine hiçbir kod enjekte etmez; ayrı bir süreç olarak çalışır, oyunun
belleğini okur ve kendi penceresinde çizim yapar.

Kaynak proje: [IMXNOOBX/cs2-external-esp](https://github.com/IMXNOOBX/cs2-external-esp)
— CC BY-NC 4.0 lisanslı, orijinal yazar ve katkıda bulunanlara aittir.

## Ne işe yarar

`status.json`, uygulamanın kendini güncellemesi için okuduğu dosyadır.
Uygulama açılışta bu dosyayı çeker, sürüm numarasını kendi sürümüyle karşılaştırır,
farklıysa indirir, **indirilen baytların SHA-256 karmasını `status.json` içindeki
karmayla karşılaştırır** ve ancak eşleşirse kurar.

Yani iki şey açıktır:

- Uygulama, manifest'te yazan adresten başka bir yerden dosya çekmez.
- Dosya beklenen karmayla birebir aynı değilse hiç kurulmaz.

Bu sağlamalardan biri olmasa güncelleme özelliği çalışmaz.

## Kim kullanabilir

Bu depo **kendi kendini güncelleme** özelliği olan sürümleri dağıtır ve
`publish_release.ps1` betiği kullanılmadan yüklenmemelidir — betik, sürüm
numarasını artırmadan yayın yapmayı reddeder.

## Sorumluluk

**Bu bir eğitim ve test amaçlı çalışmadır.** Kod ve yayınlar olduğu gibi sunulur,
hiçbir garanti verilmez.

Çevrimiçi rekabetçi maçlarda ESP kullanmak, oyunun hizmet şartlarını ihlal eder
ve hesabın askıya alınmasına yol açabilir. Bu yazılımı hangi koşulda
kullanacağınıza karar vermek ve sonucunu taşımak size aittir.

Valve, Steam veya Counter-Strike ile hiçbir ilişkisi yoktur; bu depodaki hiçbir
içerik onlar tarafından desteklenmemektedir.

## İçerik değiştirme

Bu depoyu kendi hesabınızda fork edip kullanabilirsiniz. Dikkat edilmesi gereken
tek şey, `status.json` içindeki `sha256` ve `url` alanlarının gerçekten gösterdiği
dosyaya ait olması — aksi halde uygulama güncellemeyi reddeder.