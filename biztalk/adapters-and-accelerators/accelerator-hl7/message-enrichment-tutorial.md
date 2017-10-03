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
# <a name="message-enrichment-tutorial"></a><span data-ttu-id="4acd7-102">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="4acd7-102">Message Enrichment Tutorial</span></span>
<span data-ttu-id="4acd7-103">本教學課程提供逐步程序使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]來解決特定商務問題： 訊息豐富 」 問題。</span><span class="sxs-lookup"><span data-stu-id="4acd7-103">This tutorial provides step-by-step procedures for using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to solve a particular business problem: the message enrichment problem.</span></span> <span data-ttu-id="4acd7-104">「 訊息豐富 」 教學課程描述的情況下，您不必加入或擴充、 不是 HL7 相容及/或不完整的訊息。</span><span class="sxs-lookup"><span data-stu-id="4acd7-104">The message enrichment tutorial describes a situation in which you have to add to, or enrich, a message that is not HL7-compliant and/or is incomplete.</span></span> <span data-ttu-id="4acd7-105">這可能是與應用程式，例如病患註冊應用程式，或會填入來自 XML 資料的訊息時，它會發生[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4acd7-105">This can occur with an application, such as a patient registration application, or it can occur when you are populating a message with XML data from [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="4acd7-106">在本教學課程中，您可以擷取 BTAHL7 的訊息，並提供任何遺失的資料，例如，從病患記錄資料庫。</span><span class="sxs-lookup"><span data-stu-id="4acd7-106">In this tutorial, you capture the messages with BTAHL7, and provide any missing data, for example, from a patient records database.</span></span> <span data-ttu-id="4acd7-107">然後將訊息轉換，並將它傳送至實驗室、 保險或使用 MLLP （最少較低層通訊協定） 配接器任何舊版的特定業務 (LOB) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4acd7-107">You then convert the message and send it to a laboratory, insurance, or any legacy line-of-business (LOB) application using the MLLP (Minimal Lower Layer Protocol) adapter.</span></span>  
  
 <span data-ttu-id="4acd7-108">在本教學課程中，您可以使用 Web 服務用戶端 (WSClient.exe) 應用程式在此情況下"doorbell"註冊病患觸發程序事件，透過 SOAP 配接器傳送的 XML 格式的訊息， [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] BTAHL7 與。</span><span class="sxs-lookup"><span data-stu-id="4acd7-108">In this tutorial, you use a Web service client (WSClient.exe) application to send an XML-formatted message, in this case a "doorbell" Register Patient trigger event, through the SOAP adapter to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] with BTAHL7.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4acd7-109">在 SOAP 接收的訊息接收埠，而且訊息至協調流程發佈為 Web 服務的路由。</span><span class="sxs-lookup"><span data-stu-id="4acd7-109"> receives the message in a SOAP receive port, and routes the message to an orchestration published as a Web service.</span></span> <span data-ttu-id="4acd7-110">XML 訊息包含的病患的名稱和身分證號碼。</span><span class="sxs-lookup"><span data-stu-id="4acd7-110">The XML message contains a patient name and social security number.</span></span> <span data-ttu-id="4acd7-111">您擴充訊息，並將訊息轉換為 HL7 格式使用結構描述、 對應和轉換。</span><span class="sxs-lookup"><span data-stu-id="4acd7-111">You augment the message, and use schemas, a map, and a transform to convert the message into HL7 format.</span></span> <span data-ttu-id="4acd7-112">然後，您將會透過 MLLP 配接器傳送到實驗室，保險，或 LOB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4acd7-112">You will then send it through an MLLP adapter to the laboratory, insurance, or LOB application.</span></span>  
  
 <span data-ttu-id="4acd7-113">下圖顯示程序流程的教學課程。</span><span class="sxs-lookup"><span data-stu-id="4acd7-113">The following figure shows the process flow of the tutorial.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-msgenrichtutarch.gif "hl7_msgenrichtutarch")  
  
