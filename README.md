# fix-credssp

## CredSSP Encryption Oracle Remediation คือ อะไร

- ก่อนที่จะแก้ไขอะไร เราต้องรู้จักกันก่อนครับ ตัว CredSSP เกิดจากช่องโหว่ความปลอดภัยเบอร์ CVE-2018-0886 ครับ ซึ่งช่องโหว่ CredSSP ซึ่งส่วนหนึ่งของ Authentication Provider สามารถทำให้เครื่องของผู้ถูกโจมตีจากระยะไกล โดยที่ไม่ได้รับอนุญาตได้ครับ และผู้โจมตีโจมตีใน Session ของผู้ใช้งานที่ใช้งานระบบอยู่ครับ เช่น Remote Desktop แต่ทุกคนไม่ต้องหวาดระแวงไปครับ ตอนนี้ทาง Microsoft ได้ออก Patch มาแล้วครับ ถ้าเป็น Windows 10 เป็น April Update 1803 นี่เองครับ

- ผลข้างเคียงจาก Windows Update คือ ทำให้เครื่องปลายทางที่ยังไม่ได้ Update Security Patch เราจะไม่สามารถทำอะไรได้เลย เช่น Remote Desktop ไปเครื่องปลายทาง ครับ

## cmd run as admin 

```cmd
REG ADD "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\CredSSP\Parameters" /v AllowEncryptionOracle /t REG_DWORD /d 2
```

## for delete

```cmd
REG Delete "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\CredSSP\Parameters" /v AllowEncryptionOracle
```

after command restart or relogin for effect
