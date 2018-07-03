---
title: 發現交易集重複的控制編號 |Microsoft Docs
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
ms.openlocfilehash: d6b9b55dc5cd61bc4c8c806f2dc42259cadf2f69
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977704"
---
# <a name="transaction-set-duplicate-control-number-found"></a>發現交易集重複的控制編號
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                          X12TsDuplicateNumberFoundDescription                          |
|  訊息文字   |                     發現交易集重複的控制編號                     |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換的交易集控制編號的群組中的交易集因為交換已與另一個的控制編號相同交易集在該群組中。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  
  
-   群組中的交易集的控制交易的數目會設定內送交換中，因此會不有任何重複的控制編號，交易的變更集。  
  
-   如下所示停用檢查重複的交易集控制編號：  
  
    1.  開啟 [BizTalk Server 管理] 主控台。  
  
    2.  開啟傳送交換的合作對象 [EDI 屬性] 對話方塊。  
  
    3.  對於 X12 交換，清除 「 檢查重複項目 ST2 （交易集控制編號） 群組中 」 的 X12 交換處理屬性頁面的 EDI 屬性 對話方塊。  
  
    4.  對於 EDIFACT 交換，清除 「 檢查重複項目 UNH1 （交易集參考編號） 群組中"[EDIFACT 交換處理屬性] 頁面的 [EDI 屬性] 對話方塊中的屬性。