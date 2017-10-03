---
title: "無效的引號遇到的 HTTP 標頭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb530ee6-ec6a-4791-ae99-b9db426c0896
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e154e3bacf34025edd837516a15dca6f2caa174
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="an-invalid-quoted-http-header-encountered"></a>無效的引號遇到的 HTTP 標頭
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|-|  
|訊息文字|發現無效且具引號的 HTTP 標頭。  詳細資料如下： 標頭名稱:"{0}"標頭值:"{1}"|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 AS2 接收管線或 AS2 傳送管線無法處理 AS2 訊息，因為 AS2 的名稱-從或 AS2 的訊息到 HTTP 標頭不正確地括住。 標頭名稱會以容納空格、 反斜線或在名稱中的雙引號括住。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，引號標頭名稱符合規則的 AS2 訊息中一節所述 6.2，「 AS2 系統識別碼 」，RFC 4130 「 以 MIME 為基礎安全端對端商務資料交換使用 HTTP，Applicability Statement 2 (AS2) 」。