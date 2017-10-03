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
# <a name="considerations-when-moving-the-tracking-database-if-the-messagebox-database-is-not-being-moved"></a>如果未移動 MessageBox 資料庫移動 「 追蹤 」 資料庫時的考量
如果您要移動的追蹤資料庫但不是 MessageBox 資料庫，當您編輯 SampleUpdateInfo.xml 檔案，請確定您包含 MessageBox 資料庫，項目，即使不移動 MessageBox 資料庫。 這必須以確保完成[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式工作 TrackedMessages_Copy_BizTalkMsgBoxDb 會更新為新的追蹤資料庫的位置。  
  
 例如，在下列的 SampleUpdateInfo.xml 檔案中，追蹤資料庫已從移 OldServer NewServer 至。 MessageBox 資料庫未超出 OldServer:  
  
```  
<UpdateConfiguration>  
     <MessageBoxDB oldDBName="BizTalkMgmtDb" oldDBServer="OldServer" newDBName="BizTalkMgmtDb" newDBServer="OldServer" IsMaster="1"/>  
     <TrackingDB oldDBName="BizTalkDTADB" oldDBServer="OldServer" newDBName="BizTalkDTADB" newDBServer="NewServer"/>  
     <OtherDatabases>  
     </OtherDatabases>  
</UpdateConfiguration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [移動資料庫](../technical-guides/moving-databases.md)