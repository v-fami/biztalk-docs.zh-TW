---
title: 如何更新 BAM 管理公用程式設定，備份和還原之後 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b27062b-546f-4030-983b-15d793912690
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa7d8e91ab82cc74f2af2ca0c12f79cdb0a8fcbe
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970079"
---
# <a name="how-to-update-the-bam-management-utility-configuration-after-a-backup-and-restore"></a>如何在備份和還原之後更新 BAM 管理公用程式組態
由於 BizTalk Server 環境變更 (例如備份和還原順序) 而導致伺服器\資料庫名稱組合變更時，您必須更新 BAM 管理公用程式組態檔案 (bm.exe.config)，以反映這些名稱變更。  
  
### <a name="to-update-the-bam-management-configuration-file-a-after-backup-and-restore"></a>若要在備份和還原之後更新 BAM 管理組態檔案  
  
1. 開啟 bm.exe.config 檔案使用 [記事本]，依序按一下**開始**，再按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]tracking\bm.exe.config，，然後按一下**確定**。  
  
2. 在檔案中找出 appSettings 區段和下列值：  
  
   ```  
   <!-- Default server and database for bm.exe. -->  
   <add key="DefaultServer" value="oldServerName" />  
   <add key="DefaultDatabase" value="BAMPrimaryImport" />  
   ```  
  
3. to  
  
   ```  
   <!-- Default server and database for bm.exe. -->  
   <add key="DefaultServer" value="newServerName" />  
   <add key="DefaultDatabase" value="BAMPrimaryImport" />  
   ```  
  
4. 儲存檔案。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 資料庫](../core/managing-bam-databases.md)