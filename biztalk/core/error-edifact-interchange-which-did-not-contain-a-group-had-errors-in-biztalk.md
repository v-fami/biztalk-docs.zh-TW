---
title: 在序列化期間發生錯誤。 Edifact 交換其中不包含群組發生下列錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af693139-e4cd-4bcb-922c-79caa148d3b7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72108104b359d4d06233cf9a623097bfd046a0ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241758"
---
# <a name="error-encountered-during-serialization-the-edifact-interchange-which-did-not-contain-a-group-had-the-following-errors"></a>在序列化期間發生錯誤。 Edifact 交換其中不包含群組發生下列錯誤
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|EfactFunctionalGroupSendErrorWithoutGroup|  
|訊息文字|在序列化期間發生錯誤。 其中不包含群組，交換識別碼為 '{0}'，寄件者識別碼 '{1}'，Edifact 交換接收者識別碼 '{2}' 發生下列錯誤：|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 傳送管線在外寄 EDIFACT 交換序列化因為識別的交換與敘述的錯誤時，會發生錯誤。 請注意交換不含群組。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，找出交換中的錯誤，，然後決定產品說明中的問題解決方法需要使用錯誤訊息中的資訊。