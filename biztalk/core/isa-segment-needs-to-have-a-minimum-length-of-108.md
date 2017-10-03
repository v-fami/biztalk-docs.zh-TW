---
title: "ISA 區段必須有最小長度為 108 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57641445-cebb-4219-998d-54038d7ddf19
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ecd5c6761c6dbcc59ad6353efa2772b9eecf387
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="isa-segment-needs-to-have-a-minimum-length-of-108"></a>ISA 區段的長度至少要有 108
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|NseIsaSuffix1LFDescription|  
|訊息文字|ISA 區段必須有 108 最小長度、 執行個體有 {0}|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換，因為服務結構描述所建立的數字的數目不符合交換中的 ISA 區段 (X12ServiceSchema 或EdifactServiceSchema BaseArtifacts.dll 中)。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定每個欄位 （從 ISA01 到 ISA16) ISA 區段中具有所需的一位數的最小數目。 您可以開啟 BizTalk Server 管理主控台中，查看數字的最小數目開啟 BizTalk 群組 節點、 應用程式 節點、 BizTalk EDI 應用程式 節點，和結構描述 節點中。開啟 Microsoft.BizTalk.Edi.BaseArtifacts.X12ServiceSchema ISA; 根節點然後按一下 結構描述檢視。