---
title: 無效且具引號的 HTTP 標頭發生 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb530ee6-ec6a-4791-ae99-b9db426c0896
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ca0d7463f4604e8a159c12fab690e494a13fb60
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971007"
---
# <a name="an-invalid-quoted-http-header-encountered"></a>無效且具引號的 HTTP 標頭發生
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------|
|  產品名稱   |              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]              |
| 產品版本 |                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                          |
|    事件識別碼     |                                                      -                                                       |
|  事件來源   |            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI            |
|    元件    |                                                  AS2 引擎                                                  |
|  符號名稱  |                                                      -                                                       |
|  訊息文字   | 發現無效且具引號的 HTTP 標頭。  詳細資料如下： 標頭名稱:"{0}"標頭值:"{1}」 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，AS2 接收管線或 AS2 傳送管線無法處理 AS2 訊息，因為 AS2 的名稱-從或 AS2-以 HTTP 標頭，訊息中的不正確地括住。 標頭名稱已加上引號，以容納空間、 反斜線或雙引號括住名稱。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，引號 AS2 訊息，根據規則中的標頭名稱一節所述 6.2，「 AS2 系統識別碼 」，RFC 4130 「 以 MIME 為基礎安全端對端商務資料交換使用 HTTP，Applicability Statement 2 (AS2) 」。