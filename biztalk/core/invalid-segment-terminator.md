---
title: "無效的區段結束字元 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 508dac21-4731-439d-bf4a-a50858f1ffa0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47d5a79af0616baed6d401b4df7b68f5f596ef07
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-segment-terminator"></a>無效的區段結束字元
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12Ta1InvalidSegmentTerminatorDescription|  
|訊息文字|無效的區段結束字元|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於內送交換中的區段結束字元值有 ASCII 字元集之外的字元，因此接收管線無法處理該交換。 在 X12 中，區段結束字元定義為 ISA 區段的最後一個字元。 在 EDIFACT 中，區段結束字元是 [UNA6] 欄位。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認區段結束字元 (X12 交換中 ISA 區段的最後一個字元，或 EDIFACT 交換中的 [UNA6] 欄位) 皆為 ASCII 字元集中的字元。 重新傳送交換。