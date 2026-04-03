# TRSS Simple Registry Checker

Basit, tek dosyalık bir PowerShell scripti.  
Windows üzerinde bazı registry konumlarını ve event log bulgularını hızlıca kontrol etmek için tasarlanmıştır.

Bu araç **dosya oluşturmaz**, **sadece konsola çıktı verir** ve hızlı inceleme amacıyla kullanılır.

## Ne işe yarar?

Script şu alanları kontrol eder:

- **Prefetch yapılandırması**
  - `HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management\PrefetchParameters`

- **RunOnce girdileri**
  - `HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce`
  - `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce`

- **OpenSavePidlMRU\\jar**
  - `HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\OpenSavePidlMRU\jar`
  - MRU sırasını göstermeye çalışır
  - Binary blob içinden okunabilir string / path ipuçları çıkarır

- **Security Event Log - Event ID 4657**
  - Registry value değişikliklerini kontrol eder
  - Audit Registry açıksa ve ilgili key üzerinde auditing varsa anlamlı sonuç verir

- **Event Log temizleme izi - Event ID 104**
  - Bazı log temizleme olaylarını gösterebilir

- **AppCompat policy kontrolü**
  - `HKCU\SOFTWARE\Policies\Microsoft\Windows\AppCompat`
  - `HKLM\SOFTWARE\Policies\Microsoft\Windows\AppCompat`
  - `DisablePCA` değerini kontrol eder

## Özellikler

- Tek dosya
- Kurulum gerektirmez
- Konsola çıktı verir
- Hızlı kullanım
- Temel registry / event kontrolü için uygundur

## Kullanım

PowerShell'i açıp scripti çalıştırman yeterli:

```
powershell
powershell -ExecutionPolicy Bypass -File .\TRSS-Simple-Registry-Checker.ps1
