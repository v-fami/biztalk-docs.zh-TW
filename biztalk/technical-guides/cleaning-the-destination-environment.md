---
title: 清除目的地環境 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8585853b-e625-48c3-a241-81ebf1be0e1e
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4023492bf79223b3ba6b1db5cedebadf88feb9c4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299862"
---
# <a name="cleaning-the-destination-environment"></a>清除目的地環境
如果還原作業遇到無法解決的錯誤狀況，清除目的地環境，好讓它能夠開始從空的環境。 執行預存程序**sp_LogShippingClean**位於 master 資料庫的目的地上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體將會 「 清除 」 目的地環境。 此程序會卸除所有資料庫，並刪除指定之來源的最後一個還原的資料集。  
  
 然後再執行此程序，停用**BTS 記錄傳送-還原資料庫**（取得備份歷程記錄作業可能會繼續執行） 的工作。 如需有關停用**BTS 記錄傳送-還原資料庫**作業，請參閱[如何還原資料庫中 「 備份 BizTalk Server 」 工作](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)。 之後**sp_LogShippingClean**執行程序，在下次執行還原作業會尋找最近的完整備份，以有效的後續記錄備份組設定。 如果這個集合已還原，還原作業會清除**還原**設定和所有後續的資料行設定，並接著會還原集合。  
  
> [!NOTE]  
>  因為作業會尋找最近的完整備份之後已清除的環境設定，強制進行完整備份來源系統上執行此程序之後，但在執行還原作業之前。  
  
> [!NOTE]  
>  **Sp_LogShippingClean**必須重複程序，以保持與每個其他方面的設定已套用的同步處理不同的伺服器還原指定的來源系統資料庫的所有伺服器上。  
  
 若要執行**sp_LogShippingClean**程序中，連接到 master 資料庫上所有[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]屬於嚴重損壞修復的執行個體的站台，並執行下列命令中的**新查詢**中可用的選項[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Management Studio，針對每個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體：  
  
```  
sp_LogShippingClean 'SourceID'  
```  
  
 其中**SourceID**對應至生產環境上設定的識別項[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解記錄傳送](../technical-guides/troubleshooting-log-shipping.md)