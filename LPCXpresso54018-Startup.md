# LPCXpresso54018 (OM40003) 開發版初次使用說明

## 簡介

LPCXpresso54018 此開發版官方教學是使用 MCUXpresso 作為官網教學影片的編譯與燒錄環境，

如使用 Keil 的環境進行編譯，則需進行後續設定。

---


## MCUXpresso
> LPCXpresso54018 Default Debug Interfaces
> 預設燒錄介面，確認JP5插上後便可直接燒錄
> 註: JP 只要有進行插拔，要重新啟動後(重新上電，Reset 鍵無效)才會啟動新的設定

1. JP5 shunted (linked)，JP5確認插上
2. Build，建置
3. Debug，進行燒錄


## Third party debug
> 非官方 IDE 進行 debug
> 步驟繁瑣許多且需安裝其他軟體 

1. First use should set the debug interface by LPCScrypt，請先安裝 LPCSCRYPT
2. JP5 shunted (linked)，確認JP5插上
3. Open LPCScrypt to set debug interface. (CMSIS-DAP / J-Link)，打開剛剛安裝的 LPCSCRYPT 資料夾，找到 scripts 資料夾並執行相關 script ，便可設定 debug 介面
4. JP5 open (unlinked)，之後只要確定燒錄前JP5是斷路(JP5拔掉)便可使用第三方軟體進行 debug

### Keil uVision(MDK)
1. Open options for target
2. Select debug tab

a. Use "J-Link / J-TRACE Coretex" Settings:
Setting Debug
i. 	Set Port - "SW"
ii. Set Connect & Reset Options - Connect: "Normal", Reset: "Normal"

Setting Flash Download
i.  Download function select: "Erase Sectors", "Program", "Reset and Run"
ii. RAM for Algorithm -  Start: "0x20000000", Size: "0x1000"
iii.Add Flash Programming Algorithm: "LPC540xx W25Q128JVFM", Start: "0x00000000", Size: "0x01000000"

b. Use "CMSIS-DAP Debugger" Settings:
Setting Debug
i.  Set Port - "SW"
ii. Set Connect & Reset Options - Connect: "Normal", Reset: "SYSRESETREQ"

Setting Flash Download
i.  Download function select: "Erase Sectors", "Program", "Reset and Run"
ii. RAM for Algorithm -  Start: "0x20000000", Size: "0x1000"
iii.Add Flash Programming Algorithm: "LPC540xx W25Q128JVFM", Start: "0x00000000", Size: "0x01000000"

---

# Other Tools

1. Putty:
Board Debug Baud Rate: 115200
Scan COM port

> 可使用 Putty 連接到開發版進行測試

---

# Reference

1. Getting Started with MCUXpresso SDK for LPC540xx
> Build and run Demo applications by MCUXpresso IDE & Keil uVision 5(MDK)

> Source: MCUXpresso SDK Builder
> https://mcuxpresso.nxp.com/en/welcome

2. UM11035 - LPCXpresso546x8/540xx/54S0xx Board User Manual
> LPCXpresso54608/54618/54628/54018/54S018 Board User Manual 

> Source: NXP - OM40003: LPCXpresso54018 Development Board - Documents and Software
> https://www.nxp.com/support/developer-resources/evaluation-and-development-boards/lpcxpresso-boards/lpcxpresso54018-development-board:OM40003

3. Get Started with the LPCXpresso54018
> Get Started with the LPCXpresso54018 by MCUXpresso IDE

> Source: NXP - Get Started with the LPCXpresso54018
> https://www.nxp.com/document/guide/get-started-with-the-lpcxpresso54018:GS-LPCXpresso54018

4. LPCScrypt_User_Guide
> Pre-work for running Demo applications with Keil uVision 5 (MDK).
> Select LPC-Link2 with CMSIS-DAP or Segger J-Link

> Source: NXP LPCScrypt v2.1.0
> https://www.nxp.com/support/developer-resources/software-development-tools/lpc-developer-resources-/lpc-microcontroller-utilities/lpcscrypt-v2.1.0:LPCSCRYPT

