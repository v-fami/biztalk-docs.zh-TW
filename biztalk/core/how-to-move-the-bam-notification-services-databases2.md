---
title: 如何移動 BAM Notification Services 資料庫 2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Notification Services Application database [BAM]
- Notification Services Instance database [BAM]
- migrating, Notification Services database [BAM]
ms.assetid: 4b7f3397-65c9-4c71-8374-8764f4c2e2e3
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73a995a4025bba980614d2c8cefef3da99219984
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014471"
---
# <a name="how-to-move-the-bam-notification-services-databases"></a>如何移動 BAM Notification Services 資料庫
您可使用這個程序將 BAM Notification Services 資料庫移動到另一個伺服器。  
  
> [!NOTE]
>  您必須同時移動 BAM Notification Services 應用程式 (BAMAlertsApplication) 資料庫和 BAM Notification Services 執行個體 (BAMAlertsNSMain) 資料庫。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。  
  
### <a name="to-move-the-bam-notification-services-databases"></a>移動 BAM Notification Services 資料庫  
  
1. 取得用來還原 BAM 的 .xml 檔案複本：  
  
   1. 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
   2. 在命令提示字元中，瀏覽至下列目錄：  
  
       **%SystemDrive%\Program Files\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\Tracking**   
  
   3. 在命令提示字元中，輸入：  
  
      ```  
      Bm.exe get-config –filename:BAMConfiguration.xml  
      ```  
  
      > [!NOTE]
      >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
2. 在命令提示字元中，輸入：  
  
   ```  
   Net stop NS$BamAlerts  
   ```  
  
3. 依照《SQL Server 線上叢書》中關於如何在舊伺服器上備份資料庫的指示執行。  
  
4. 將 BAM Notification Services 資料庫複製到新的 SQL Server。  
  
5. 依照《SQL Server 線上叢書》中關於如何在新伺服器上還原資料庫的指示執行。  
  
6. 編輯 BAMConfiguration.xml 檔案，並將警示 DeploymentUnit 區段中的 ServerName 變更為新的伺服器名稱。  
  
7. 儲存並關閉 BAMConfiguration.xml 檔案。  
  
8. 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
9. 在命令提示字元中，瀏覽至下列目錄：  
  
     **%SystemDrive%\Program Files\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\Tracking**   
  
10. 在命令提示字元中，輸入：  
  
    ```  
    bm.exe update-config -FileName:BAMConfiguration.xml  
    ```  
  
    > [!NOTE]
    >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
11. 更新 BAM Notification Services 資料庫的參考。 如需詳細資訊，請參閱 <<c0> [ 如何更新 BAM Notification Services 資料庫參考](../core/how-to-update-references-to-the-bam-notification-services-databases.md)。  
  
## <a name="see-also"></a>另請參閱  
 [移動 BizTalk Server 資料庫](../core/moving-biztalk-server-databases.md)