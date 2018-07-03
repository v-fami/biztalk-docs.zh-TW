---
title: 交換發生結構錯誤的第一個功能群組之前 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 12202148-0a32-464e-8dbd-d01b9ba530eb
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04150fc8db853719517c26e7ae91a904e7096fb5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996655"
---
# <a name="the-interchange-had-a-structural-error-in-before-the-first-functional-group"></a>交換發生結構錯誤的第一個功能群組之前
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                  |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                        |
| 產品版本 |                                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                    |
|    事件識別碼     |                                                                -                                                                 |
|  事件來源   |                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                      |
|    元件    |                                                            將 EDI 引擎                                                            |
|  符號名稱  |                                           X12InterchangeStructuralErrorBefore1stGroup                                            |
|  訊息文字   | 交換識別碼 '{0}'，寄件者識別碼為'{1}'，接收者識別碼 '{2}' 中/前第一次的功能群組發生結構錯誤 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送交換中，其中一個原因如下：  
  
-   結構的錯誤發生的 ISA 和 IEA 區段或第一個功能群組的交換，因此適用的結構描述不符合交換。  
  
-   未部署的 X12ServiceSchema （在 BaseArtifacts.dll)。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  
  
-   已交換變更 ISA 的寄件者和/或 IEA 區段或第一個功能群組，使其符合適用的結構描述，並再重新傳送交換。  
  
-   請確定 BaseArtifacts.dll 包含 X12ServiceSchema 和部署。 您可以藉由開啟 BizTalk Server 管理主控台，開啟 BizTalk EDI 應用程式 節點和 結構描述 節點中，確認已列出 X12ServiceSchema 來這麼做。