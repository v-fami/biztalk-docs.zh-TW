---
title: "讀取 ISA 資料分隔符號中發生錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cb60abd-53c8-45e1-a840-d27dc974aad7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fcde2519740adc5531363911146164f460f9b3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-in-reading-delimiters-from-isa-data"></a>讀取 ISA 資料分隔符號中發生錯誤
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|InvalidIsaData|  
|訊息文字|讀取 ISA 資料分隔符號中發生錯誤|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線發生錯誤時正在處理內送 X12 交換因為無法剖析從 ISA 區段的分隔符號。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認內送交換的 ISA 區段中的分隔符號是唯一且有效。 否則，請將傳送者交換的唯一且有效的值輸入至每個分隔符號欄位 （ISA11 區段做為重複分隔符號與 ISA16 區段的元件分隔符號），然後再重新傳送交換。