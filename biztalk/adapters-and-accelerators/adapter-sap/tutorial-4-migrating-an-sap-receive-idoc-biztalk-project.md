---
title: 教學課程 4： 移轉 SAP 接收 IDOC 的 BizTalk 專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migration, SAP Receive IDOC BizTalk project
- migrating, SAP Receive IDOC BizTalk project
- migration
ms.assetid: 74b667d8-2d8c-4c15-9dd2-f13521404b85
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 943c80e84bc192330fd870a45c0b5fb60761a33d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217886"
---
# <a name="tutorial-4-migrating-an-sap-receive-idoc-biztalk-project"></a><span data-ttu-id="f44fa-102">教學課程 4： 移轉 SAP 接收 IDOC 的 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="f44fa-102">Tutorial 4: Migrating an SAP Receive IDOC BizTalk Project</span></span>
<span data-ttu-id="f44fa-103">SAP 配接器隨附於 Microsoft BizTalk Server 的先前版本不同於 WCF 基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在許多方面，包括：</span><span class="sxs-lookup"><span data-stu-id="f44fa-103">The previous version of the SAP adapter that shipped with Microsoft BizTalk Server differs from the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in many aspects, including:</span></span>  
  
-   <span data-ttu-id="f44fa-104">建立 BizTalk 專案的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="f44fa-104">The design-time experience of creating a BizTalk project.</span></span>  
  
-   <span data-ttu-id="f44fa-105">中繼資料擷取的經驗。</span><span class="sxs-lookup"><span data-stu-id="f44fa-105">The metadata retrieval experience.</span></span>  
  
-   <span data-ttu-id="f44fa-106">結構描述檔案名稱和命名空間。</span><span class="sxs-lookup"><span data-stu-id="f44fa-106">Schema file name and namespace.</span></span>  
  
-   <span data-ttu-id="f44fa-107">資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="f44fa-107">Data type mappings.</span></span>  
  
-   <span data-ttu-id="f44fa-108">可以使用配接器中執行的作業。</span><span class="sxs-lookup"><span data-stu-id="f44fa-108">The operations that can be performed using the adapter.</span></span>  
  
-   <span data-ttu-id="f44fa-109">在 BizTalk Server 管理主控台中的實體連接埠設定。</span><span class="sxs-lookup"><span data-stu-id="f44fa-109">Physical port configuration in the BizTalk Server Administration console.</span></span>  
  
 <span data-ttu-id="f44fa-110">中的主題將說明這些差異所[移轉 BizTalk 專案建立使用上一個版本的 SAP 配接器](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37)。</span><span class="sxs-lookup"><span data-stu-id="f44fa-110">These differences are explained in the topics within [Migrating BizTalk Projects Created Using the Previous Version of the SAP Adapter](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37).</span></span>  
  
 <span data-ttu-id="f44fa-111">不過，您可以使用舊版的配接器所建立的 BizTalk 專案中進行變更並讓它運作以 WCF 為基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f44fa-111">However, you can make changes to the BizTalk project created using the previous version of the adapter and make it work with the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
 <span data-ttu-id="f44fa-112">本教學課程提供指示應該對現有的 BizTalk 專案使用舊版的配接器所建立的變更。</span><span class="sxs-lookup"><span data-stu-id="f44fa-112">This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the previous version of the adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f44fa-113">在此教學課程中，為了簡短起見，舊版的 SAP 配接器將會稱為 vPrev SAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="f44fa-113">In this tutorial, for the sake of brevity, the previous version of the SAP adapter will be referred to as vPrev SAP adapter.</span></span> <span data-ttu-id="f44fa-114">同樣地，使用 vPrev SAP 配接器的 BizTalk 專案將被稱為 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="f44fa-114">Similarly, a BizTalk project that uses the vPrev SAP adapter will be referred to as vPrev BizTalk project.</span></span>  
  
