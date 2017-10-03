---
title: "訊息擴充教學課程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial
- message enrichment tutorial, about the tutorial
- messages, tutorial
- tutorials, message enrichment tutorial
ms.assetid: 4ffb047f-457a-4a80-b7ec-4b61ae16f35f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 532fc0e8a9aeefbc35a892277c68be8d640b5588
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-enrichment-tutorial"></a>訊息擴充教學課程
本教學課程提供逐步程序使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]來解決特定商務問題： 訊息豐富 」 問題。 「 訊息豐富 」 教學課程描述的情況下，您不必加入或擴充、 不是 HL7 相容及/或不完整的訊息。 這可能是與應用程式，例如病患註冊應用程式，或會填入來自 XML 資料的訊息時，它會發生[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]。  
  
 在本教學課程中，您可以擷取 BTAHL7 的訊息，並提供任何遺失的資料，例如，從病患記錄資料庫。 然後將訊息轉換，並將它傳送至實驗室、 保險或使用 MLLP （最少較低層通訊協定） 配接器任何舊版的特定業務 (LOB) 應用程式。  
  
 在本教學課程中，您可以使用 Web 服務用戶端 (WSClient.exe) 應用程式在此情況下"doorbell"註冊病患觸發程序事件，透過 SOAP 配接器傳送的 XML 格式的訊息， [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] BTAHL7 與。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]在 SOAP 接收的訊息接收埠，而且訊息至協調流程發佈為 Web 服務的路由。 XML 訊息包含的病患的名稱和身分證號碼。 您擴充訊息，並將訊息轉換為 HL7 格式使用結構描述、 對應和轉換。 然後，您將會透過 MLLP 配接器傳送到實驗室，保險，或 LOB 應用程式。  
  
 下圖顯示程序流程的教學課程。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-msgenrichtutarch.gif "hl7_msgenrichtutarch")  
  
> [!NOTE]
>  本教學課程需要 Windows Server Standard、 Enterprise、 Datacenter 或 Web Edition 和自訂的 BTAHL7 安裝包含 MLLP 測試工具。 此外，您應該熟悉[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]中的開發[!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)]中找到的資訊和[深入了解 HL7 加速器以及可用的 BizTalk 工具](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)。  
  
> [!NOTE]
>  您可以避免錯誤解除部署組件，停止傳送埠和停用接收位置，您在先前的教學課程中使用。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1： 設定應用程式集區識別](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-application-pool-identity.md)  
  
-   [步驟 2： 建立新的專案](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md)  
  
-   [步驟 3： 指派強式名稱組件](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md)  
  
-   [步驟 4： 建立結構描述](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-schemas.md)  
  
-   [步驟 5： 升級結構描述屬性](../../adapters-and-accelerators/accelerator-hl7/step-5-promote-schema-properties.md)  
  
-   [步驟 6： 驗證結構描述](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md)  
  
-   [步驟 7： 簽署和建置的專案](../../adapters-and-accelerators/accelerator-hl7/step-7-sign-and-build-the-projects.md)  
  
-   [步驟 8： 使用 BizTalk 對應工具建立對應](../../adapters-and-accelerators/accelerator-hl7/step-8-create-a-map-with-biztalk-mapper.md)  
  
-   [步驟 9： 驗證和建置對應專案](../../adapters-and-accelerators/accelerator-hl7/step-9-validate-and-build-the-map-project.md)  
  
-   [步驟 10： 建立協調流程](../../adapters-and-accelerators/accelerator-hl7/step-10-create-an-orchestration.md)  
  
-   [步驟 11： 建立協調流程變數](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md)  
  
-   [步驟 12： 設定協調流程圖形](../../adapters-and-accelerators/accelerator-hl7/step-12-configure-orchestration-shapes.md)  
  
-   [步驟 13： 建立和設定連接埠](../../adapters-and-accelerators/accelerator-hl7/step-13-create-and-configure-ports.md)  
  
-   [步驟 14： 發佈為 Web 服務的協調流程](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md)  
  
-   [步驟 15： 設定傳送埠和接收埠](../../adapters-and-accelerators/accelerator-hl7/step-15-configure-the-send-and-receive-ports.md)  
  
-   [步驟 16： 啟動協調流程](../../adapters-and-accelerators/accelerator-hl7/step-16-start-the-orchestration.md)  
  
-   [步驟 17： 建立 WSClient 應用程式](../../adapters-and-accelerators/accelerator-hl7/step-17-create-the-wsclient-application.md)  
  
-   [步驟 18： 測試您的新訊息擴充方案](../../adapters-and-accelerators/accelerator-hl7/step-18-test-your-new-message-enrichment-solution.md)