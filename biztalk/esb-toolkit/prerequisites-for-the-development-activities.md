---
title: 開發活動的必要條件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 54c91405-f9a4-4676-b5c5-fe90b3b51b45
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbc79fd31e78581d98ecad34579958ff90f3b1e1
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006255"
---
# <a name="prerequisites-for-the-development-activities"></a><span data-ttu-id="6a1ca-102">開發活動的必要條件</span><span class="sxs-lookup"><span data-stu-id="6a1ca-102">Prerequisites for the Development Activities</span></span>
<span data-ttu-id="6a1ca-103">本章節描述如何準備您的環境，完成的一部分的開發活動中的步驟[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6a1ca-103">This section describes how to prepare your environment to complete the steps in the development activities that are included as part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="6a1ca-104">才能嘗試進行任何開發活動中的程序，請完成下列設定：</span><span class="sxs-lookup"><span data-stu-id="6a1ca-104">Complete the following setup before you attempt any of the procedures in the development activities:</span></span>  
  
## <a name="set-up-your-computer-to-perform-the-procedures-in-the-biztalk-esb-toolkit-development-activities"></a><span data-ttu-id="6a1ca-105">BizTalk ESB Toolkit 開發活動中執行的程序設定您的電腦</span><span class="sxs-lookup"><span data-stu-id="6a1ca-105">Set up your computer to perform the procedures in the BizTalk ESB Toolkit development activities</span></span>  
  
1.  <span data-ttu-id="6a1ca-106">安裝和部署路線範例應用程式、 動態解析範例應用程式和多個 Web 服務範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a1ca-106">Install and deploy the Itinerary sample application, the Dynamic Resolution sample application, and the Multiple Web Services sample application.</span></span> <span data-ttu-id="6a1ca-107">如需有關安裝和部署這些應用程式的詳細資訊，請參閱[BizTalk ESB 工具組範例應用程式](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="6a1ca-107">For more information about installing and deploying these applications, see [BizTalk ESB Toolkit Sample Applications](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md).</span></span>  
  
2.  <span data-ttu-id="6a1ca-108">執行 「 UDDI 發行者 」 公用程式。</span><span class="sxs-lookup"><span data-stu-id="6a1ca-108">Run the UDDI Publisher Utility.</span></span>  
  
3.  <span data-ttu-id="6a1ca-109">在開發電腦，在 Windows 檔案總管 中，建立下列路徑：</span><span class="sxs-lookup"><span data-stu-id="6a1ca-109">On your development computer, in Windows Explorer, create the following paths:</span></span>  
  
    -   <span data-ttu-id="6a1ca-110">C:\HowTos</span><span class="sxs-lookup"><span data-stu-id="6a1ca-110">C:\HowTos</span></span>  
  
    -   <span data-ttu-id="6a1ca-111">C:\HowTos\Itineraries</span><span class="sxs-lookup"><span data-stu-id="6a1ca-111">C:\HowTos\Itineraries</span></span>  
  
    -   <span data-ttu-id="6a1ca-112">C:\HowTos\DropFolder</span><span class="sxs-lookup"><span data-stu-id="6a1ca-112">C:\HowTos\DropFolder</span></span>  
  
    -   <span data-ttu-id="6a1ca-113">C:\HowTos\Out</span><span class="sxs-lookup"><span data-stu-id="6a1ca-113">C:\HowTos\Out</span></span>  
  
4.  <span data-ttu-id="6a1ca-114">請確認您的 BizTalk Server 服務帳戶具有**完全控制**C:\HowTos 目錄結構的權限。</span><span class="sxs-lookup"><span data-stu-id="6a1ca-114">Ensure that your BizTalk Server service account has **Full Control** permissions to the C:\HowTos directory structure.</span></span>  
  
5.  <span data-ttu-id="6a1ca-115">請確認您的 Microsoft BizTalk Server 服務帳戶具有**寫入**C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out 的權限。</span><span class="sxs-lookup"><span data-stu-id="6a1ca-115">Ensure that your Microsoft BizTalk Server service account has **Write** permissions to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out.</span></span>  
  
6.  <span data-ttu-id="6a1ca-116">複製下列測試訊息到 C:\HowTos 資料夾：</span><span class="sxs-lookup"><span data-stu-id="6a1ca-116">Copy the following test message to the C:\HowTos folder:</span></span>  
  
    -   <span data-ttu-id="6a1ca-117">C:\Projects\Microsoft.Practices.ESB\Source\Samples\Itinerary\Test\Data\NAOrderDoc.xml</span><span class="sxs-lookup"><span data-stu-id="6a1ca-117">C:\Projects\Microsoft.Practices.ESB\Source\Samples\Itinerary\Test\Data\NAOrderDoc.xml</span></span>  
  
7.  <span data-ttu-id="6a1ca-118">在 C:\HowTos 資料夾中建立的捷徑至路線測試用戶端應用程式，在下列位置找到：</span><span class="sxs-lookup"><span data-stu-id="6a1ca-118">In the C:\HowTos folder, create a shortcut to the Itinerary Test Client application, found at the following location:</span></span>  
  
    -   <span data-ttu-id="6a1ca-119">C:\Projects\Microsoft.Practices.ESB\Source\Samples\Itinerary\Source\ESB。Itinerary.Test\bin\Debug\ESB。Itinerary.Test.exe</span><span class="sxs-lookup"><span data-stu-id="6a1ca-119">C:\Projects\Microsoft.Practices.ESB\Source\Samples\Itinerary\Source\ESB.Itinerary.Test\bin\Debug\ESB.Itinerary.Test.exe</span></span>  
  
## <a name="create-the-visual-studio-solution"></a><span data-ttu-id="6a1ca-120">建立 Visual Studio 方案</span><span class="sxs-lookup"><span data-stu-id="6a1ca-120">Create the Visual Studio solution</span></span>  
  
1.  <span data-ttu-id="6a1ca-121">在 Visual Studio 中，在 檔案 功能表上指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="6a1ca-121">In Visual Studio, on the File menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="6a1ca-122">在**新專案**對話方塊，在 專案類型 窗格中，按一下**Visual C#**，然後按一下 **類別庫**在範本窗格中。</span><span class="sxs-lookup"><span data-stu-id="6a1ca-122">In the **New Project** dialog box, in the Project types pane, click **Visual C#**, and then click **Class Library** in the Templates pane.</span></span>  
  
3.  <span data-ttu-id="6a1ca-123">在**名稱**方塊中，輸入**ItineraryLibrary**。</span><span class="sxs-lookup"><span data-stu-id="6a1ca-123">In the **Name** box, type **ItineraryLibrary**.</span></span>  
  
4.  <span data-ttu-id="6a1ca-124">在**位置**方塊中，輸入**C:\HowTos**。</span><span class="sxs-lookup"><span data-stu-id="6a1ca-124">In the **Location** box, type **C:\HowTos**.</span></span>  
  
5.  <span data-ttu-id="6a1ca-125">選取**為方案建立目錄**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6a1ca-125">Select the **Create directory for solution** check box.</span></span>  
  
6.  <span data-ttu-id="6a1ca-126">在**方案名稱**方塊中，輸入**模式**，然後按一下**確定**即可建立方案。</span><span class="sxs-lookup"><span data-stu-id="6a1ca-126">In the **Solution Name** box, type **Patterns**, and then click **OK** to create the solution.</span></span>  
  
7.  <span data-ttu-id="6a1ca-127">刪除**Class1.cs**檔案從**ItineraryLibrary**專案。</span><span class="sxs-lookup"><span data-stu-id="6a1ca-127">Delete the **Class1.cs** file from the **ItineraryLibrary** project.</span></span>