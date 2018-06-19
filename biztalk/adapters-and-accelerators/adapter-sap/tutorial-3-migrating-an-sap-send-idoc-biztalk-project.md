---
title: 教學課程 3： 移轉 SAP 傳送 IDOC 的 BizTalk 專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migrating, SAP Send IDOC BizTalk project
- migration
ms.assetid: c0a11432-5388-4054-8996-08a957cc02eb
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52f8bc638d1adefe952ce055542706d11e0ca61f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217038"
---
# <a name="tutorial-3-migrating-an-sap-send-idoc-biztalk-project"></a><span data-ttu-id="42145-102">教學課程 3： 移轉 SAP 傳送 IDOC BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="42145-102">Tutorial 3: Migrating an SAP Send IDOC BizTalk Project</span></span>
<span data-ttu-id="42145-103">SAP 配接器隨附於 Microsoft BizTalk Server 的先前版本不同於 WCF 基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在許多方面，包括：</span><span class="sxs-lookup"><span data-stu-id="42145-103">The previous version of the SAP adapter that shipped with Microsoft BizTalk Server differs from the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in many aspects, including:</span></span>  
  
-   <span data-ttu-id="42145-104">建立 BizTalk 專案的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="42145-104">The design-time experience of creating a BizTalk project.</span></span>  
  
-   <span data-ttu-id="42145-105">中繼資料擷取的經驗。</span><span class="sxs-lookup"><span data-stu-id="42145-105">The metadata retrieval experience.</span></span>  
  
-   <span data-ttu-id="42145-106">結構描述檔案名稱和命名空間。</span><span class="sxs-lookup"><span data-stu-id="42145-106">Schema file name and namespace.</span></span>  
  
-   <span data-ttu-id="42145-107">資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="42145-107">Data type mappings.</span></span>  
  
-   <span data-ttu-id="42145-108">可以使用配接器中執行的作業。</span><span class="sxs-lookup"><span data-stu-id="42145-108">The operations that can be performed using the adapter.</span></span>  
  
-   <span data-ttu-id="42145-109">在 BizTalk Server 管理主控台中的實體連接埠設定。</span><span class="sxs-lookup"><span data-stu-id="42145-109">Physical port configuration in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="42145-110">中的主題將說明這些差異所[移轉 BizTalk 專案建立使用上一個版本的 SAP 配接器](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37)。</span><span class="sxs-lookup"><span data-stu-id="42145-110">These differences are explained in the topics within [Migrating BizTalk Projects Created Using the Previous Version of the SAP Adapter](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37).</span></span>  
  
 <span data-ttu-id="42145-111">不過，您可以使用舊版的配接器所建立的 BizTalk 專案中進行變更並讓它運作以 WCF 為基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="42145-111">However, you can make changes to the BizTalk project created using the previous version of the adapter and make it work with the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
 <span data-ttu-id="42145-112">本教學課程提供指示應該對現有的 BizTalk 專案使用舊版的配接器所建立的變更。</span><span class="sxs-lookup"><span data-stu-id="42145-112">This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the previous version of the adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42145-113">在此教學課程中，為了簡短起見，舊版的 SAP 配接器將會稱為 vPrev SAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="42145-113">In this tutorial, for the sake of brevity, the previous version of the SAP adapter will be referred to as vPrev SAP adapter.</span></span> <span data-ttu-id="42145-114">同樣地，使用 vPrev SAP 配接器的 BizTalk 專案將被稱為 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="42145-114">Similarly, a BizTalk project that uses the vPrev SAP adapter will be referred to as vPrev BizTalk project.</span></span>  
  
## <a name="sample-used-for-the-tutorial"></a><span data-ttu-id="42145-115">教學課程使用範例</span><span class="sxs-lookup"><span data-stu-id="42145-115">Sample Used for the Tutorial</span></span>  
 <span data-ttu-id="42145-116">本教學課程根據範例 (SendIDOC_Migration)，示範如何移轉傳送 IDOC 到 SAP 系統的 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="42145-116">This tutorial is based upon a sample (SendIDOC_Migration) that demonstrates how to migrate a vPrev BizTalk project that sends an IDOC to an SAP system.</span></span> <span data-ttu-id="42145-117">此範例隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="42145-117">The sample is provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="42145-118">如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="42145-118">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="42145-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="42145-119">Prerequisites</span></span>  
  
