---
title: 交換發生結構錯誤。 可能的原因是因為遺失歸位無效的區段結束字元和-或換行字元分隔符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 035e37d5-d4a8-49d0-8d75-3bcf2426cac7
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e1d3c90d69b3e482ac570538f5dcc6997a63aea
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988767"
---
# <a name="the-interchange-had-structural-error-a-likely-cause-is-invalid-segment-terminator-due-to-missing-carriage-line-and-or-line-feed-seperators"></a>交換發生結構錯誤。 可能的原因是因為遺失歸位無效的區段結束字元和-或換行字元分隔符號
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                                   |
| 產品版本 |                                                                                                              [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                                               |
|    事件識別碼     |                                                                                                                                           -                                                                                                                                           |
|  事件來源   |                                                                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                                                                 |
|    元件    |                                                                                                                                      將 EDI 引擎                                                                                                                                       |
|  符號名稱  |                                                                                                                        EfactInterchangeStructuralErrorAfterUnb                                                                                                                        |
|  訊息文字   | 交換識別碼 '{0}'，寄件者識別碼為'{1}'，接收者識別碼 '{2}' 發生結構錯誤。 可能的原因是因為遺失歸位/換行字元或分隔符號的無效的區段結束字元。 錯誤後的部分已遭到擱置，請參閱擱置佇列，以取得詳細資料 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線，而傳送管線 」 或 「 批次處理協調流程無法處理 EDIFACT 交換，因為在交換中的線段沒有必要的區段結束字元。 內送的交換，在 UNA 區段中，找到分隔符號或 UNA 區段不存在，如果 EfactDelimiters 管線屬性。 針對外寄交換的 [EDI 屬性] 對話方塊中的 [UNA 區段定義] 頁面中所識別的分隔符號。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，確定交換中的所有區段具有必要的區段結束字元，就會重新傳送交換。