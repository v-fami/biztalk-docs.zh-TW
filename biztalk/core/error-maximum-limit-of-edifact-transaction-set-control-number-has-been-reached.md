---
title: 通知產生失敗，因為合作對象設定已達到的 Edifact 交易集控制編號的最大限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bcbb6374-0403-42b0-892b-b35157a2c74a
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b639f80d6ad203074e0542df6672f2d7b89aa2ec
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001343"
---
# <a name="acknowledgement-generation-has-failed-as-maximum-limit-of-edifact-transaction-set-control-number-has-been-reached-for-party-settings"></a>通知產生失敗，因為合作對象設定已達到最大限制的 Edifact 交易集控制編號
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                          |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                            |
| 產品版本 |                                                                                        [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                        |
|    事件識別碼     |                                                                                                                    -                                                                                                                     |
|  事件來源   |                                                                                                            BizTalk Server EDI                                                                                                            |
|    元件    |                                                                                                                將 EDI 引擎                                                                                                                |
|  符號名稱  |                                                                                                                    -                                                                                                                     |
|  訊息文字   | 通知產生失敗，因為最大上限為可接受 Edifact 交易集控制編號已達到合作對象{0}。 瀏覽至合作對象，傳送者角色畫面，欄位 [UNH 1 在夥伴協議] 管理員中，重設計數器。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 可能無法產生 EDIFACT 交換通知因為它已進入通知的交易集參考編號 (UNH1) 的控制編號大於UNH1 允許的最大值。 在此情況下，BizTalk Server 會使用 EDI 合作對象屬性建立通知。  
  
 交易集參考編號的最大值取決於用來參考編號的數字數目。 參考編號的字元數上限為 14 個字元，前置詞和後置詞上限為 13 個字元，而三個欄位總共不得超過 14 個字元。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設為低於最大限制值的交易集參考編號 (UNH1) 的 UNG 和 UNH 區段定義頁面中的參考編號欄位 (UNH1.2)。 在 [EDI 屬性] 對話方塊中，在 BizTalk Server 管理主控台中設定此屬性。