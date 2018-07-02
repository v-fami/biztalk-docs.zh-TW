---
title: 備份檔案損毀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48197c-944a-4f0a-ba01-8e1d91c88ad3
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5947b527dea1206255daf52f128569fd7a4f659c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987911"
---
# <a name="corrupt-backup-files"></a>備份檔案損毀
備份檔案可能損毀、 已損毀或遺失。 如果發生這種情況，就無法還原至少一個檔案。 發生失敗的系統上的還原作業會搜尋下一個有效的完整備份組。 在大部分情況下它必須在來源系統上強制進行完整備份。 如果沒有這樣的集合存在，還原作業失敗，直到抵達有效的完整備份集，每個後續的執行也會失敗。 如果一組不存在，它用來修復環境。  
  
> [!NOTE]
>  因為方法[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]將備份資料寫入至檔案，就可以，[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]會報告已成功完成，即使實際將資料寫入期間備份失敗。 要寫入的磁碟不是本機電腦和網路失敗或發生中斷時，主要是就會發生這種情況。 基於一般考量，如果備份作業執行時，就會發生網路失敗，強制進行完整備份之後解決網路連線問題。  
  
## <a name="see-also"></a>另請參閱  
 [針對記錄傳送進行疑難排解](../technical-guides/troubleshooting-log-shipping.md)