---
title: 命名慣例的伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, naming conventions
- naming conventions, servers
- installation, naming conventions
ms.assetid: 98989c15-51d7-4a67-b054-abe6993a98a6
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a54e61a9ec37754158697a57a3f310d9edb90ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22273198"
---
# <a name="server-naming-conventions"></a>伺服器命名慣例
完成 BizTalk Server 部署的系統架構的詳細資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。  
  
 下表說明主題中的圖表中的伺服器[大型分散式架構](../core/large-distributed-architecture.md)，及其功能。  
  
|圖中的伺服器名稱|函數|Description|  
|----------------------------|--------------|-----------------|  
|FW4|防火牆|網際網路與周邊網路之間的 forefront Threat Management Gateway (TMG) 2010 server。|  
|HTTP (接收)|網頁伺服器|接收 HTTP 配接器訊息的 Web 伺服器。 此伺服器並未安裝 BizTalk Server 元件；它擁有可將訊息傳送到服務介面網域的 ASP.NET 頁面。 您可以使用從 FW 4 到 FW 3 的反向 Proxy 來取代 ASP.NET 頁面。 若您使用反向 Proxy，就不需要此伺服器。|  
|Exchange (傳送/接收)|郵件伺服器|BizTalk Server 用來傳送和接收 SMTP 訊息的郵件伺服器。 POP3 配接器會讀取已接收的訊息|  
|FTP (傳送/接收)|網頁伺服器|代表 BizTalk 傳送和接收訊息的檔案傳輸通訊協定 (FTP) 伺服器。 這可以是遠端伺服器。|  
|SQL|SQL Server|擁有 SQL 配接器所使用的 SQL Server 資料庫的伺服器。|  
|檔案|檔案伺服器|擁有檔案目錄的伺服器，服務介面網域中的 File 配接器會從中放置和拾取檔案。|  
|FW3|防火牆|Forefront Threat Management Gateway (TMG) 2010 server 保護服務介面網域免受周邊網路與企業網域。|  
|Processing|處理伺服器|此伺服器可處理訊息。 它擁有 BizTalk Server 執行階段、商務規則引擎以及企業單一登入 (SSO) 服務。 BizTalk 組件、主控件執行個體、協調流程、結構描述以及對應都在此伺服器上。 指定的處理伺服器可擁有不同主控件的主控件執行個體。|  
|接收處理常式<br /><br /> (外掛式主控件)|接收/傳送伺服器|專門從 HTTP 與 SOAP 配接器接收訊息的 BizTalk Server。 指定的接收/傳送伺服器可擁有不同主控件的主控件執行個體。|  
|接收處理常式<br /><br /> (內含式主控件)|接收/傳送伺服器|專門用來從 SQL、FTP、EDI、File、POP3 以及 BizTalk 訊息佇列配接器接收訊息的 BizTalk Server。 指定的接收/傳送伺服器可擁有不同主控件的主控件執行個體。|  
|傳送處理常式|接收/傳送伺服器|專門傳送所有配接器的訊息的 BizTalk Server。 指定的伺服器可擁有用來傳送訊息的不同主控件的主控件執行個體。|  
|FW2|防火牆|Forefront Threat Management Gateway (TMG) 2010 server 保護服務網域從服務介面與公司的網域 （作業服務）。|  
|追蹤主控件|追蹤伺服器|擁有用來追蹤的 BizTalk 主控件之主控件執行個體的伺服器。|  
|管理工具|管理伺服器|具有 BizTalk Server 執行階段、 BizTalk Server 管理主控台中，以及部署工具的伺服器。|  
|主要密碼伺服器|主要密碼伺服器|管理整個環境的主要密碼金鑰之 SSO 伺服器。 此電腦上沒有其他 BizTalk Server 元件。|  
|FW1|防火牆|保護資料網域和服務介面與服務網域影響的 forefront Threat Management Gateway (TMG) 2010 server。|  
|MessageBox 1<br /><br /> MessageBox 2<br /><br /> MessageBox 'n'|資料伺服器|包含 MessageBox 資料庫的 SQL Server。 您可以讓每個 MessageBox 資料庫有不同的 SQL Server。|  
|SSO|資料伺服器|包含 SSO 資料庫的 SQL Server，供企業單一登入以加密形式儲存用於登入其他系統的使用者 ID 與認證，並且以加密形式儲存 BizTalk Server 所用配接器的組態資訊表單。|  
|記錄傳送的備份/還原|資料伺服器|用來還原 BizTalk Server 資料庫產生之資料庫備份的 SQL Server。|  
|BizTalk 分析|資料伺服器|包含 BizTalk 分析資料庫的分析伺服器。|  
  
 下表說明主題中的圖表中的其他伺服器[具有資訊工作者服務的大型分散式架構](../core/large-distributed-architecture-with-information-worker-services.md)及其功能 > 主題中的圖進行比較[大分散式架構](../core/large-distributed-architecture.md)。  
  
|伺服器名稱|函數|Description|  
|-----------------|--------------|-----------------|  
|BAM 入口網站|BAM 入口網站|包含 BAM 入口網站的伺服器。 商務使用者使用 BAM 入口網站來存取 BAM 資料庫，以監控「關鍵效能指標」(KPI) 以及商務程序的其他相關資訊。|  
|通知服務<br /><br /> Windows SharePoint Services 組態<br /><br /> Windows SharePoint Services 內容<br /><br /> BAM 星狀結構描述<br /><br /> BAM 主要匯入<br /><br /> BAM 封存<br /><br /> BAM 分析 (OLAP)|IW 資料伺服器|包含商務活動監控所用的資料庫的 SQL Server。 您可以在這些資料庫使用多重 SQL Server。|  
|IW 用戶端|IW 用戶端|資訊工作者用於商務活動監控的用戶端電腦。|  
  
## <a name="see-also"></a>另請參閱  
 [大型分散式的架構](../core/large-distributed-architecture.md)   
 [具有資訊工作者服務的大型分散式的架構](../core/large-distributed-architecture-with-information-worker-services.md)   
 [BizTalk Server 架構範例](../core/sample-biztalk-server-architectures.md)