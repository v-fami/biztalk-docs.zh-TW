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
# <a name="message-enrichment-tutorial"></a><span data-ttu-id="4090d-102">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="4090d-102">Message Enrichment Tutorial</span></span>
<span data-ttu-id="4090d-103">本教學課程提供逐步程序使用的 Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]來解決特定商務問題： 訊息豐富 」 問題。</span><span class="sxs-lookup"><span data-stu-id="4090d-103">This tutorial provides step-by-step procedures for using Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to solve a particular business problem: the message enrichment problem.</span></span> <span data-ttu-id="4090d-104">訊息擴充教學課程將告訴您不必加入或擴充的情況下，不符合規範 HL7 和/或不完整的訊息。</span><span class="sxs-lookup"><span data-stu-id="4090d-104">The message enrichment tutorial describes a situation in which you have to add to, or enrich, a message that is not HL7-compliant and/or is incomplete.</span></span> <span data-ttu-id="4090d-105">這可能與應用程式，例如病患的註冊應用程式，或可能會填入來自 Microsoft 的 XML 資料的訊息時[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4090d-105">This can occur with an application, such as a patient registration application, or it can occur when you are populating a message with XML data from Microsoft [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="4090d-106">在本教學課程中，您可以擷取 BTAHL7 的訊息，並提供任何遺漏的資料，例如從病患記錄資料庫。</span><span class="sxs-lookup"><span data-stu-id="4090d-106">In this tutorial, you capture the messages with BTAHL7, and provide any missing data, for example, from a patient records database.</span></span> <span data-ttu-id="4090d-107">然後將訊息轉換，並將它傳送至一個實驗室、 保險或使用 MLLP （最少較低層通訊協定） 配接器任何舊版的特定業務 (LOB) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4090d-107">You then convert the message and send it to a laboratory, insurance, or any legacy line-of-business (LOB) application using the MLLP (Minimal Lower Layer Protocol) adapter.</span></span>  
  
 <span data-ttu-id="4090d-108">在本教學課程中，您可以使用 Web 服務用戶端 (WSClient.exe) 應用程式在此情況下 「 doorbell"註冊病患觸發程序事件，透過 SOAP 配接器傳送的 XML 格式的訊息， [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] BTAHL7 使用。</span><span class="sxs-lookup"><span data-stu-id="4090d-108">In this tutorial, you use a Web service client (WSClient.exe) application to send an XML-formatted message, in this case a "doorbell" Register Patient trigger event, through the SOAP adapter to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] with BTAHL7.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4090d-109"> 接收 SOAP 中的訊息接收埠，而且訊息至協調流程發佈為 Web 服務的路由。</span><span class="sxs-lookup"><span data-stu-id="4090d-109"> receives the message in a SOAP receive port, and routes the message to an orchestration published as a Web service.</span></span> <span data-ttu-id="4090d-110">XML 訊息會包含病患的名稱和身分證號碼。</span><span class="sxs-lookup"><span data-stu-id="4090d-110">The XML message contains a patient name and social security number.</span></span> <span data-ttu-id="4090d-111">您擴大訊息，並將訊息轉換成 HL7 格式使用結構描述、 對應和轉換。</span><span class="sxs-lookup"><span data-stu-id="4090d-111">You augment the message, and use schemas, a map, and a transform to convert the message into HL7 format.</span></span> <span data-ttu-id="4090d-112">然後，您會透過 MLLP 配接器傳送到實驗室環境，保險、 或 LOB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4090d-112">You will then send it through an MLLP adapter to the laboratory, insurance, or LOB application.</span></span>  
  
 <span data-ttu-id="4090d-113">下圖顯示本教學課程的處理流程。</span><span class="sxs-lookup"><span data-stu-id="4090d-113">The following figure shows the process flow of the tutorial.</span></span>  
  
 <span data-ttu-id="4090d-114">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-msgenrichtutarch.gif "hl7_msgenrichtutarch")</span><span class="sxs-lookup"><span data-stu-id="4090d-114">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-msgenrichtutarch.gif "hl7_msgenrichtutarch")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4090d-115">本教學課程需要 Windows Server Standard、 Enterprise、 Datacenter 或 Web Edition 和自訂的 BTAHL7 安裝包含 MLLP 測試工具。</span><span class="sxs-lookup"><span data-stu-id="4090d-115">This tutorial requires Windows Server Standard, Enterprise, Datacenter, or Web Edition, and a custom BTAHL7 installation that includes the MLLP test tools.</span></span> <span data-ttu-id="4090d-116">此外，您應該先熟悉[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]中的程式開發[!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)]中找到的資訊並[深入了解 HL7 加速器以及可用的 BizTalk 工具](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)。</span><span class="sxs-lookup"><span data-stu-id="4090d-116">Additionally, you should be familiar with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] development in [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] and the information found in [learn about the HL7 accelerator and the BizTalk tools available](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md).</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="4090d-117">您可以避免解除部署組件，停止傳送埠的錯誤和停用接收位置，您在先前的教學課程中使用。</span><span class="sxs-lookup"><span data-stu-id="4090d-117">You can avoid errors by undeploying assemblies, stopping send ports, and disabling receive locations that you used in previous tutorials.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4090d-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="4090d-118">In this section</span></span>  
  
