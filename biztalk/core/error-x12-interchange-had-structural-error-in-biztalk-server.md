---
title: "交換有結構的錯誤。 最後一個結構上有效的功能群組識別碼為: |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd62855b-ecc6-4cfd-be9c-0025348eb841
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 565a4865455cabef3cd53988d601a89ecf1549e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-interchange-had-structural-error-last-structurally-valid-functional-group-id-was"></a>交換有結構的錯誤。 最後一個結構有效的功能群組識別碼是：
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12InterchangeStructuralErrorAfter1stGroup|  
|訊息文字|交換傳送者識別碼 '{1}' 識別碼為 '{0}'、 接收者識別碼 '{2}' 有結構的錯誤。 上次結構上有效的功能群組識別碼為 '{3}'|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換，因為指定的功能群組後發生交換中的結構化的錯誤。 這可能會發生已被保留，與在錯誤時暫停交易集的交換。 這個錯誤，交易集 （或集合） 的結果包含錯誤的暫止，但其餘的交易設定已處理保留批次的一部分。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，將傳送者的交換修正結構的錯誤，然後再重新傳送交換。