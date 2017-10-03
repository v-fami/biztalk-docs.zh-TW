---
title: "在序列化期間發生錯誤。 X12 功能群組發生下列錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dad987c3-92f3-4a6b-ba1a-b60f6ea2fbe4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27c6b74d713f0d182a07cc6a509cd7d06fc34b82
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-serialization-the-x12-functional-group-had-the-following-errors"></a>在序列化期間發生錯誤。 X12 功能群組發生下列錯誤
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12FunctionalGroupSendError|  
|訊息文字|在序列化期間發生錯誤。 X12 功能群組寄件者識別碼 '{2}'，識別碼為 '{0}'，識別碼 '{1}' 交換中接收者識別碼 '{3}' 發生下列錯誤：|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 傳送管線發生錯誤，當序列化 X12 外寄交換，因為與識別功能群組敘述的錯誤。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，錯誤訊息中使用的資訊來識別功能群組中的錯誤，然後決定產品說明中的問題解決方法。