---
title: 安裝 BizTalk Server 2016 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f5ac913-0734-45b2-8e25-1db146d81858
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f6c6868302554aa14d80c296955e657c9f171d6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003735"
---
# <a name="install-biztalk-server-2016"></a>安裝 BizTalk Server 2016
在單一電腦上安裝 BizTalk Server。

## <a name="before-you-get-started"></a>在開始之前

* **系統管理員** – 當您安裝 SQL Server 時，安裝程式會自動將系統管理員權限授與您所登入的帳戶。 由於安裝 BizTalk Server 也需要這些權限，因此請執行下列其中一項動作：
  * 使用您在安裝 SQL Server 時所使用的相同帳戶。
  * 將系統管理員權限授與所登入的帳戶。
  * 確認所登入的帳戶是本機系統管理員群組的成員。
* **帳戶名稱** – 您應該盡量使用預設帳戶名稱。 BizTalk Server 安裝程式會自動輸入預設帳戶。 如果在網域中有多個 BizTalk Server 群組，請變更帳戶名稱以避免發生衝突。 如果您要變更名稱，BizTalk Server 只支援 *NetBIOS 網域名稱\使用者*這種名稱格式的服務帳戶和 Windows 群組。
* **帳戶名稱與 BAM 管理 Web 服務** – BizTalk Server 不支援使用內建帳戶或無密碼的帳戶作為 BAM 管理 Web 服務使用者。 Web 服務會存取 BizTalk Server 資料庫，而這類帳戶可能會帶來安全性威脅。

    > [!NOTE] 
    > 使用這類帳戶來設定 BizTalk Server 可能會成功，但 BAM 管理 Web 服務會失敗。 內建帳戶或無密碼的帳戶可用於 BAM 應用程式集區。

* **BizTalk 組件檢視工具** – 不支援 64 位元平台。 
* **安裝和解除安裝** – 解除安裝 BizTalk Server 時，需要手動刪除 BizTalk Server 資料庫。 如果以開發人員或評估員身分來安裝 BizTalk Server，請使用虛擬機器。 如果需要重新安裝，您可以輕鬆復原虛擬機器，而不需要解除安裝和刪除資料庫。
* **32 位元和 64 位元電腦** – 在 32 位元或 64 位元電腦上安裝 BizTalk Server 時有幾項差異。 安裝和設定的內容涵蓋 32 位元和 64 位元的電腦， 但會註明任何差異。
* **工作群組** - 支援在工作群組環境中的單一電腦上安裝和設定 BizTalk Server。 SQL Server 與 BizTalk Server 的功能和元件係在同一部電腦上安裝和設定。


## <a name="install-biztalk-server"></a>安裝 BizTalk Server
1. 關閉所有開啟的程式。 以系統管理員身分執行 BizTalk Server 安裝程式。
2. 選取 [安裝 Microsoft BizTalk Server 2016]。
3. 輸入您的 [使用者名稱]、[組織] 和產品金鑰。 選取 **[下一步]**。
4. 接受授權合約，然後選取 [下一步]。
5. 選擇參與「客戶經驗改進計畫」，然後選取 [下一步]。
6. 選擇您想要安裝的元件：

    ![bts2016install_components](../install-and-config-guides/media/bts2016install-components.gif)
  
    請務必選取 [其他軟體]。 您也可以變更安裝位置： 
  
    ![bts2016install_additional](../install-and-config-guides/media/bts2016install-additional.gif)

    選取 **[下一步]**。   
  
   7. 根據您選擇的元件，可能有一些額外的必要條件，例如 ADOMD.NET。 安裝程式會自動為您安裝所有必要的可轉散發套件。 選項包含：
7. **手動安裝必要的可轉散發套件**：系統會關閉安裝精靈，以便您手動安裝遺漏的必要條件。
8. **從 Web 自動安裝必要的可轉散發套件**：預設值。 需要存取網際網路。
9. **下載必要的可轉散發套件封包檔**：下載封包檔，以便稍後安裝。
10. **從封包檔自動安裝必要的可轉散發套件**：如果您已下載封包檔，即可選取此選項來使用這些封包檔。 

    選取 **[下一步]**。
  
11. 檢閱摘要頁面。 若要進行任何變更，請選取 [上一步] 以選取或取消選取任何元件。 

      若要啟用在系統重新開機之後自動登入的功能，請選取 [設定] 並輸入登入資訊。 這只會在 BizTalk 安裝期間啟用。 安裝程式完成時，即會停用此設定。 

     選取 [安裝]。
  
12. 若要立即設定 BizTalk，請選取 [啟動 BizTalk Server 組態]。 如果您不想立即設定 BizTalk，請取消選取這個選項，並選取 [完成] 以關閉安裝精靈。 

暫存資料夾中即會產生安裝程式記錄檔，其類似於 `C:\Users\*username*\AppData\Local\Setup(011217 xxxxxx).htm`
  
## <a name="check-the-installation"></a>檢查安裝

* [程式和功能] 中應列出 BizTalk Server。
* `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0` 登錄機碼應列出 BizTalk Server 的版本、安裝路徑、版本號碼和其他詳細資料。
* 您的應用程式中應列出 BizTalk Server 管理、組態和其他元件。 

## <a name="next-step"></a>下一步
[設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)