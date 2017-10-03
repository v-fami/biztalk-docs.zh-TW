---
title: "交換發生結構錯誤的第一個功能群組之前 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12202148-0a32-464e-8dbd-d01b9ba530eb
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d5ab490de214f53e85ea32c1b243456f837c72e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-interchange-had-a-structural-error-in-before-the-first-functional-group"></a>交換發生結構錯誤的第一個功能群組之前
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12InterchangeStructuralErrorBefore1stGroup|  
|訊息文字|交換傳送者識別碼 '{1}' 識別碼為 '{0}'、 接收者識別碼 '{2}' 必須在/之前第一個功能群組的結構錯誤|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送交換中，其中一個原因如下：  
  
-   結構的錯誤發生的 ISA 和 IEA 區段或交換的第一個的功能群組中，因此適用的結構描述不符合交換。  
  
-   未部署的 X12ServiceSchema （在 BaseArtifacts.dll)。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列其中一項：  
  
-   交換變更 ISA 的寄件者及/或 IEA 區段或第一次的功能群組，使其符合適用的結構描述，而且再重新傳送交換。  
  
-   請確定 BaseArtifacts.dll 包含 X12ServiceSchema 和部署。 您可以藉由開啟 BizTalk Server 管理主控台，開啟 [BizTalk EDI 應用程式] 節點和 [結構描述] 節點中，確認 X12ServiceSchema 列。