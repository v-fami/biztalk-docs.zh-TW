---
title: 如何備份自訂資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom databases
- customizing, custom databases
- backing up, custom databases
ms.assetid: 86bebf3c-968e-4fad-9dab-ced1b04aaac7
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2993de90de3f7b768cc5368012d1f27f8940a99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247334"
---
# <a name="how-to-back-up-custom-databases"></a>如何備份自訂資料庫
由於自訂資料庫不會隨 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 一起安裝，因此沒有包括在可供「備份 BizTalk Server」作業標示及備份的預設資料庫清單中。 如果要讓「備份 BizTalk Server」工作備份自訂資料庫，您必須手動將該資料庫加入「備份 BizTalk Server」工作。  
  
## <a name="prerequisites"></a>必要條件  
  
1.  SQL Server 必須設定為使用完整復原模式，以確保資料完整性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫備份集。  如需詳細資訊，請參閱[記錄傳送](../core/log-shipping.md)。  
  
2.  若要備份自訂資料庫，您必須透過有權存取待備份之各個資料庫的使用者帳戶進行登入。  
  
     BizTalk Server 包含名為 BTS_BACKUP_USERS 的 SQL Server 角色；如此一來，除非是在控制備份程序的主要伺服器中，否則您用來備份資料庫的使用者帳戶並不需要 SQL Server 中的「系統管理員」權限。  
  
     設定用來備份資料庫的使用者帳戶時，要注意下列事項：  
  
    -   您必須為此使用者建立 SQL Server 登入帳戶，並且在每部伺服器上將該使用者指派給 BizTalk BTS_BACKUP_USERS 角色。  
  
    -   BizTalk Server 的備份工作可以設定為在不同的 SQL Server Agent 服務所使用的使用者帳戶下執行。  
  
    -   您必須設定 SQL Server 代理程式服務，才能以網域帳戶來執行。 如果所有資料庫都在同一台電腦，您可以設定 SQL Server 代理程式使用本機帳戶。  
  
### <a name="to-back-up-custom-databases"></a>備份自訂資料庫  
  
1.  在新資料庫中建置物件：  
  
    -   瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]結構描述目錄，並針對所有想要備份您自訂資料庫執行 Backup_Setup_All_Procs.sql 和 Backup_Setup_All_Tables.sql。 這會建立必要的程序、資料表和角色，並將權限指派給預存程序。  
  
2.  執行下列組態：  
  
    -   將裝載 BizTalk 管理資料庫的 SQL Server 連結至裝載新資料庫的 SQL Server。 在管理 SQL Server 上用來執行 SQL Server 代理程式服務的帳戶必須是對應到每一台儲存待備份資料庫之電腦的網域帳戶。 如果資料庫是在同一台電腦上，您可以略過此步驟。 步驟會自動完成。  
  
    -   為在管理 SQL Server 上執行 SQL Server 代理程式服務的帳戶在裝載新資料庫的 SQL Server 中新增登入。 如果資料庫是在同一台電腦上，您可以略過此步驟。  
  
    -   在新資料庫中為上一個步驟建立的登入新增使用者，並將他們新增至 BTS_BACKUP_USERS 角色。 這個角色是由步驟 1 的指令碼建立並授與必要程序的「執行」權限。  
  
3.  在 BizTalk 管理 (BizTalkMgmtDb) 資料庫中，使用 SQL Server Enterprise Manager 或 SQL Server Management Studio，來修改**adm_OtherBackupDatabases**包含自訂資料庫的每個資料列的資料表。  
  
4.  請在對應欄位中輸入新的伺服器及資料庫名稱，如下表所示。  
  
    |資料行|值|  
    |------------|-----------|  
    |DefaultDatabaseName|自訂資料庫的易記名稱。|  
    |DatabaseName|自訂資料庫的名稱。|  
    |ServerName|執行 SQL Server 的電腦名稱。|  
    |BTSServerName|BizTalk Server 的名稱。 雖然用不到這個值，但還是必須含有一個值。|  
  
 下次執行「備份 BizTalk Server」工作時，此工作便會備份自訂資料庫。  
  
## <a name="see-also"></a>另請參閱  
 [備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)   
 [備份和還原的相關進階的資訊](../core/advanced-information-about-backup-and-restore1.md)