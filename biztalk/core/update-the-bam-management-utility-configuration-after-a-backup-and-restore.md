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
# <a name="how-to-update-the-bam-management-utility-configuration-after-a-backup-and-restore"></a><span data-ttu-id="a141f-102">如何在備份和還原之後更新 BAM 管理公用程式組態</span><span class="sxs-lookup"><span data-stu-id="a141f-102">How to Update the BAM Management Utility Configuration After a Backup and Restore</span></span>
<span data-ttu-id="a141f-103">由於 BizTalk Server 環境變更 (例如備份和還原順序) 而導致伺服器\資料庫名稱組合變更時，您必須更新 BAM 管理公用程式組態檔案 (bm.exe.config)，以反映這些名稱變更。</span><span class="sxs-lookup"><span data-stu-id="a141f-103">When the server\database name combination changes as the result of a change in your BizTalk Server environment such as a backup and restore sequence, you must update the BAM management utility configuration file (bm.exe.config) to reflect these name changes.</span></span>  
  
### <a name="to-update-the-bam-management-configuration-file-a-after-backup-and-restore"></a><span data-ttu-id="a141f-104">若要在備份和還原之後更新 BAM 管理組態檔案</span><span class="sxs-lookup"><span data-stu-id="a141f-104">To update the BAM management configuration file a after backup and restore</span></span>  
  
1. <span data-ttu-id="a141f-105">開啟 bm.exe.config 檔案使用 [記事本]，依序按一下**開始**，再按一下**執行**，輸入 notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]tracking\bm.exe.config，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a141f-105">Open the bm.exe.config file using Notepad by clicking **Start**, clicking **Run**, typing notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]tracking\bm.exe.config, and then clicking **OK**.</span></span>  
  
2. <span data-ttu-id="a141f-106">在檔案中找出 appSettings 區段和下列值：</span><span class="sxs-lookup"><span data-stu-id="a141f-106">Locate the appSettings section in the file and change the following values:</span></span>  
  
   ```  
   <!-- Default server and database for bm.exe. -->  
   <add key="DefaultServer" value="oldServerName" />  
   <add key="DefaultDatabase" value="BAMPrimaryImport" />  
   ```  
  
3. <span data-ttu-id="a141f-107">to</span><span class="sxs-lookup"><span data-stu-id="a141f-107">to</span></span>  
  
   ```  
   <!-- Default server and database for bm.exe. -->  
   <add key="DefaultServer" value="newServerName" />  
   <add key="DefaultDatabase" value="BAMPrimaryImport" />  
   ```  
  
4. <span data-ttu-id="a141f-108">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="a141f-108">Save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a141f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a141f-109">See Also</span></span>  
 [<span data-ttu-id="a141f-110">管理 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="a141f-110">Managing BAM Databases</span></span>](../core/managing-bam-databases.md)