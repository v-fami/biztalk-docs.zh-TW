---
title: "如何建立追蹤設定檔 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking profiles, creating
- creating, tracking profiles
ms.assetid: 676ae7e8-f3eb-45f1-ad2e-807b434c0bf9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34f5d6cbb210cb292cd8ae7d0e2f4ff811984377
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="4783b-102">如何建立追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4783b-102">How to Create a Tracking Profile</span></span>
<span data-ttu-id="4783b-103">您可建立追蹤設定檔，將 BAM 活動定義連結到部署的組件和 BizTalk Server 傳訊屬性。</span><span class="sxs-lookup"><span data-stu-id="4783b-103">You create tracking profiles to link BAM activity definitions to deployed assemblies and BizTalk Server messaging properties.</span></span> <span data-ttu-id="4783b-104">當您開啟追蹤設定檔編輯器時，可以按一下匯入活動連結或匯入功能表項目建立新的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="4783b-104">When you open the Tracking Profile Editor, you can create a new tracking profile by either clicking the import activity link or the import menu item.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4783b-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="4783b-105">Prerequisites</span></span>  
 <span data-ttu-id="4783b-106">以下是執行此主題中之程序的必要條件：</span><span class="sxs-lookup"><span data-stu-id="4783b-106">The following are prerequisites for performing the procedure in this topic:</span></span>  
  
-   <span data-ttu-id="4783b-107">您具有權限的現有 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="4783b-107">An existing BizTalk Management database to which you have permissions.</span></span>  
  
-   <span data-ttu-id="4783b-108">設定為使用 BizTalk 管理資料庫的 TPE。</span><span class="sxs-lookup"><span data-stu-id="4783b-108">The TPE configured to use the BizTalk Management database.</span></span>  
  
-   <span data-ttu-id="4783b-109">BAM 主要匯入資料庫中的現有 BAM 活動定義。</span><span class="sxs-lookup"><span data-stu-id="4783b-109">An existing BAM activity definition in the BAM Primary Import database.</span></span>  
  
### <a name="to-create-a-tracking-profile"></a><span data-ttu-id="4783b-110">建立追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4783b-110">To create a tracking profile</span></span>  
  
1.  <span data-ttu-id="4783b-111">在電腦或在已識別為來源系統的電腦，開啟**追蹤設定檔編輯器**。</span><span class="sxs-lookup"><span data-stu-id="4783b-111">On the computer or computers that you have identified as the source system, open the **Tracking Profile Editor**.</span></span> <span data-ttu-id="4783b-112">若要這樣做，請按一下**啟動**，按一下**執行**，型別**BTSTrkEditor.exe**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="4783b-112">To do this, click **Start**, click **Run**, type **BTSTrkEditor.exe**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4783b-113">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="4783b-113">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="4783b-114">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="4783b-114">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="4783b-115">中間的 TPE 左窗格中，按一下**按一下這裡匯入 BAM 活動定義**連結。</span><span class="sxs-lookup"><span data-stu-id="4783b-115">In the middle of the left pane of the TPE, click **Click here to import a BAM Activity Definition** link.</span></span> <span data-ttu-id="4783b-116">這會開啟**匯入 BAM 活動定義** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4783b-116">This opens the **Import BAM Activity Definition** dialog box.</span></span>  
  
3.  <span data-ttu-id="4783b-117">從**BAM 活動定義名稱**清單方塊選取要設立追蹤的活動。</span><span class="sxs-lookup"><span data-stu-id="4783b-117">From the **BAM Activity Definition Name** list box select the activity on which to base the tracking.</span></span> <span data-ttu-id="4783b-118">如果您的清單包含許多已部署的活動，您可以輸入中的活動名稱的一部分**中字串**文字方塊中，然後按一下**搜尋** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4783b-118">If your list contains many deployed activities, you can type part of the activity name in the **In String** text box and click the **Search** button.</span></span> <span data-ttu-id="4783b-119">如此便會限定所顯示的活動清單，只列出其名稱包含所輸入之部分名稱的活動。</span><span class="sxs-lookup"><span data-stu-id="4783b-119">This limits the list of activities displayed to those whose names contain the partial name entered.</span></span>  
  
4.  <span data-ttu-id="4783b-120">一旦您選取活動，按一下**確定** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4783b-120">Once you have selected the activity, click the **OK** button.</span></span> <span data-ttu-id="4783b-121">這會根據所選取的活動開啟新的追蹤設定檔，並在 TPE 的左窗格中顯示該設定檔。</span><span class="sxs-lookup"><span data-stu-id="4783b-121">This opens a new tracking profile based on the activity selected and displays the profile in the left pane of the TPE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4783b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4783b-122">See Also</span></span>  
 [<span data-ttu-id="4783b-123">建立追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="4783b-123">Creating Tracking Profiles</span></span>](../core/creating-tracking-profiles.md)