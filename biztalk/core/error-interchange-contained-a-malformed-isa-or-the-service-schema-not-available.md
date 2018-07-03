---
title: 交換包含格式不正確的 ISA，或無法使用服務結構描述 |Microsoft Docs
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
ms.openlocfilehash: cce469b25a2ba15c3038ea9079c3f22fc4f8c0c2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010711"
---
# <a name="the-interchange-contained-a-malformed-isa-or-the-service-schema-was-not-available"></a>交換包含格式不正確的 ISA，或服務結構描述無法使用
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                 |
| 產品版本 |                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                             |
|    事件識別碼     |                                                         -                                                          |
|  事件來源   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI               |
|    元件    |                                                     將 EDI 引擎                                                     |
|  符號名稱  |                                                 MalformedIsaError                                                  |
|  訊息文字   | 交換包含格式不正確的 ISA 或服務結構描述無法使用，它完全拒絕 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送的交換，因為 X12ServiceSchema，不符合交換中的 ISA 或 IEA 區段，或 （在 BaseArtifacts.dll) X12ServiceSchema未部署。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  
  
-   有的寄件者的交換變更 ISA 和 IEA 區段，使它們符合 X12ServiceSchema。  
  
-   請確定 BaseArtifacts.dll 包含 X12ServiceSchema 和部署。 您可以藉由開啟 BizTalk Server 管理主控台，開啟 BizTalk EDI 應用程式 節點，然後 結構描述 節點中，確認已列出 X12ServiceSchema 來這麼做。