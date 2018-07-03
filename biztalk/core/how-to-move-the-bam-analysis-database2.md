---
title: 如何移動 BAM 分析 Database2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migrating, Analysis database [BAM]
- Analysis database [BAM], migrating
ms.assetid: b0320273-4840-4573-bb82-bba95021535e
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 237f951a4795ef6571a72989be22893d57572df9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011791"
---
# <a name="how-to-move-the-bam-analysis-database"></a>如何移動 BAM 分析資料庫
您可以使用這個程序，將 BAM 分析資料庫移動到其他伺服器。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。  
  
### <a name="to-move-the-bam-analysis-database"></a>移動 BAM 分析資料庫  
  
1. 取得用來還原 BAM 的 .xml 檔案複本：  
  
   1. 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
   2. 在命令提示字元中，瀏覽至下列目錄：  
  
       [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking  
  
   3. 在命令提示字元中，輸入：  
  
      ```  
      Bm.exe get-config –filename:BAMConfiguration.xml  
      ```  
  
      > [!NOTE]
      >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
2. 依照《SQL Server 線上叢書》中關於如何在舊伺服器上備份資料庫的指示執行。  
  
3. 將 BAM 分析資料庫複製到新的 SQL Server。  
  
4. 依照《SQL Server 線上叢書》中關於如何在新伺服器上還原資料庫的指示執行。  
  
5. 編輯 BAMConfiguration.xml 檔案，並將 AnalysisDatabase DeploymentUnit 區段中的 ServerName 變更為新的伺服器名稱。  
  
6. 儲存並關閉 BAMConfiguration.xml 檔案。  
  
7. 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
8. 在命令提示字元中，瀏覽至下列目錄：  
  
    [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking  
  
9. 在命令提示字元中，輸入：  
  
    ```  
    bm.exe update-config -FileName:BAMConfiguration.xml  
    ```  
  
    > [!NOTE]
    >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="see-also"></a>另請參閱  
 [移動 BizTalk Server 資料庫](../core/moving-biztalk-server-databases.md)