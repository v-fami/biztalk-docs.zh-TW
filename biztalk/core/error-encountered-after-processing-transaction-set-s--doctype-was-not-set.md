---
title: "在處理交易 Set(s) 因為沒有設定文件類型之後所發生的錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a323658c-77d8-4059-aa15-d88c08e5450d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 874b0229eecdd5fe9c046f69789c4708b9280031
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-after-processing-transaction-sets-because-doctype-was-not-set"></a>在處理交易 Set(s) 因為沒有設定文件類型之後所發生的錯誤
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|DocTypeNotSet|  
|訊息文字|在處理 {0} 交易 Set(s) 之後發生的錯誤。 未設定文件類型|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送交易設定，因為 ST01 (對於 X12 交換) 或 UNH2.1 （適用於 EDIFACT 交換） 未設定為交易集。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，確認的交易集發生錯誤的 ST01 或 UNH1 區段設定為有效的文件類型。