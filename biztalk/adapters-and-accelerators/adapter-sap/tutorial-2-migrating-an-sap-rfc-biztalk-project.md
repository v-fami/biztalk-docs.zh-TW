---
title: 教學課程 2： 移轉 SAP RFC BizTalk 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migrating, BizTalk project from previous version of the SAP adapter
- migration
- migrating, SAP RFC BizTalk project
ms.assetid: b4943613-23d2-4869-b033-ec07daabfac5
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf741fdbbf996fa54c227cc879c850304413d25f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978983"
---
# <a name="tutorial-2-migrating-an-sap-rfc-biztalk-project"></a><span data-ttu-id="2ab04-102">教學課程 2： 移轉 SAP RFC BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="2ab04-102">Tutorial 2: Migrating an SAP RFC BizTalk Project</span></span>
<span data-ttu-id="2ab04-103">不同於以 WCF 為基礎的 SAP 配接器隨附於 Microsoft BizTalk Server 舊版[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在許多方面，包括：</span><span class="sxs-lookup"><span data-stu-id="2ab04-103">The previous version of the SAP adapter that shipped with Microsoft BizTalk Server differs from the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in many aspects, including:</span></span>  
  
- <span data-ttu-id="2ab04-104">建立 BizTalk 專案的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="2ab04-104">The design-time experience of creating a BizTalk project.</span></span>  
  
- <span data-ttu-id="2ab04-105">中繼資料的擷取體驗。</span><span class="sxs-lookup"><span data-stu-id="2ab04-105">The metadata retrieval experience.</span></span>  
  
- <span data-ttu-id="2ab04-106">結構描述檔案名稱和命名空間。</span><span class="sxs-lookup"><span data-stu-id="2ab04-106">Schema file name and namespace.</span></span>  
  
- <span data-ttu-id="2ab04-107">資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="2ab04-107">Data type mappings.</span></span>  
  
- <span data-ttu-id="2ab04-108">可以使用配接器執行的作業。</span><span class="sxs-lookup"><span data-stu-id="2ab04-108">The operations that can be performed using the adapter.</span></span>  
  
- <span data-ttu-id="2ab04-109">在 BizTalk Server 管理主控台中的實體連接埠組態。</span><span class="sxs-lookup"><span data-stu-id="2ab04-109">Physical port configuration in the BizTalk Server Administration console.</span></span>  
  
  <span data-ttu-id="2ab04-110">中的主題會說明這些差異[移轉 BizTalk 專案建立使用上一個版本的 SAP 配接器](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37)。</span><span class="sxs-lookup"><span data-stu-id="2ab04-110">These differences are explained in the topics within [Migrating BizTalk Projects Created Using the Previous Version of the SAP Adapter](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37).</span></span>  
  
  <span data-ttu-id="2ab04-111">不過，您可以對使用舊版的配接器建立 BizTalk 專案中的變更，並讓其使用以 WCF 為基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2ab04-111">However, you can make changes to the BizTalk project created using the previous version of the adapter and make it work with the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
  <span data-ttu-id="2ab04-112">本教學課程會提供指示，您應該對現有的 BizTalk 專案使用舊版的配接器所建立的變更。</span><span class="sxs-lookup"><span data-stu-id="2ab04-112">This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the previous version of the adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ab04-113">在本教學課程中，為了保持簡潔，舊版的 SAP 配接器會稱為 vPrev SAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="2ab04-113">In this tutorial, for the sake of brevity, the previous version of the SAP adapter will be referred to as vPrev SAP adapter.</span></span> <span data-ttu-id="2ab04-114">同樣地，使用 vPrev SAP 配接器的 BizTalk 專案會被稱為 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="2ab04-114">Similarly, a BizTalk project that uses the vPrev SAP adapter will be referred to as vPrev BizTalk project.</span></span>  
  
## <a name="sample-used-for-the-tutorial"></a><span data-ttu-id="2ab04-115">用於本教學課程的範例</span><span class="sxs-lookup"><span data-stu-id="2ab04-115">Sample Used for the Tutorial</span></span>  
 <span data-ttu-id="2ab04-116">本教學課程是以示範如何將 SAP 系統中叫用 RFC vPrev BizTalk 專案的範例 (SAP_RFC_Migration) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="2ab04-116">This tutorial is based upon a sample (SAP_RFC_Migration) that demonstrates how to migrate a vPrev BizTalk project that invokes an RFC in an SAP system.</span></span> <span data-ttu-id="2ab04-117">提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2ab04-117">The sample is provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="2ab04-118">如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="2ab04-118">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2ab04-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="2ab04-119">Prerequisites</span></span>  
  
-   <span data-ttu-id="2ab04-120">您必須具有 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="2ab04-120">You must have a vPrev BizTalk project.</span></span> <span data-ttu-id="2ab04-121">本教學課程包含叫用 SD_RFC_CUSTOMER_GET RFC BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="2ab04-121">This tutorial involves a BizTalk project that invokes the SD_RFC_CUSTOMER_GET RFC.</span></span>  
  
-   <span data-ttu-id="2ab04-122">您必須執行才能叫用使用 vPrev SAP 配接器 SD_RFC_CUSTOMER_GET RFC 的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="2ab04-122">You must have a request message to perform to invoke the SD_RFC_CUSTOMER_GET RFC using the vPrev SAP adapter.</span></span> <span data-ttu-id="2ab04-123">要求訊息必須符合 RFC 使用 vPrev SAP 配接器所產生的結構描述。</span><span class="sxs-lookup"><span data-stu-id="2ab04-123">The request message must conform to the schema of the RFC generated using the vPrev SAP adapter.</span></span> <span data-ttu-id="2ab04-124">本教學課程中所提供的範例包含這個要求訊息。</span><span class="sxs-lookup"><span data-stu-id="2ab04-124">The sample provided for this tutorial contains this request message.</span></span>  
  
-   [<span data-ttu-id="2ab04-125">建立強式名稱金鑰檔案，並了解工具</span><span class="sxs-lookup"><span data-stu-id="2ab04-125">Create strong-name key file, and learn the tools</span></span>](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="2ab04-126">了解 BizTalk 專案使用舊版配接器的建立</span><span class="sxs-lookup"><span data-stu-id="2ab04-126">Understanding a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="2ab04-127">若要叫用 RFC vPrev BizTalk 專案的關鍵要素是：</span><span class="sxs-lookup"><span data-stu-id="2ab04-127">The key constituents of a vPrev BizTalk project to invoke an RFC are:</span></span>  
  
-   <span data-ttu-id="2ab04-128">**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="2ab04-128">**BizTalk orchestration**.</span></span> <span data-ttu-id="2ab04-129">這是簡單的協調流程會挑選要求訊息的檔案位置，要使用 SAP 的 SAP 系統的要求訊息傳送-接收的傳送埠、 接收回應，並將它儲存到另一個檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="2ab04-129">This is a simple orchestration that picks request messages from a file location, sends the request message to the SAP system using an SAP send-receive port, receives the response, and saves it to another file location.</span></span>  
  
-   <span data-ttu-id="2ab04-130">**您想要在 SAP 系統中叫用 RFC 的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="2ab04-130">**Schema for the RFC you want to invoke in the SAP system**.</span></span> <span data-ttu-id="2ab04-131">本教學課程包含叫用 SD_RFC_CUSTOMER_GET RFC BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="2ab04-131">This tutorial involves a BizTalk project that invokes the SD_RFC_CUSTOMER_GET RFC.</span></span> <span data-ttu-id="2ab04-132">Rfc 所產生的結構描述是 SD_RFC_CUSTOMER_GET__x32003.xsd。</span><span class="sxs-lookup"><span data-stu-id="2ab04-132">The schema generated for the RFC is SD_RFC_CUSTOMER_GET__x32003.xsd.</span></span> <span data-ttu-id="2ab04-133">此結構描述是使用 vPrev SAP 配接器所產生的。</span><span class="sxs-lookup"><span data-stu-id="2ab04-133">This schema is generated using the vPrev SAP adapter.</span></span>  
  
-   <span data-ttu-id="2ab04-134">**要求訊息**。</span><span class="sxs-lookup"><span data-stu-id="2ab04-134">**Request message**.</span></span> <span data-ttu-id="2ab04-135">要叫用 SD_RFC_CUSTOMER_GET RFC 的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="2ab04-135">The request message to invoke the SD_RFC_CUSTOMER_GET RFC.</span></span> <span data-ttu-id="2ab04-136">要求訊息的結構描述符合 SD_RFC_CUSTOMER_GET RFC 的結構描述，因為呈現 vPrev SAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="2ab04-136">The schema of the request message conforms to the schema of the SD_RFC_CUSTOMER_GET RFC as surfaced by the vPrev SAP adapter.</span></span>  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="2ab04-137">如何移轉 BizTalk 專案可讓您建立使用舊版的配接器</span><span class="sxs-lookup"><span data-stu-id="2ab04-137">How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="2ab04-138">本移轉教學課程的目標是要讓您傳送要求訊息，這符合 vPrev SAP 配接器使用 WCF 自訂連接埠，只有處理程序符合以 WCF 為基礎的訊息所產生的結構描述[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2ab04-138">The goal of this migration tutorial is to enable you to send a request message, which conforms to schema generated by the vPrev SAP adapter, using a WCF-Custom port that can only process messages conforming to the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="2ab04-139">因此，簡單地說，在移轉作業牽涉到設定不符合 WCF 為基礎的處理訊息的 WCF 自訂連接埠[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]的結構描述。</span><span class="sxs-lookup"><span data-stu-id="2ab04-139">So, in short, the migration exercise involves configuring the WCF-Custom port to process messages that do not conform to the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]'s schema.</span></span>  
  
 <span data-ttu-id="2ab04-140">不過，若要能夠適當地設定 WCF 自訂連接埠，您必須執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="2ab04-140">However, to be able to configure the WCF-Custom port appropriately, you must perform the following tasks:</span></span>  
  
- <span data-ttu-id="2ab04-141">產生中繼資料的使用以 WCF 為基礎的 SD_RFC_CUSTOMER_GET RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2ab04-141">Generate metadata for the SD_RFC_CUSTOMER_GET RFC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
- <span data-ttu-id="2ab04-142">將叫用 RFC 使用 vPrev SAP 配接器的要求訊息來叫用 RFC 使用以 WCF 為基礎的要求訊息對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2ab04-142">Map the request message for invoking the RFC using the vPrev SAP adapter to a request message for invoking the RFC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
- <span data-ttu-id="2ab04-143">將使用以 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]vPrev SAP 配接器的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="2ab04-143">Map the response message received using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to the response message for the vPrev SAP adapter.</span></span>  
  
- <span data-ttu-id="2ab04-144">建立 WCF 自訂 SAP 傳送接收 BizTalk Server 管理主控台中的連接埠。</span><span class="sxs-lookup"><span data-stu-id="2ab04-144">Create a WCF-Custom SAP send-receive port in the BizTalk Server Administration console.</span></span>  
  
- <span data-ttu-id="2ab04-145">設定 WCF 自訂連接埠，若要使用的要求和回應的對應。</span><span class="sxs-lookup"><span data-stu-id="2ab04-145">Configure the WCF-Custom port to use the request and response mappings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ab04-146">本節內容</span><span class="sxs-lookup"><span data-stu-id="2ab04-146">In This Section</span></span>  
  
-   [<span data-ttu-id="2ab04-147">步驟 1：修改 vPrev BizTalk 專案以便叫用 RFC</span><span class="sxs-lookup"><span data-stu-id="2ab04-147">Step 1: Modify the vPrev BizTalk Project for Invoking an RFC</span></span>](../../adapters-and-accelerators/adapter-sap/step-1-modify-the-vprev-biztalk-project-for-invoking-an-rfc.md)  
  
-   [<span data-ttu-id="2ab04-148">步驟 2：在 BizTalk Server 管理主控台設定協調流程</span><span class="sxs-lookup"><span data-stu-id="2ab04-148">Step 2: Configure the Orchestration in BizTalk Server Administration Console</span></span>](../../adapters-and-accelerators/adapter-sap/step-2-configure-the-orchestration-in-biztalk-server-administration-console1.md)  
  
-   [<span data-ttu-id="2ab04-149">步驟 3：測試已移轉的應用程式</span><span class="sxs-lookup"><span data-stu-id="2ab04-149">Step 3: Test the Migrated Application</span></span>](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application6.md)  
  
## <a name="see-also"></a><span data-ttu-id="2ab04-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ab04-150">See Also</span></span>  
 [<span data-ttu-id="2ab04-151">SAP 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="2ab04-151">SAP Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)