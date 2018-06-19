---
title: 遺漏或無效的交易集識別項 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 282c8128-7d23-44e2-bf44-e90e52cb5fb1
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f23f44587abf67e608cff79150d9633f1707ff2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263006"
---
# <a name="missing-or-invalid-transaction-set-identifier"></a>遺漏或無效的交易集識別項
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|EfactTsMissingOrInvalidTsIdentiferDescription|  
|訊息文字|遺漏或無效的交易集識別項|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收或傳送管線無法處理 EDIFACT 交換，因為交易集識別項 （在 [UNH2.1] 欄位中） 的值已遺失或有無效的值。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定交換已 UNH2.1 欄位的值。 請確認 UNH2.1 的值為有效的單位數以六位數文件類型指示項。