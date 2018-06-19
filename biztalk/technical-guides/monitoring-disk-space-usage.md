---
title: 監視磁碟空間使用量 |Microsoft 文件
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
ms.openlocfilehash: 7ae87de0b00e70ae03a30dd8ef20ede4a972388d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298590"
---
# <a name="monitoring-disk-space-usage"></a>監視磁碟空間使用量
監視的程序的操作整備[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，監視的磁碟空間使用量，如下所示：  
  
-   **判斷磁碟所需的空間。**  
  
     當使用檔案或 MSMQ 傳送 / 接收位置時，請確認有足夠的磁碟空間可容納的中斷[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或接收的系統。 例如，如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在 SAN 上的寫入檔案到共用，並接收系統已關閉，有兩天，判斷是否有足夠的磁碟空間，以允許將排入佇列檔案。  
  
-   **定期清除 BizTalk Server 的備份檔案的目錄。**  
  
     您可以執行此清除使用呼叫 SQL Server Agent 作業的指令碼。  
  
-   **定期清除 BizTalk 追蹤資料庫封存檔案目錄。**  
  
-   **請確認有足夠的磁碟空間可容納更大的 BizTalk Server 資料庫 (.mdf) 和交易記錄 (.ldf) 檔案，在尖峰資料流程的時間。**