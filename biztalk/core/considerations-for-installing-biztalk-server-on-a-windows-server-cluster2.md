---
title: "Windows Server Cluster2 上安裝 BizTalk Server 的考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Configure Your Server Wizard
- installing, Windows Server cluster
- BizTalk Server Configuration Wizard
- Windows Server cluster, warnings
- high availability, Windows Server cluster
- clustering, Windows Server cluster
- domain groups
- Windows Server cluster, Configure Your Server Wizard
- Network DTC access
- MSDTC
ms.assetid: 4daea7c6-7d26-440c-a2a0-fa018a25b2b3
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38bd34862efb0cd73e66a2c694abd26b823766db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-for-installing-biztalk-server-on-a-windows-server-cluster"></a>在 Windows 伺服器叢集上安裝 BizTalk Server 的考量
在 Windows 伺服器叢集上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時必須有一些特殊考量。 本主題將列出這些考量。  
  
## <a name="a-non-clustered-biztalk-host-instance-should-not-be-run-on-a-windows-server-cluster-where-the-enterprise-sso-service-is-clustered"></a>非叢集 BizTalk 主控件執行個體不應該在「企業單一登入」服務已叢集化的 Windows 伺服器叢集上執行  
 建議的做法是在主動/被動組態中叢集化「企業單一登入主要密碼伺服器」，為主要密碼伺服器提供高可用性。 如果非叢集 BizTalk 主控件執行個體與「企業單一登入」服務的叢集執行個體在相同的叢集節點上執行，則一旦叢集「企業單一登入」服務移至叢集中的其他節點，BizTalk 主控件執行個體就會失效。 BizTalk 主控件與本機執行的「企業單一登入」服務執行個體保持相依。 因此如果 「 企業單一登入 」 服務設定為叢集資源，然後在叢集節點上執行所有 BizTalk 主控件必須都設定為相同的叢集群組中叢集資源。  
  
## <a name="configure-the-microsoft-distributed-transaction-coordinator-msdtc-as-a-clustered-resource-before-installing-biztalk-server-on-a-cluster"></a>在叢集上安裝 BizTalk Server 前，必須先將 Microsoft 分散式交易協調器 (MSDTC) 設定為叢集資源  
 如果您打算在 Windows 伺服器叢集上安裝 BizTalk Server，必須先將 Microsoft 分散式交易協調器叢集化。  
  
 若要在 Windows Server 2008 容錯移轉叢集上叢集 MSDTC，請遵循中概述的步驟[檢查清單： Windows Server 2008 容錯移轉叢集中建立 MS DTC 資源](http://go.microsoft.com/fwlink/?LinkID=129677)  
  
## <a name="network-dtc-access-must-be-enabled-on-all-biztalk-servers-and-on-the-sql-server-before-installing-or-configuring-biztalk-server"></a>所有 BizTalk Server 和 SQL Server，才能安裝或設定 BizTalk Server 上必須啟用網路 DTC 存取  
 若要啟用網路 DTC 存取 SQL Server 將裝載 BizTalk Server 資料庫以及每個叢集節點上，請依照下列所述的步驟[如何啟用網頁伺服器上的 MSDTC](http://go.microsoft.com/fwlink/?LinkId=189701) (http://go.microsoft.com/fwlink/?LinkId=189701)。 必須啟用網路 DTC 存取，才能配合 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的交易支援。 建議您在完成該份知識庫文章中說明的步驟後重新啟動每一部伺服器。  
  
## <a name="you-must-manually-create-domain-groups-in-active-directory-before-you-configure-biztalk-server"></a>您必須先在 Active Directory 中手動建立網域群組，然後再設定 BizTalk Server  
 如果您安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]多部電腦，您必須指定網域群組和使用者帳戶[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態精靈。 如果您使用網域群組您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態中，您必須手動建立群組之後再設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。