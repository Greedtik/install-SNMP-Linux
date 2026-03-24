# 🚀 Linux SNMP Auto-Installer

Script สำหรับติดตั้งและตั้งค่า SNMP Service (`snmpd`) บนระบบปฏิบัติการ Linux แบบอัตโนมัติ ออกแบบมาให้ใช้งานง่าย รองรับ Linux หลายตระกูล และสามารถรันจบได้ในคำสั่งเดียว เหมาะสำหรับการเตรียม Server เพื่อเชื่อมต่อกับระบบ Monitoring อย่างรวดเร็ว

## ✨ Features (คุณสมบัติเด่น)

- **Auto-Detect OS:** ตรวจสอบ OS อัตโนมัติและเลือกใช้ Package Manager ที่เหมาะสม (`apt`, `yum`/`dnf`, `zypper`)
- **Interactive Prompt:** ถามค่า Community String ก่อนติดตั้ง (หากไม่ระบุจะใช้ค่า Default คือ `public`)
- **IPv4 & IPv6 Support:** ตั้งค่าให้ `snmpd` รับการเชื่อมต่อผ่านพอร์ต UDP 161 สำหรับ IPv4 ทุก Interface และ IPv6 บน Localhost (`[::1]`)
- **View-Based Access Control:** สร้าง View ชื่อ `systemonly` ที่ครอบคลุม Root OID (`.1`) และผูกเข้ากับ Community String ทำให้สามารถเข้าถึงข้อมูลระบบได้ครบถ้วน
- **Safe Configuration:** ทำการ Backup ไฟล์ `snmpd.conf` เดิมให้อัตโนมัติก่อนสร้างไฟล์ใหม่
- **Log Spam Reduction:** ปิดการบันทึก Log การเชื่อมต่อ (`TCPWrappersConnects`) เพื่อป้องกันปัญหา Log บวมเมื่อถูก Monitoring Server ดึงข้อมูลถี่ๆ
- **Built-in Self-Test:** ทดสอบการดึงข้อมูล System MIBs ด้วย `snmpwalk` ทันทีหลังติดตั้งเสร็จ

## 🐧 Supported Operating Systems

- **Debian-based:** Ubuntu, Debian
- **RHEL-based:** CentOS, Red Hat Enterprise Linux (RHEL), Rocky Linux, AlmaLinux, Fedora
- **SUSE-based:** SLES, openSUSE

## 🛠️ Quick Start (วิธีใช้งาน)

รันคำสั่งด้านล่างนี้ใน Terminal ของเครื่อง Server ที่ต้องการติดตั้ง (ต้องมีสิทธิ์ Root หรือรันด้วย `sudo`)

```bash
curl -sL https://raw.githubusercontent.com/Greedtik/install-SNMP-Linux/refs/heads/main/install_snmp.sh | sudo bash
