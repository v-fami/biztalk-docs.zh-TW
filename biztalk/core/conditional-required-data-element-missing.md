---
title: 條件式的必要資料元素遺失 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5105c03-fa26-4c38-a276-c656f3076d5f
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f43ebf2ba593ad5133b93400bf0e9cb1151dc45b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978439"
---
# <a name="conditional-required-data-element-missing"></a>遺失條件式的必要資料元素
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                 X12DeConditionalRequiredDataElementMissingDescription                  |
|  訊息文字   |                       遺失條件式的必要資料元素                        |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送交換，因為不存在 X12ConditionDesignatorX 規則所需的資料元素，這是在交換中。  
  
## <a name="user-action"></a>使用者動作  
 此錯誤可能是使用內送交換，而非與組態或 BizTalk server 作業的問題。 若要解決這個錯誤，請連絡交換的寄件者，並指出它們需要變更在交換中使用的字元或使其符合，UNB1.1 欄位中所識別的字元集。