---
title: HomeLab
slug: homelab
ghost_id: 67dec6355fce5a0001f860c2
type: page
status: published
visibility: public
featured: false
created_at: '2025-03-22T14:16:21.000Z'
updated_at: '2025-03-23T10:05:14.000Z'
published_at: '2025-03-22T14:48:03.000Z'
authors:
- Gbanyan
feature_image: ../assets/photo-1551703599-6b3e8379aa8c.jpg
---

記載了 HomeLab 的架設經過及配置

## 硬體

* 暢網 Intel J4125 四網口小機器
* 2nd i3-8100 主 HomeLab Server
  + UMAX DDR4 16G x 2 = Total 32 GB
  + PCIE 3.0 x 16 NVMe SSD Expansion Card with 4 slots (自帶晶片)
    - NVMe SSD 500GB x 2
    - NVMe SSD 1TB x 2
  + Asrock H370M ITX/ac
    - 1 SATA SSD for Proxmox VE host
    - 1 SATA SSD for Temp Download
    - AQ107 M.2 to 10 Gbps Ethernet Cards
* Synology NAS

i3-8100 是 朋友換機後收來的，後來深入研究後，發現竟然是同一系列少數支援 ECC Memory 的型號，但後來沒有特別去搞

會選中 i3-8100， 主要是長時間的待機功耗與所需效能間平衡點的考量。雖然可以選 N100 但是擴充性不佳，且新品不若 i3-8100 便宜。核心數或時脈再上去的 CPU 則待機功耗會增加。目前評估，這是現階段 HomeLab 耗電與效能間的最佳平衡。

會選這張主機板，是看中有兩個網路孔，可以當作軟路由使用，不過朋友贈送一台 J4125 小機器，故主機暫時未充當軟路由的角色。未來應該是看誰先壞掉，J4125 小機器壞掉的話這台就可以繼續以 Proxmox VE 的 VM image 備份檔直接接手軟路由功能。

為了塞進去機櫃不充裕的空間，選了 ITX 主機板，結果擴充時綁手綁腳。四顆 NVMe SSD 擴充卡已經佔掉了唯一的 PCIE 3.0 x 16 插槽，想擴充 10Gbps 網路時，竟然成功硬幹，從淘寶買了一張 M.2 介面 轉 10Gbps 的網路卡，順利啟用 PCIE 3.0 x 4 的頻寬，真的是很神奇的一件事。

## 軟體規劃

HomeLab server 目的有：

* 自架服務，如廣告 DNS Block、智慧家庭、多媒體音樂、相簿、程式碼 Repo、密碼庫及其他
* 備份中介站，Syncthing 常駐以隨時與其他裝置串接同步
* 暫時性外網檔案分享區，避免在外面電腦登入 Google Drive, Microsoft Onedrive 等敏感性帳號的風險
* 內網 Samba 分享服務
* 其他需長期執行，不適合桌面 PC 長時間開機，增加耗電的程序，如爬蟲、下載等

HomeLab 有人玩到自動追劇、新動畫番自動下載歸類、還有其他有的沒有的，
雖然以前曾經會花時間試有的沒有的 Self-hosted Service, 如記帳、家庭物料整備整理等等，不過現在偏向收斂，維持必要服務運行。

### 服務架構

不談太多細節，僅列出核心

* 對外 PPPoE 撥號及防火牆以 OPNSense 運行，虛擬化在 Proxmox VE 上，運行在 J4125 機器上
  + 規劃 VLAN區隔子網段，並分別配置防火牆規則，將內外網分離
  + 訂閱 Firehol IP 清單，阻隔威脅
  + Unbound DNS 啟用訂閱 Block 清單，為家裡人網路多一份保障
* Home Assistant OS 虛擬化運行在 Proxmox VE 上
  + 提供家庭裝置基本儀表板，可連結空調、蘋果裝置、智慧螢幕、路由器、智慧開關等
  + 可配合手機 App 設定位置偵測及觸發條件，例如一出門就自動關閉智慧開關、冷氣配合室外溫度自動設定目標溫度等
* 主 HomeLab Server (i3-8100) 配合內外網 VLAN ，在 Proxmox VE Bridge 上設定 VLAN 以及各 LXC 上設定 Tag
  + 各服務使用 Caddy or Traefik + Cloudflare DNS API ，一律在 Reverse Proxy 上自訂網域及自動申請對應 SSL憑證
  + 高度安全性需求，無必要對外暴露服務，一律僅限內網存取，在外行動透過 VPN 連回
    - ssh-remote 遠端桌機 Linux 開發
    - Vaultwarden 密碼庫服務
    - Samba 檔案存取...
  + 對外暴露服務，如與他人分享的 git repo Gitea, 暫時存放檔案的 filebrowser, 個別 LXC 指定外網 VLAN Tag, 並設定防火牆條件令他們無法存取內網
* 在主 Proxmox VE Server 上面設定 ZFS Pool，四顆汰換下來的 SSD 組成 RAID 10 陣列
  + 所有 LXC 及 VM image 的主儲存區
  + 內網 Samba 的檔案儲存區
  + 以 Memory 當作 Arc Cache
* 所有 Proxmox VE 虛擬化的 VM 跟 LXC image ，設定每日深夜自動備份至 Synology NAS
  + Proxmox VE 的虛擬化，讓 LXC Container Image 如果遭到攻擊或感染，也不會影響到其他 Container 及備份主機
  + 已經有多次因為更新或者更改配置導致服務掛掉，直接從備份救回的例子
  + Synology NAS 由於是傳統 HDD，精神是以 SSD 為日間主要服務載體，然後至夜間由 Synology NAS 接手備份及上傳至雲端，在深夜時段由於睡眠故可放心頻寬佔用
* 以服務時段來分配設備自動開關機排程，達到省電節約能源目的
  + Synology NAS 內存放的是長期冷儲存檔案或者保存之媒體檔案
  + 以時段來說為周六日才較有機會存取，故安排六日之外其餘時間只有深夜開機
  + 深夜開機主要負責 Proxmox VE 備份及雲端上傳服務
  + Synology NAS 效能不一定是最好，但是所有設備中最穩定的，故擔任家用備份終端點任務
