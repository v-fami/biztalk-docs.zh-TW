---
title: "步驟 1： 建立和部署接收 IDOC vPrev BizTalk 專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migration, building and deploying previous version of BizTalk project for receiving an IDOC
- migrating, building and deploying previous version of BizTalk project for receiving an IDOC
- migration
ms.assetid: ab6bdf9a-dca5-4acd-97b2-a9afe9792978
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f99971a421530e4901c8bbac6533809a0f2f273c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-build-and-deploy-the-vprev-biztalk-project-for-receiving-an-idoc"></a><span data-ttu-id="65705-102">步驟 1： 建立和部署接收 IDOC vPrev BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="65705-102">Step 1: Build and Deploy the vPrev BizTalk Project for Receiving an IDOC</span></span>
<span data-ttu-id="65705-103">![步驟 3 之 1](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span><span class="sxs-lookup"><span data-stu-id="65705-103">![Step 1 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span></span>  
  
 <span data-ttu-id="65705-104">**若要完成的時間：** 5 分鐘</span><span class="sxs-lookup"><span data-stu-id="65705-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="65705-105">**目標：**在此步驟中，您要建置和部署現有的 vPrev BizTalk 專案，從 SAP 系統接收 IDOC。</span><span class="sxs-lookup"><span data-stu-id="65705-105">**Objective:** In this step, you build and deploy your existing vPrev BizTalk project to receive an IDOC from an SAP system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65705-106">您不需要進行任何變更 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="65705-106">You do not need to make any change to the vPrev BizTalk project.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="65705-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="65705-107">Prerequisites</span></span>  
 <span data-ttu-id="65705-108">您必須從 SAP 系統接收 IDOC ORDERS03 vPrev BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="65705-108">You must have a vPrev BizTalk project to receive an ORDERS03 IDOC from an SAP system.</span></span>  
  
### <a name="to-build-and-deploy-the-vprev-biztalk-project"></a><span data-ttu-id="65705-109">若要建置和部署 vPrev BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="65705-109">To build and deploy the vPrev BizTalk project</span></span>  
  
1.  <span data-ttu-id="65705-110">建立強式名稱金鑰檔案，才能建立及部署方案。</span><span class="sxs-lookup"><span data-stu-id="65705-110">Create a strong-name key file required to build and deploy the solution.</span></span> <span data-ttu-id="65705-111">若要建立強式名稱金鑰檔，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="65705-111">To create a strong-name key file, do the following:</span></span>  
  
    1.  <span data-ttu-id="65705-112">啟動 Visual Studio 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="65705-112">Start Visual Studio Command Prompt.</span></span>  
  
    2.  <span data-ttu-id="65705-113">在命令提示字元中瀏覽至您要建立金鑰檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="65705-113">At the command prompt navigate to the folder where you want to create the key file.</span></span> <span data-ttu-id="65705-114">例如，輸入**cd C:\Sample**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="65705-114">For example, type **cd C:\Sample**, and then press ENTER.</span></span>  
  
    3.  <span data-ttu-id="65705-115">在命令提示字元中，輸入**sn-k\<金鑰檔名稱\>.snk**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="65705-115">At the command prompt, type **sn -k \<key file name\>.snk**, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="65705-116">以滑鼠右鍵按一下方案總管 中的 BizTalk 方案名稱，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="65705-116">Right-click the BizTalk solution name in Solution Explorer, and then click **Properties**.</span></span> <span data-ttu-id="65705-117">在**屬性頁**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="65705-117">In the **Property Pages** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="65705-118">按一下**組態屬性**從左的窗格中，並確定核取方塊，**建置**和**部署**選取資料行。</span><span class="sxs-lookup"><span data-stu-id="65705-118">Click **Configuration Properties** from the left pane, and make sure the check boxes in the **Build** and **Deploy** columns are selected.</span></span>  
  
    2.  <span data-ttu-id="65705-119">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="65705-119">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="65705-120">以滑鼠右鍵按一下方案總管 中的 BizTalk 專案，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="65705-120">Right-click the BizTalk project in Solution Explorer, and then click **Properties**.</span></span> <span data-ttu-id="65705-121">在**屬性頁**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="65705-121">In the **Property Pages** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="65705-122">在左窗格中，依序展開**通用屬性**，然後按一下 組件。</span><span class="sxs-lookup"><span data-stu-id="65705-122">In the left pane, expand **Common Properties**, and then click Assembly.</span></span>  
  
    2.  <span data-ttu-id="65705-123">在右窗格中，在**強式名稱**類別，如**組件金鑰檔案**屬性，提供您稍早建立的組件金鑰檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="65705-123">In the right pane, under the **Strong name** category, for the **Assembly Key File** property, provide the path to the assembly key file you created earlier.</span></span>  
  
    3.  <span data-ttu-id="65705-124">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="65705-124">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="65705-125">在 [方案總管] 中，以滑鼠右鍵按一下方案名稱，然後**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="65705-125">In Solution Explorer, right-click the solution name, and then click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="65705-126">已成功建置方案之後，以滑鼠右鍵按一下方案名稱，然後按一下**部署方案**。</span><span class="sxs-lookup"><span data-stu-id="65705-126">After the solution successfully builds, right-click the solution name, and then click **Deploy Solution**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="65705-127">後續步驟</span><span class="sxs-lookup"><span data-stu-id="65705-127">Next Steps</span></span>  
 <span data-ttu-id="65705-128">建立及設定 WCF 自訂接收埠，並將它設定為從使用 WCF 為基礎的 SAP 系統接收 Idoc[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]中所述，[步驟 2： 設定 Wcf-custom 單向接收埠](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-receive-port.md)。</span><span class="sxs-lookup"><span data-stu-id="65705-128">Create and configure a WCF-Custom receive port and configure it to receive IDOCs from an SAP system using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], as described in [Step 2: Configure a WCF-Custom One-way Receive Port](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-receive-port.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65705-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="65705-129">See Also</span></span>  
 [<span data-ttu-id="65705-130">教學課程 4：移轉 SAP 接收 IDOC BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="65705-130">Tutorial 4: Migrating an SAP Receive IDOC BizTalk Project</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-4-migrating-an-sap-receive-idoc-biztalk-project.md)