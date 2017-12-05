---
title: "目的地 URL 屬性的限制 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [HTTP adapters], restrictions
- HTTP adapters, restrictions
ms.assetid: 982a5122-e43d-4730-a8b9-ceb1ff88638c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f7966fccca324a1453f0ea84e79cd7d9d3d55ad
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="restrictions-on-the-destination-url-property"></a>目的地 URL 屬性的限制
目的地 URL 是指定 HTTP 伺服器位址的字串，您在這裡使用 HTTP 通訊協定來傳送訊息。  
  
 下列規則與限制適用於目的地 URL 屬性：  
  
-   您必須永遠以下列格式指定目的地 URL 屬性：  
  
     http [s]://\<主機\>[:\<連接埠\>] [/\<路徑\>[/\<檔案\>[？\<查詢字串\>]]]  
  
-   整個字串不一定是 URI 編碼。  
  
-   整個字串，除了查詢字串中，不能包含任何下列字元： \< \> : \ &#124;" ? *.  
  
-   屬性不區分大小寫。  
  
-   字串長度不能超過 256 個字元。  
  
## <a name="see-also"></a>請參閱  
 [設定 HTTP 傳送埠](../core/configuring-an-http-send-port.md)