-   [<span data-ttu-id="4090d-119">步驟 1：設定應用程式集區識別</span><span class="sxs-lookup"><span data-stu-id="4090d-119">Step 1: Configure Application Pool Identity</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-application-pool-identity.md)  
  
-   [<span data-ttu-id="4090d-120">步驟 2：建立新的專案</span><span class="sxs-lookup"><span data-stu-id="4090d-120">Step 2: Create a New Project</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md)  
  
-   [<span data-ttu-id="4090d-121">步驟 3：指派強式名稱給組件</span><span class="sxs-lookup"><span data-stu-id="4090d-121">Step 3: Assign a Strong Name to the Assembly</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md)  
  
-   [<span data-ttu-id="4090d-122">步驟 4：建立結構描述</span><span class="sxs-lookup"><span data-stu-id="4090d-122">Step 4: Create the Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-schemas.md)  
  
-   [<span data-ttu-id="4090d-123">步驟 5：升級結構描述屬性</span><span class="sxs-lookup"><span data-stu-id="4090d-123">Step 5: Promote Schema Properties</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-5-promote-schema-properties.md)  
  
-   [<span data-ttu-id="4090d-124">步驟 6：驗證結構描述</span><span class="sxs-lookup"><span data-stu-id="4090d-124">Step 6: Validate the Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md)  
  
-   [<span data-ttu-id="4090d-125">步驟 7：簽署和建置專案</span><span class="sxs-lookup"><span data-stu-id="4090d-125">Step 7: Sign and Build the Projects</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-7-sign-and-build-the-projects.md)  
  
-   [<span data-ttu-id="4090d-126">步驟 8：使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="4090d-126">Step 8: Create a Map with BizTalk Mapper</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-8-create-a-map-with-biztalk-mapper.md)  
  
-   [<span data-ttu-id="4090d-127">步驟 9：驗證和建置對應專案</span><span class="sxs-lookup"><span data-stu-id="4090d-127">Step 9: Validate and Build the Map Project</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-9-validate-and-build-the-map-project.md)  
  
-   [<span data-ttu-id="4090d-128">步驟 10：建立協調流程</span><span class="sxs-lookup"><span data-stu-id="4090d-128">Step 10: Create an Orchestration</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-10-create-an-orchestration.md)  
  
-   [<span data-ttu-id="4090d-129">步驟 11：建立協調流程變數</span><span class="sxs-lookup"><span data-stu-id="4090d-129">Step 11: Create Orchestration Variables</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md)  
  
-   [<span data-ttu-id="4090d-130">步驟 12：設定協調流程圖形</span><span class="sxs-lookup"><span data-stu-id="4090d-130">Step 12: Configure Orchestration Shapes</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-12-configure-orchestration-shapes.md)  
  
-   [<span data-ttu-id="4090d-131">步驟 13：建立和設定連接埠</span><span class="sxs-lookup"><span data-stu-id="4090d-131">Step 13: Create and Configure Ports</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-13-create-and-configure-ports.md)  
  
-   [<span data-ttu-id="4090d-132">步驟 14：將協調流程發佈為 Web 服務</span><span class="sxs-lookup"><span data-stu-id="4090d-132">Step 14: Publish the Orchestration as a Web Service</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md)  
  
-   [<span data-ttu-id="4090d-133">步驟 15：部署並設定傳送埠和接收埠</span><span class="sxs-lookup"><span data-stu-id="4090d-133">Step 15: Configure the Send and Receive Ports</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-15-configure-the-send-and-receive-ports.md)  
  
-   [<span data-ttu-id="4090d-134">步驟 16：啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="4090d-134">Step 16: Start the Orchestration</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-16-start-the-orchestration.md)  
  
-   [<span data-ttu-id="4090d-135">步驟 17：建立 WSClient 應用程式</span><span class="sxs-lookup"><span data-stu-id="4090d-135">Step 17: Create the WSClient Application</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-17-create-the-wsclient-application.md)  
  
-   [<span data-ttu-id="4090d-136">步驟 18：測試您的新訊息擴充方案</span><span class="sxs-lookup"><span data-stu-id="4090d-136">Step 18: Test Your New Message Enrichment Solution</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-18-test-your-new-message-enrichment-solution.md)