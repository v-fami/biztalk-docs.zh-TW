---
title: "使用 JD Edwards OneWorld 系統 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5346aa04-ebd7-4545-9062-b349fd73b7f1
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 835432e50bce3f347e6f769fb8182ab35fc4f949
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-jd-edwards-oneworld-system"></a><span data-ttu-id="e6203-102">使用 JD Edwards OneWorld 系統</span><span class="sxs-lookup"><span data-stu-id="e6203-102">Using a JD Edwards OneWorld System</span></span>
<span data-ttu-id="e6203-103">您可以使用 JD Edwards OneWorld 配接器從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統存取 JD Edwards OneWorld 系統。</span><span class="sxs-lookup"><span data-stu-id="e6203-103">The JD Edwards OneWorld system is accessible from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system by using the JD Edwards OneWorld adapter.</span></span> <span data-ttu-id="e6203-104">此配接器是一群八個 Microsoft 隨附以供搭配使用的特定業務 (LOB) 配接器的其中一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e6203-104">This adapter is one of a group of eight line-of-business (LOB) adapters shipped by Microsoft for use with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e6203-105">JD Edwards OneWorld 實驗室的工作分成兩個部分。</span><span class="sxs-lookup"><span data-stu-id="e6203-105">The JD Edwards OneWorld lab work is divided into two parts.</span></span> <span data-ttu-id="e6203-106">第一個實驗室 (實驗室 1) 讓您不需有 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 或任何 Microsoft 產品，即可使用 JD Edwards OneWorld 系統。</span><span class="sxs-lookup"><span data-stu-id="e6203-106">This first lab (Lab 1) allows you to use the JD Edwards OneWorld system without needing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or any Microsoft products.</span></span> <span data-ttu-id="e6203-107">您將會使用 JD Edwards OneWorld Client 工具連接至 JD Edwards OneWorld 資料庫，並且根據位址找出特定記錄。</span><span class="sxs-lookup"><span data-stu-id="e6203-107">You will use the JD Edwards OneWorld Client tool to connect to a JD Edwards OneWorld database and locate a specific record based upon address.</span></span>  
  
 <span data-ttu-id="e6203-108">在第二個實驗室 (實驗室 2) 中，您將建立 BizTalk 專案和協調流程。</span><span class="sxs-lookup"><span data-stu-id="e6203-108">In the second lab (Lab 2), you will create a BizTalk project and orchestration.</span></span> <span data-ttu-id="e6203-109">建立應用程式之後，您將會使用 JD Edwards OneWorld 配接器來部署它並使用它來連線至 JD Edwards OneWorld 系統。</span><span class="sxs-lookup"><span data-stu-id="e6203-109">After you create the application, you will deploy it and use it to connect to a JD Edwards OneWorld system by using the JD Edwards OneWorld adapter.</span></span> <span data-ttu-id="e6203-110">目標是透過 BizTalk 應用程式存取資料，使用配接器。</span><span class="sxs-lookup"><span data-stu-id="e6203-110">The goal is to access data through the BizTalk application by using the adapter.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e6203-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="e6203-111">Prerequisites</span></span>  
 <span data-ttu-id="e6203-112">若要執行此實驗室的程序，您需要安裝 JD Edwards OneWorld 用戶端軟體及其最新更新。</span><span class="sxs-lookup"><span data-stu-id="e6203-112">To perform the procedures for this lab, you need to install the JD Edwards OneWorld client software and its latest update.</span></span> <span data-ttu-id="e6203-113">若要使用任何用戶端軟體工具，您需要有 JD Edwards OneWorld 資料庫、與該資料庫的網路連線，以及該系統上的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="e6203-113">To use any of the client software tools you will need a JD Edwards OneWorld database, network connectivity to that database, and a user account on that system.</span></span> <span data-ttu-id="e6203-114">您不需要有 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 即可完成此實驗室。</span><span class="sxs-lookup"><span data-stu-id="e6203-114">You do not need [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to complete this lab.</span></span>  
  
## <a name="lab-1---using-a-jd-edwards-oneworld-system"></a><span data-ttu-id="e6203-115">實驗室 1 - 使用 JD Edwards OneWorld 系統</span><span class="sxs-lookup"><span data-stu-id="e6203-115">Lab 1 - Using a JD Edwards OneWorld System</span></span>  
 <span data-ttu-id="e6203-116">在此實驗室中，您將會在不使用任何 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 元件的情況下，使用 JD Edwards OneWorld 系統。</span><span class="sxs-lookup"><span data-stu-id="e6203-116">In this lab, you will use the JD Edwards OneWorld system without using any components of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="e6203-117">目標是要測試您對 JD Edwards OneWorld 的連線能力，以確定第二個實驗室可正常進行。</span><span class="sxs-lookup"><span data-stu-id="e6203-117">The goals are to test your connectivity to JD Edwards OneWorld and to ensure that the second lab will work correctly.</span></span> <span data-ttu-id="e6203-118">您將會使用 JD Edwards OneWorld SQL Plus 工具建立和操作 JD Edwards OneWorld 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="e6203-118">You will use the JD Edwards OneWorld SQL Plus tool to create and manipulate a data table in a JD Edwards OneWorld database.</span></span>  
  
## <a name="procedures-for-lab-1---using-a-jd-edwards-oneworld-system"></a><span data-ttu-id="e6203-119">實驗室 1 - 使用 JD Edwards OneWorld 系統的程序</span><span class="sxs-lookup"><span data-stu-id="e6203-119">Procedures for Lab 1 - Using a JD Edwards OneWorld System</span></span>  
  
#### <a name="to-log-on-to-jd-edwards-oneworld-by-using-a-browser"></a><span data-ttu-id="e6203-120">使用瀏覽器登入 JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="e6203-120">To log on to JD Edwards OneWorld by using a browser</span></span>  
  
-   <span data-ttu-id="e6203-121">JD Edwards OneWorld 圖示，即可登入 JD Edwards OneWorld 系統。</span><span class="sxs-lookup"><span data-stu-id="e6203-121">Log on to the JD Edwards OneWorld system by clicking the JD Edwards OneWorld icon.</span></span> <span data-ttu-id="e6203-122">輸入您**使用者識別碼**，**密碼**，和**環境**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="e6203-122">Enter your **User ID**, **Password**, and **Environment**, and then click **OK**.</span></span>  
  
     ![](../core/media/f04db2ef-d587-4357-b9e8-c96319886e97.gif "f04db2ef-d587-4357-b9e8-c96319886e97")  
  
#### <a name="to-locate-and-view-jd-edwards-oneworld-data"></a><span data-ttu-id="e6203-123">若要找出並檢視 JD Edwards OneWorld 資料</span><span class="sxs-lookup"><span data-stu-id="e6203-123">To locate and view JD Edwards OneWorld data</span></span>  
  
1.  <span data-ttu-id="e6203-124">成功的登入將放在您**JD Edwards OneWorld 總管**。</span><span class="sxs-lookup"><span data-stu-id="e6203-124">A successful logon places you at the **JD Edwards OneWorld Explorer**.</span></span>  
  
     ![](../core/media/14e8c206-7e38-48f8-9108-e32a7ac9a740.gif "14e8c206-7e38-48f8-9108-e32a7ac9a740")  
  
2.  <span data-ttu-id="e6203-125">展開**主目錄**，然後**基礎系統**，然後**通訊錄**，然後**每日處理**。</span><span class="sxs-lookup"><span data-stu-id="e6203-125">Expand **Master Directory**, then **Foundation Systems**, then **Address Book**, and then **Daily Processing**.</span></span>  
  
     ![](../core/media/1f742221-00e5-4697-95ff-64aa63ed567a.gif "1f742221-00e5-4697-95ff-64aa63ed567a")  
  
3.  <span data-ttu-id="e6203-126">在右視窗中，按兩下**通訊錄修訂**。</span><span class="sxs-lookup"><span data-stu-id="e6203-126">In the right-hand window, double-click **Address Book Revisions**.</span></span>  
  
     ![](../core/media/a6d4e871-9c9c-4bc0-9c4f-4bdfd7cc5031.gif "a6d4e871-9c9c-4bc0-9c4f-4bdfd7cc5031")  
  
4.  <span data-ttu-id="e6203-127">如**Alpha 名稱**，輸入`Ga`，選取**顯示位址**核取方塊，然後**尋找**工具列上。</span><span class="sxs-lookup"><span data-stu-id="e6203-127">For **Alpha Name**, enter `Ga`, select the **Display Address** check box, and then click **Find** on the toolbar.</span></span>  
  
     ![](../core/media/2f58413f-41a9-4ed9-ba5c-1d6d59eafb01.gif "2f58413f-41a9-4ed9-ba5c-1d6d59eafb01")  
  
     <span data-ttu-id="e6203-128">在**通訊錄修訂-[使用位址]**對話方塊中，做為搜尋結果不會顯示兩個記錄。</span><span class="sxs-lookup"><span data-stu-id="e6203-128">In the **Address Book Revisions - [Work With Addresses]** dialog box, two records are displayed as a result of the search.</span></span>  
  
     ![](../core/media/9284df4e-ca9b-48ab-b2bf-a90d765d4a05.gif "9284df4e-ca9b-48ab-b2bf-a90d765d4a05")  
  
     <span data-ttu-id="e6203-129">尋找資料的替代方法是清除**Alpha 名稱**欄位中，按一下上面的文字方塊中的 **位址編號**資料行，並輸入`500`。</span><span class="sxs-lookup"><span data-stu-id="e6203-129">An alternative method of locating data is to clear the **Alpha Name** field, click in the text box above the **Address Number** column, and enter `500`.</span></span> <span data-ttu-id="e6203-130">按一下**尋找**顯示搜尋結果 工具列上。</span><span class="sxs-lookup"><span data-stu-id="e6203-130">Click **Find** on the toolbar to display the search results.</span></span>  
  
     ![](../core/media/a88bd867-9a16-416a-a43e-cdfcc65fc670.gif "a88bd867-9a16-416a-a43e-cdfcc65fc670")  
  
     <span data-ttu-id="e6203-131">在實驗室 2 中，會使用 JD Edwards OneWorld 配接器擷取的資訊的指示**位址編號**的`500`。</span><span class="sxs-lookup"><span data-stu-id="e6203-131">In Lab 2, there will be instructions for using the JD Edwards OneWorld adapter to retrieve the information for an **Address Number** of `500`.</span></span>  
  
5.  <span data-ttu-id="e6203-132">在**檔案**功能表上，按一下 **結束**結束 JE Edwards OneWorld 用戶端工作階段。</span><span class="sxs-lookup"><span data-stu-id="e6203-132">On the **File** menu, click **Exit** to exit the JE Edwards OneWorld Client session.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="e6203-133">摘要</span><span class="sxs-lookup"><span data-stu-id="e6203-133">Summary</span></span>  
 <span data-ttu-id="e6203-134">在此實驗室中，您使用了 JD Edwards OneWorld Client 工具登入 JD Edwards OneWorld 系統。</span><span class="sxs-lookup"><span data-stu-id="e6203-134">In this lab, you used the JD Edwards OneWorld Client tool to log on to the JD Edwards OneWorld system.</span></span> <span data-ttu-id="e6203-135">您已連接之後，您會搜尋特定的資料，而檢視傳回的資料記錄。</span><span class="sxs-lookup"><span data-stu-id="e6203-135">After you were connected, you searched for specific data and viewed the data records returned.</span></span>