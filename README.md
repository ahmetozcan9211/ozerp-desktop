# OZERP Desktop: Kendi DSL Diline Sahip Masaüstü ERP

Ekranların ve modüllerin kod yazmadan, **özel bir alan diliyle (DSL)** tanımlandığı; çok firmalı, çok tesisli ve çok depolu modüler masaüstü ERP platformu.

> Bu depo bir proje vitrinidir. Kaynak kod paylaşılmamaktadır.

## Fikir

Klasik ERP'lerde her yeni ekran için geliştirici gerekir. OZERP'te bir modül, menü, ekran ve alanlar birkaç satırlık DSL ile tanımlanır; çalışma anında JavaFX formuna ve veritabanı işlemlerine dönüştürülür.

```
MODULE StokModulu LABEL "Stok Yönetimi"
  MENU "Tanımlar"
    ITEM "Malzeme Kartı" SCREEN MalzemeKarti
  SCREEN MalzemeKarti TABLE materials PRIMARY code
    FIELD code  TEXT    LABEL "Malzeme Kodu" REQUIRED
    FIELD name  TEXT    LABEL "Açıklama"
    FIELD price DECIMAL LABEL "Birim Fiyat"
```

## DSL motoru

- **El yazısı lexer** ve **recursive descent parser** (parser üreteci kullanılmadı)
- Anlamsal doğrulayıcı: tablo ve alan varlığı, tip uyumu, zorunlu alanlar
- Çalışma zamanı: DSL → dinamik JavaFX formu + CRUD işlemleri
- Lexer, parser, doğrulayıcı ve çalışma zamanı için ayrı birim testleri

## Platform

- Çok firma, çok tesis ve çok depo yapısı
- Rol tabanlı yetkilendirme, BCrypt ile şifreleme
- Barkod ve QR üretimi, PDF çıktı
- Flyway ile sürümlü veritabanı migrasyonları

## Teknolojiler

`Java 21` · `JavaFX 21` · `Maven` · `PostgreSQL 16` · `Hibernate 6 / JPA` · `HikariCP` · `Flyway` · `ZXing` · `PDFBox` · `JUnit 5` · `Mockito` · `Docker`
