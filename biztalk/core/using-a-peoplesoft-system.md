---
title: "使用 PeopleSoft 系統 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c228ac23-184f-4c08-922b-ba84f5f2c52f
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c93e025ddb2ccec4b0088c20837a4f307f40aada
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-peoplesoft-system"></a><span data-ttu-id="62059-102">使用 PeopleSoft 系統</span><span class="sxs-lookup"><span data-stu-id="62059-102">Using a PeopleSoft System</span></span>
<span data-ttu-id="62059-103">您可以從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統使用 PeopleSoft 配接器存取 PeopleSoft 系統。</span><span class="sxs-lookup"><span data-stu-id="62059-103">The PeopleSoft system is accessible from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system by using the PeopleSoft adapter.</span></span> <span data-ttu-id="62059-104">此配接器是一群八個 Microsoft 隨附以供搭配使用的特定業務 (LOB) 配接器的其中一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="62059-104">This adapter is one of a group of eight line-of-business (LOB) adapters shipped by Microsoft for use with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="62059-105">PeopleSoft 實驗室工作分成兩個部分。</span><span class="sxs-lookup"><span data-stu-id="62059-105">The PeopleSoft lab work is divided into two parts.</span></span> <span data-ttu-id="62059-106">第一個實驗室 (實驗室 1) 可讓您不需要使用 PeopleSoft 系統[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或任何 Microsoft 產品 （但可能是 Internet Explorer 中，但是您可以使用任何瀏覽器）。</span><span class="sxs-lookup"><span data-stu-id="62059-106">This first lab (Lab 1) allows you to use the PeopleSoft system without needing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or any Microsoft products (except perhaps Internet Explorer, but you can use any browser).</span></span> <span data-ttu-id="62059-107">在這個實驗室中，您將會連接至 PeopleSoft 系統來找出和修改的簡單資料記錄。</span><span class="sxs-lookup"><span data-stu-id="62059-107">In this lab, you will connect to the PeopleSoft system to locate and modify a simple data record.</span></span>  
  
 <span data-ttu-id="62059-108">在第二個實驗室 (實驗室 2) 中，您將建立 BizTalk 專案和協調流程。</span><span class="sxs-lookup"><span data-stu-id="62059-108">In the second lab (Lab 2), you will create a BizTalk project and orchestration.</span></span> <span data-ttu-id="62059-109">建立應用程式之後，您會將它部署，並使用它來連線至 PeopleSoft 系統使用 PeopleSoft 配接器。</span><span class="sxs-lookup"><span data-stu-id="62059-109">After you create the application, you will deploy it and use it to connect to a PeopleSoft system by using the PeopleSoft adapter.</span></span> <span data-ttu-id="62059-110">目標是透過 BizTalk 應用程式存取資料，使用配接器。</span><span class="sxs-lookup"><span data-stu-id="62059-110">The goal is to access data through the BizTalk application by using the adapter.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="62059-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="62059-111">Prerequisites</span></span>  
 <span data-ttu-id="62059-112">若要執行本實驗室的程序，您需要在瀏覽器和網際網路連線，以及 PeopleSoft 系統上的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="62059-112">To perform the procedures for this lab, you need a browser and an Internet connection, along with a user account on a PeopleSoft system.</span></span> <span data-ttu-id="62059-113">您需要知道要瀏覽至您的 PeopleSoft 系統的 Web 存取的位置。</span><span class="sxs-lookup"><span data-stu-id="62059-113">You need to know the location to browse to for gaining Web access to your PeopleSoft system.</span></span> <span data-ttu-id="62059-114">您不需要[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]或任何其他 Microsoft 技術。</span><span class="sxs-lookup"><span data-stu-id="62059-114">You do not need [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or any other Microsoft technologies.</span></span>  
  
## <a name="lab-1---using-a-peoplesoft-system"></a><span data-ttu-id="62059-115">實驗室 1-使用 PeopleSoft 系統</span><span class="sxs-lookup"><span data-stu-id="62059-115">Lab 1 - Using a PeopleSoft System</span></span>  
 <span data-ttu-id="62059-116">在這個實驗室中，您將使用 PeopleSoft 系統，而不使用的任何元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="62059-116">In this lab, you will use the PeopleSoft system without using any components of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="62059-117">目標是要測試您的連線以確保能夠正確地設定第二個實驗室 PeopleSoft。</span><span class="sxs-lookup"><span data-stu-id="62059-117">The goal is to test your connectivity to PeopleSoft to ensure that the second lab will work correctly.</span></span> <span data-ttu-id="62059-118">一開始您連接至 PeopleSoft 系統透過 Web 介面，可讓您使用如 Internet Explorer 的瀏覽器登入。</span><span class="sxs-lookup"><span data-stu-id="62059-118">Initially you connect to the PeopleSoft system through its Web interface that allows you to log on by using a browser such as Internet Explorer.</span></span>  
  
## <a name="procedures-for-lab-1---using-a-peoplesoft-system"></a><span data-ttu-id="62059-119">實驗室 1-使用 PeopleSoft 系統的程序</span><span class="sxs-lookup"><span data-stu-id="62059-119">Procedures for Lab 1 - Using a PeopleSoft System</span></span>  
  
#### <a name="to-log-on-to-peoplesoft-by-using-a-browser"></a><span data-ttu-id="62059-120">使用瀏覽器登入 PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="62059-120">To log on to PeopleSoft by using a browser</span></span>  
  
-   <span data-ttu-id="62059-121">瀏覽 PeopleSoft 登入網頁登入 PeopleSoft 系統。</span><span class="sxs-lookup"><span data-stu-id="62059-121">Log on to the PeopleSoft system by browsing to a PeopleSoft logon page.</span></span> <span data-ttu-id="62059-122">輸入您**使用者識別碼**和**密碼**，然後按一下 **登入**。</span><span class="sxs-lookup"><span data-stu-id="62059-122">Enter your **User ID** and **Password** and then click **Sign In**.</span></span>  
  
     ![](../core/media/1e3e5c0f-316b-4aa3-946e-3bb3665b0ddb.gif "1e3e5c0f-316b-4aa3-946e-3bb3665b0ddb")  
  
#### <a name="to-locate-and-modify-peoplesoft-data"></a><span data-ttu-id="62059-123">若要找出和修改 PeopleSoft 資料</span><span class="sxs-lookup"><span data-stu-id="62059-123">To locate and modify PeopleSoft data</span></span>  
  
1.  <span data-ttu-id="62059-124">成功的登入將放在您個人化您選擇其配置看到的內容頁面。</span><span class="sxs-lookup"><span data-stu-id="62059-124">A successful logon places you at the page to personalize the content you see by choosing its layout.</span></span> <span data-ttu-id="62059-125">向下捲動並展開**設定財務/供應鏈**，按一下 **一般定義**，按一下 **位置**，然後按一下 **位置**一次。</span><span class="sxs-lookup"><span data-stu-id="62059-125">Scroll down and expand **Set Up Financials/Supply Chain**, click **Common Definitions**, click **Location**, and then click **Location** again.</span></span> <span data-ttu-id="62059-126">這會帶您到**位置**搜尋介面。</span><span class="sxs-lookup"><span data-stu-id="62059-126">This brings you to the **Location** search interface.</span></span>  
  
     ![](../core/media/62a89cd4-464c-42fd-91cd-60ceeab5b006.gif "62a89cd4-464c-42fd-91cd-60ceeab5b006")  
  
2.  <span data-ttu-id="62059-127">若要開始搜尋，請設定**SetID**至 **=** ，將**Location Code**至**開頭**，輸入，然後按一下 **搜尋**。</span><span class="sxs-lookup"><span data-stu-id="62059-127">To begin the search, set **SetID** to **=**, set **Location Code** to **begins with**, enter **A**, and then click **Search**.</span></span> <span data-ttu-id="62059-128">這會顯示其名稱開頭中的城市**搜尋結果**介面區段。</span><span class="sxs-lookup"><span data-stu-id="62059-128">This displays cities whose names start with A in the **Search Results** section of the interface.</span></span>  
  
     ![](../core/media/86661144-c666-4d72-9227-9f17df715ba4.gif "86661144-c666-4d72-9227-9f17df715ba4")  
  
3.  <span data-ttu-id="62059-129">按一下其中一個位置，以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="62059-129">Click one of the locations to get its detail information.</span></span> <span data-ttu-id="62059-130">例如，在下圖中，使用者按一下**AUS01**中連結**Location Code**資料行。</span><span class="sxs-lookup"><span data-stu-id="62059-130">For example, in the figure below, the user clicked the **AUS01** link in the **Location Code** column.</span></span>  
  
4.  <span data-ttu-id="62059-131">輸入其中一個欄位的一些新的資料 (例如**位址 2**欄位)，按一下 **儲存**左下角。</span><span class="sxs-lookup"><span data-stu-id="62059-131">Enter some new data into one of the fields (such as the **Address 2** field) and click **Save** in the lower-left corner.</span></span> <span data-ttu-id="62059-132">這會將新輸入的資料儲存到記錄中。</span><span class="sxs-lookup"><span data-stu-id="62059-132">This saves the newly entered data into the record.</span></span>  
  
     ![](../core/media/b6eb137c-c0b0-4906-8fbd-1bc036069fb0.gif "b6eb137c-c0b0-4906-8fbd-1bc036069fb0")  
  
5.  <span data-ttu-id="62059-133">若要確認這項變更成功，重複步驟 2 中的程序、 尋找此相同的記錄一次，並觀察記錄所做的變更。</span><span class="sxs-lookup"><span data-stu-id="62059-133">To verify the success of this change, repeat the process from step 2, find this same record again, and observe the changes made to the record.</span></span>  
  
6.  <span data-ttu-id="62059-134">在視窗右上方部分中，按一下**登出**結束您的 PeopleSoft 工作階段。</span><span class="sxs-lookup"><span data-stu-id="62059-134">In the upper-right portion of the window, click **Sign out** to end your PeopleSoft session.</span></span>  
  
     ![](../core/media/7760b541-5155-453e-a682-4780412f3c13.gif "7760b541-5155-453e-a682-4780412f3c13")  
  
    > [!NOTE]
    >  <span data-ttu-id="62059-135">在下一個實驗室中有使用 PeopleSoft 配接器擷取您所修改的位置記錄 (AUS01) 資訊的指示。</span><span class="sxs-lookup"><span data-stu-id="62059-135">In the next lab there are instructions for using the PeopleSoft adapter to retrieve the information for the location record (AUS01) that you modified.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="62059-136">摘要</span><span class="sxs-lookup"><span data-stu-id="62059-136">Summary</span></span>  
 <span data-ttu-id="62059-137">在這個實驗室中您可登入 PeopleSoft 系統，透過瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="62059-137">In this lab you logged on to the PeopleSoft system through a browser.</span></span> <span data-ttu-id="62059-138">您已連接之後，您搜尋的資料，然後操作並更新資料錄的地址欄位。</span><span class="sxs-lookup"><span data-stu-id="62059-138">After you were connected, you searched for data, and then manipulated and updated a record's address field.</span></span> <span data-ttu-id="62059-139">後認可變更，您無法修改的資料瀏覽器中檢視可讓您確認變更正確執行。</span><span class="sxs-lookup"><span data-stu-id="62059-139">After committing the change, you could view the modified data in the browser to verify that the change executed properly.</span></span>