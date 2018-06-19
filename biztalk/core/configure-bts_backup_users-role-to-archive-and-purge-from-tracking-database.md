---
title: 如何設定 BTS_BACKUP_USERS 角色以封存和清除來自 BizTalk 追蹤資料庫資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- purging, BTS_BACKUP_USERS role
- Tracking database, purging
- BTS_BACKUP_USERS role
- DTA Purge and Archive job
- archiving [Tracking database], BTS_BACKUP_USERS role
- archiving [Tracking database], DTA Purge and Archive job
- Tracking database, BTS_BACKUP_USERS role
- Tracking database, archiving
- purging, DTA Purge and Archive job
ms.assetid: c27aad2a-5788-4236-b5eb-ca730bf79851
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 923fb083f3755259ab2176541213d1637ce872c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232446"
---
# <a name="how-to-configure-the-btsbackupusers-role-for-archiving-and-purging-data-from-the-biztalk-tracking-database"></a>如何設定 BTS_BACKUP_USERS 角色以封存和清除來自 BizTalk 追蹤資料庫的資料
DTA 清除與封存 (BizTAlkDTADb) 工作通常使用已登入 SQL Server 代理程式服務帳戶使用者的認證來執行。 不過，若要確保更高的安全性，您可以設定 DTA 清除與封存 (BizTalkDTADb) 工作使用 BTS_BACKUP_USERS 角色之成員帳戶的認證來執行。 以具有基本權限之帳戶執行 SQL Server 代理程式工作有助於防止提升權限。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。  
  
### <a name="to-configure-the-btsbackupusers-role-for-archiving-and-purging-data-from-the-biztalk-tracking-database"></a>若要設定 BTS_BACKUP_USERS 角色以封存和清除來自 BizTalk 追蹤資料庫的資料  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft SQL Server 2008 SP2**，然後按一下  **SQL Server Management Studio**。  
  
2.  在**連接到伺服器**對話方塊中，指定 BizTalk 追蹤 (BizTalkDTADb) 資料庫所在的 SQL server 和適當的驗證類型的名稱，然後按一下**連接**至連接到適當的 SQL Server。  
  
3.  在**Microsoft SQL Server Management Studio**，連按兩下**BizTalkDTADb**，連按兩下**安全性**，連按兩下**角色**，和然後按兩下**資料庫角色**。  
  
4.  在**物件總管詳細資料** 窗格中，按兩下**BTS_BACKUP_USERS**。  
  
5.  在**資料庫角色屬性 – BTS_BACKUP_USERS**對話方塊的 **此角色的成員**，按一下 **新增**。  
  
6.  在**選取資料庫使用者或角色**對話方塊中，輸入具有 SQL Server Agent 服務認證的使用者帳戶，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)