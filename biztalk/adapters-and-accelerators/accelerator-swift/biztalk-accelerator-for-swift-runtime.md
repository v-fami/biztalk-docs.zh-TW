---
title: "BizTalk Accelerator for SWIFT 的執行階段 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime, architecture
- developing, components
- architecture, topology
- messages, message flow diagram
- runtime, components
- SWIFT runtime
- architecture, runtime architecture
- SWIFT network
- A4SWIFT, network
- topology
ms.assetid: c0f59760-7d7d-4b22-a7dc-54e563971d4a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 340cb27daf29e08ad63f20168680c6596650ca0d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="biztalk-accelerator-for-swift-runtime"></a>BizTalk Accelerator for SWIFT 的執行階段
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]提供兩種形式的功能： 開發資料和執行階段元件。 開發材料包括 XSD 結構描述，驗證規則和原則和範例程式碼。 執行階段元件包括自訂 SWIFT 解譯器、 自訂 SWIFT 組譯工具、 Message Repair 和 New Submission 協調流程 (MrsrRepair.odx) 和 FIN 回應對帳協調流程 (FrrMain.odx)。 如需有關 Message Repair 和 New Submission 的詳細資訊，請參閱[Message Repair 和 New Submission](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission.md)。 如需有關 FRR 的詳細資訊，請參閱[FIN 回應對帳](../../adapters-and-accelerators/accelerator-swift/fin-response-reconciliation.md)。  
  
 如下圖所示的高層級的系統架構[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]。  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-end-to-end.gif "A4SWIFTSystemArchitecture_End_to_End")  
  
 下圖說明 A4SWIFT 與後端應用程式之間訊息的流程為何及如何使用 A4SWIFT [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] MRSR 中的表單的 Message Repair 和 New Submission 網站。  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-interfaceswithbackendapplications.gif "A4SWIFTSystemArchitecture_InterfaceswithBackEndApplications")  
  
 下圖說明訊息 A4SWIFT SWIFT 網路之間流動的方式。  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-interfaceswiththeswiftnetwork.gif "A4SWIFTSystemArchitecture_InterfaceswiththeSWIFTNetwork")  
  
 您可以定義所有 A4SWIFT 元件為 BizTalk Server 應用程式元件垂直專屬實作。 BizTalk 「 加速器 」 提供開發和執行階段以加速上方的垂直特定 BizTalk 應用程式開發功能[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 因此，所有的 A4SWIFT 元件 （開發或執行階段） 遵守，並放入 BizTalk Server 應用程式架構。 A4SWIFT 安裝到執行階段元件[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]做為自訂元件的執行階段。 在開發之後材料編譯和部署，A4SWIFT 和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行階段使用它們來提供 SWIFT 訊息和自動化功能。  
  
 下圖顯示 BizTalk server 的高階應用程式拓樸。  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro1.gif "FSA_Intro1")  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式模型使用的 MessageBox 資料庫和管理訊息流程進出 MessageBox 資料庫的發行者訂閱者模式。 如需 BizTalk 架構和應用程式設計的詳細資訊，請參閱 BizTalk Server 說明。  
  
 A4SWIFT 應用程式模型繼承[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式模型，並將它加入 SWIFT 特有的元件，以便 SWIFT 相關解決方案上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 下列清單描述這些 A4SWIFT 特有的元件：  
  
-   **執行階段元件。** SWIFT 中 SWIFT 組合器的傳送管線、 Message Repair 和 New Submission 協調流程和 FIN 回應對帳協調流程中，接收管線的解譯器。  
  
-   **開發材料。** SWIFT 的結構描述、 規則、 協調流程和包含在客戶解決方案並部署到執行的執行階段的範例專案。  
  
 本章節描述 A4SWIFT 中的執行階段詳細資料。  
  
 此部分包含：  
  
-   [SWIFT 解譯器](../../adapters-and-accelerators/accelerator-swift/swift-disassembler.md)  
  
-   [SWIFT 組合器](../../adapters-and-accelerators/accelerator-swift/swift-assembler.md)  
  
-   [透過接收位置和 InfoPath 表單提交訊息](../../adapters-and-accelerators/accelerator-swift/submitting-messages-through-receive-locations-and-infopath-forms.md)  
  
-   [訊息驗證引擎](../../adapters-and-accelerators/accelerator-swift/message-validation-engine.md)