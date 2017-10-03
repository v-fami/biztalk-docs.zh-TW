---
title: "無效的 AS2-從收到的標頭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d773e09-8526-4533-9066-8e743e65a688
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f20a74e60a6365c0c16e139e8b2caca1bc33646
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-as2-from-header-received"></a>收到無效的 AS2-From 標頭
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|InvalidAS2FromNameHeaderReceivedError|  
|訊息文字|收到無效的 AS2-From 標頭。  值： {0}|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於訊息中的 AS2-From 標頭值不符合 AS2 RFC 4130 中的規格，因此接收管線無法處理內送交換。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認訊息之 AS2-From 標頭中的值符合 AS2 RFC 4130 第 6.2 節的規格，然後再重新傳送訊息。