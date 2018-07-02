---
title: 監視磁碟空間使用量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ac68022-a9c5-4eb9-8854-cd1ee849282b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25035d50c6e69fcf74e1cf75e8f073b19cc0b47f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986927"
---
# <a name="monitoring-disk-space-usage"></a>監視磁碟空間使用量
作業整備狀態的監視程序的一部分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，監視磁碟空間使用量，如下所示：  

- **決定磁碟所需的空間。**  

   當使用檔案或 MSMQ 傳送 / 接收位置時，請確定沒有足夠的磁碟空間可容納的中斷[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或接收的系統。 例如，如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在 SAN 上的寫入檔案共用，而且接收端系統已關閉兩天內，判斷是否有足夠的磁碟空間，以允許檔案排入佇列。  

- **定期清除 BizTalk Server 的備份檔案的目錄。**  

   您可以執行使用指令碼從 SQL Server Agent 作業呼叫此清除工作。  

- **定期清除 BizTalk 追蹤資料庫封存的檔案目錄。**  

- **請確定沒有足夠的磁碟空間可容納更大的 BizTalk Server 資料庫 (.mdf) 和交易記錄 (.ldf) 檔案最大資源資料流中的時間。**
