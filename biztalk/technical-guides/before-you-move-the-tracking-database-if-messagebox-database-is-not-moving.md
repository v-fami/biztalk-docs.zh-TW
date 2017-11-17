---
title: "如果未移動 MessageBox 資料庫移動 「 追蹤 」 資料庫時的考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee4066cb-da5b-4d04-a3b8-23fbf2d0c92a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ecb2fcb6ad9ead42bd3e09c84a8895758d82293f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-moving-the-tracking-database-if-the-messagebox-database-is-not-being-moved"></a><span data-ttu-id="568d4-102">如果未移動 MessageBox 資料庫移動 「 追蹤 」 資料庫時的考量</span><span class="sxs-lookup"><span data-stu-id="568d4-102">Considerations When Moving the Tracking Database if the MessageBox Database Is Not Being Moved</span></span>
<span data-ttu-id="568d4-103">如果您要移動的追蹤資料庫但不是 MessageBox 資料庫，當您編輯 SampleUpdateInfo.xml 檔案，請確定您包含 MessageBox 資料庫，項目，即使不移動 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="568d4-103">If you are moving the Tracking database but not the MessageBox database, when you edit the SampleUpdateInfo.xml file, make sure that you include an entry for the MessageBox database as well, even though the MessageBox database is not being moved.</span></span> <span data-ttu-id="568d4-104">這必須以確保完成[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式工作 TrackedMessages_Copy_BizTalkMsgBoxDb 會更新為新的追蹤資料庫的位置。</span><span class="sxs-lookup"><span data-stu-id="568d4-104">This must be done to ensure that the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent job TrackedMessages_Copy_BizTalkMsgBoxDb is updated with the location of the new Tracking database.</span></span>  
  
 <span data-ttu-id="568d4-105">例如，在下列的 SampleUpdateInfo.xml 檔案中，追蹤資料庫已從移 OldServer NewServer 至。</span><span class="sxs-lookup"><span data-stu-id="568d4-105">For example, in the following SampleUpdateInfo.xml file, only the Tracking database is being moved from OldServer to NewServer.</span></span> <span data-ttu-id="568d4-106">MessageBox 資料庫未超出 OldServer:</span><span class="sxs-lookup"><span data-stu-id="568d4-106">The MessageBox database is staying on OldServer:</span></span>  
  
```  
<UpdateConfiguration>  
     <MessageBoxDB oldDBName="BizTalkMgmtDb" oldDBServer="OldServer" newDBName="BizTalkMgmtDb" newDBServer="OldServer" IsMaster="1"/>  
     <TrackingDB oldDBName="BizTalkDTADB" oldDBServer="OldServer" newDBName="BizTalkDTADB" newDBServer="NewServer"/>  
     <OtherDatabases>  
     </OtherDatabases>  
</UpdateConfiguration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="568d4-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="568d4-107">See Also</span></span>  
 [<span data-ttu-id="568d4-108">移動資料庫</span><span class="sxs-lookup"><span data-stu-id="568d4-108">Moving Databases</span></span>](../technical-guides/moving-databases.md)