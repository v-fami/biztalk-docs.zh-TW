---
title: 連接埠為企業單一登入伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 2016-01-07
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ports, SSO
- SSO
ms.assetid: 30eb99f9-02cb-43c9-b038-d7bd898e3a7a
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c0335a6a09cb8d323261c2d8357cc3d5b929b61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22265302"
---
# <a name="ports-for-the-enterprise-single-sign-on-servers"></a>企業單一登入伺服器的連接埠
如需保護 BizTalk Server 部署安全的完整資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。  
  
 下表列出處理網域中的「企業單一登入」伺服器存取主要密碼伺服器與 SSO 資料庫所需的連接埠。 您必須為輸入與輸出流量開啟這些連接埠。  
  
|服務或應用程式內容|目的地伺服器|目的地服務|通訊埠|通訊協定|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|登入使用者|SSO 資料庫|SQL Server|1433|TCP|建立和連線到 SSO 資料庫。|  
|單一登入服務帳戶|主要密碼伺服器|單一登入服務|135|TCP|單一登入服務的 SQL Server 交易連線，以擷取主要密碼伺服器的主要密碼|  
|單一登入服務帳戶|主要密碼伺服器|單一登入服務|50000-50200|TCP|用來從主要密碼伺服器擷取密碼的次要 RPC 連接埠。 **注意：** 您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
  
 下表列出必須設定用於「企業單一登入」(SSO) 主要密碼伺服器以存取它們所需服務的連接埠。 您需要開啟連接埠的防火牆，視目的地伺服器在架構中的位置而不同。 您必須為輸入與輸出流量開啟這些連接埠。  
  
|服務或應用程式內容|目的地伺服器|目的地服務|通訊埠|通訊協定|Reason|  
|------------------------------------|------------------------|-------------------------|----------|--------------|------------|  
|登入使用者|SSO 資料庫|SQL Server|1433|TCP|建立和連線到 SSO 資料庫。|  
|單一登入服務帳戶|處理伺服器|單一登入服務|135|TCP|單一登入服務的 SQL Server 交易連線，以擷取主要密碼伺服器的主要密碼|  
|單一登入服務帳戶|處理伺服器|單一登入服務|50000-50200|TCP|用來從主要密碼伺服器擷取密碼的次要 RPC 連接埠。 **注意：** 您可能需要開啟多個次要的 RPC 連接埠，根據您的伺服器負載。|  
  
## <a name="see-also"></a>另請參閱  
 [伺服器命名慣例](../core/server-naming-conventions.md)   
 [SSO 安全性建議](../core/sso-security-recommendations.md)   
 [具有資訊工作者服務的大型分散式的架構](../core/large-distributed-architecture-with-information-worker-services.md)   
 [必要的連接埠，以便讓 BizTalk Server](../core/required-ports-for-biztalk-server.md)