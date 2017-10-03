---
title: "無效的元件元素分隔符號 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 738a1107-86e6-4475-a61d-ed1d9ab7e5d2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4abf047a61dc8b8f2eb89e436594e47e6f4cb067
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-component-element-separator"></a>無效的元件元素分隔符號
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12Ta1InvalidComponentElementSeparatorDescription\|  
|訊息文字|無效的元件元素分隔符號|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換的交換中的元件分隔符號的值因為無法限制為 ASCII 字元集中的字元。 在 X12 中，區段結束字元是 ISA16 欄位。 在 EDIFACT 中，區段結束字元是 UNA1 欄位。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認區段結束字元 (ISA16 欄位中的 X12 交換] 或 [EDIFACT 交換中的 UNA1 欄位) 限制為 ASCII 字元集中的字元。 重新傳送交換。