---
title: "處理伺服器的連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 2016-01-07
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, processing
- ports, processing servers
ms.assetid: 0207b68f-8769-4674-aadc-b3a67b6f210b
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4539a17ae95f02c17c754ddcf44882911d805b5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ports-for-the-processing-servers"></a>處理伺服器的連接埠
如需保護 BizTalk Server 部署安全的完整資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。  
  
 下表列出處理伺服器存取所需服務時，必須設定的連接埠。 您需要開啟連接埠的防火牆，視目的地伺服器在架構中的位置而不同。 您必須為輸入與輸出流量開啟這些連接埠。  
  
|服務或應用程式內容|目的地伺服器|目的地服務|通訊埠|通訊協定|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|登入使用者|BizTalk 管理資料庫|SQL Server|1433|TCP|建立和設定 BizTalk 管理資料庫|  
|登入使用者|BizTalk 管理資料庫|DTC|135|TCP|用於建立、設定及更新資料庫的 SQL Server 交易連線|  
|登入使用者|BizTalk 管理資料庫|DTC|50000-50200|TCP|次要 RPC 連接埠**附註：**您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|登入使用者|MessageBox 資料庫|SQL Server|1433|TCP|建立和設定 MessageBox 資料庫|  
|登入使用者|MessageBox 資料庫|DTC|135|TCP|用於建立主控件的 SQL Server 交易連線|  
|登入使用者|MessageBox 資料庫|DTC|50000-50200|TCP|次要 RPC 連接埠**附註：**您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|SSO 服務帳戶|SSO 資料庫|SQL Server|1433|TCP|供企業單一登入服務連接到 SSO 資料庫|  
|登入使用者|SSO 資料庫|DTC|135|TCP|用於連接到 SSO 資料庫的 SQL Server 交易連線|  
|登入使用者|SSO 資料庫|DTC|50000-50200|TCP|次要 RPC 連接埠**附註：**您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|登入使用者|追蹤資料庫|SQL Server|1433|TCP|建立和設定追蹤資料庫|  
|登入使用者|追蹤資料庫|DTC|135|TCP|SQL Server 交易連線|  
|登入使用者|追蹤資料庫|DTC|50000-50200|TCP|次要 RPC 連接埠**附註：**您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|登入使用者|商務規則引擎資料庫|SQL Server|1433|TCP|建立和設定商務規則引擎資料庫|  
|登入使用者|商務規則引擎資料庫|DTC|135|TCP|用於建立、設定及更新資料庫的 SQL Server 交易連線|  
|登入使用者|商務規則引擎資料庫|DTC|50000-50200|TCP|次要 RPC 連接埠**附註：**您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|登入使用者|BAM 分析資料庫|OLAP|2393|TCP|更新和擷取 BAM 分析資料庫資訊|  
|登入使用者|BAM 分析資料庫|OLAP 伺服器檔案系統|445|TCP|在遠端電腦上建立 OLAP 資料檔案 (.mdb)|  
|登入使用者|BAM 分析資料庫|OLAP|2725|TCP|擷取資料以進行分析 (樞紐分析表)|  
|登入使用者|BizTalk 分析資料庫|OLAP|2393|TCP|若要建立和設定 BizTalk 分析資料庫**附註：**處理伺服器連接到此資料庫，只有當您執行 BizTalk 組態管理員時，才需要。|  
|登入使用者|BizTalk 分析資料庫|OLAP 伺服器檔案系統|445|TCP|若要在遠端電腦上建立 OLAP 資料檔案 (.mdb)**附註：**處理伺服器連接到此資料庫，只有當您執行 BizTalk 組態管理員時，才需要。|  
|登入使用者|BizTalk 分析資料庫|OLAP|2725|TCP|建立和設定資料庫，並擷取資料以分析 (樞紐分析表)|  
|單一登入服務帳戶|主要密碼伺服器|RPC|135|TCP|供 SSO 服務連接到主要密碼伺服器的 SQL Server 交易連線|  
|單一登入服務帳戶|主要密碼伺服器|次要 RPC|50000-50200|TCP|供 SSO 服務連接到主要密碼伺服器的次要 RPC 連接埠。 **注意：**您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|BizTalk 主控件執行個體的服務帳戶|MessageBox 資料庫|SQL Server|1433|TCP|在執行階段作業期間更新和擷取資料庫的資訊|  
|BizTalk 主控件執行個體的服務帳戶|BizTalk 管理資料庫|SQL Server|1433|TCP|在執行階段作業期間更新和擷取資料庫的資訊|  
|BizTalk 主控件執行個體的服務帳戶|SSO 資料庫|SQL Server|1433|TCP|在執行階段作業期間更新和擷取資料庫的資訊|  
|BizTalk 主控件執行個體的服務帳戶|追蹤資料庫|SQL Server|1433|TCP|在執行階段作業期間更新和擷取資料庫的資訊|  
  
## <a name="see-also"></a>另請參閱  
 [伺服器命名慣例](../core/server-naming-conventions.md)   
 [BizTalk Server 執行階段安全性建議](../core/biztalk-server-runtime-security-recommendations.md)   
 [商務規則引擎安全性建議](../core/business-rule-engine-security-recommendations.md)   
 [具有資訊工作者服務的大型分散式的架構](../core/large-distributed-architecture-with-information-worker-services.md)   
 [必要的連接埠，以便讓 BizTalk Server](../core/required-ports-for-biztalk-server.md)