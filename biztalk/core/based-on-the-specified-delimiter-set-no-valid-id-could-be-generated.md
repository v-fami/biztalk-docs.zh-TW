---
title: 根據指定的分隔符號集，沒有有效的識別碼可能會產生 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ab5f018-b56f-4e3c-97e4-f9ea4258f6d9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d70c4210ce57f4af9fb318caaf8274a0c6effc7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231406"
---
# <a name="based-on-the-specified-delimiter-set-no-valid-id-could-be-generated"></a>根據指定的分隔符號集，無法產生有效的識別碼
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|根據指定的分隔符號集，無法產生有效的識別碼。 請使用另一個的分隔符號集。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，EDI 傳送管線無法產生有效的識別碼值，因此識別項欄位的外寄交換中使用的字元是分隔符號字元相同。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，變更分隔符號值用於 edi 傳送管線，建立一則訊息，因此沒有分隔符號字元會識別項欄位的外寄交換中使用的字元相同。 執行下列其中之一：  
  
-   對於傳送給已解析合作對象的 X12 交換，針對做為交換接收者的合作對象在 [ISA 區段定義] 頁面變更分隔符號設定。  
  
-   對於傳送給未解析之合作對象的 X12 交換，在 [ISA 區段定義] 全域屬性頁面中變更分隔符號設定。  
  
-   EDIFACT 交換傳送至合作對象解析變更做為交換接收者的合作對象 [UNA 區段定義] 頁面中的分隔符號設定。  
  
-   針對傳送至合作對象已解析的 EDIFACT 交換，變更分隔符號設定 UNA 區段定義 全域屬性頁面中。