---
title: "如何移動 BAM 星狀結構描述 Database1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Star Schema database [BAM], migrating
- migrating, Star Schema database [BAM]
ms.assetid: b4a5f8fc-0dc4-4987-b96f-ecd49bd4dba3
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6661a9ae315988a5348198fa463e24ea508cf50f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-bam-star-schema-database"></a>如何移動 BAM 星狀結構描述資料庫
您可以使用這個程序將「BAM 星狀結構描述」資料庫移動到其他伺服器。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。  
  
### <a name="to-move-the-bam-star-schema-database"></a>移動 BAM 星狀結構描述資料庫  
  
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
  
2.  依照《SQL Server 線上叢書》中關於如何在舊伺服器上備份資料庫的指示執行。  
  
3.  將「BAM 星狀結構描述」資料庫複製到新的 SQL Server。  
  
4.  依照《SQL Server 線上叢書》中關於如何在新伺服器上還原資料庫的指示執行。  
  
5.  編輯 BAMConfiguration.xml 檔案，並將 StarSchemaDatabase DeploymentUnit 區段中的 ServerName 變更為新的伺服器名稱。  
  
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
  
10. 依照下列步驟，更新 SQL 連線 2 以變更所有 BAM 分析 DTS 封裝中的伺服器及資料庫名稱 (這些名稱以 "BAM_AN_" 作為前置詞)：  
  
    1.  使用 SQL Server Management Studio，開啟裝載 BAM 的伺服器。  
  
    2.  開啟**Data Transformation Services**資料夾。  
  
    3.  開啟**本機封裝**資料夾。  
  
    4.  開啟 DTS 封裝，然後再連按兩下**連線 2**來開啟連接。  
  
    5.  選取下拉式方塊中的新伺服器及資料庫名稱。  
  
11. 更新 BAM 分析資料庫中的資料來源，如下所示：  
  
    1.  使用 SQL Server 分析管理員，開啟裝載 BAM 分析資料庫的伺服器。  
  
    2.  開啟**資料來源**資料夾。  
  
    3.  以滑鼠右鍵按一下 cube 的資料來源，然後按一下**編輯**。  
  
    4.  在**連接**索引標籤上，輸入新的伺服器名稱和 BAM 星狀結構描述資料庫的資料庫名稱，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [移動 BizTalk Server 資料庫](../core/moving-biztalk-server-databases.md)