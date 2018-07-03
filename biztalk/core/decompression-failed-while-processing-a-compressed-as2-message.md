---
title: 處理壓縮的 AS2 訊息時，解壓縮失敗。 | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5246ee97-cc60-4878-9447-de870c0f4c34
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c77bead00b97bf6fa072223485f2d1cc422053b7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001887"
---
# <a name="decompression-failed-while-processing-a-compressed-as2-message"></a>處理壓縮的 AS2 訊息時，解壓縮失敗。
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       AS2 引擎                                       |
|  符號名稱  |                                           -                                            |
|  訊息文字   |       處理壓縮的 AS2 訊息時，解壓縮失敗。 錯誤： {0}       |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線的 AS2 解碼器元件無法解壓縮 AS2 訊息。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  
  
-   確認 AS2 訊息中的壓縮包裝函式有效。  
  
-   確認解壓縮已啟用 BizTalk server，藉由驗證，「 訊息應該壓縮 會檢查屬性對象當做 AS2 訊息傳送者頁面的 AS2 屬性 對話方塊中 （是否覆寫輸入訊息屬性會檢查屬性）.  
  
-   您可以使用提供錯誤訊息文字中的錯誤描述來識別特定的問題。