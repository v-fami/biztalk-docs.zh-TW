---
title: "交換有結構的錯誤。 可能的原因是因為遺漏歸位無效的區段結束字元和-或換行字元 seperators |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 035e37d5-d4a8-49d0-8d75-3bcf2426cac7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e983e44b1284bf16e06dbfc90159afc0ed5608c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-interchange-had-structural-error-a-likely-cause-is-invalid-segment-terminator-due-to-missing-carriage-line-and-or-line-feed-seperators"></a>交換有結構的錯誤。 可能的原因是因為遺漏歸位無效的區段結束字元和-或換行字元 seperators
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|EfactInterchangeStructuralErrorAfterUnb|  
|訊息文字|交換傳送者識別碼 '{1}' 識別碼為 '{0}'、 接收者識別碼 '{2}' 有結構的錯誤。 可能的原因是因為遺漏歸位字元列及/或換行字元 seperators 無效的區段結束字元。 錯誤後的部分已遭到擱置，請參閱擱置佇列，以取得詳細資料|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線，傳送管線或批次處理協調流程無法處理 EDIFACT 交換，因為交換中的區段沒有必要的區段結束字元。 內送交換，分隔符號在 UNA 區段中，識別或 UNA 區段不存在，如果 EfactDelimiters 管線屬性。 針對外寄交換，EDI 屬性 對話方塊的 UNA 區段定義 頁面中所識別的分隔符號。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認交換中的所有區段具有必要的區段結束字元，則需要重新傳送交換。