## <a name="sample-used-for-the-tutorial"></a><span data-ttu-id="f44fa-115">教學課程使用範例</span><span class="sxs-lookup"><span data-stu-id="f44fa-115">Sample Used for the Tutorial</span></span>  
 <span data-ttu-id="f44fa-116">本教學課程根據範例 (ReceiveIDOC_Migration)，示範如何移轉從 SAP 系統接收一般檔案 IDOC 的 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="f44fa-116">This tutorial is based upon a sample (ReceiveIDOC_Migration) that demonstrates how to migrate a vPrev BizTalk project that receives a flat-file IDOC from an SAP system.</span></span> <span data-ttu-id="f44fa-117">此範例隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f44fa-117">The sample is provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="f44fa-118">如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="f44fa-118">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f44fa-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="f44fa-119">Prerequisites</span></span>  
  
-   <span data-ttu-id="f44fa-120">您必須 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="f44fa-120">You must have a vPrev BizTalk project.</span></span> <span data-ttu-id="f44fa-121">本教學課程牽涉到從 SAP 系統接收 ORDERS03 IDOC 的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="f44fa-121">This tutorial involves a BizTalk project that receives an ORDERS03 IDOC from an SAP system.</span></span>  
  
-   [<span data-ttu-id="f44fa-122">建立強式名稱金鑰檔，並了解工具</span><span class="sxs-lookup"><span data-stu-id="f44fa-122">Create strong-name key file, and learn the tools</span></span>](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)

  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="f44fa-123">了解 BizTalk 專案建立使用配接器的先前版本</span><span class="sxs-lookup"><span data-stu-id="f44fa-123">Understanding a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="f44fa-124">接收 IDOC vPrev BizTalk 專案的關鍵要素是：</span><span class="sxs-lookup"><span data-stu-id="f44fa-124">The key constituents of a vPrev BizTalk project to receive an IDOC are:</span></span>  
  
-   <span data-ttu-id="f44fa-125">**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="f44fa-125">**BizTalk orchestration**.</span></span> <span data-ttu-id="f44fa-126">這是簡單的 SAP 所組成的協調流程接收埠從 SAP 系統接收一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="f44fa-126">This is a simple orchestration that consists of an SAP receive port that receives a flat-file IDOC from an SAP system.</span></span> <span data-ttu-id="f44fa-127">BizTalk 專案包含要轉換為 XML，一般檔案 IDOC 一般檔案解譯器，使其可以用於協調流程中。</span><span class="sxs-lookup"><span data-stu-id="f44fa-127">The BizTalk project contains a flat-file disassembler to convert the flat-file IDOC to an XML, so that it can be used in an orchestration.</span></span> <span data-ttu-id="f44fa-128">XML IDOC 複製到檔案位置的檔案連接埠之前，會將它轉換回使用一般檔案組合器的一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="f44fa-128">Before the XML IDOC is copied to a file location through a file port, it is converted back into a flat-file IDOC using a flat-file assembler.</span></span>  
  
-   <span data-ttu-id="f44fa-129">**您想要傳送至 SAP 系統的 idoc 的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="f44fa-129">**Schema for the IDOC you want to send to the SAP system**.</span></span> <span data-ttu-id="f44fa-130">本教學課程牽涉到從 SAP 系統接收 IDOC ORDERS03 的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="f44fa-130">This tutorial involves a BizTalk project that receives ORDERS03 IDOC from the SAP system.</span></span> <span data-ttu-id="f44fa-131">產生 idoc 的結構描述是 ORDERS03.xsd。</span><span class="sxs-lookup"><span data-stu-id="f44fa-131">The schema generated for the IDOC is ORDERS03.xsd.</span></span> <span data-ttu-id="f44fa-132">此結構描述會產生使用 vPrev SAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="f44fa-132">This schema is generated using the vPrev SAP adapter.</span></span>  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="f44fa-133">使用舊版的配接器如何移轉 BizTalk 專案建立</span><span class="sxs-lookup"><span data-stu-id="f44fa-133">How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="f44fa-134">本移轉教學課程的目標是要讓您從 SAP 系統，而不傳送埠使用 Wcf-custom 傳送埠 vPrev SAP 配接器的接收一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="f44fa-134">The goal of this migration tutorial is to enable you to receive a flat-file IDOC from an SAP system using a WCF-Custom send port instead of the send port for the vPrev SAP adapter.</span></span> <span data-ttu-id="f44fa-135">之前了解哪些設定所需的 Wcf-custom 傳送埠，您必須先了解哪些實體連接埠所需的 vPrev 傳送 IDOC 的協調流程。</span><span class="sxs-lookup"><span data-stu-id="f44fa-135">Before understanding what settings are required for the WCF-Custom send port, you must first understand what physical ports are required for the vPrev send IDOC orchestration.</span></span>  
  
