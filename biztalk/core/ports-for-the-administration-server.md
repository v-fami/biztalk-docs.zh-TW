---
title: "管理伺服器的連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, administration server
- administration server
ms.assetid: dc0094b2-5ba2-4b8f-84aa-b6232be358ee
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd44158d721f8b6d247b51073e9f9e77ea7f6deb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ports-for-the-administration-server"></a>管理伺服器的連接埠
如需保護 BizTalk Server 部署安全的完整資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。  
  
 下表列出您必須為管理伺服器設定的連接埠，以存取它們所需的服務。 您需要開啟連接埠的防火牆，視目的地伺服器在架構中的位置而不同。 
  
|目的地伺服器|目的地服務|通訊埠|通訊協定|Reason|  
|---|---|---|---|---|  
|BizTalk 管理資料庫|SQL Server|1433|TCP|建立、設定及存取 BizTalk 管理資料庫中的資訊|  
|BizTalk 管理資料庫|DTC|135|TCP|用於更新資料庫的 SQL Server 交易連線|  
|BizTalk 管理資料庫|DTC|50000-50200|TCP|次要 RPC 連接埠**附註：**您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|BAM 主要匯入資料庫|SQL Server|1433|TCP|使用 BizTalk 管理主控台 (或 WMI) 驗證 BAM 主要匯入資料庫的存在|  
|BizTalk 管理資料庫|SQL Server|1433|TCP|使用 BizTalk 管理主控台 (或 WMI) 檢視組態資料與安裝主控件執行個體|  
|BizTalk 管理資料庫|DTC|135|TCP|用於使用 BizTalk 管理主控台 (或 WMI) 建立和更新主控件的 SQL Server 交易連線|  
|BizTalk 管理資料庫|DTC|50000-50200|TCP|使用 BizTalk 管理主控台 （或 WMI） 建立主控件的次要 RPC 連接埠**附註：**您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|MessageBox 資料庫|SQL Server|1433|TCP|使用 BizTalk 管理主控台 (或 WMI) 建立主控件|  
|MessageBox 資料庫|DTC|135|TCP|用於使用 BizTalk 管理主控台 (或 WMI) 建立和更新主控件的 SQL Server 交易連線|  
|MessageBox 資料庫|DTC|50000-50200|TCP|使用 BizTalk 管理主控台 （或 WMI） 建立主控件的次要 RPC 連接埠**附註：**您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|處理伺服器|WMI/RPC|135|TCP|用於使用 BizTalk 管理主控台 (或 WMI) 將新伺服器加入群組的 SQL Server 交易連線|  
|處理伺服器|WMI/RPC|50000-50200|TCP|使用 BizTalk 管理主控台 （或 WMI） 將新的伺服器新增至群組的次要 RPC 連接埠**附註：**您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|處理伺服器|伺服器訊息區塊 (SMB)|445|TCP|用來存取檔案共用。 也可能需要安裝使用 BizTalk 管理主控台 （或 WMI） 的主控件執行個體。|  
|商務規則引擎資料庫|SQL Server|1433|TCP|使用商務規則引擎部署精靈部署商務規則|  
|商務規則引擎資料庫|DTC|135|TCP|用於使用商務規則引擎部署精靈來部署商務規則的 SQL Server 交易連線|  
|商務規則引擎資料庫|DTC|50000-50200|TCP|使用商務規則引擎部署精靈來部署商務規則的次要 RPC 連接埠 **注意：**您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
|BizTalk 管理資料庫|SQL Server|1433|TCP|部署組件|  
|追蹤資料庫|SQL Server|1433|TCP|部署組件|  
|IIS 伺服器|IIS|1164|TCP|若要啟用以 HTTP 或 Web 服務連接埠的 BizTalk 應用程式部署 IIS 伺服器上裝載包裝在 msi。|  
  
## <a name="see-also"></a>另請參閱  
 [伺服器命名慣例](../core/server-naming-conventions.md)   
 [應用程式部署的安全性建議](../core/application-deployment-security-recommendations.md)   
 [訊息與執行個體資料追蹤的安全性考量](../core/security-considerations-for-message-and-instance-data-tracking.md)   
 [具有資訊工作者服務的大型分散式的架構](../core/large-distributed-architecture-with-information-worker-services.md)   
 [必要的連接埠，以便讓 BizTalk Server](../core/required-ports-for-biztalk-server.md)