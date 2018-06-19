---
title: 交易集的重複控制編號找到 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b2779a0-b365-4c4b-81c7-8f9284748b6e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe63d3814bcce178164054ab8dcf673eeb4f395a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278558"
---
# <a name="transaction-set-duplicate-control-number-found"></a>找到的交易集重複控制編號
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12TsDuplicateNumberFoundDescription|  
|訊息文字|找到的交易集重複控制編號|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換的交易集控制編號的群組中的交易集，因為已交換控制編號，另一個相同該群組中的交易集。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列其中一項：  
  
-   群組中的交易集的控制交易的數字設定內送交換中，因此交易不重複控制編號的變更集。  
  
-   停用重複交易集控制編號檢查如下：  
  
    1.  開啟 [BizTalk Server 管理] 主控台。  
  
    2.  開啟傳送交換的合作對象 [EDI 屬性] 對話方塊。  
  
    3.  對於 X12 交換，清除 「 核取的重複項目 ST2 （交易集控制編號） 群組中 」 的 [X12 交換處理屬性] 頁面的 [EDI 屬性] 對話方塊。  
  
    4.  對於 EDIFACT 交換，清除 「 核取的重複 UNH1 （交易集參考編號） 群組中 「 [EDIFACT 交換處理屬性] 頁面的 [EDI 屬性] 對話方塊中的屬性。