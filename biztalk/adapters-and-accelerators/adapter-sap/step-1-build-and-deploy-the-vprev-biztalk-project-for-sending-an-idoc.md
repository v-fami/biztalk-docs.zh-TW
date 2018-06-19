---
title: 步驟 1： 建置並部署 BizTalk 專案 vPrev 傳送 IDOC |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migration, building and deploying previous version of BizTalk project for sending an IDOC
- migration
ms.assetid: 1982b318-45d1-464e-b7e4-65d459c439e3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b9089e90fc3a429d6d594a18b0e1fb6e94d4f72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216886"
---
# <a name="step-1-build-and-deploy-the-vprev-biztalk-project-for-sending-an-idoc"></a><span data-ttu-id="e1d7d-102">步驟 1： 建立和部署傳送 IDOC vPrev BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="e1d7d-102">Step 1: Build and Deploy the vPrev BizTalk Project for Sending an IDOC</span></span>
<span data-ttu-id="e1d7d-103">![步驟 3 之 1](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span><span class="sxs-lookup"><span data-stu-id="e1d7d-103">![Step 1 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span></span>  
  
 <span data-ttu-id="e1d7d-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="e1d7d-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="e1d7d-105">**目標：** 在此步驟中，您要建置和部署現有的 vPrev BizTalk 專案，以傳送 IDOC 至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-105">**Objective:** In this step, you build and deploy your existing vPrev BizTalk project to send an IDOC to an SAP system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1d7d-106">您不需要進行任何變更 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-106">You do not need to make any change to the vPrev BizTalk project.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e1d7d-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="e1d7d-107">Prerequisites</span></span>  
 <span data-ttu-id="e1d7d-108">您必須傳送 BOMDOC IDOC 到 SAP 系統 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-108">You must have a vPrev BizTalk project to send a BOMDOC IDOC to an SAP system.</span></span>  
  
### <a name="to-build-and-deploy-the-vprev-biztalk-project"></a><span data-ttu-id="e1d7d-109">若要建置和部署 vPrev BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="e1d7d-109">To build and deploy the vPrev BizTalk project</span></span>  
  
1.  <span data-ttu-id="e1d7d-110">建立強式名稱金鑰檔案，才能建立及部署方案。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-110">Create a strong-name key file required to build and deploy the solution.</span></span> <span data-ttu-id="e1d7d-111">若要建立強式名稱金鑰檔，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e1d7d-111">To create a strong-name key file, do the following:</span></span>  
  
    1.  <span data-ttu-id="e1d7d-112">啟動 Visual Studio 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-112">Start Visual Studio Command Prompt.</span></span>  
  
    2.  <span data-ttu-id="e1d7d-113">在命令提示字元中瀏覽至您要建立金鑰檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-113">At the command prompt navigate to the folder where you want to create the key file.</span></span> <span data-ttu-id="e1d7d-114">例如，輸入**cd C:\Sample**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-114">For example, type **cd C:\Sample**, and then press ENTER.</span></span>  
  
    3.  <span data-ttu-id="e1d7d-115">在命令提示字元中，輸入**sn-k\<金鑰檔名稱 >.snk**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-115">At the command prompt, type **sn -k \<key file name>.snk**, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="e1d7d-116">以滑鼠右鍵按一下方案總管 中的 BizTalk 方案名稱，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-116">Right-click the BizTalk solution name in Solution Explorer, and then click **Properties**.</span></span> <span data-ttu-id="e1d7d-117">在**屬性頁**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e1d7d-117">In the **Property Pages** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="e1d7d-118">從左窗格中，按一下 組態屬性，並確定核取方塊後**建置**和**部署**選取資料行。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-118">Click Configuration Properties from the left pane, and make sure the check boxes in the **Build** and **Deploy** columns are selected.</span></span>  
  
    2.  <span data-ttu-id="e1d7d-119">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-119">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="e1d7d-120">以滑鼠右鍵按一下方案總管 中的 BizTalk 專案，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-120">Right-click the BizTalk project in Solution Explorer, and then click **Properties**.</span></span> <span data-ttu-id="e1d7d-121">在**屬性頁**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e1d7d-121">In the **Property Pages** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="e1d7d-122">在左窗格中，依序展開**通用屬性**，然後按一下 組件。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-122">In the left pane, expand **Common Properties**, and then click Assembly.</span></span>  
  
    2.  <span data-ttu-id="e1d7d-123">在右窗格中，在**強式名稱**類別，如**組件金鑰檔案**屬性，提供您稍早建立的組件金鑰檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-123">In the right pane, under the **Strong name** category, for the **Assembly Key File** property, provide the path to the assembly key file you created earlier.</span></span>  
  
    3.  <span data-ttu-id="e1d7d-124">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-124">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="e1d7d-125">在 [方案總管] 中，以滑鼠右鍵按一下方案名稱，然後**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-125">In Solution Explorer, right-click the solution name, and then click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="e1d7d-126">已成功建置方案之後，以滑鼠右鍵按一下方案名稱，然後按一下**部署方案**。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-126">After the solution successfully builds, right-click the solution name, and then click **Deploy Solution**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e1d7d-127">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e1d7d-127">Next Steps</span></span>  
 <span data-ttu-id="e1d7d-128">建立和設定 Wcf-custom 傳送埠，並將它設定為傳送 Idoc 至 SAP 系統使用 WCF 型[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]中所述，[步驟 2： 設定 Wcf-custom 單向傳送埠](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="e1d7d-128">Create and configure a WCF-Custom send port and configure it to send IDOCs to an SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], as described in [Step 2: Configure a WCF-Custom One-way Send Port](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-send-port.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d7d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1d7d-129">See Also</span></span>  
 [<span data-ttu-id="e1d7d-130">教學課程 3： 移轉 SAP 傳送 IDOC BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="e1d7d-130">Tutorial 3: Migrating an SAP Send IDOC BizTalk Project</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-3-migrating-an-sap-send-idoc-biztalk-project.md)