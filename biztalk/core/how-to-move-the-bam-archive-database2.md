---
title: 如何移動 BAM 封存 Database2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Archive database [BAM], migrating
- migrating, Archive database [BAM]
ms.assetid: 88b96dc2-8c9c-43f5-afb9-a937e05de36b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4398e155168a903d39f3fbd1c9fd8f1421862cc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22253990"
---
# <a name="how-to-move-the-bam-archive-database"></a>如何移動 BAM 封存資料庫
您可以使用這個程序，將 BAM 封存資料庫移動到其他伺服器。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。  
  
### <a name="to-move-the-bam-archive-database"></a>移動 BAM 封存資料庫  
  
1.  取得用來還原 BAM 的 .xml 檔案複本：  
  
    1.  按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
    2.  在命令提示字元中，瀏覽至下列目錄：  
  
         [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking  
  
    3.  在命令提示字元中，輸入：  
  
        ```  
        Bm.exe get-config –filename:BAMConfiguration.xml  
        ```  
  
        > [!NOTE]
        >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
2.  依照 SQL Server 線上叢書 》 中的指示，備份舊伺服器上的資料庫。  
  
3.  將 BAM 封存資料庫複製到新的 SQL 伺服器。  
  
4.  依照 SQL Server 線上叢書 》 中的指示，將新的伺服器上還原資料庫。  
  
5.  編輯 BAMConfiguration.xml 檔案，並將 ArchivingDatabase DeploymentUnit 區段中的 ServerName 變更為新的伺服器名稱。  
  
6.  儲存並關閉 BAMConfiguration.xml 檔案。  
  
7.  按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
8.  在命令提示字元中，瀏覽至下列目錄：  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking  
  
9. 在命令提示字元中，輸入：  
  
    ```  
    bm.exe update-config -FileName:BAMConfiguration.xml  
    ```  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>另請參閱  
 [移動 BizTalk Server 資料庫](../core/moving-biztalk-server-databases.md)