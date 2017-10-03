---
title: "不是唯一分隔符號 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c37cc55-8923-4124-9004-91ee5093df9c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8cc4f9c8eeb3a16fdd45222313bfb013dbf32ae5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-are-not-unique"></a>不是唯一分隔符號
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|不是唯一分隔符號|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，EDI 傳送管線無法處理外寄交換因為兩個或多個分隔符號的交換，識別，且用來分隔的交換，facet 都相同。 X12 的 ISA 區段中所識別的分隔符號交換和 EDIFACT 的 UNA 區段中交換。 保留批次的情況下，可能會發生兩個或多個具有相同值的分隔符號或交換是透過傳遞傳輸接收，然後挑選向上為 MessageBox 中 XML 檔案傳送埠。 這個錯誤狀況會導致失敗之交換的處理。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，找出交換內的分隔符號有相同的值，並變更其中一個分隔符號的值。