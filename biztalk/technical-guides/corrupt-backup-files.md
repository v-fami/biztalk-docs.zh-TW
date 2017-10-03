---
title: "備份檔損毀 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc48197c-944a-4f0a-ba01-8e1d91c88ad3
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fda5acae756fd2c4d0afc0263bc723af3ba77e15
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="corrupt-backup-files"></a>備份檔損毀
備份檔案可能變成損毀、 損毀或遺失。 如果發生這種情況，無法還原至少一個檔案。 發生失敗的系統上的還原作業會搜尋下一個有效的完整備份組。 在大部分情況下它必須在來源系統上強制進行完整備份。 如果沒有這類集存在，還原作業失敗，並等到抵達有效的完整備份集，每個後續的執行也會失敗。 如果一組不存在，它用來修復環境。  
  
> [!NOTE]  
>  由於之方式[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]寫入備份資料檔案，可能的[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]會報告成功完成，即使實際的寫入資料的期間備份失敗。 此案例主要是正在寫入的磁碟不是本機電腦和網路失敗或中斷，就會發生時發生。 基於一般考量，如果備份作業執行時，就會發生網路失敗，完整備份之後強制網路連線問題已解決。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解記錄傳送](../technical-guides/troubleshooting-log-shipping.md)