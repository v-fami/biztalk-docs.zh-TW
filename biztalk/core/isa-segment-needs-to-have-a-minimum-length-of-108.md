---
title: 必須有 108 最小長度 ISA 區段 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57641445-cebb-4219-998d-54038d7ddf19
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a67aa005be3107fde9ec617fc70f0d9e694e8599
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975159"
---
# <a name="isa-segment-needs-to-have-a-minimum-length-of-108"></a>ISA 區段的長度至少要有 108
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                               NseIsaSuffix1LFDescription                               |
|  訊息文字   |          必須有 108 最小長度 ISA 區段中，執行個體 {0}           |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換，因為服務結構描述所建立的數字數目不符合交換中的 ISA 區段 (X12ServiceSchema 或EdifactServiceSchema BaseArtifacts.dll 中)。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定每個欄位在 ISA 區段 （從 ISA01 到 ISA16) 中具有所需的最小數目的數字。 您可以看到數字的最小數目，藉由開啟 BizTalk Server 管理主控台中;開啟 [BizTalk 群組] 節點、 應用程式] 節點、 [BizTalk EDI 應用程式] 節點中，和在結構描述的節點開啟 Microsoft.BizTalk.Edi.BaseArtifacts.X12ServiceSchema ISA; 的根節點然後按一下 [結構描述檢視。