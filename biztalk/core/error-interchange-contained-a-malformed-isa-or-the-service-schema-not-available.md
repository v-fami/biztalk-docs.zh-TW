---
title: 交換包含格式不正確的 ISA 或無法使用服務結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 78d285f6-26fb-4a3b-a959-a17623321b20
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84aec7600b71d48becfdeb30e34f837292c5ecfa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241654"
---
# <a name="the-interchange-contained-a-malformed-isa-or-the-service-schema-was-not-available"></a>交換包含格式不正確的 ISA 或服務結構描述無法使用
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|MalformedIsaError|  
|訊息文字|交換包含格式不正確的 ISA 或服務結構描述無法使用，完全它已被拒絕|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送的交換，因為 X12ServiceSchema，不符合交換中的 ISA 或 IEA 區段，或 （在 BaseArtifacts.dll) X12ServiceSchema未部署。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列其中一項：  
  
-   具有的寄件者的交換變更 ISA 和 IEA 區段，如此它們符合 X12ServiceSchema。  
  
-   請確定 BaseArtifacts.dll 包含 X12ServiceSchema 和部署。 您可以藉由開啟 BizTalk Server 管理主控台，開啟 [BizTalk EDI 應用程式] 節點，然後 [結構描述] 節點中，確認 X12ServiceSchema 列。