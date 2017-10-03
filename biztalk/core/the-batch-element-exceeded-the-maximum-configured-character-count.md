---
title: "批次項目已超過設定的最大字元數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ad12733-295a-43ba-8147-34c8716c2d37
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dac259db250a88e434efb649a2baf2e75b805a40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-batch-element-exceeded-the-maximum-configured-character-count"></a>批次項目已超過設定的最大字元數
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|批次處理引擎|  
|符號名稱|MessageExceededCharacterCount|  
|訊息文字|批次項目已超過設定的最大字元數|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，批次處理協調流程無法產生批次的交換因為批次處理協調流程收取批次項目中的字元數超過所指定的字元數批次釋放準則 「 最大的交換中的字元數 」 屬性。 會產生此錯誤訊息的批次項目不會挑選要批次，但是批次元素之後的第一個元素已經批次處理的第一個批次元素。 請注意相較於最大值的字元數不在信封中包含的字元數。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列其中一項：  
  
1.  增加做為交換接收者的合作對象的交換批次建立設定 頁面的 EDI 屬性 對話方塊中的 「 最大的交換中的字元數 」 屬性。 若要這樣做，您必須停止協調流程執行個體中，增加的屬性中的字元數上限，然後重新啟動協調流程執行個體。  
  
2.  需要寄件者傳送具有字元少於最大字元數的交易集。