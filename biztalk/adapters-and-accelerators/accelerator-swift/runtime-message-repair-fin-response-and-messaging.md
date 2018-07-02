---
title: 執行階段、 訊息修復、 FIN 回應和傳訊 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, about architecture
- architecture
- BizTalk Accelerator for SWIFT, architecture
ms.assetid: c7f34517-6663-44a6-b6ea-6d55fdb08caf
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 360a2e3974f1e4ea5858c583c5dc5fcc364e9756
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974631"
---
# <a name="runtime-message-repair-fin-response-and-messaging"></a>執行階段、 訊息修復、 FIN 回應和傳訊

## <a name="overview"></a>概觀
Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]讓客戶和夥伴財務產業特定傳訊和連線功能，可協助加速實作[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]為中介軟體的財務組織。  
  
 利用開放式標準基礎的工具和執行階段功能的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]若要實作類似 SWIFT 的訊息格式的支援，A4SWIFT 減少屏障採用更新的 SWIFT 標準採用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]為一般用途中介軟體整合平台。  
  
 A4SWIFT 和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]減少時間上市同時也降低總擁有成本 (TCO)，藉由減少整體的維護與支援成本，提供企業類別裝載應用程式和整合，以及工作流程伺服器金融服務產業中的實作。  
  
 您可以廣泛分類 A4SWIFT messaging 的 SWIFT 和 SWIFT 的連線能力的功能。 完整 A4SWIFT 訊息包含 SWIFT 訊息剖析和驗證 （包括輸入/輸出批次處理）、 訊息項目和修復 (包括與 Microsoft 的整合[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]做為前端使用者工具)，和其他營運 (LOB) 應用程式。  
  
 [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] 提供 XSD 結構描述和完整的驗證，包括網路規則，所有 358 的財務 (FIN) 訊息。 它也提供輸入解除批次處理。  

## <a name="next-steps"></a>後續的步驟  
 此部分包含：  
  
-   [元件](components.md)  
  
-   [BizTalk Accelerator for SWIFT 執行階段](biztalk-accelerator-for-swift-runtime.md)  
  
-   [Message Repair 和 New Submission](message-repair-and-new-submission.md)  
  
-   [FIN 回應對帳](fin-response-reconciliation.md)  
  
-   [SWIFT 訊息](swift-messages.md)

- [A4SWIFT_* 升級屬性](a4swift-promoted-properties.md)