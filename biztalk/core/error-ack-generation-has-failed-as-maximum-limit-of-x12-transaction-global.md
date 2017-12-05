---
title: "錯誤通知的產生失敗，因為 X12 全域交易的最大限制 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bbcae14-6e5c-4f79-87c6-311b4b54c7ff
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1eaef5e736ad01a9b49a3b46188b85b85a97e06
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="error-ack-generation-has-failed-as-maximum-limit-of-x12-transaction-global"></a>錯誤通知的產生失敗，因為 X12 全域交易的最大限制
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|BizTalk Server EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|通知產生失敗，因為可接受的 X12 交易集控制編號已達到 Guest 設定的最大限制。 瀏覽至 通用設定寄件者角色畫面，欄位 ST 2 在夥伴協議管理員 中，重設計數器|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法產生 x12 交換，因為它進入交易控制編號設定的通知控制編號 (ST2) 大於通知允許的項目 ST2 的最大值。 在本例中，BizTalk Server 會使用 EDI 全域屬性，若要建立通知。  
  
 交易集控制編號的最大值取決於用來控制編號的數字的數目。 這三個欄位的最大長度為 9;前置詞和尾碼欄位的最大長度為 8。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設控制編號欄位 (ST2.2) 的交易集控制編號 (ST2) 的 GS 和 ST 區段定義頁面的值小於最大限制。 在 BizTalk Server 管理主控台的 [EDI 全域屬性] 對話方塊中設定這個屬性。