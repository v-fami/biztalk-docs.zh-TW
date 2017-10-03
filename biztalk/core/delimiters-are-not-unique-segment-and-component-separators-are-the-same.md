---
title: "不是唯一分隔符號，區段和元件分隔符號相同 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13c41899-02af-4678-a4ad-f3dc48c1fdfb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69475949b404474ff4dc9fe53d553c24e125939c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-are-not-unique-segment-and-component-separators-are-the-same"></a>不是唯一分隔符號，區段和元件分隔符號相同
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|不是唯一分隔符號，區段和元件分隔符號相同|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，EDI 傳送管線無法處理外寄交換因為區段結束字元或元件分隔符號相同的值。 在 X12 交換，區段結束字元是最後一個字元位置的 ISA 區段中的字元和元件分隔符號是 ISA16 欄位中的字元。 在 EDIFACT 交換中，區段結束字元是 [UNA6] 欄位中的字元和元件分隔符號是 UNA1 欄位中的字元。 兩個具有相同值的分隔符號可能 （但會導致錯誤狀況） 中保留的批次的案例中，或交換是透過傳遞傳輸接收，然後挑選向上為 MessageBox 中 XML 檔案傳送埠。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，區段結束字元或交換中的元件分隔符號的值變更，然後再重新送出交換。