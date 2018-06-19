---
title: 值不可為空白或 null 以外 Exists 運算子 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44de42c8-eab7-4b13-b55a-d33eabe75c52
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b5e257b78df8bf872764542d711637d33714349
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279662"
---
# <a name="the-value-cannot-be-empty-or-null-for-an-operator-other-than-exists"></a>值不可為空白或 null Exists 以外的運算子
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|批次處理引擎|  
|符號名稱|ValueCannotBeNullOrEmpty|  
|訊息文字|值不可為空白或 null Exists 以外的運算子|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示批次篩選條件 對話方塊中的資料列中的屬性輸入的值無效，因為運算子不存在，但輸入的值是空白或 null。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，開啟 [批次篩選條件] 對話方塊從內 [交換批次建立設定] 頁面的 [EDI 屬性] 對話方塊。 請確定該運算子的資料列不存在，如果輸入的值是空的或 null。