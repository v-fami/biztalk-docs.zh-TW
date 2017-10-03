---
title: "訊息未包含 UNA 和分隔符號的管線屬性是格式不正確 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b761d820-e09d-4949-bb41-da9e66054c60
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6310c96f897126a498772f2147a20c84f7e926a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-did-not-contain-una-and-pipeline-property-for-delimiters-was-incorrect-format"></a>訊息未包含 UNA 和分隔符號的管線屬性是格式不正確
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|EfactDelimiterIncorrectFormat|  
|訊息文字|訊息未包含 UNA 和分隔符號的管線屬性是格式不正確 '{0}'|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送 EDIFACT 交換因為它無法判斷用來處理交換所需的分隔符號。 如果交換沒有 UNA 區段和 EfactDelimiters 管線屬性並未適當定義的分隔符號，這可能會發生。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列其中一項：  
  
1.  請確定交換已定義的交換，分隔符號的 UNA 區段，然後再重新傳送交換。  
  
2.  EfactDelimiters 管線屬性的傳送管線藉由開啟 BizTalk Server 管理主控台，以滑鼠右鍵按一下接收位置，將接收交換、 按一下 [內容]，按一下省略符號的管線，來設定和然後輸入字串，包含分隔符號的值。