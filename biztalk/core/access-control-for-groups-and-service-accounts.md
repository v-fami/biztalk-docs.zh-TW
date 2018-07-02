---
title: 群組和服務帳戶的存取控制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- access control, service accounts
- user accounts, default accounts
- service accounts, security
- user accounts, unsupported
- access control, groups
- service accounts, access control
- groups, access control
- groups, security
ms.assetid: 411a7bfa-6675-4d09-9e37-83e2941df3c6
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da1bb9a52bef2e81729a8b566e4af4dcbed89c2a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021788"
---
# <a name="access-control-for-groups-and-service-accounts"></a>群組和服務帳戶的存取控制
每個 BizTalk 主控件執行個體會在使用者建立的服務帳戶下執行。 在電腦上建立主控件執行個體時，您必須提供服務帳戶及密碼。 BizTalk Server 會接著確定帳戶擁有執行工作所需的最低使用者權限，其方法是新增這每一個服務帳戶到本機或網域的 Windows 群組，然後再將此群組加入至該主控件特定的「SQL Server 資料庫」角色。  
  
 這種處理方式會產生下列好處：  
  
- 您可以賦予每個主控件執行個體各自不同的服務帳戶，讓每個主控件執行個體都可以變更密碼，而無須使伺服器離線。 您可以執行輪替的密碼更新，而不會中斷服務。  
  
  > [!NOTE]
  >  對於驗證為信任的主控件以及未驗證為信任的主控件，不可以兩邊都使用相同的服務帳戶。  
  
- 如果是在 Microsoft SQL Server™ 層級將資源使用者權限授與本機或網域群組，您就可以增加或減少服務帳戶，而無須變更 SQL Server 所授與的使用者權限；因此可以減輕您的管理負擔和擁有帳戶的總成本。  
  
  為了確保服務帳戶擁有執行其工作所需的最低使用者權限，BizTalk Server 為服務帳戶建立的「SQL Server 資料庫」角色，在所有的 BizTalk Server 資料庫上都不盡相同。 在「管理」和「追蹤」資料庫中，所有的主控件執行個體服務帳戶都必須存取相同的 SQL Server 物件，因此 BizTalk Server 建立名為 BTS_Host_User 的單一「SQL Server 資料庫」角色。 BizTalk 會將針對 BizTalk 主控件而建立的所有 Windows 群組新增到這個「SQL Server 資料庫」角色。  
  
  在 MessageBox 資料庫中，每個主控件都有一些本身專用的資源。 BizTalk Server 會建立 SQL Server 資料庫角色，每一部主機，命名為 Bts_&lt\<*hostname*\>（_u)，並新增到其個別的 SQL Server 資料庫角色的每個主控件 Windows 群組，以封鎖存取的其中一個由另一部主機的主機資源。  
  
## <a name="accounts-not-supported-by-biztalk-server"></a>BizTalk Server 不支援的帳戶  
 BizTalk Server 不支援使用下列任何內建的 Windows 帳戶：  
  
-   NT_AUTHORITY\NetworkService  
  
-   LocalSystem  
  
-   NT_AUTHORITY\LocalService  
  
## <a name="see-also"></a>另請參閱  
 [系統管理角色的存取控制](../core/access-control-for-administrative-roles.md)   
 [最低安全性使用者權限](../core/minimum-security-user-rights.md)   
 [Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)   
 [存取控制和資料安全性](../core/access-control-and-data-security.md)