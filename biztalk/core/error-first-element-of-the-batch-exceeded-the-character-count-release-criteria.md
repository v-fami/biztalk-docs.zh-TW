---
title: "批次的第一個項目超過字元計數發行準則集 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4b06f8f-247d-4e93-8c4e-5e86e4ad70c9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 746fbfabb2fe411310735f66c6d8a8398a94a5dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-first-element-of-the-batch-exceeded-the-character-count-release-criteria-set"></a>批次的第一個項目超過字元計數發行準則集
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|批次處理引擎|  
|符號名稱|FirstElementExceededCharCount|  
|訊息文字|批次的第一個項目超過字元計數發行準則集。 請變更要能夠處理此訊息的字元計數釋放準則。 訊息將會需要修改設定之後重新傳送至批次處理系統|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，批次處理協調流程無法產生批次的交換，因為第一個批次處理協調流程收取的批次項目中的字元數超過字元數批次釋放準則的 「 最大的交換中的字元數 」 屬性所指定。 請注意相較於最大值的字元數不在信封中包含的字元數。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列其中一項：  
  
1.  增加做為交換接收者的合作對象的交換批次建立設定 頁面的 EDI 屬性 對話方塊中的 「 最大的交換中的字元數 」 屬性。 若要這樣做，您必須停止協調流程執行個體中，增加的屬性中的字元數上限，然後重新啟動協調流程執行個體。 必須重新傳送訊息寄件者。  
  
2.  需要寄件者傳送具有字元少於最大字元數的交易集。