---
title: "如何更新 BAM 管理公用程式組態之後備份和還原 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b27062b-546f-4030-983b-15d793912690
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf316e7275b3db47b02a7f09ed5d2a66571c4de1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-the-bam-management-utility-configuration-after-a-backup-and-restore"></a>如何在備份和還原之後更新 BAM 管理公用程式組態
由於 BizTalk Server 環境變更 (例如備份和還原順序) 而導致伺服器\資料庫名稱組合變更時，您必須更新 BAM 管理公用程式組態檔案 (bm.exe.config)，以反映這些名稱變更。  
  
### <a name="to-update-the-bam-management-configuration-file-a-after-backup-and-restore"></a>若要在備份和還原之後更新 BAM 管理組態檔案  
  
1.  開啟 bm.exe.config 檔案，即可使用 [記事本]**啟動**，然後按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]tracking\bm.exe.config，然後再按一下**確定**。  
  
2.  在檔案中找出 appSettings 區段和下列值：  
  
    ```  
    <!-- Default server and database for bm.exe. -->  
    <add key="DefaultServer" value="oldServerName" />  
    <add key="DefaultDatabase" value="BAMPrimaryImport" />  
    ```  
  
3.  to  
  
    ```  
    <!-- Default server and database for bm.exe. -->  
    <add key="DefaultServer" value="newServerName" />  
    <add key="DefaultDatabase" value="BAMPrimaryImport" />  
    ```  
  
4.  儲存檔案。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 資料庫](../core/managing-bam-databases.md)