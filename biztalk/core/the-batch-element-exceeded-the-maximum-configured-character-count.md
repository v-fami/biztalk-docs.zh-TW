---
title: 批次項目已超過設定的最大字元計數 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7ad12733-295a-43ba-8147-34c8716c2d37
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 689ba342affa3ed4f246e9aa963f8ea4e22704af
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992415"
---
# <a name="the-batch-element-exceeded-the-maximum-configured-character-count"></a>批次項目已超過設定的最大字元計數
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                    批次引擎                                     |
|  符號名稱  |                             MessageExceededCharacterCount                              |
|  訊息文字   |           批次項目已超過設定的最大字元計數            |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，批次處理協調流程無法產生批次的交換因為的批次處理協調流程收取批次項目中的字元數超過指定的字元數目批次釋放準則的 「 最大的交換中的字元數 」 屬性。 會產生此錯誤訊息的批次項目不會挑選要批次，但是批次元素已批次處理的第一個元素之後的第一個批次元素。 請注意相較於最大值的字元數目不在信封中包含的字元數。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  
  
1.  增加做為交換接收者的合作對象的交換批次建立設定 頁面中的 EDI 屬性 對話方塊中的 「 最大的交換中的字元數 」 屬性。 若要這樣做，您必須先停止協調流程執行個體中，增加最大的在屬性中的字元數，然後重新啟動協調流程執行個體。  
  
2.  已傳送的交易集具有較少的字元，最大字元數比寄件者。