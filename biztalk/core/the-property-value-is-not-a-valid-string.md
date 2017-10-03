---
title: "屬性值不是有效的字串 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78df6aca-26b5-4d49-93b0-71de19f5c9dd
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7dfcceba7944226f801101818c2bf8c96ac42ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-property-value-is-not-a-valid-string"></a>不是有效的字串屬性值。
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|批次處理引擎|  
|符號名稱|InvalidPropertyValue|  
|訊息文字|不是有效的字串屬性值。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示批次篩選條件 對話方塊中的資料列中的屬性輸入的值無效，因為屬性需要字串值，但輸入的值並不是 string。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，開啟 [批次篩選條件] 對話方塊從內 [交換批次建立設定] 頁面的 [EDI 屬性] 對話方塊。 請確定輸入為字串屬性的值是字串。