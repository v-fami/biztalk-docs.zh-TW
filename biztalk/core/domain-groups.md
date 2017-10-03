---
title: "網域群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: domain groups
ms.assetid: 9adc090e-e18c-46b6-b985-49b200d42966
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52fc5cc05718aa6d9e0ca89bc48467052fb916a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="domain-groups"></a>網域群組
BizTalk Server 在單一電腦組態和多電腦組態中都支援網域群組和使用者帳戶。 對於多電腦組態，您必須遵守本節以及《安裝指南》中的＜多伺服器環境的考量＞所規定的要求。 如需詳細資訊，請參閱[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)。  
  
-   若您在 BizTalk Server 組態使用網域群組，則必須在設定 BizTalk Server 之前手動建立群組。 「組態管理員」無法建立網域群組。  
  
-   建立網域群組和/或使用者帳戶之後, 將使用者帳戶新增到正確的群組中的群組分支機構根據[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。  
  
-   使用 **\<DomainName >\\< 使用者名稱\>** Configuration Manager 中指定網域帳戶資訊時。  
  
-   BizTalk Server 需要網域帳戶，才能用於所有叢集實例。 您無法將本機帳戶用於叢集化 SQL Server 或叢集化 SSO Server (主要密碼伺服器)。  
  
-   安裝和設定 BizTalk Server 系統管理員必須是下列群組的成員： SSO 系統管理員 （僅在設定主要密碼伺服器）。本機系統管理員。sysadmin SQL Server 角色。OLAP 系統管理員。  
  
> [!NOTE]
>  如果您在「SSO 系統管理員」和「SSO 分支機構系統管理員」組態設定期間指定網域群組，而且也有足夠的權限，則可以自動建立網域群組。 若您沒有足夠的權限，請確定這些群組已經存在。  
  
## <a name="see-also"></a>另請參閱  
 [本機群組](../core/local-groups.md)   
 [BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)   
 [BizTalk Server 中的 Windows 群組和使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)