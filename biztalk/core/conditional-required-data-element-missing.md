---
title: "條件式的必要資料元素遺失 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5105c03-fa26-4c38-a276-c656f3076d5f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d77a25e60af0d8287515d6fb3a7e2797d5af0b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="conditional-required-data-element-missing"></a>遺失條件式的必要資料元素
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12DeConditionalRequiredDataElementMissingDescription|  
|訊息文字|遺失條件式的必要資料元素|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送交換，因為交換中不存在 X12ConditionDesignatorX 規則所需的資料元素。  
  
## <a name="user-action"></a>使用者動作  
 這個錯誤可能是內送交換，而不設定或 BizTalk server 作業的問題。 若要解決這個錯誤，請連絡交換的寄件者，指示他們必須變更交換中使用的字元或識別 UNB1.1 欄位中，使其相符的字元集。