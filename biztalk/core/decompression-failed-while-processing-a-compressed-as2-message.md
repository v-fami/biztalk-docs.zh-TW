---
title: "處理壓縮的 AS2 訊息時，解壓縮失敗。 | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5246ee97-cc60-4878-9447-de870c0f4c34
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4121fc3598913f4c3edab52655866c02b5a4fe86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="decompression-failed-while-processing-a-compressed-as2-message"></a>處理壓縮的 AS2 訊息時，解壓縮失敗。
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|-|  
|訊息文字|處理壓縮的 AS2 訊息時，解壓縮失敗。 錯誤： {0}|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線的 AS2 解碼器元件無法解壓縮 AS2 訊息。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列其中一項：  
  
-   驗證 AS2 訊息中的壓縮包裝函式有效。  
  
-   確認解壓縮已啟用 BizTalk server 進行驗證，「 訊息應該壓縮 會檢查屬性的合作對象當做 AS2 訊息傳送者 頁面的 AS2 屬性 對話方塊 （如果覆寫輸入訊息屬性會檢查屬性）.  
  
-   使用錯誤訊息文字中提供的錯誤描述來識別特定的問題。