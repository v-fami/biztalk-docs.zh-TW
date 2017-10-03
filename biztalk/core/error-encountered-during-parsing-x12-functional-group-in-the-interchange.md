---
title: "在剖析期間發生錯誤。 X12 交換中的功能群組發生下列錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2229c83-89bd-491f-9504-4afbf0084297
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4e519e8f89f00574ad2b51c1f9884889077c902
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-parsing-the-x12-functional-group-in-the-interchange-had-the-following-errors"></a>在剖析期間發生錯誤。 X12 交換中的功能群組發生下列錯誤
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12FunctionalGroupReceiveError|  
|訊息文字|在剖析期間發生錯誤。 X12 功能群組寄件者識別碼 '{2}'，識別碼為 '{0}'，識別碼 '{1}' 交換中接收者識別碼 '{3}' 發生下列錯誤：|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線時發生錯誤剖析內送 X12 交換，因為與識別功能群組敘述的錯誤。  
  
## <a name="user-action"></a>使用者動作  
 若要解決此錯誤，使用錯誤訊息中的資訊識別群組中的錯誤，然後決定產品說明中的問題解決方法。