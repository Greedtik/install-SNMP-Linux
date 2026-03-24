# 🚀 Linux SNMP Auto-Installer (Bulletproof Edition)

Script สำหรับติดตั้งและตั้งค่า SNMP Service (`snmpd`) บนระบบปฏิบัติการ Linux แบบอัตโนมัติ ออกแบบมาให้ถึกทน ใช้งานง่าย รองรับตั้งแต่ OS รุ่นเก่าไปจนถึงรุ่นใหม่ และสามารถรันจบได้ในคำสั่งเดียว

## ✨ Features (คุณสมบัติเด่น)

- **Legacy & Modern OS Support:** ตรวจสอบ OS อัตโนมัติ รองรับทั้งระบบที่ใช้ `systemctl` (รุ่นใหม่) และ `service` (เช่น Ubuntu 14, CentOS 6)
- **Copy-Paste Safe (No EOF Bugs):** โครงสร้างโค้ดใช้คำสั่ง `echo` สร้างไฟล์ Config ทีละบรรทัด หมดปัญหา Script พังจากการ Copy-Paste ข้าม OS (ปัญหาเว้นบรรทัดแบบ CRLF)
- **Reliable Self-Test:** ระบบทดสอบหลังติดตั้งใช้ OID ตัวเลขโดยตรง (`.1.3.6.1.2.1.1`) ป้องกัน Error ทิพย์ `Unknown Object Identifier` บนเครื่องที่ไม่มีฐานข้อมูล MIBs
- **Interactive Prompt:** ถามค่า Community String ก่อนติดตั้ง (หากไม่ระบุจะใช้ค่า Default คือ `public`) พร้อมระบบลบช่องว่าง/อักขระพิเศษอัตโนมัติ
- **IPv4 & IPv6 Support:** ตั้งค่าให้ `snmpd` รับการเชื่อมต่อผ่านพอร์ต UDP 161 สำหรับ IPv4 ทุก Interface และ IPv6 บน Localhost (`[::1]`)
- **View-Based Access Control:** สร้าง View ชื่อ `systemonly` ที่ครอบคลุม Root OID (`.1`) ทำให้ Monitor Server เข้าถึงข้อมูลระบบได้ครบถ้วน
- **Log Spam Reduction:** ปิดการบันทึก Log การเชื่อมต่อ (`TCPWrappersConnects`) ป้องกันปัญหา Log บวมเมื่อถูก Monitoring Server ดึงข้อมูลถี่ๆ

## 🐧 Supported Operating Systems

- **Debian-based:** Ubuntu (ตั้งแต่ 14.04 ขึ้นไป), Debian
- **RHEL-based:** CentOS (6, 7, 8+), Red Hat Enterprise Linux (RHEL), Rocky Linux, AlmaLinux, Fedora
- **SUSE-based:** SLES, openSUSE

## 🛠️ Quick Start (วิธีใช้งาน)

รันคำสั่งด้านล่างนี้ใน Terminal ของเครื่อง Server ที่ต้องการติดตั้ง (ต้องมีสิทธิ์ Root หรือรันด้วย `sudo`)

```bash
curl -sL https://raw.githubusercontent.com/Greedtik/install-SNMP-Linux/refs/heads/main/install_snmp.sh | sudo bash
