---
title: 公開程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- public processes, orchestrations
- business processes, public processes
- public processes, trading partners
- BTARN, public processes
- orchestrations, public-process orchestrations
- public processes
- trading partners, public processes
- public processes, about public processes
ms.assetid: 5ccc7449-5741-4d49-beb6-567bcd93f679
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f9d0288defa0705c7e12f102011edbf9ee7e90d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984719"
---
# <a name="public-processes"></a>公開程序
Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]實作商務程序牽涉到與交易夥伴的公開程序整合。 並將組織內部的商務程序實作為私用程序。 使用公開程序和私用程序，會將 RosettaNet 實作架構 (RNIF) 處理 (在公開程序中) 從服務內容處理及後端整合 (在私用程序中) 隔離出來。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會實作公開程序做為長期執行的 BizTalk 協調流程。 一個公開程序協調流程會在啟動者端執行，另一個則是在回應者端執行。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 安裝程式為 RNIF 1.1 與 RNIF 2.01 都提供了啟動者及回應者公開程序協調流程版本。  
  
 這些公開程序協調流程會實作所有的 RNIF 程序。 公開程序對其餘的元件隱藏了 RNIF 的複雜性。 公開程序除了強制執行 RNIF 相容的訊息流程之外，也會決定預設追蹤設定，並提供執行階段的程序狀態資訊， 但不會處理訊息的服務內容。 這種工作是由私用程序執行。  
  
 每個交易夥伴協議都會參考單一公開程序，以啟動或回應交易夥伴介面程序 (PIP) 動作。 不過，公開程序無法確認 PIP 是否存在。  
  
 RosettaNet 規格規定了公開程序的設計。 建議您不要修改公開程序。 公開程序協調流程已建立版本並經過簽署。 如果修改公開程序，就不再與 RNIF 相容。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [啟動者公開程序](../../adapters-and-accelerators/accelerator-rosettanet/initiator-public-process.md)  
  
-   [回應者公開程序](../../adapters-and-accelerators/accelerator-rosettanet/responder-public-process.md)