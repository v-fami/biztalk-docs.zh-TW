---
title: 接收和傳送伺服器的連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 2016-01-07
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection strings
- servers, sending
- ports, servers
- servers, receiving
- BizTalk Server, service accounts
- SSO, service accounts
ms.assetid: 19cafe74-6676-4779-8ced-de0841dba19f
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04ddda71d04cf784f07cf8e0783775d7ae91e6d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22266478"
---
# <a name="ports-for-the-receive-and-send-servers"></a>接收和傳送伺服器的連接埠
如需保護 BizTalk Server 部署安全的完整資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。  
  
 下表列出接收和傳送伺服器存取所需的服務時，必須設定的連接埠。 您需要開啟連接埠的防火牆，視目的地伺服器在架構中的位置而不同。 您必須為輸入與輸出流量開啟這些連接埠。  
  
|服務或應用程式內容|目的地伺服器|目的地服務|通訊埠|通訊協定|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|BizTalk 服務帳戶|檔案共用<br /><br /> EDI 文件首頁共用|接收/傳送伺服器|445|TCP|擷取和放置檔案至 FILE 配接器的檔案位置|  
|BizTalk 服務帳戶|FTP 伺服器|FTP 服務|20|TCP|供 FTP 配接器從 FTP 伺服器擷取和放置檔案|  
|BizTalk 服務帳戶|FTP 伺服器|FTP 服務|21|TCP|供 FTP 配接器從 FTP 伺服器擷取和放置檔案|  
|BizTalk 服務帳戶|POP3 伺服器|POP3 服務|110|TCP|供 POP3 配接器從 POP3 伺服器擷取電子郵件|  
|BizTalk 服務帳戶|處理伺服器|Windows 訊息佇列|1801|TCP|供 BizTalk 訊息佇列配接器從 BizTalk 執行階段接收和傳送訊息|  
|連接字串|SQL 配接器目標|SQL Server|1433|TCP|從 SQL 配接器所用的資料庫擷取和傳送訊息|  
|連接字串|SQL 配接器目標|DTC|135|TCP|用於 SQL 配接器的 SQL Server 交易連線|  
|連接字串|SQL 配接器目標|DTC|50000-50200|TCP|SQL 配接器的次要 RPC 連接埠**附註：** 您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|BizTalk 服務帳戶|SMTP/Exchange|SMTP|25|TCP|供 SMTP 配接器連接到 SMTP 伺服器|  
|登入使用者|BizTalk 管理資料庫|SQL Server|1433|TCP|建立和設定 BizTalk 管理資料庫|  
|登入使用者|BizTalk 管理資料庫|DTC|135|TCP|用於建立、設定及更新資料庫的 SQL Server 交易連線|  
|登入使用者|BizTalk 管理資料庫|DTC|50000-50200|TCP|次要 RPC 連接埠**附註：** 您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|登入使用者|MessageBox 資料庫|SQL Server|1433|TCP|建立和設定 MessageBox 資料庫|  
|登入使用者|MessageBox 資料庫|DTC|135|TCP|用於建立主控件的 SQL Server 交易連線|  
|登入使用者|MessageBox 資料庫|DTC|50000-50200|TCP|次要 RPC 連接埠**附註：** 您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|SSO 服務帳戶|SSO 資料庫|SQL Server|1433|TCP|供企業單一登入服務連接到 SSO 資料庫|  
|登入使用者|SSO 資料庫|DTC|135|TCP|用於連接到 SSO 資料庫的 SQL Server 交易連線|  
|登入使用者|SSO 資料庫|DTC|50000-50200|TCP|次要 RPC 連接埠**附註：** 您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|登入使用者|追蹤資料庫|SQL Server|1433|TCP|建立和設定追蹤資料庫|  
|登入使用者|追蹤資料庫|DTC|135|TCP|SQL Server 交易連線|  
|登入使用者|追蹤資料庫|DTC|50000-50200|TCP|次要 RPC 連接埠**附註：** 您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|登入使用者|商務規則引擎資料庫|SQL Server|1433|TCP|建立和設定商務規則引擎資料庫|  
|登入使用者|商務規則引擎資料庫|DTC|135|TCP|用於建立、設定及更新資料庫的 SQL Server 交易連線|  
|登入使用者|商務規則引擎資料庫|DTC|50000-50200|TCP|次要 RPC 連接埠**附註：** 您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|登入使用者|BAM 分析資料庫|OLAP|2383 (SQL Server 2005 Analysis Services)|TCP|更新和擷取 BAM 分析資料庫資訊|  
|登入使用者|BAM 分析資料庫|OLAP 伺服器檔案系統|445|TCP|在遠端電腦上建立 OLAP 資料檔案 (.mdb)|  
|登入使用者|BAM 分析資料庫|OLAP|2725|TCP|擷取資料以分析 (樞紐分析表®)|  
|登入使用者|BizTalk 分析資料庫|OLAP|2383 (SQL Server 2005 Analysis Services)|TCP|若要建立和設定 BizTalk 分析資料庫**附註：** 處理伺服器連接到此資料庫，只有當您執行 BizTalk 組態管理員時，才需要。|  
|登入使用者|BizTalk 分析資料庫|OLAP 伺服器檔案系統|445|TCP|若要在遠端電腦上建立 OLAP 資料檔案 (.mdb)**附註：** 處理伺服器連接到此資料庫，只有當您執行 BizTalk 組態管理員時，才需要。|  
|登入使用者|BizTalk 分析資料庫|OLAP|2725|TCP|建立和設定資料庫，並擷取資料以分析 (樞紐分析表)|  
|單一登入服務帳戶|主要密碼伺服器|RPC|135|TCP|供 SSO 服務連接到主要密碼伺服器的 SQL Server 交易連線|  
|單一登入服務帳戶|主要密碼伺服器|次要 RPC|50000-50200|TCP|供 SSO 服務連接到主要密碼伺服器的次要 RPC 連接埠。 **注意：** 您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|BizTalk 主控件執行個體的服務帳戶|MessageBox 資料庫|SQL Server|1433|TCP|在執行階段作業期間更新和擷取資料庫的資訊|  
|BizTalk 主控件執行個體的服務帳戶|BizTalk 管理資料庫|SQL Server|1433|TCP|在執行階段作業期間更新和擷取資料庫的資訊|  
|BizTalk 主控件執行個體的服務帳戶|SSO 資料庫|SQL Server|1433|TCP|在執行階段作業期間更新和擷取資料庫的資訊|  
|BizTalk 主控件執行個體的服務帳戶|追蹤資料庫|SQL Server|1433|TCP|在執行階段作業期間更新和擷取資料庫的資訊|  
  
## <a name="see-also"></a>另請參閱  
 [伺服器命名慣例](../core/server-naming-conventions.md)   
 [HTTP 配接器安全性建議](../core/http-adapter-security-recommendations.md)   
 [SOAP 配接器安全性建議](../core/soap-adapter-security-recommendations.md)   
 [FTP 配接器安全性建議](http://msdn.microsoft.com/library/ea7c0577-9d72-4d63-94e7-8f649c6e713f)   
 [SMTP 配接器安全性建議](../core/smtp-adapter-security-recommendations.md)   
 [檔案配接器安全性建議](http://msdn.microsoft.com/library/fe4d51c0-b697-457b-bf27-f1cf6965d954)   
 [具有資訊工作者服務的大型分散式的架構](../core/large-distributed-architecture-with-information-worker-services.md)   
 [必要的連接埠，以便讓 BizTalk Server](../core/required-ports-for-biztalk-server.md)