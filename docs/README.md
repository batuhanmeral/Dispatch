# ESMS Dokümantasyonu (Güncel)

Bu klasör, sistemin **mevcut** durumunu anlatan sadeleştirilmiş dokümantasyondur.

## Sistem Özeti

Enterprise Service Management System (ESMS), kurum içi talep/bilet yönetimi için geliştirilmiş bir Django uygulamasıdır.

- Uygulamalar: `identity`, `departments`, `tickets`, `notifications`, `reports`, `dashboard`
- Mimari: SSR (Django Template) + sınırlı REST API
- Veritabanı: PostgreSQL
- Kimlik modeli: `AUTH_USER_MODEL = identity.User`
- Roller: `EMPLOYEE`, `AGENT`, `MANAGER`, `ADMIN`

## Güncel URL Yapısı

### SSR

- `/` → Dashboard
- `/identity/` → Giriş, kayıt, profil, kullanıcı yönetimi
- `/departments/` → Departman/kategori yönetimi
- `/tickets/` → Bilet yönetimi
- `/notifications/` → Bildirimler
- `/reports/` → Rapor ekranı + export
- `/admin/` → Django admin

### API (mevcut)

Sistemde API katmanı artık sadece ticket süreçleri için aktiftir:

- `/api/v1/tickets/`
- `/api/v1/tickets/<pk>/`
- `/api/v1/tickets/<pk>/take/`
- `/api/v1/tickets/<pk>/close/`
- `/api/v1/tickets/<pk>/transfer/`
- `/api/v1/tickets/<pk>/reopen/`
- `/api/v1/tickets/<pk>/comments/`

### API Dokümantasyonu

- `/api/v1/schema/`
- `/api/v1/docs/`
- `/api/v1/redoc/`

## Temel Özellikler

- Rol bazlı erişim kontrolü (RBAC)
- Bilet yaşam döngüsü: `OPEN -> IN_PROGRESS -> CLOSED` (+ reopen/transfer)
- Yorum, etiket ve dosya ekleri
- Bildirim üretimi ve okunma yönetimi
- Rapor ekranı ve dışa aktarım (CSV, XLSX, PDF)
- i18n (TR/EN) ve dark mode desteği

## Notlar

- `reports` uygulamasında aktif model bulunmamaktadır; raporlama view tabanlı çalışır.
- API kapsamı bilinçli şekilde daraltılmıştır; identity/departments/notifications/reports/dashboard için API endpoint yoktur.
