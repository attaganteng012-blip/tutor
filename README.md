Panduan Lengkap Web Security Testing: Manual, Otomatis, OWASP, dan Pelaporan

«Metodologi, Langkah Praktis, dan Template Laporan»

Target/Organisasi: "[Nama Target/Organisasi]"
Tanggal: "[Tanggal]"
Disusun oleh: "[Disusun oleh]"

«[!WARNING]
Disclaimer Legal: Seluruh teknik dalam dokumen ini hanya boleh dilakukan pada sistem milik sendiri, lab pribadi, atau target yang memiliki izin tertulis. Tanpa izin, tindakan ini dapat masuk pidana.»

---

📚 Daftar Isi

- "1. Pengertian Lengkap" (#1-pengertian-lengkap)
  - "1.1 Definisi Web Security Testing" (#11-definisi-web-security-testing)
  - "1.2 Tujuan dan Manfaat" (#12-tujuan-dan-manfaat)
  - "1.3 Manual vs Otomatis" (#13-perbedaan-scanning-manual-vs-otomatis)
  - "1.4 OWASP WSTG v4.2" (#14-owasp-wstg-v42)
  - "1.5 OWASP Top 10:2025" (#15-owasp-top-102025)
- "2. Scanning Manual" (#2-scanning-manual--step-by-step)
  - "Step 1 — Reconnaissance" (#step-1--reconnaissance--application-mapping)
  - "Step 2 — Authentication" (#step-2--authentication-testing)
  - "Step 3 — Authorization" (#step-3--authorization-testing)
  - "Step 4 — Input Validation" (#step-4--input-validation--injection-testing)
  - "Step 5 — Session Management" (#step-5--session-management-testing)
  - "Step 6 — Business Logic" (#step-6--business-logic-testing)
- "3. Scanning Otomatis" (#3-scanning-otomatis--step-by-step)
- "4. Pemetaan OWASP Top 10" (#4-pemetaan-ke-owasp-top-10)
- "5. Pelaporan" (#5-cara-membuat-laporan-lengkap-pdf--word)
- "6. Ringkasan Alur" (#6-ringkasan-alur-lengkap)
- "Lampiran" (#lampiran)
- "Referensi" (#referensi)
- "Glosarium" (#glosarium)

---

1. Pengertian Lengkap

1.1 Definisi Web Security Testing

Web Security Testing adalah proses sistematis untuk memeriksa keamanan aplikasi web, API, konfigurasi server, authentication, authorization, session management, input pengguna, serta business logic.

Tujuan utamanya adalah menemukan kelemahan keamanan sebelum kelemahan tersebut disalahgunakan.

Pengujian keamanan yang profesional harus memiliki:

- Scope yang jelas
- Target yang diizinkan
- Waktu pengujian
- Akun testing
- Batasan aktivitas
- Metodologi
- Dokumentasi
- Prosedur pelaporan

Contoh scope:

Target:
https://[LAB_TARGET]

Diizinkan:
- Web application
- API /api/*
- Akun testing

Tidak diizinkan:
- DoS/DDoS
- Social engineering
- Pengujian terhadap pengguna lain
- Penghapusan data produksi
- Akses sistem di luar scope

---

1.2 Tujuan dan Manfaat

Tujuan

Web Security Testing bertujuan untuk:

- Menemukan vulnerability.
- Memeriksa authentication.
- Memeriksa authorization.
- Memeriksa session management.
- Menguji input validation.
- Mengidentifikasi security misconfiguration.
- Menguji business logic.
- Menemukan informasi sensitif yang terekspos.
- Memberikan rekomendasi perbaikan.
- Melakukan retesting setelah vulnerability diperbaiki.

Manfaat

Manfaat untuk developer:

- Mengetahui bagian kode yang perlu diperbaiki.
- Memahami akar masalah vulnerability.
- Meningkatkan secure coding.

Manfaat untuk organisasi:

- Mengurangi risiko keamanan.
- Mengurangi kemungkinan kebocoran data.
- Meningkatkan monitoring.
- Meningkatkan keamanan deployment.
- Membantu memenuhi requirement keamanan.

---

1.3 Perbedaan Scanning Manual vs Otomatis

Manual Testing

Manual testing dilakukan dengan menganalisis aplikasi dan mencoba berbagai kondisi secara langsung.

Contoh:

Browser
   ↓
Proxy
   ↓
Request
   ↓
Manipulasi parameter
   ↓
Response
   ↓
Analisis

Kelebihan:

- Memahami konteks aplikasi.
- Cocok untuk business logic.
- Dapat menemukan authorization flaw yang kompleks.
- Dapat melakukan validasi false positive.

Kekurangan:

- Membutuhkan waktu.
- Membutuhkan pengetahuan.
- Hasil dapat bergantung pada pengalaman tester.

Automated Testing

Automated testing menggunakan tool untuk melakukan pemeriksaan berdasarkan rule atau template.

Contoh:

- Nuclei
- OWASP ZAP
- Burp Scanner
- Nikto
- sqlmap

Kelebihan:

- Cepat.
- Repeatable.
- Cocok untuk baseline scan.
- Dapat menghasilkan output terstruktur.

Kekurangan:

- False positive.
- False negative.
- Tidak selalu memahami business logic.
- Hasil tetap membutuhkan validasi manusia.

Metode yang disarankan

Automated Discovery
        ↓
Manual Validation
        ↓
Risk Assessment
        ↓
Reporting
        ↓
Remediation
        ↓
Retesting

---

1.4 OWASP WSTG v4.2

OWASP Web Security Testing Guide (WSTG) adalah panduan metodologi untuk melakukan pengujian keamanan aplikasi web.

Kategori utama WSTG meliputi:

Kode| Kategori
INFO| Information Gathering
CONF| Configuration and Deployment Management Testing
IDNT| Identity Management Testing
AUTHN| Authentication Testing
AUTHZ| Authorization Testing
SESS| Session Management Testing
INPV| Input Validation Testing
ERRH| Error Handling Testing
CRYP| Cryptography
BUSL| Business Logic Testing
CLNT| Client-side Testing
API| API Testing

WSTG sebaiknya digunakan sebagai checklist metodologi, bukan hanya kumpulan payload.

Contoh authentication testing:

Login
 ↓
Credential policy
 ↓
Rate limiting
 ↓
Session creation
 ↓
MFA
 ↓
Password reset
 ↓
Logout
 ↓
Session invalidation

---

1.5 OWASP Top 10:2025

OWASP Top 10:2025 merupakan daftar kategori risiko keamanan aplikasi web dari OWASP.

Rank| Kategori
A01| Broken Access Control
A02| Security Misconfiguration
A03| Software Supply Chain Failures
A04| Cryptographic Failures
A05| Injection
A06| Insecure Design
A07| Authentication Failures
A08| Software or Data Integrity Failures
A09| Security Logging and Alerting Failures
A10| Mishandling of Exceptional Conditions

Perubahan dari 2021

2025| Perubahan
A01| Tetap di posisi #1 dan mencakup SSRF
A02| Naik dari #5
A03| Memperluas kategori vulnerable/outdated components
A04| Turun dari #2
A05| Turun dari #3
A06| Turun dari #4
A07| Nama berubah menjadi Authentication Failures
A08| Tetap di posisi #8
A09| Nama berubah dan menekankan alerting
A10| Kategori baru

---

A01:2025 — Broken Access Control

Terjadi ketika aplikasi gagal membatasi akses user terhadap resource atau fungsi.

Contoh konsep:

User A → Object A → Allowed

User B → Object A → Should be denied

Jika User B dapat mengakses Object A tanpa authorization yang sesuai, terdapat indikasi Broken Access Control.

Contoh umum:

- IDOR
- Horizontal privilege escalation
- Vertical privilege escalation
- Missing authorization
- SSRF

---

A02:2025 — Security Misconfiguration

Contoh:

- Debug mode aktif.
- Default credentials.
- Directory listing.
- Error message terlalu detail.
- Security header tidak sesuai.
- Service yang tidak diperlukan aktif.
- Konfigurasi cloud terlalu permisif.

---

A03:2025 — Software Supply Chain Failures

Mencakup risiko pada software supply chain.

Contoh:

- Dependency tidak dikelola.
- Dependency rentan.
- Package dari sumber tidak tepercaya.
- CI/CD tidak aman.
- Build artifact tidak diverifikasi.
- Repository tidak dilindungi.

---

A04:2025 — Cryptographic Failures

Contoh:

- Password storage tidak aman.
- Transport protection tidak memadai.
- Algoritma kriptografi tidak sesuai.
- Secret/key dikelola dengan buruk.
- Data sensitif tidak terlindungi.

---

A05:2025 — Injection

Injection terjadi ketika input pengguna dapat memengaruhi interpreter atau query secara tidak semestinya.

Contoh:

- SQL Injection
- XSS
- Command Injection
- NoSQL Injection
- LDAP Injection
- Template Injection

---

A06:2025 — Insecure Design

Masalah keamanan berasal dari desain sistem.

Contoh:

Frontend melakukan validasi
        ↓
Server tidak melakukan validasi
        ↓
Business rule dapat dilewati

Security harus dipertimbangkan sejak tahap desain.

---

A07:2025 — Authentication Failures

Contoh:

- Password policy lemah.
- Brute-force protection tidak memadai.
- Password reset tidak aman.
- MFA implementation bermasalah.
- Session tidak diinvalidasi dengan benar.

---

A08:2025 — Software or Data Integrity Failures

Berhubungan dengan kegagalan menjaga integritas software dan data.

Contoh:

- Update tidak diverifikasi.
- Artifact tidak memiliki integrity checking.
- Data dari trust boundary tidak divalidasi.
- Deployment pipeline tidak dilindungi.

---

A09:2025 — Security Logging and Alerting Failures

Contoh:

Login gagal berulang
        ↓
Event tidak dicatat
        ↓
Tidak ada alert
        ↓
Serangan sulit dideteksi

Security event penting harus dicatat dan dipantau sesuai kebutuhan.

---

A10:2025 — Mishandling of Exceptional Conditions

Mencakup kesalahan ketika aplikasi menangani kondisi abnormal.

Contoh:

- Fail-open.
- Error handling buruk.
- State tidak konsisten.
- Exception menyebabkan authorization bypass.
- Transaksi gagal sebagian tetapi state tetap berubah.

---

2. Scanning Manual — Step by Step

«Penting: Semua contoh aktif di bagian ini hanya untuk "localhost", lab pribadi, CTF, atau target yang memiliki izin tertulis.»

---

Step 1 — Reconnaissance & Application Mapping

Tujuan tahap ini adalah memahami struktur aplikasi.

2.1 Konfigurasi Burp Suite / OWASP ZAP

Arsitektur:

Browser
   ↓
Burp Suite / OWASP ZAP
   ↓
Web Application

Catat:

- Domain.
- Endpoint.
- HTTP method.
- Parameter.
- Cookie.
- API.
- Authentication flow.
- JavaScript.
- Upload endpoint.
- Admin panel.
- Redirect.
- Error response.

---

2.2 Directory Brute-Forcing

Untuk lab lokal:

ffuf -u http://127.0.0.1:8000/FUZZ \
-w /path/ke/wordlist.txt \
-fc 404 \
-o ffuf-result.json \
-of json

Contoh hasil:

/admin
/login
/api
/uploads
/assets

Hasil discovery tetap harus divalidasi secara manual.

---

2.3 Fingerprinting Teknologi

Identifikasi:

- Web server.
- Framework.
- Programming language.
- JavaScript framework.
- CMS.
- API technology.
- Database indicator.

Sumber informasi:

HTTP Headers
Source Code
Cookies
JavaScript
URL Structure
Error Messages

Fingerprinting tidak otomatis berarti vulnerability.

---

2.4 Review JavaScript

Cari:

/api/
/graphql
/login
/upload
/admin

Perhatikan:

- API endpoint.
- Route.
- Parameter.
- Public configuration.
- Feature flag.
- Source map.

Jangan menganggap setiap string sebagai secret.

---

2.5 Dokumentasi Entry Point

Endpoint| Method| Auth| Parameter| Keterangan
"/login"| POST| No| username/password| Login
"/profile"| GET| Yes| -| Profile
"/api/orders/{id}"| GET| Yes| ID| Order
"/upload"| POST| Yes| File| Upload

Checklist WSTG

INFO-02
INFO-03
INFO-05

---

Step 2 — Authentication Testing

2.6 Credential Enumeration

Gunakan akun testing.

Bandingkan:

Username valid + password salah

Username tidak valid + password salah

Periksa apakah:

- status code berbeda;
- response berbeda;
- pesan error berbeda;
- waktu response berbeda secara konsisten.

---

2.7 Brute Force Protection

Periksa:

- Rate limiting.
- Progressive delay.
- Account lockout.
- CAPTCHA.
- Monitoring.
- Alerting.

Jangan melakukan percobaan password secara agresif terhadap akun atau sistem yang bukan milik sendiri.

---

2.8 Password Policy

Periksa:

- Minimum length.
- Password umum.
- Password reuse.
- Password change.
- Password reset.
- Password lama.

---

2.9 MFA

Workflow:

Username
   ↓
Password
   ↓
MFA
   ↓
Session
   ↓
Protected Resource

Pastikan protected resource tidak dapat digunakan sebelum MFA selesai.

---

2.10 Session Fixation

Bandingkan session identifier:

Before login:
SESSION=[VALUE-A]

After login:
SESSION=[VALUE-B]

Jika session seharusnya diregenerasi setelah authentication tetapi tidak berubah, lakukan investigasi.

---

2.11 Password Reset

Periksa:

- Token expiration.
- Single-use.
- Token invalidation.
- Ownership.
- Rate limiting.
- Password lama.
- Session setelah reset.

Checklist WSTG

AUTHN-02
AUTHN-07
AUTHN-09

---

Step 3 — Authorization Testing

2.12 Horizontal Privilege Escalation / IDOR

Gunakan dua akun testing.

User A
  ↓
Object A

User B
  ↓
Object A

Jika User B dapat mengakses Object A tanpa permission yang sesuai, dokumentasikan temuan.

---

2.13 Vertical Privilege Escalation

Contoh:

Role:
User

Protected function:
Admin

Periksa apakah server benar-benar memvalidasi role.

Checklist

ATHZ-02
ATHZ-04

---

Step 4 — Input Validation & Injection Testing

2.14 Reflected XSS

Untuk lab, payload sederhana:

<script>alert(document.domain)</script>

Periksa:

Input
 ↓
Reflection
 ↓
HTML parsing
 ↓
JavaScript execution

Jangan menggunakan payload yang mengirim cookie, token, atau data keluar dari sistem.

---

2.15 SQL Injection

SQL Injection terjadi ketika input user dapat memengaruhi struktur query database.

Untuk lab:

'

atau:

' OR '1'='1

Yang diperhatikan:

- Database error.
- Perubahan response.
- Perubahan hasil.
- Status code.
- Perbedaan perilaku.

Jangan melakukan extraction atau perubahan data pada database produksi.

---

2.16 Command Injection

Konsep:

User Input
    ↓
Application
    ↓
OS Command

Pengujian harus menggunakan indikator aman pada lab.

Hindari command yang:

- menghapus file;
- mengubah konfigurasi;
- menghentikan service;
- mengakses data pengguna;
- merusak sistem.

Checklist

INPV-01
INPV-05
INPV-12

---

Step 5 — Session Management Testing

2.17 Cookie Attributes

Contoh:

Set-Cookie: session=VALUE; Secure; HttpOnly; SameSite=Lax

Periksa:

- "Secure"
- "HttpOnly"
- "SameSite"
- Expiration
- Domain
- Path
- Session rotation

---

2.18 CSRF

Periksa:

- CSRF token.
- SameSite cookie.
- Origin checking.
- State-changing endpoint.
- Server-side validation.

Workflow:

GET Form
 ↓
CSRF Token
 ↓
POST Request
 ↓
Server Validation

Checklist

SESS-02
SESS-05

---

Step 6 — Business Logic Testing

2.19 Flow Bypass

Contoh:

Add to Cart
     ↓
Checkout
     ↓
Payment
     ↓
Confirmation

Pertanyaan testing:

Apakah Confirmation dapat dilakukan
sebelum Payment?

Pengujian harus menggunakan transaksi dummy/lab.

---

2.20 Quantity Manipulation

Misalnya:

quantity = 1

Periksa validasi server terhadap nilai tidak wajar:

0
-1
999999

Tujuan pengujian adalah memastikan business rule ditegakkan di server.

Checklist

BUSL-06
BUSL-08

---

3. Scanning Otomatis — Step by Step

3.1 Tools Utama

Tool| Fungsi| Lisensi
Burp Suite| Proxy, repeater, scanner| Community/Professional
OWASP ZAP| Proxy dan vulnerability scanner| Open Source
Nuclei| Template-based scanner| Open Source
Nikto| Web server scanner| Open Source
sqlmap| SQL injection automation| Open Source

---

3.2 Nuclei

Install

Jika Go telah tersedia:

go install -v github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest

Periksa:

nuclei -version

---

Update Template

nuclei -update-templates

---

Scan Lab

nuclei -u http://127.0.0.1:8000

Untuk target berizin:

nuclei -u https://[LAB_TARGET]

---

Simpan Output JSON

nuclei \
-u https://[LAB_TARGET] \
-json-export nuclei-results.json

JSON dapat digunakan untuk:

- Dokumentasi.
- Reporting.
- Analisis.
- Retesting.
- Audit trail.

---

3.3 Burp Suite Active Scan

Workflow:

Browser
   ↓
Burp Proxy
   ↓
HTTP History
   ↓
Scope Review
   ↓
Active Scan
   ↓
Manual Validation
   ↓
Report

Sebelum menjalankan active scan:

- Pastikan target benar.
- Pastikan scope benar.
- Pastikan tidak ada sistem pihak ketiga.
- Gunakan akun testing.
- Hindari fungsi destruktif.
- Tentukan batas request.

---

3.4 Validasi False Positive

Scanner tidak selalu benar.

Gunakan proses:

Scanner Finding
       ↓
Review Request
       ↓
Review Response
       ↓
Manual Reproduction
       ↓
Confirmed?
   ↙        ↘
 YES        NO
  ↓          ↓
Report    False Positive

Contoh:

Tool:
Nuclei

Finding:
Missing Security Header

Status:
Confirmed

Evidence:
Header tidak ditemukan.

Recommendation:
Tambahkan header sesuai kebutuhan aplikasi.

---

4. Pemetaan ke OWASP Top 10

Finding| OWASP 2025| Keterangan
IDOR| A01| Broken Access Control
Vertical Privilege Escalation| A01| Authorization failure
SSRF| A01| Masuk A01 pada 2025
Debug Mode| A02| Security Misconfiguration
Directory Listing| A02| Misconfiguration
Vulnerable Dependency| A03| Supply Chain
Weak Cryptography| A04| Cryptographic Failure
SQL Injection| A05| Injection
XSS| A05| Injection
Command Injection| A05| Injection
Business Logic Flaw| A06| Dapat berasal dari desain
Authentication Bypass| A07| Authentication Failure
Integrity Failure| A08| Software/Data Integrity
Missing Security Alert| A09| Logging/Alerting
Fail-open| A10| Exceptional Conditions

«Catatan: Satu vulnerability dapat memiliki lebih dari satu klasifikasi yang relevan. Pilih kategori berdasarkan akar masalah dan jelaskan alasan pemetaan.»

---

5. Cara Membuat Laporan Lengkap (PDF / Word)

5.1 Struktur Laporan

Struktur umum:

1. Cover
2. Executive Summary
3. Scope
4. Methodology
5. Risk Summary
6. Technical Findings
7. Recommendations
8. Retesting
9. Appendices

---

5.2 Executive Summary

Contoh:

Assessment:
[Web Application Security Assessment]

Target:
[Nama Target]

Tanggal:
[Tanggal]

Scope:
[Scope]

Testing Period:
[Tanggal Mulai] - [Tanggal Selesai]

Isi executive summary menjelaskan:

- tujuan assessment;
- scope;
- metodologi;
- ringkasan temuan;
- risiko utama;
- rekomendasi umum.

---

5.3 Technical Findings

Format standar:

Field| Isi
Judul| [Nama Vulnerability]
Severity| [Severity]
CVSS Vector| [CVSS Vector]
Deskripsi| [Deskripsi]
Langkah Reproduksi| [Steps]
Dampak| [Impact]
Bukti| [Evidence]
Rekomendasi| [Recommendation]
Referensi| [References]

---

Template Finding

[F-001] [Judul Vulnerability]

Severity: "[Critical/High/Medium/Low/Informational]"

CVSS Vector: "[CVSS_VECTOR]"

Deskripsi

[Jelaskan vulnerability secara singkat dan teknis.]

Langkah Reproduksi

1. Login menggunakan [TEST_ACCOUNT].
2. Buka [ENDPOINT].
3. Kirim request [REQUEST].
4. Amati response.
5. Bandingkan dengan expected behavior.

Dampak

[Jelaskan dampak keamanan dan bisnis.]

Bukti

GET /api/[TEST_RESOURCE]
Authorization: [REDACTED]

Response:

[REDACTED]

Rekomendasi

[Jelaskan perbaikan teknis.]

Referensi

- OWASP Top 10
- OWASP WSTG
- CWE
- Dokumentasi vendor

---

5.4 Appendices

Lampiran dapat berisi:

Appendix A — Scope
Appendix B — Methodology
Appendix C — Tools
Appendix D — Evidence
Appendix E — Raw Scanner Results
Appendix F — Retest
Appendix G — CVSS

Jangan memasukkan:

- password;
- API key;
- session token;
- private key;
- data pribadi yang tidak diperlukan.

---

5.5 Template GitHub

Template laporan pentest gratis dapat ditemukan pada repository:

MSaiRam10/pentest-report-templates

Repository tersebut menyediakan berbagai template laporan penetration testing.

«Gunakan template sebagai referensi struktur dan sesuaikan dengan kebutuhan assessment.»

---

5.6 APTRS

APTRS (Automated Penetration Testing Reporting System) dapat digunakan untuk membantu proses reporting penetration testing.

Fitur yang tersedia dalam proyek antara lain:

- Project management.
- Vulnerability management.
- Evidence.
- Report generation.
- Template.
- PDF.
- DOCX.
- Excel.

Contoh instalasi melalui repository:

git clone https://github.com/APTRS/APTRS
cd APTRS
cp env.docker .env
docker-compose up

Selalu cek dokumentasi resmi proyek untuk perubahan perintah instalasi pada versi terbaru.

---

5.7 SysReptor

SysReptor merupakan platform untuk membuat laporan security assessment.

Workflow sederhana:

Finding
   ↓
Markdown / Editor
   ↓
Evidence
   ↓
Risk
   ↓
Recommendation
   ↓
PDF

SysReptor dapat digunakan ketika membutuhkan reporting yang lebih terstruktur dan dapat dikustomisasi.

---

5.8 Markdown / Word → PDF

Workflow paling sederhana:

Markdown
   ↓
Pandoc
   ↓
PDF

Contoh:

pandoc laporan.md \
-o laporan.pdf \
--pdf-engine=xelatex

Atau:

Microsoft Word
      ↓
Save As
      ↓
PDF

Untuk GitHub, format Markdown (".md") sangat cocok karena dapat dibaca langsung melalui repository.

---

5.9 Checklist Sebelum Mengirim Laporan

Legal

- [ ] Scope telah disetujui.
- [ ] Target benar.
- [ ] Waktu pengujian sesuai.
- [ ] Tidak ada aktivitas di luar scope.

Technical

- [ ] Finding sudah divalidasi.
- [ ] False positive telah dihapus.
- [ ] Evidence tersedia.
- [ ] Reproduction steps jelas.
- [ ] Impact dijelaskan.
- [ ] Recommendation dapat dilakukan.
- [ ] CVSS diperiksa.

Privacy

- [ ] Password dihapus.
- [ ] Token dihapus.
- [ ] API key dihapus.
- [ ] Data pribadi diminimalkan.
- [ ] Screenshot telah disensor.

Report

- [ ] Executive Summary.
- [ ] Scope.
- [ ] Methodology.
- [ ] Findings.
- [ ] Recommendations.
- [ ] Appendices.
- [ ] References.
- [ ] Version dokumen.

---

6. Ringkasan Alur Lengkap

┌─────────────────────────────┐
│ 1. LEGAL & AUTHORIZATION    │
│    Scope + Written Permission│
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│ 2. RECONNAISSANCE           │
│    Application Mapping      │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│ 3. AUTOMATED DISCOVERY      │
│    Nuclei / ZAP / Scanner   │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│ 4. MANUAL TESTING           │
│    Auth / Authz / Input     │
│    Session / Business Logic │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│ 5. VALIDATION               │
│    Confirm / False Positive │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│ 6. RISK ASSESSMENT          │
│    Severity + CVSS          │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│ 7. OWASP MAPPING            │
│    WSTG + OWASP Top 10      │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│ 8. REPORTING                │
│    Executive + Technical    │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│ 9. REMEDIATION              │
│    Developer Fix            │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│ 10. RETESTING               │
│     Verify Fix              │
└─────────────────────────────┘

---

Lampiran

A. Checklist Web Security Testing

Information Gathering

- [ ] Domain diketahui.
- [ ] Scope dikonfirmasi.
- [ ] Endpoint didokumentasikan.
- [ ] Parameter didokumentasikan.
- [ ] Technology fingerprint dilakukan.
- [ ] JavaScript direview.
- [ ] API ditemukan.
- [ ] Entry point dicatat.

Authentication

- [ ] Login.
- [ ] Logout.
- [ ] Password policy.
- [ ] Credential enumeration.
- [ ] Rate limiting.
- [ ] MFA.
- [ ] Password reset.
- [ ] Session rotation.

Authorization

- [ ] Horizontal access.
- [ ] Vertical access.
- [ ] Object ownership.
- [ ] Admin endpoint.
- [ ] API authorization.

Input Validation

- [ ] XSS.
- [ ] SQL Injection.
- [ ] Command Injection.
- [ ] File upload.
- [ ] Parameter manipulation.
- [ ] Server-side validation.

Session

- [ ] Cookie flags.
- [ ] Session expiration.
- [ ] Session rotation.
- [ ] CSRF.
- [ ] Logout invalidation.

Business Logic

- [ ] Workflow bypass.
- [ ] Quantity manipulation.
- [ ] Price manipulation.
- [ ] State manipulation.
- [ ] Race-condition considerations.

---

B. Format Severity

Severity dapat menggunakan skema:

Critical
High
Medium
Low
Informational

Severity harus mempertimbangkan:

- Attack Vector.
- Privileges Required.
- User Interaction.
- Scope.
- Confidentiality.
- Integrity.
- Availability.
- Business impact.

Untuk CVSS, gunakan versi dan kalkulator yang sesuai dengan metodologi assessment.

---

C. Contoh Struktur Repository

web-security-testing/
│
├── README.md
│
├── methodology/
│   ├── reconnaissance.md
│   ├── authentication.md
│   ├── authorization.md
│   ├── injection.md
│   ├── session.md
│   └── business-logic.md
│
├── reports/
│   ├── template.md
│   └── findings/
│
├── evidence/
│   └── .gitkeep
│
├── scans/
│   └── .gitkeep
│
└── references/
    └── references.md

«Catatan keamanan: Jangan meng-upload credential, API key, private key, session token, database dump, atau data pribadi ke repository GitHub.»

---

Referensi

OWASP

- OWASP Top 10:2025
  https://owasp.org/Top10/

- OWASP Web Security Testing Guide
  https://owasp.org/www-project-web-security-testing-guide/

- OWASP WSTG v4.2
  https://owasp.org/www-project-web-security-testing-guide/v42/

PortSwigger

- Web Security Academy
  https://portswigger.net/web-security

OWASP ZAP

- https://www.zaproxy.org/

Nuclei

- https://github.com/projectdiscovery/nuclei

Nikto

- https://github.com/sullo/nikto

sqlmap

- https://github.com/sqlmapproject/sqlmap

APTRS

- https://github.com/APTRS/APTRS

Pentest Report Templates

- https://github.com/MSaiRam10/pentest-report-templates

---

Glosarium

Istilah| Pengertian
API| Application Programming Interface
Authentication| Proses memastikan identitas user
Authorization| Proses menentukan hak akses user
CVSS| Common Vulnerability Scoring System
CSRF| Cross-Site Request Forgery
CSP| Content Security Policy
IDOR| Insecure Direct Object Reference
Injection| Memasukkan input yang memengaruhi interpreter/query
MFA| Multi-Factor Authentication
OWASP| Open Worldwide Application Security Project
SSRF| Server-Side Request Forgery
XSS| Cross-Site Scripting
WSTG| Web Security Testing Guide
Reconnaissance| Pengumpulan informasi target
Scope| Batas sistem yang boleh diuji
False Positive| Hasil scanner yang ternyata bukan vulnerability
Retesting| Pengujian ulang setelah perbaikan
Evidence| Bukti teknis suatu temuan
Attack Surface| Bagian sistem yang dapat menjadi titik interaksi/serangan
Endpoint| URL atau route yang menyediakan fungsi tertentu
Rate Limiting| Pembatasan jumlah request dalam periode tertentu
Session| Mekanisme mempertahankan keadaan/login user
Business Logic| Aturan proses bisnis dalam aplikasi

---

Penutup

Web Security Testing bukan hanya menjalankan scanner dan menunggu hasil. Metodologi yang baik menggabungkan:

Legal Authorization
        +
Reconnaissance
        +
Manual Testing
        +
Automated Scanning
        +
Manual Validation
        +
Risk Assessment
        +
OWASP Mapping
        +
Professional Reporting
        +
Remediation
        +
Retesting

Dengan pendekatan tersebut, hasil security testing dapat menjadi dokumen teknis yang berguna bagi developer, administrator, security team, maupun manajemen.

Dokumen ini siap dikonversi ke PDF atau Word.