-   <span data-ttu-id="42145-120">您必須 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="42145-120">You must have a vPrev BizTalk project.</span></span> <span data-ttu-id="42145-121">本教學課程包含傳送 BOMDOC IDOC 到 SAP 系統的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="42145-121">This tutorial involves a BizTalk project that sends a BOMDOC IDOC to an SAP system.</span></span>  
  
-   <span data-ttu-id="42145-122">您必須使用 vPrev SAP 配接器之 SAP 系統傳送一般檔案 BOMDOC IDOC。</span><span class="sxs-lookup"><span data-stu-id="42145-122">You must have a flat-file BOMDOC IDOC to send to the SAP system using the vPrev SAP adapter.</span></span> <span data-ttu-id="42145-123">在此教學課程提供的範例包含這個一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="42145-123">The sample provided for this tutorial contains this flat-file IDOC.</span></span>  
  
-   [<span data-ttu-id="42145-124">建立強式名稱金鑰檔，並了解工具</span><span class="sxs-lookup"><span data-stu-id="42145-124">Create strong-name key file, and learn the tools</span></span>](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="42145-125">了解 BizTalk 專案建立使用配接器的先前版本</span><span class="sxs-lookup"><span data-stu-id="42145-125">Understanding a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="42145-126">傳送 IDOC vPrev BizTalk 專案的關鍵要素是：</span><span class="sxs-lookup"><span data-stu-id="42145-126">The key constituents of a vPrev BizTalk project to send an IDOC are:</span></span>  
  
-   <span data-ttu-id="42145-127">**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="42145-127">**BizTalk orchestration**.</span></span> <span data-ttu-id="42145-128">這是簡單的協調流程，從檔案位置挑選一般檔案 IDOC，並將傳送至 SAP 系統，使用 SAP IDOC 的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="42145-128">This is a simple orchestration that picks a flat-file IDOC from a file location and sends the IDOC to the SAP system using an SAP send port.</span></span> <span data-ttu-id="42145-129">BizTalk 專案包含要轉換為 XML，一般檔案 IDOC 一般檔案解譯器，使其可以用於協調流程中。</span><span class="sxs-lookup"><span data-stu-id="42145-129">The BizTalk project contains a flat-file disassembler to convert the flat-file IDOC to an XML, so that it can be used in an orchestration.</span></span> <span data-ttu-id="42145-130">XML IDOC 由 vPrev SAP 傳送埠之前，會將它轉換回使用一般檔案組合器的一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="42145-130">Before the XML IDOC is consumed by the vPrev SAP send port, it is converted back into a flat-file IDOC using a flat-file assembler.</span></span>  
  
-   <span data-ttu-id="42145-131">**您想要傳送至 SAP 系統的 idoc 的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="42145-131">**Schema for the IDOC you want to send to the SAP system**.</span></span> <span data-ttu-id="42145-132">此教學課程中，您需要傳送 BOMDOC01 IDOC 至 SAP 系統的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="42145-132">For this tutorial, you take a BizTalk project that sends BOMDOC01 IDOC to the SAP system.</span></span> <span data-ttu-id="42145-133">產生 idoc 的結構描述是 BOMDOC01.xsd。</span><span class="sxs-lookup"><span data-stu-id="42145-133">The schema generated for the IDOC is BOMDOC01.xsd.</span></span> <span data-ttu-id="42145-134">此結構描述會產生使用 vPrev SAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="42145-134">This schema is generated using the vPrev SAP adapter.</span></span>  
  
-   <span data-ttu-id="42145-135">**一般檔案 IDOC**。</span><span class="sxs-lookup"><span data-stu-id="42145-135">**The flat-file IDOC**.</span></span> <span data-ttu-id="42145-136">這是傳送到 SAP 系統的一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="42145-136">This is the flat-file IDOC that is sent to the SAP system.</span></span>  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="42145-137">使用舊版的配接器如何移轉 BizTalk 專案建立</span><span class="sxs-lookup"><span data-stu-id="42145-137">How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="42145-138">本移轉教學課程的目標是讓您將傳送到 SAP 系統，而不傳送埠使用 Wcf-custom 傳送埠 vPrev SAP 配接器的一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="42145-138">The goal of this migration tutorial is to enable you to send a flat-file IDOC to an SAP system using a WCF-Custom send port instead of the send port for the vPrev SAP adapter.</span></span> <span data-ttu-id="42145-139">之前了解哪些設定所需的 Wcf-custom 傳送埠，您必須先了解哪些實體連接埠所需的 vPrev 傳送 IDOC 的協調流程：</span><span class="sxs-lookup"><span data-stu-id="42145-139">Before understanding what settings are required for the WCF-Custom send port, you must first understand what physical ports are required for the vPrev send IDOC orchestration:</span></span>  
  
-   <span data-ttu-id="42145-140">File 接收挑選一般檔案 IDOC 的連接埠。</span><span class="sxs-lookup"><span data-stu-id="42145-140">A file receive port that picks the flat-file IDOC.</span></span> <span data-ttu-id="42145-141">此連接埠會使用一般檔案解譯器管線中的 BizTalk 應用程式，可用來將一般檔案轉換成符合結構描述 (BOMDOC01.xsd) 使用 vPrev SAP 配接器所產生的 XML。</span><span class="sxs-lookup"><span data-stu-id="42145-141">This port uses the flat-file disassembler pipeline, available in the BizTalk application, to convert the flat-file into an XML that conforms to the schema (BOMDOC01.xsd) generated using the vPrev SAP adapter.</span></span>  
  
-   <span data-ttu-id="42145-142">SAP vPrev 傳送埠傳送一般檔案 IDOC 至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="42145-142">A vPrev SAP send port that sends the flat-file IDOC to the SAP system.</span></span> <span data-ttu-id="42145-143">在傳送之前一般檔案，連接埠會使用一般檔案組合器將 XML IDOC 轉換成一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="42145-143">Before sending the flat-file, the port uses the flat-file assembler to convert the XML IDOC into a flat-file IDOC.</span></span>  
  
 <span data-ttu-id="42145-144">若要移轉現有的 vPrev BizTalk 專案，您不需要變更檔案接收埠挑選一般檔案 IDOC，並將一般檔案 IDOC 轉換為使用一般檔案解譯器的 XML。</span><span class="sxs-lookup"><span data-stu-id="42145-144">To migrate your existing vPrev BizTalk project, you do not need to change the file receive port that picks the flat-file IDOC and converts the flat-file IDOC to XML using a flat-file disassembler.</span></span> <span data-ttu-id="42145-145">您只需要以正確的組態設定來設定新的 WCF 自訂傳送連接埠。</span><span class="sxs-lookup"><span data-stu-id="42145-145">You only need to configure a new WCF-Custom send port with the right configuration settings.</span></span> <span data-ttu-id="42145-146">本教學課程示範如何設定 Wcf-custom 傳送埠傳送 Idoc 至 SAP 系統使用 WCF 型[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="42145-146">This tutorial demonstrates how to configure the WCF-Custom send port to send IDOCs to an SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42145-147">本節內容</span><span class="sxs-lookup"><span data-stu-id="42145-147">In This Section</span></span>  
  
-   [<span data-ttu-id="42145-148">步驟 1： 建立和部署傳送 IDOC vPrev BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="42145-148">Step 1: Build and Deploy the vPrev BizTalk Project for Sending an IDOC</span></span>](../../adapters-and-accelerators/adapter-sap/step-1-build-and-deploy-the-vprev-biztalk-project-for-sending-an-idoc.md)  
  
-   [<span data-ttu-id="42145-149">步驟 2： 設定 Wcf-custom 單向傳送埠</span><span class="sxs-lookup"><span data-stu-id="42145-149">Step 2: Configure a WCF-Custom One-way Send Port</span></span>](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-send-port.md)  
  
-   [<span data-ttu-id="42145-150">步驟 3： 測試已移轉的應用程式</span><span class="sxs-lookup"><span data-stu-id="42145-150">Step 3: Test the Migrated Application</span></span>](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application2.md)  
  
## <a name="see-also"></a><span data-ttu-id="42145-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42145-151">See Also</span></span>  
 [<span data-ttu-id="42145-152">SAP 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="42145-152">SAP Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)