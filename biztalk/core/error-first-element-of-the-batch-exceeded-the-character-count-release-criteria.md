---
title: 批次的第一個項目已超過字元計數釋放準則集 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4b06f8f-247d-4e93-8c4e-5e86e4ad70c9
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 880e29ceb2be1c574aeaec248ce47317e332e5a6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972655"
---
# <a name="the-first-element-of-the-batch-exceeded-the-character-count-release-criteria-set"></a>批次的第一個項目已超過字元計數釋放準則集
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                         |
| 產品版本 |                                                                                                     [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                                     |
|    事件識別碼     |                                                                                                                                 -                                                                                                                                  |
|  事件來源   |                                                                                       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                                                       |
|    元件    |                                                                                                                          批次引擎                                                                                                                           |
|  符號名稱  |                                                                                                                   FirstElementExceededCharCount                                                                                                                    |
|  訊息文字   | 批次的第一個項目已超過字元計數釋放準則集。 請變更要能夠處理此訊息的字元計數釋放準則。 訊息將會需要修改設定之後重新傳送至批次處理系統 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，批次處理協調流程無法產生批次的交換因為揀取批次處理協調流程的第一個批次項目中的字元數超過字元數屬性所指定 「 最大的交換中的字元數 」 的批次釋放準則。 請注意相較於最大值的字元數目不在信封中包含的字元數。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  
  
1.  增加做為交換接收者的合作對象的交換批次建立設定 頁面中的 EDI 屬性 對話方塊中的 「 最大的交換中的字元數 」 屬性。 若要這樣做，您必須先停止協調流程執行個體中，增加最大的在屬性中的字元數，然後重新啟動協調流程執行個體。 已重新傳送訊息的寄件者。  
  
2.  已傳送的交易集具有較少的字元，最大字元數比寄件者。