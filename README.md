# Kütüphane Otomasyon Sistemi

Bu proje, C++ Qt kütüphanesi kullanılarak geliştirilmiş bir kütüphane otomasyon sistemidir. Kütüphane üyelerini, kitapları ve ödünç alma ile iade etme işlemlerini yönetir. Proje, veri depolama ve geri çağırma işlemleri için veri tabanı entegrasyonu içermektedir.

## Özellikler

1. **Giriş Ekranı**
   - Veri tabanına başarıyla bağlanıldığını belirten mesaj statüs-bar'da gösterilir.
   - Üye İşlemleri, Kitap İşlemleri ve Ödünç Alma/İade İşlemleri ekranlarına gitmek için butonlar bulunur.
  ![image](https://github.com/metinncetinn/QtOtomasyon/assets/110323658/de59214e-aeed-42a3-94eb-afccf3872ae3)

2. **Üye İşlemleri**
   - Tablodaki bir üyeye tıklandığında, üyenin bilgileri yan taraftaki alanlara aktarılır.
   - **Yeni Kayıt**: Girilen bilgilere göre veri tabanına yeni üye ekler ve tabloyu günceller. Alanlar boş ise uyarı verir.
   - **Güncelle**: Girilen bilgilere göre üye bilgilerini günceller ve tabloyu yeniler.
   - **Sil**: Seçilen üyeyi siler, ancak üyenin iade edilmemiş kitabı varsa silme işlemi yapılmaz. Tablo güncellenir.
  ![image](https://github.com/metinncetinn/QtOtomasyon/assets/110323658/111e2440-fc49-44fb-8ff4-b28e0a8e7e7d)

3. **Kitap İşlemleri**
   - Üstteki tabloda tüm kitaplar listelenir. Bir kitaba tıklandığında, o kitabın mevcut ve geçmiş ödünç alma kayıtları alt tablolarda gösterilir.
   - **Yeni Kayıt**: Girilen bilgilere göre veri tabanına yeni kitap ekler ve tabloyu günceller. Alanlar boş ise uyarı verir.
   - **Güncelle**: Kitap bilgilerini günceller ve tabloyu yeniler.
   - **Sil**: Seçilen kitabı siler, ancak kitap ödünç verilmişse silinmez. Tablo güncellenir.
  ![image](https://github.com/metinncetinn/QtOtomasyon/assets/110323658/a88b9007-4862-4ab7-8f9c-3468d6a00357)

4. **Ödünç Alma İşlemleri**
   - Üst soldaki tabloda tüm üyeler, üst sağdaki tabloda tüm kitaplar, alttaki tabloda ise mevcut ödünç alınmış kitaplar listelenir.
   - **Ödünç Al**: Üye ve kitap numaraları ile ödünç alma tarihine göre `odunc_alinan` tablosuna kayıt ekler. Kitap stoğu ve üyenin kitabı daha önce alıp almadığı kontrol edilir.
  ![image](https://github.com/metinncetinn/QtOtomasyon/assets/110323658/bacebe79-f1f6-4e15-a620-b710c9575e92)

5. **Ödünç Teslim Etme İşlemleri**
   - Sol tarafta mevcut ödünç alınan kitaplar, sağ tarafta ise teslim edilen kitaplar listelenir.
   - **Ödünç Ver**: Seçilen kaydı `odunc_alinan` tablosundan `odunc_teslim_edilen` tablosuna taşır, teslim tarihini kaydeder ve borç hesaplaması yapar. Tablolar güncellenir.
  ![image](https://github.com/metinncetinn/QtOtomasyon/assets/110323658/46edd90c-ca9b-42a4-91a7-ce494954e291)

## Veri Tabanı Şeması

- **Üye Tablosu (`uye`)**:
  - `uye_no` (int)
  - `uye_ad` (text)
  - `uye_soyad` (text)

- **Kitap Tablosu (`kitap`)**:
  - `kitap_no` (int)
  - `kitap_ad` (text)
  - `kitap_sayisi` (int)

- **Ödünç Alınan Kitaplar Tablosu (`odunc_alinan`)**:
  - `uye_no` (int)
  - `kitap_no` (int)
  - `odunc_alma_tarihi` (text)

- **Ödünç Teslim Edilen Kitaplar Tablosu (`odunc_teslim_edilen`)**:
  - `uye_no` (int)
  - `kitap_no` (int)
  - `alma_tarihi` (text)
  - `verme_tarihi` (text)
  - `borc` (int)
