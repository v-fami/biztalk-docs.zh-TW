---
title: "BizTalk Server 如何傳送 EDI 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4eaf1085-4244-4df2-9d89-52ebdf6bcbbc
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4727a407c28ede98bba67774576d4d43329a946
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-biztalk-server-sends-edi-messages"></a>BizTalk Server 傳送 EDI 訊息的方式
當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送 EDI 訊息時，它會執行協議尋查和結構描述探索、驗證訊息、傳送通知 (適當情況下)，以及序列化 EDI 批次。 EDI 組合器會在「EDI 傳送管線」中執行這項處理。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [EDI 傳送元件](../core/edi-send-components.md)  
  
-   [協議解析和外寄 EDI 訊息的結構描述判斷](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)  
  
-   [「 EDI 組合器 」 的運作方式](../core/how-the-edi-assembler-works.md)  
  
-   [覆寫 EDI 標頭](../core/overriding-edi-headers.md)  
  
-   [外寄 EDI 訊息的驗證](../core/validation-of-outgoing-edi-messages.md)  
  
-   [批次處理外寄 EDI 訊息](../core/batching-outgoing-edi-messages.md)  
  
-   [處理接收的通知](../core/processing-a-received-acknowledgment.md)