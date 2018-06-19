---
title: BizTalk 設計階段工具 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Adapter Framework
- schemas, tools
- BizTalk Orchestration Designer
- schemas, BTARN schemas
- BizTalk Editor
- BizTalk Mapper
- tools, schemas
- BTARN, schemas
- BizTalk Pipeline Designer
ms.assetid: a981e167-f178-4fef-be0e-02fa15feffc2
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f259167112ab87da5af14ca73f735ae38d8789e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006625"
---
# <a name="biztalk-design-time-tools"></a>BizTalk 設計階段工具
開發人員在[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]可以使用 BizTalk Server 內建的設計階段工具的集合。 這些工具已整合至[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]。 如需有關[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]工具，請參閱[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server 說明。  
  
## <a name="biztalk-editor"></a>BizTalk Editor (BizTalk 編輯器)  
 您可以使用 [BizTalk 編輯器] 來管理[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]RosettaNet 夥伴介面程序 (Pip) 為基礎的 XSD 結構描述。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]會安裝您的方案開發的下列結構描述：  
  
-   0A1_FailureNotificationPropertySchema.xsd  
  
-   0A1_MS_V02_00_FailureNotification.xsd  
  
-   0A1_V1_FailureNotificationMessageGuideline.xsd  
  
-   0C1_MS_R01_02_AsynchronousTestNotification.xsd  
  
-   0C2_MS_R01_02_AsynchronousTestConfirmation.xsd  
  
-   0C2_MS_R01_02_AsynchronousTestRequest.xsd  
  
-   0C3_MS_R01_02_SynchronousTestNotification.xsd  
  
-   0C4_MS_R01_02_SynchronousTestQuery.xsd  
  
-   0C4_MS_R01_02_SynchronousTestResponse.xsd  
  
-   2A12_MS_V01_03_ProductMasterNotification.xsd  
  
-   3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.xsd  
  
-   3A2PriceAndAvailabilityResponseMessageGuideline_v1_3.xsd  
  
-   3A4_MS_V02_02_PurchaseOrderConfirmation.xsd  
  
-   3A4_MS_V02_02_PurchaseOrderRequest.xsd  
  
 這些結構描述位於\<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本\>Accelerator for rosettanet\sdk\schemas。  
  
 您可以加入多個結構描述從 RosettaNet 網站下載 Pip [http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859)。 如需詳細資訊，請參閱[納入新的交易夥伴介面程序](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)。  
  
## <a name="biztalk-mapper"></a>BizTalk Mapper (BizTalk 對應工具)  
 使用「BizTalk 對應工具」可以建立和自訂定義資料轉換的對應。 您可以使用「BizTalk 對應工具」對應 RosettaNet 輸入和輸出訊息類型的轉換。  
  
## <a name="biztalk-orchestration-designer"></a>BizTalk 協調流程設計師  
 「BizTalk 協調流程設計師」可以設計和實作商務程序。 您可以自訂 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 提供的私用程序。 如需詳細資訊，請參閱[私用程序 &#91;RN3 &#93;](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)和[自訂私用程序 &#91;RN3 &#93;](../../adapters-and-accelerators/accelerator-rosettanet/customizing-private-processes.md). 您不能自訂公開程序，如果這樣做，將會失去與 RosettaNet 的相容性。  
  
## <a name="biztalk-pipeline-designer"></a>BizTalk 管線設計師  
 「BizTalk 管線設計師」可以建立和設定用來定義及連結訊息處理步驟的管線。 管線會將訊息處理分成幾個階段，並決定每個工作類別的執行順序。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 包含接收和傳送這兩種 RosettaNet 實作架構 (RNIF) 管線。 如需詳細資訊，請參閱[RNIF 管線](../../adapters-and-accelerators/accelerator-rosettanet/rnif-pipelines.md)。  
  
## <a name="biztalk-adapter-framework"></a>BizTalk 配接器架構  
 「BizTalk 配接器架構」可以搭配端點配接器一起使用，以便與交易夥伴及應用程式進行整合。  
  
## <a name="see-also"></a>請參閱  
 [BizTalk Server 與 BTARN 的工具和功能](../../adapters-and-accelerators/accelerator-rosettanet/tools-and-features-of-biztalk-server-and-btarn.md)   
 [管理和執行階段工具](../../adapters-and-accelerators/accelerator-rosettanet/administration-and-run-time-tools.md)   
 [分析工具](../../adapters-and-accelerators/accelerator-rosettanet/analysis-tools1.md)   
 [整合新的交易夥伴介面程序](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)