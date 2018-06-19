---
title: 主機 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- host instances, servers
- hosts, isolated
- host instances, relationships
- hosts, in-process hosts
- servers, hosts
- hosts, host instances
- hosts, relationships
- In-Process BizTalk Host groups
- hosts, about hosts
- hosts, untrusted
- host instances, hosts
- hosts, servers
- hosts
- servers, host instances
- Isolated Host Users group
- hosts, trusted
ms.assetid: d96537e0-e679-407a-8870-34a663acfed9
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a1c61995bca06203208c057762db7f737afd6eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247222"
---
# <a name="hosts"></a>主控件
BizTalk 主控件物件代表零個或多個執行階段程序的一組邏輯，在此執行階段程序中您可以部署服務、管線與其他成品。 主控件物件也代表執行階段執行個體的集合 (零個或多個)，是已部署的項目實際執行的位置。  
  
 在您建立主控件 (邏輯容器) 之後，可以將實體 BizTalk 伺服器 (主控件執行個體) 新增至主控件。 您不能新增 BizTalk Server 至相同的主控件一次以上。 您可以新增單一主控件執行個體至多個主控件。  
  
 包含在 BizTalk 主控件中的項目 (例如，配接器處理常式、接收位置 (包括管線) 以及協調流程) 可以執行下列功能：  
  
-   **接收**。 在接收位置拾取訊息之後，這些項目會進行訊息的初始處理。 當主控件包含接收項目時 (例如接收位置或管線)，它將做為安全範圍，而訊息解碼和解密都發生在主控件的管線中。  
  
-   **傳送**。 這些項目會在訊息傳送到傳送埠之前，進行訊息的最後處理。 當主控件包含傳送項目時 (例如，傳送埠或管線)，主控件將做為安全範圍，而訊息簽章和加密都發生在主控件的管線中。  
  
-   **處理**。 這些項目會處理以協調流程中指示為基礎的訊息。  
  
 一個 BizTalk 主控件可以包含接收、傳送和處理訊息的項目。 建議您為每個功能建立不同的主控件，以建立安全範圍並協助管理。 尤其，建議您使用不同的主控件來進行處理、接收/傳送，並將信任和非信任的項目分開。  
  
 下圖顯示伺服器、主控件與主控件執行個體之間的關係。  
  
 ![主控件、 主控件執行個體和伺服器關係](../core/media/ebiz-ops-adm01.gif "ebiz_ops_adm01")  
主控件、主控件執行個體與伺服器之間的關係  
  
 如需主控件執行個體的詳細資訊，請參閱[主控件執行個體](../core/host-instances.md)。  
  
 根據裝載的實體組態與配接器類型，共有兩種類型的主控件：內含式主控件與外掛式主控件。  
  
## <a name="in-process-hosts"></a>內含式主控件  
 內含式主控件代表系統管理員建立、 刪除和完全控制 Windows Management Instrumentation (WMI) 與 BizTalk 管理主控台中的服務執行個體。  
  
 內含式主控件具有下列特性：  
  
-   您可以將任何協調流程登錄到內含式主控件。  
  
-   內含式主控件可以裝載任何傳送處理常式。  
  
-   內含式主控件可以裝載 SOAP 和 HTTP 以外的任何接收處理常式：  
  
    -   FILE  
  
    -   FTP  
  
    -   MQSeries  
  
    -   MSMQ  
  
    -   POP3  
  
    -   SQL  
  
    -   Windows SharePoint Services  
  
-   您在建立第一個 「 內含式主控件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署**預設主控件**，您不能刪除它。 「BizTalk 訊息佇列」配接器為靜態處理常式組態使用預設主控件。 加入配接器可以為預設主控件自動建立接收埠和傳送埠。  
  
## <a name="isolated-hosts"></a>外掛式主控件  
 外掛式主控件代表解決方案開發人員可用程式設計方式來建立、刪除和控制的服務執行個體。 系統管理員會使用 WMI 與 BizTalk 管理主控台來設定這些主控件 (例如，設定主控件服務帳戶與驗證信任)。  
  
 外掛式主控件主要裝載必須在一般 BizTalk Server 執行階段程序之外執行的配接器。 例如，您可以使用外掛式主控件為外部程序 (例如 ISAPI 延伸模組與 ASP.NET) 裝載配接器。  
  
 外掛式主控件具有下列特性：  
  
-   您不能將協調流程登錄到外掛式主控件。  
  
-   外掛式主控件不能裝載傳送處理常式。  
  
-   外掛式主控件只能裝載與 HTTP/S 及 SOAP 配接器 (外掛式類型配接器) 關聯的接收處理常式。  
  
-   外掛式主控件不能裝載追蹤。  
  
-   外掛式主控件不能做為預設主控件。  
  
-   外掛式主控件的狀態永遠是**狀態無法使用**。 BizTalk Server 不會存取外部程序的狀態資訊。  
  
> [!NOTE]
>  只要主控件執行個體共用相同的安全性組態 (驗證信任)，它們就可以共用相同的服務帳戶。  
  
## <a name="trusted-and-untrusted-hosts"></a>信任與非信任的主控件  
 BizTalk Server 可讓識別為驗證信任的主控件指出信任的主控件佇列至 MessageBox 資料庫的訊息傳送者為實體，而不是信任的主控件本身。 驗證信任的主要目的是要讓管線解析為「產品識別碼」(PID)，並將該 PID 傳遞至取用的服務，以供授權和輸出合作對象解析使用，並讓傳送者的「Windows 安全性識別碼」(SSID) 傳輸到取用的服務，以供協調流程動作授權使用。  
  
## <a name="see-also"></a>另請參閱  
 [主控件執行個體](../core/host-instances.md)   
 [管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)  
 [實體](../core/entities.md)