---
title: "項目具有無效的結構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb94843c-cd21-48e3-ba30-aed0518b4d78
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b825fb0d2f5b4fe985a2024b1c97e21f4308b58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-element-has-an-invalid-structure"></a>項目具有無效的結構
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12NseStructurallyInvalidElementDescription|  
|訊息文字|項目 '{0}' 具有無效的結構|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送的交換，或傳送管線無法處理外寄交換，因為沒有適用於所指定的結構資料元素。結構描述。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，在外寄交換中，修正資料元素的結構，或具有寄件者的交換修正內送的交換中的資料元素的結構，使其符合文件結構描述。