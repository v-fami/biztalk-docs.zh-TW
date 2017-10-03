---
title: "元件無法重複，因為它有無效的重複計數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 040d7ea4-60a9-495f-91d7-b5b868957e2d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d535d72b5f265f07e6ae3fb468ed56efdc7975b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="component-cannot-repeat-because-it-has-an-invalid-repetition-count"></a>元件無法重複，因為它有無效的重複計數
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|SchemaCode118EInvalidRepetition|  
|訊息文字|元件無法重複，它的重複計數 {0} 無效|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於交換中的元素元件、元素、區段或迴圈重複，但結構描述不允許重複，因此接收管線無法處理內送交換，或傳送管線無法處理外寄交換。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認交換中的元素元件、元素、區段或迴圈未重複 (如結構描述要求)，然後再重新傳送訊息。