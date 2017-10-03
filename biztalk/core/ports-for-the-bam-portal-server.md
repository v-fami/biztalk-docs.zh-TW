---
title: "BAM 入口網站伺服器的連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 2016-01-07
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df67c31c-a7a3-4bff-9374-0d8a0cf0ad21
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: adfa47415c1e367941203d20533c5e3ac3f431da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ports-for-the-bam-portal-server"></a>BAM 入口網站伺服器的連接埠
如需保護 BizTalk Server 部署安全的完整資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。  
  
 下表列出的連接埠必須針對 BAM 入口網站進行設定，才可存取它們所需要的服務。 您需要開啟連接埠的防火牆，視目的地伺服器在架構中的位置而不同。 您必須為輸入與輸出流量開啟這些連接埠。  
  
|服務或應用程式內容|目的地伺服器|目的地服務|通訊埠|通訊協定|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|登入使用者|BizTalk 管理資料庫|SQL Server|1433|TCP|建立和設定資料庫|  
|登入使用者|BizTalk 管理資料庫|DTC|135|TCP|用於建立、設定及更新資料庫的 SQL Server 交易連線|  
|登入使用者|BizTalk 管理資料庫|DTC|50000-50200|TCP|建立及連接到此資料庫的次要 RPC 連接埠**附註：**您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|應用程式集區|輸入用戶端|HTTP(S)|80 或 443|TCP|適用於網站的輸入流量|  
|登入使用者|MessageBox 資料庫|SQL Server|1433|TCP|建立和設定資料庫|  
|登入使用者|MessageBox 資料庫|DTC|135|TCP|用於建立、設定及更新資料庫的 SQL Server 交易連線|  
|登入使用者|MessageBox 資料庫|DTC|50000-50200|TCP|次要 RPC 連接埠**附註：**您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|SSO 服務帳戶|SSO 資料庫|SQL Server|1433|TCP|連線到 SSO 資料庫|  
|登入使用者|追蹤資料庫|SQL Server|1433|TCP|建立和設定資料庫|  
|登入使用者|商務規則引擎資料庫|SQL Server|1433|TCP|建立和設定資料庫|  
|登入使用者|商務規則引擎資料庫|DTC|135|TCP|用於建立、設定及更新資料庫的 SQL Server 交易連線|  
|登入使用者|商務規則引擎資料庫|DTC|50000-50200|TCP|次要 RPC 連接埠**附註：**您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|登入使用者|BAM 分析資料庫|OLAP|2393|TCP|建立和設定資料庫|  
|登入使用者|BAM 分析資料庫|OLAP 伺服器檔案系統|445|TCP|在遠端電腦建立 OLAP 資料檔案 (.mdb)|  
|登入使用者|BAM 分析資料庫|OLAP|2725|TCP|更新和擷取資料庫的資訊|  
|SSO 服務帳戶|SSO 資料庫|SQL Server|1433|TCP|供 SSO 服務更新及擷取資料庫的資訊|  
|SSO 服務帳戶|主要密碼伺服器|主要密碼伺服器|135|TCP|供 SSO 服務連接到主要密碼伺服器的 SQL Server 交易連線|  
|SSO 服務|主要密碼伺服器|次要 RPC|50000-50200|TCP|供 SSO 服務連接到主要密碼伺服器的次要 RPC 連接埠。 **注意：**您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|BizTalk 主控件執行個體|MessageBox 資料庫|SQL Server|1433|TCP|在執行階段作業期間更新和擷取資料庫的資訊|  
|BizTalk 主控件執行個體|BizTalk 管理資料庫|SQL Server|1433|TCP|在執行階段作業期間更新和擷取資料庫的資訊|  
|BizTalk 主控件執行個體|SSO 資料庫|SQL Server|1433|TCP|在執行階段作業期間更新和擷取資料庫的資訊|  
|BizTalk 主控件執行個體|追蹤資料庫|SQL Server|1433|TCP|在執行階段作業期間更新和擷取資料庫的資訊|  
|BAM 應用程式集區使用者|BAM Notification Services|SQL Server|1433|TCP|存取 BAM Notification Services 資料庫|  
  
## <a name="see-also"></a>另請參閱  
 [伺服器命名慣例](../core/server-naming-conventions.md)   
 [BAM 入口網站的安全性考量](../core/security-considerations-for-the-bam-portal.md)   
 [具有資訊工作者服務的大型分散式的架構](../core/large-distributed-architecture-with-information-worker-services.md)   
 [必要的連接埠，以便讓 BizTalk Server](../core/required-ports-for-biztalk-server.md)