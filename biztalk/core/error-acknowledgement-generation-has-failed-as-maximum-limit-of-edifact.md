---
title: "通知產生失敗，因為已達到上限的 Edifact 交易集控制編號之全域設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6adc02d7-ebc4-4da0-a19a-3a423d63499d
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 252f0fd6dbe77eb83018e2bb34d4a6cd07cdbdf2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="acknowledgement-generation-has-failed-as-maximum-limit-of-edifact-transaction-set-control-number-has-been-reached-for-global-settings"></a>通知產生失敗，因為全域設定已達到可接受 Edifact 交易集控制編號的上限
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|通知產生失敗，因為最大的可接受 Edifact 交易集控制編號已達到 Guest 設定的限制。 瀏覽至 通用設定寄件者角色畫面，欄位 UNH 1 在夥伴協議管理員 中，重設計數器。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，BizTalk Server 無法產生 EDIFACT 交換通知因為高於它進入交易集參考編號 (UNH1) 的通知控制編號UNH1 允許的最大值。 在本例中，BizTalk Server 會使用 EDI 全域屬性，若要建立通知。  
  
 交易集參考編號的最大值取決於用來參考編號的數字的數目。 參考編號的字元數上限為 14 個字元，前置詞和後置詞上限為 13 個字元，而三個欄位總共不得超過 14 個字元。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設為低於最大限制值的交易集參考編號 (UNH1) 的 UNG 和 UNH 區段定義頁面中的參考編號欄位 (UNH1.2)。 在 [EDI 全域屬性] 對話方塊中設定此屬性[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]管理主控台。