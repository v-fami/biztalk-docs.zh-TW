---
title: "交換有結構的錯誤。 錯誤處於暫停狀態後的部分 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9071825d-7b90-42bf-bcf9-2a15ae36086d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a028608e9843ee40c26bc7e8b158d97552a58163
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-interchange-had-structural-error-the-part-after-the-error-is-being-suspended"></a>交換有結構的錯誤。 錯誤後的部分正在遭到擱置
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|EfactInterchangeStructuralError|  
|訊息文字|交換傳送者識別碼 '{1}' 識別碼為 '{0}'、 接收者識別碼 '{2}' 有結構的錯誤。 錯誤後的部分已遭到擱置，請參閱擱置佇列，以取得詳細資料|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送 EDIFACT 交換，因為交換中發生的結構化的錯誤。 這會發生已被保留，與在錯誤時暫停交易集的交換。 這個錯誤，交易集 （或集合） 的結果包含錯誤的暫止，但其餘的交易設定已處理保留批次的一部分。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，將傳送者的交換修正結構的錯誤，然後再重新傳送交換。