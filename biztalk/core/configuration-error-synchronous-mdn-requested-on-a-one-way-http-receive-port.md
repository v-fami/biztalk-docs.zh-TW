---
title: 組態錯誤。 對單向 HTTP 要求同步 MDN 的接收埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f140c7a4-46bf-4557-9679-cdaf2fbe66f4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa49120ecbdbd0a00de1bbd6cd552f56cb626ddd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232198"
---
# <a name="configuration-error-synchronous-mdn-requested-on-a-one-way-http-receive-port"></a>組態錯誤。 對單向 HTTP 接收埠要求同步 MDN
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|組態錯誤。 對單向 HTTP 傳送埠要求同步 MDN。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法在接收 AS2 訊息之後傳回同步的 MDN，因為處理內送 AS2 訊息的 HTTP 接收埠是單向連接埠。 雙向要求-回應接收埠，才能傳回同步 MDN 以回應內送的 AS2 訊息。 在此情況下，MDN 就必須傳回以同步方式因為 AS2 訊息包含配置通知至] 標頭或合作對象當做 AS2 訊息傳送者，會檢查傳入的訊息內容屬性的覆寫，產生的組態勾選 MDN] 屬性，以及傳輸 MDN] 屬性是以非同步的方式清除。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，變更會接收 AS2 訊息是要求回應接收埠，接收埠，而不是單向接收埠。 設定傳送管線的要求回應接收非 EDI 交換是 AS2EdiSend EDI 交換或 AS2Send 的位置。