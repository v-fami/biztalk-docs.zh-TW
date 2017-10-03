---
title: "包含的交易集數目不相符 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db958803-4667-4558-81a6-70c62d6fe8bf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16a28544757c3e9ae75dd7230673c4526fc2c8f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="number-of-included-transaction-sets-do-not-match"></a>包含的交易集數目不相符
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12FaNumberOfTsMismatchDescription|  
|訊息文字|包含的交易集數目不相符|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示交易的數目設定群組中的 x12 交換不等於群組結尾 （GE01 欄位） 中的數字。 會發生這種情況時保留交換，並發生錯誤時暫停交換。 （錯誤訊息不張貼如果保留交換和交易集發生錯誤時，就會暫停，或是在交換分割。）  
  
## <a name="user-action"></a>使用者動作  
 若要解決此錯誤，確定群組結尾之 GE01 欄位中的數目與交換之群組中的交易集數目相同，然後重新傳送交換。