> [!NOTE]
>  <span data-ttu-id="4acd7-114">本教學課程需要 Windows Server Standard、 Enterprise、 Datacenter 或 Web Edition 和自訂的 BTAHL7 安裝包含 MLLP 測試工具。</span><span class="sxs-lookup"><span data-stu-id="4acd7-114">This tutorial requires Windows Server Standard, Enterprise, Datacenter, or Web Edition, and a custom BTAHL7 installation that includes the MLLP test tools.</span></span> <span data-ttu-id="4acd7-115">此外，您應該熟悉[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]中的開發[!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)]中找到的資訊和[深入了解 HL7 加速器以及可用的 BizTalk 工具](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)。</span><span class="sxs-lookup"><span data-stu-id="4acd7-115">Additionally, you should be familiar with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] development in [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] and the information found in [learn about the HL7 accelerator and the BizTalk tools available](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4acd7-116">您可以避免錯誤解除部署組件，停止傳送埠和停用接收位置，您在先前的教學課程中使用。</span><span class="sxs-lookup"><span data-stu-id="4acd7-116">You can avoid errors by undeploying assemblies, stopping send ports, and disabling receive locations that you used in previous tutorials.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4acd7-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="4acd7-117">In this section</span></span>  
  
-   [<span data-ttu-id="4acd7-118">步驟 1： 設定應用程式集區識別</span><span class="sxs-lookup"><span data-stu-id="4acd7-118">Step 1: Configure Application Pool Identity</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-application-pool-identity.md)  
  
-   [<span data-ttu-id="4acd7-119">步驟 2： 建立新的專案</span><span class="sxs-lookup"><span data-stu-id="4acd7-119">Step 2: Create a New Project</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md)  
  
-   [<span data-ttu-id="4acd7-120">步驟 3： 指派強式名稱組件</span><span class="sxs-lookup"><span data-stu-id="4acd7-120">Step 3: Assign a Strong Name to the Assembly</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md)  
  
-   [<span data-ttu-id="4acd7-121">步驟 4： 建立結構描述</span><span class="sxs-lookup"><span data-stu-id="4acd7-121">Step 4: Create the Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-schemas.md)  
  
-   [<span data-ttu-id="4acd7-122">步驟 5： 升級結構描述屬性</span><span class="sxs-lookup"><span data-stu-id="4acd7-122">Step 5: Promote Schema Properties</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-5-promote-schema-properties.md)  
  
-   [<span data-ttu-id="4acd7-123">步驟 6： 驗證結構描述</span><span class="sxs-lookup"><span data-stu-id="4acd7-123">Step 6: Validate the Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md)  
  
-   [<span data-ttu-id="4acd7-124">步驟 7： 簽署和建置的專案</span><span class="sxs-lookup"><span data-stu-id="4acd7-124">Step 7: Sign and Build the Projects</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-7-sign-and-build-the-projects.md)  
  
-   [<span data-ttu-id="4acd7-125">步驟 8： 使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="4acd7-125">Step 8: Create a Map with BizTalk Mapper</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-8-create-a-map-with-biztalk-mapper.md)  
  
-   [<span data-ttu-id="4acd7-126">步驟 9： 驗證和建置對應專案</span><span class="sxs-lookup"><span data-stu-id="4acd7-126">Step 9: Validate and Build the Map Project</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-9-validate-and-build-the-map-project.md)  
  
-   [<span data-ttu-id="4acd7-127">步驟 10： 建立協調流程</span><span class="sxs-lookup"><span data-stu-id="4acd7-127">Step 10: Create an Orchestration</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-10-create-an-orchestration.md)  
  
-   [<span data-ttu-id="4acd7-128">步驟 11： 建立協調流程變數</span><span class="sxs-lookup"><span data-stu-id="4acd7-128">Step 11: Create Orchestration Variables</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md)  
  
-   [<span data-ttu-id="4acd7-129">步驟 12： 設定協調流程圖形</span><span class="sxs-lookup"><span data-stu-id="4acd7-129">Step 12: Configure Orchestration Shapes</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-12-configure-orchestration-shapes.md)  
  
-   [<span data-ttu-id="4acd7-130">步驟 13： 建立和設定連接埠</span><span class="sxs-lookup"><span data-stu-id="4acd7-130">Step 13: Create and Configure Ports</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-13-create-and-configure-ports.md)  
  
-   [<span data-ttu-id="4acd7-131">步驟 14： 發佈為 Web 服務的協調流程</span><span class="sxs-lookup"><span data-stu-id="4acd7-131">Step 14: Publish the Orchestration as a Web Service</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-14-publish-the-orchestration-as-a-web-service.md)  
  
-   [<span data-ttu-id="4acd7-132">步驟 15： 設定傳送埠和接收埠</span><span class="sxs-lookup"><span data-stu-id="4acd7-132">Step 15: Configure the Send and Receive Ports</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-15-configure-the-send-and-receive-ports.md)  
  
-   [<span data-ttu-id="4acd7-133">步驟 16： 啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="4acd7-133">Step 16: Start the Orchestration</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-16-start-the-orchestration.md)  
  
-   [<span data-ttu-id="4acd7-134">步驟 17： 建立 WSClient 應用程式</span><span class="sxs-lookup"><span data-stu-id="4acd7-134">Step 17: Create the WSClient Application</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-17-create-the-wsclient-application.md)  
  
-   [<span data-ttu-id="4acd7-135">步驟 18： 測試您的新訊息擴充方案</span><span class="sxs-lookup"><span data-stu-id="4acd7-135">Step 18: Test Your New Message Enrichment Solution</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-18-test-your-new-message-enrichment-solution.md)