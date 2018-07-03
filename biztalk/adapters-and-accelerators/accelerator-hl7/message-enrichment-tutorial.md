---
title: 訊息擴充教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial
- message enrichment tutorial, about the tutorial
- messages, tutorial
- tutorials, message enrichment tutorial
ms.assetid: 4ffb047f-457a-4a80-b7ec-4b61ae16f35f
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f60a6cc6bcb98e01489e981a39370215744ab860
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004039"
---
# <a name="message-enrichment-tutorial"></a>訊息擴充教學課程
本教學課程提供逐步程序使用的 Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]來解決特定商務問題： 訊息豐富 」 問題。 訊息擴充教學課程將告訴您不必加入或擴充的情況下，不符合規範 HL7 和/或不完整的訊息。 這可能與應用程式，例如病患的註冊應用程式，或可能會填入來自 Microsoft 的 XML 資料的訊息時[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]。  
  
 在本教學課程中，您可以擷取 BTAHL7 的訊息，並提供任何遺漏的資料，例如從病患記錄資料庫。 然後將訊息轉換，並將它傳送至一個實驗室、 保險或使用 MLLP （最少較低層通訊協定） 配接器任何舊版的特定業務 (LOB) 應用程式。  
  
 在本教學課程中，您可以使用 Web 服務用戶端 (WSClient.exe) 應用程式在此情況下 「 doorbell"註冊病患觸發程序事件，透過 SOAP 配接器傳送的 XML 格式的訊息， [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] BTAHL7 使用。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 接收 SOAP 中的訊息接收埠，而且訊息至協調流程發佈為 Web 服務的路由。 XML 訊息會包含病患的名稱和身分證號碼。 您擴大訊息，並將訊息轉換成 HL7 格式使用結構描述、 對應和轉換。 然後，您會透過 MLLP 配接器傳送到實驗室環境，保險、 或 LOB 應用程式。  
  
 下圖顯示本教學課程的處理流程。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-msgenrichtutarch.gif "hl7_msgenrichtutarch")  
  
> [!NOTE]
>  本教學課程需要 Windows Server Standard、 Enterprise、 Datacenter 或 Web Edition 和自訂的 BTAHL7 安裝包含 MLLP 測試工具。 此外，您應該先熟悉[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]中的程式開發[!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)]中找到的資訊並[深入了解 HL7 加速器以及可用的 BizTalk 工具](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)。  
> 
> [!NOTE]
>  您可以避免解除部署組件，停止傳送埠的錯誤和停用接收位置，您在先前的教學課程中使用。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1：設定應用程式集區識別](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-application-pool-identity.md)  
  
-   [步驟 2：建立新的專案](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md)  
  
-   [步驟 3：指派強式名稱給組件](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md)  
  
-   [步驟 4：建立結構描述](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-schemas.md)  
  
-   [步驟 5：升級結構描述屬性](../../adapters-and-accelerators/accelerator-hl7/step-5-promote-schema-properties.md)  
  
-   [步驟 6：驗證結構描述](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md)  
  
-   [步驟 7：簽署和建置專案](../../adapters-and-accelerators/accelerator-hl7/step-7-sign-and-build-the-projects.md)  
  
-   [步驟 8：使用 BizTalk 對應工具建立對應](../../adapters-and-accelerators/accelerator-hl7/step-8-create-a-map-with-biztalk-mapper.md)  
  
-   [步驟 9：驗證和建置對應專案](../../adapters-and-accelerators/accelerator-hl7/step-9-validate-and-build-the-map-project.md)  
  
-   [步驟 10：建立協調流程](../../adapters-and-accelerators/accelerator-hl7/step-10-create-an-orchestration.md)  
  
-   [步驟 11：建立協調流程變數](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md)  
  
-   [步驟 12：設定協調流程圖形](../../adapters-and-accelerators/accelerator-hl7/step-12-configure-orchestration-shapes.md)  
  
-   [步驟 13：建立和設定連接埠](../../adapters-and-accelerators/accelerator-hl7/step-13-create-and-configure-ports.md)  
  
-   [步驟 14：將協調流程發佈為 Web 服務](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md)  
  
-   [步驟 15：部署並設定傳送埠和接收埠](../../adapters-and-accelerators/accelerator-hl7/step-15-configure-the-send-and-receive-ports.md)  
  
-   [步驟 16：啟動協調流程](../../adapters-and-accelerators/accelerator-hl7/step-16-start-the-orchestration.md)  
  
-   [步驟 17：建立 WSClient 應用程式](../../adapters-and-accelerators/accelerator-hl7/step-17-create-the-wsclient-application.md)  
  
-   [步驟 18：測試您的新訊息擴充方案](../../adapters-and-accelerators/accelerator-hl7/step-18-test-your-new-message-enrichment-solution.md)