-   <span data-ttu-id="f44fa-136">VPrev SAP 接收埠從 SAP 系統接收一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="f44fa-136">A vPrev SAP receive port that receives a flat-file IDOC from an SAP system.</span></span> <span data-ttu-id="f44fa-137">連接埠也會將此轉換使用一般檔案解譯器，也就是使用 XML IDOC vPrev BizTalk 應用程式的一部分。</span><span class="sxs-lookup"><span data-stu-id="f44fa-137">The port also converts this to an XML IDOC using a flat-file disassembler, which is available as part of the vPrev BizTalk application.</span></span> <span data-ttu-id="f44fa-138">XML IDOC 符合您使用 vPrev SAP 配接器產生的結構描述 (ORDERS03.xsd)。</span><span class="sxs-lookup"><span data-stu-id="f44fa-138">The XML IDOC conforms to the schema (ORDERS03.xsd) that you generated using the vPrev SAP adapter.</span></span>  
  
-   <span data-ttu-id="f44fa-139">File 傳送埠可將 IDOC 複製到資料夾。</span><span class="sxs-lookup"><span data-stu-id="f44fa-139">A file send port which copies the IDOC to folder.</span></span> <span data-ttu-id="f44fa-140">此連接埠也會使用一般檔案組合器的 BizTalk 應用程式中，您可以使用管線將 XML IDOC 轉換成一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="f44fa-140">This port also uses the flat-file assembler pipeline, available in the BizTalk application, to convert the XML IDOC to a flat-file IDOC.</span></span>  
  
 <span data-ttu-id="f44fa-141">若要移轉現有的 vPrev BizTalk 專案，您不需要變更複製到資料夾的一般檔案 IDOC 的 file 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f44fa-141">To migrate your existing vPrev BizTalk project, you do not need to change the file send port that copies the flat-file IDOC to a folder.</span></span> <span data-ttu-id="f44fa-142">您只需要設定新的 WCF 自訂接收埠，以正確的組態設定。</span><span class="sxs-lookup"><span data-stu-id="f44fa-142">You only need to configure a new WCF-Custom receive port with the right configuration settings.</span></span> <span data-ttu-id="f44fa-143">本教學課程示範如何設定 Wcf-custom 接收埠，從使用 WCF 為基礎的 SAP 系統接收 Idoc [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f44fa-143">This tutorial demonstrates how to configure the WCF-Custom receive port to receive IDOCs from an SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f44fa-144">本節內容</span><span class="sxs-lookup"><span data-stu-id="f44fa-144">In This Section</span></span>  
  
-   [<span data-ttu-id="f44fa-145">步驟 1： 建立和部署接收 IDOC vPrev BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="f44fa-145">Step 1: Build and Deploy the vPrev BizTalk Project for Receiving an IDOC</span></span>](../../adapters-and-accelerators/adapter-sap/step-1-build-and-deploy-the-vprev-biztalk-project-for-receiving-an-idoc.md)  
  
-   [<span data-ttu-id="f44fa-146">步驟 2： 設定 Wcf-custom 單向接收埠</span><span class="sxs-lookup"><span data-stu-id="f44fa-146">Step 2: Configure a WCF-Custom One-way Receive Port</span></span>](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-receive-port.md)  
  
-   [<span data-ttu-id="f44fa-147">步驟 3： 測試已移轉的應用程式</span><span class="sxs-lookup"><span data-stu-id="f44fa-147">Step 3: Test the Migrated Application</span></span>](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application5.md)  
  
## <a name="see-also"></a><span data-ttu-id="f44fa-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f44fa-148">See Also</span></span>  
 [<span data-ttu-id="f44fa-149">SAP 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="f44fa-149">SAP Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)