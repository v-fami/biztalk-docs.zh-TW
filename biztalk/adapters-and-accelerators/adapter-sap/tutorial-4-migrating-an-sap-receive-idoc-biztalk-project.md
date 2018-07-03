---
title: 教學課程 4： 移轉 SAP 接收 IDOC BizTalk 專案 |Microsoft Docs
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
ms.openlocfilehash: e943c3663767d2b684b0f4657f639d752705b86f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011255"
---
# <a name="tutorial-4-migrating-an-sap-receive-idoc-biztalk-project"></a><span data-ttu-id="0f479-102">教學課程 4： 移轉 SAP 接收 IDOC BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="0f479-102">Tutorial 4: Migrating an SAP Receive IDOC BizTalk Project</span></span>
<span data-ttu-id="0f479-103">不同於以 WCF 為基礎的 SAP 配接器隨附於 Microsoft BizTalk Server 舊版[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在許多方面，包括：</span><span class="sxs-lookup"><span data-stu-id="0f479-103">The previous version of the SAP adapter that shipped with Microsoft BizTalk Server differs from the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in many aspects, including:</span></span>  
  
- <span data-ttu-id="0f479-104">建立 BizTalk 專案的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="0f479-104">The design-time experience of creating a BizTalk project.</span></span>  
  
- <span data-ttu-id="0f479-105">中繼資料的擷取體驗。</span><span class="sxs-lookup"><span data-stu-id="0f479-105">The metadata retrieval experience.</span></span>  
  
- <span data-ttu-id="0f479-106">結構描述檔案名稱和命名空間。</span><span class="sxs-lookup"><span data-stu-id="0f479-106">Schema file name and namespace.</span></span>  
  
- <span data-ttu-id="0f479-107">資料類型對應。</span><span class="sxs-lookup"><span data-stu-id="0f479-107">Data type mappings.</span></span>  
  
- <span data-ttu-id="0f479-108">可以使用配接器執行的作業。</span><span class="sxs-lookup"><span data-stu-id="0f479-108">The operations that can be performed using the adapter.</span></span>  
  
- <span data-ttu-id="0f479-109">在 BizTalk Server 管理主控台中的實體連接埠組態。</span><span class="sxs-lookup"><span data-stu-id="0f479-109">Physical port configuration in the BizTalk Server Administration console.</span></span>  
  
  <span data-ttu-id="0f479-110">中的主題會說明這些差異[移轉 BizTalk 專案建立使用上一個版本的 SAP 配接器](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37)。</span><span class="sxs-lookup"><span data-stu-id="0f479-110">These differences are explained in the topics within [Migrating BizTalk Projects Created Using the Previous Version of the SAP Adapter](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37).</span></span>  
  
  <span data-ttu-id="0f479-111">不過，您可以對使用舊版的配接器建立 BizTalk 專案中的變更，並讓其使用以 WCF 為基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0f479-111">However, you can make changes to the BizTalk project created using the previous version of the adapter and make it work with the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
  <span data-ttu-id="0f479-112">本教學課程會提供指示，您應該對現有的 BizTalk 專案使用舊版的配接器所建立的變更。</span><span class="sxs-lookup"><span data-stu-id="0f479-112">This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the previous version of the adapter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f479-113">在本教學課程中，為了保持簡潔，舊版的 SAP 配接器會稱為 vPrev SAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="0f479-113">In this tutorial, for the sake of brevity, the previous version of the SAP adapter will be referred to as vPrev SAP adapter.</span></span> <span data-ttu-id="0f479-114">同樣地，使用 vPrev SAP 配接器的 BizTalk 專案會被稱為 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="0f479-114">Similarly, a BizTalk project that uses the vPrev SAP adapter will be referred to as vPrev BizTalk project.</span></span>  
  
## <a name="sample-used-for-the-tutorial"></a><span data-ttu-id="0f479-115">用於本教學課程的範例</span><span class="sxs-lookup"><span data-stu-id="0f479-115">Sample Used for the Tutorial</span></span>  
 <span data-ttu-id="0f479-116">本教學課程是以示範如何將 SAP 系統從接收一般檔案 IDOC vPrev BizTalk 專案的範例 (ReceiveIDOC_Migration) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="0f479-116">This tutorial is based upon a sample (ReceiveIDOC_Migration) that demonstrates how to migrate a vPrev BizTalk project that receives a flat-file IDOC from an SAP system.</span></span> <span data-ttu-id="0f479-117">提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0f479-117">The sample is provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="0f479-118">如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0f479-118">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0f479-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="0f479-119">Prerequisites</span></span>  
  
-   <span data-ttu-id="0f479-120">您必須具有 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="0f479-120">You must have a vPrev BizTalk project.</span></span> <span data-ttu-id="0f479-121">本教學課程中牽涉到從 SAP 系統接收 ORDERS03 IDOC BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="0f479-121">This tutorial involves a BizTalk project that receives an ORDERS03 IDOC from an SAP system.</span></span>  
  
-   [<span data-ttu-id="0f479-122">建立強式名稱金鑰檔案，並了解工具</span><span class="sxs-lookup"><span data-stu-id="0f479-122">Create strong-name key file, and learn the tools</span></span>](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)

  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="0f479-123">了解 BizTalk 專案使用舊版配接器的建立</span><span class="sxs-lookup"><span data-stu-id="0f479-123">Understanding a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="0f479-124">接收 IDOC vPrev BizTalk 專案的關鍵要素是：</span><span class="sxs-lookup"><span data-stu-id="0f479-124">The key constituents of a vPrev BizTalk project to receive an IDOC are:</span></span>  
  
-   <span data-ttu-id="0f479-125">**BizTalk 協調流程**。</span><span class="sxs-lookup"><span data-stu-id="0f479-125">**BizTalk orchestration**.</span></span> <span data-ttu-id="0f479-126">這是一項簡單的 SAP 所組成的協調流程接收埠從 SAP 系統接收一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="0f479-126">This is a simple orchestration that consists of an SAP receive port that receives a flat-file IDOC from an SAP system.</span></span> <span data-ttu-id="0f479-127">BizTalk 專案包含要轉換成 XML 的 一般檔案 IDOC 一般檔案解譯器，以便用於協調流程。</span><span class="sxs-lookup"><span data-stu-id="0f479-127">The BizTalk project contains a flat-file disassembler to convert the flat-file IDOC to an XML, so that it can be used in an orchestration.</span></span> <span data-ttu-id="0f479-128">XML IDOC 會複製到檔案位置透過 file 連接埠之前，它會轉換回使用一般檔案組合器的一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="0f479-128">Before the XML IDOC is copied to a file location through a file port, it is converted back into a flat-file IDOC using a flat-file assembler.</span></span>  
  
-   <span data-ttu-id="0f479-129">**您想要傳送至 SAP 系統的 IDOC 的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="0f479-129">**Schema for the IDOC you want to send to the SAP system**.</span></span> <span data-ttu-id="0f479-130">本教學課程中，牽涉到從 SAP 系統接收 ORDERS03 IDOC BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="0f479-130">This tutorial involves a BizTalk project that receives ORDERS03 IDOC from the SAP system.</span></span> <span data-ttu-id="0f479-131">產生的 IDOC 的結構描述是 ORDERS03.xsd。</span><span class="sxs-lookup"><span data-stu-id="0f479-131">The schema generated for the IDOC is ORDERS03.xsd.</span></span> <span data-ttu-id="0f479-132">此結構描述是使用 vPrev SAP 配接器所產生的。</span><span class="sxs-lookup"><span data-stu-id="0f479-132">This schema is generated using the vPrev SAP adapter.</span></span>  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a><span data-ttu-id="0f479-133">如何移轉 BizTalk 專案可讓您建立使用舊版的配接器</span><span class="sxs-lookup"><span data-stu-id="0f479-133">How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter</span></span>  
 <span data-ttu-id="0f479-134">本移轉教學課程的目標是要讓您從 SAP 系統，而不傳送埠使用 Wcf-custom 傳送埠，vPrev SAP 配接器的接收一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="0f479-134">The goal of this migration tutorial is to enable you to receive a flat-file IDOC from an SAP system using a WCF-Custom send port instead of the send port for the vPrev SAP adapter.</span></span> <span data-ttu-id="0f479-135">之前了解哪些設定所需的 Wcf-custom 傳送埠，您必須先了解哪些實體連接埠所需的 vPrev 傳送 IDOC 的協調流程。</span><span class="sxs-lookup"><span data-stu-id="0f479-135">Before understanding what settings are required for the WCF-Custom send port, you must first understand what physical ports are required for the vPrev send IDOC orchestration.</span></span>  
  
- <span data-ttu-id="0f479-136">VPrev SAP 接收從 SAP 系統接收一般檔案 IDOC 的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0f479-136">A vPrev SAP receive port that receives a flat-file IDOC from an SAP system.</span></span> <span data-ttu-id="0f479-137">連接埠也會將此轉換使用一般檔案解譯器，也就是 可用 XML IDOC vPrev BizTalk 應用程式的一部分。</span><span class="sxs-lookup"><span data-stu-id="0f479-137">The port also converts this to an XML IDOC using a flat-file disassembler, which is available as part of the vPrev BizTalk application.</span></span> <span data-ttu-id="0f479-138">XML IDOC 符合結構描述 (ORDERS03.xsd)，您就會產生使用 vPrev SAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="0f479-138">The XML IDOC conforms to the schema (ORDERS03.xsd) that you generated using the vPrev SAP adapter.</span></span>  
  
- <span data-ttu-id="0f479-139">它將會複製到資料夾的 IDOC 的 file 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="0f479-139">A file send port which copies the IDOC to folder.</span></span> <span data-ttu-id="0f479-140">此連接埠也會使用一般檔案組合器的 BizTalk 應用程式中，您可以使用管線將 XML IDOC 轉換成一般檔案 IDOC。</span><span class="sxs-lookup"><span data-stu-id="0f479-140">This port also uses the flat-file assembler pipeline, available in the BizTalk application, to convert the XML IDOC to a flat-file IDOC.</span></span>  
  
  <span data-ttu-id="0f479-141">若要移轉您現有的 vPrev BizTalk 專案，您不需要變更檔案傳送埠，以將一般檔案 IDOC 複製到資料夾。</span><span class="sxs-lookup"><span data-stu-id="0f479-141">To migrate your existing vPrev BizTalk project, you do not need to change the file send port that copies the flat-file IDOC to a folder.</span></span> <span data-ttu-id="0f479-142">您只需要設定新 WCF 自訂接收連接埠，以正確的組態設定。</span><span class="sxs-lookup"><span data-stu-id="0f479-142">You only need to configure a new WCF-Custom receive port with the right configuration settings.</span></span> <span data-ttu-id="0f479-143">本教學課程示範如何設定 Wcf-custom 接收埠以使用以 WCF 為基礎的 SAP 系統接收 Idoc [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0f479-143">This tutorial demonstrates how to configure the WCF-Custom receive port to receive IDOCs from an SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f479-144">本節內容</span><span class="sxs-lookup"><span data-stu-id="0f479-144">In This Section</span></span>  
  
-   [<span data-ttu-id="0f479-145">步驟 1：建置並部署 vPrev BizTalk 專案以便接收 IDOC</span><span class="sxs-lookup"><span data-stu-id="0f479-145">Step 1: Build and Deploy the vPrev BizTalk Project for Receiving an IDOC</span></span>](../../adapters-and-accelerators/adapter-sap/step-1-build-and-deploy-the-vprev-biztalk-project-for-receiving-an-idoc.md)  
  
-   [<span data-ttu-id="0f479-146">步驟 2：設定 Wcf-Custom 單向接收埠</span><span class="sxs-lookup"><span data-stu-id="0f479-146">Step 2: Configure a WCF-Custom One-way Receive Port</span></span>](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-receive-port.md)  
  
-   [<span data-ttu-id="0f479-147">步驟 3：測試已移轉的應用程式</span><span class="sxs-lookup"><span data-stu-id="0f479-147">Step 3: Test the Migrated Application</span></span>](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application5.md)  
  
## <a name="see-also"></a><span data-ttu-id="0f479-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f479-148">See Also</span></span>  
 [<span data-ttu-id="0f479-149">SAP 配接器教學課程</span><span class="sxs-lookup"><span data-stu-id="0f479-149">SAP Adapter Tutorials</span></span>](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)