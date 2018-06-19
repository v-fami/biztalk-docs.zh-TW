---
title: 步驟 1： 設定應用程式集區識別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, application pools
- application pools
ms.assetid: 66286327-8580-4378-89ee-ddd7204b03c6
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e61ee2994e81c3fdd352506d6a9757cde557fbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206574"
---
# <a name="step-1-configure-application-pool-identity"></a><span data-ttu-id="5f2ce-102">步驟 1： 設定應用程式集區識別</span><span class="sxs-lookup"><span data-stu-id="5f2ce-102">Step 1: Configure Application Pool Identity</span></span>
<span data-ttu-id="5f2ce-103">在本教學課程中，您可以使用應用程式集區中的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]網際網路資訊服務 (IIS) 處理協調流程，您將發佈為 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-103">In this tutorial, you use an application pool in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Internet Information Services (IIS) to process the orchestration, which you publish as a Web service.</span></span> <span data-ttu-id="5f2ce-104">應用程式集區是由背景工作處理序的一個或多個 url 群組。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-104">An application pool is a grouping of one or more URLs served by a worker process.</span></span>  
  
 <span data-ttu-id="5f2ce-105">應用程式集區的識別是應用程式集區的工作者處理序所執行的服務帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-105">The identity of an application pool is the name of the service account under which the worker process of the application pool runs.</span></span> <span data-ttu-id="5f2ce-106">根據預設，應用程式集區是以 Network Service 使用者帳戶，具有低層級的使用者存取權限，並不足以進行本教學課程函式運作。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-106">By default, application pools operate under the Network Service user account, which has low-level user-access rights and is insufficient for this tutorial to function.</span></span> <span data-ttu-id="5f2ce-107">基於安全性理由，您想要設定應用程式集區識別的使用者帳戶，絕對最小權限，但在最低權限可以寫入組態資料庫 (也稱為 BizTalk 與 MessageBox 資料庫 (BizTalkMsgBoxDb)管理資料庫或 BizTalkMgmtDb）。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-107">For security reasons, you want to configure the application pool identity to a user account with the absolute minimum permissions, but at least permissions to write to the MessageBox database (BizTalkMsgBoxDb) and Configuration database (also known as the BizTalk Management database, or BizTalkMgmtDb).</span></span>  
  
### <a name="to-change-the-service-account-under-which-an-application-pool-runs"></a><span data-ttu-id="5f2ce-108">若要變更應用程式集區所執行的服務帳戶</span><span class="sxs-lookup"><span data-stu-id="5f2ce-108">To change the service account under which an application pool runs</span></span>  
  
1.  <span data-ttu-id="5f2ce-109">按一下**啟動**，指向 **程式**，指向 **系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**.</span><span class="sxs-lookup"><span data-stu-id="5f2ce-109">Click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="5f2ce-110">在 [網際網路資訊服務 (IIS) 管理員] 中，展開本機電腦，及**應用程式集區**。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-110">In Internet Information Services (IIS) Manager, expand the local computer, and expand **Application Pools**.</span></span>  
  
3.  <span data-ttu-id="5f2ce-111">以滑鼠右鍵按一下您想要設定的應用程式集區 (依預設，此教學課程中，執行**DefaultAppPool**)，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-111">Right-click the application pool you want to configure (by default, this tutorial runs under the **DefaultAppPool**), and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="5f2ce-112">在 [DefaultAppPool 屬性] 對話方塊上**識別**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="5f2ce-112">In the DefaultAppPool Properties dialog box, on the **Identity** tab, do the following:</span></span>  
  
    |<span data-ttu-id="5f2ce-113">使用</span><span class="sxs-lookup"><span data-stu-id="5f2ce-113">Use this</span></span>|<span data-ttu-id="5f2ce-114">動作</span><span class="sxs-lookup"><span data-stu-id="5f2ce-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="5f2ce-115">**預先定義的**</span><span class="sxs-lookup"><span data-stu-id="5f2ce-115">**Predefined**</span></span>|<span data-ttu-id="5f2ce-116">取消選取**預先定義的**。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-116">Deselect **Predefined**.</span></span> <span data-ttu-id="5f2ce-117">**預先定義的**指的是標準的服務帳戶，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5f2ce-117">**Predefined** refers to standard service accounts, such as the following:</span></span><br /><br /> <span data-ttu-id="5f2ce-118">-   **網路服務**（預設值），其中包含可用於存取遠端電腦上的資源的低層級的使用者存取權限。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-118">-   **Network Service** (the default), which has low-level user access rights that can be used for access to resources on remote computers.</span></span><br /><span data-ttu-id="5f2ce-119">-   **本機服務**，具有低層級的存取權限。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-119">-   **Local Service**, which has low-level access rights.</span></span> <span data-ttu-id="5f2ce-120">您不需要在遠端電腦上的資源的存取權的情況下使用這項設定。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-120">You use this setting for situations that do not require access to resources on remote computers.</span></span><br /><span data-ttu-id="5f2ce-121">-   **本機系統**，這是具有多個與 Network Service 或 Local Service 帳戶的使用者權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-121">-   **Local System**, which is an account with more user rights than the Network Service or Local Service account.</span></span>|  
    |<span data-ttu-id="5f2ce-122">**可設定**</span><span class="sxs-lookup"><span data-stu-id="5f2ce-122">**Configurable**</span></span>|<span data-ttu-id="5f2ce-123">選取**可設定**。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-123">Select **Configurable**.</span></span> <span data-ttu-id="5f2ce-124">**可設定**指的是已註冊的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-124">**Configurable** refers to registered user names.</span></span>|  
    |<span data-ttu-id="5f2ce-125">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="5f2ce-125">**User name**</span></span>|<span data-ttu-id="5f2ce-126">輸入要在其下運作的工作者處理序的帳戶的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-126">Type the user name of the account under which you want the worker process to operate.</span></span>|  
    |<span data-ttu-id="5f2ce-127">**密碼**</span><span class="sxs-lookup"><span data-stu-id="5f2ce-127">**Password**</span></span>|<span data-ttu-id="5f2ce-128">輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-128">Type the password.</span></span>|  
  
5.  <span data-ttu-id="5f2ce-129">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-129">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5f2ce-130">此外，為了提高安全性，您可以建立全新的應用程式集區的權限為本教學課程量身訂做的自訂身分識別下執行。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-130">Alternatively, for increased security, you could create an entirely new application pool that runs under a custom identity that you create with permissions tailored for this tutorial.</span></span>  
  
 <span data-ttu-id="5f2ce-131">若要繼續[步驟 2： 建立新的專案](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md)。</span><span class="sxs-lookup"><span data-stu-id="5f2ce-131">Proceed to [Step 2: Create a New Project](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f2ce-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f2ce-132">See Also</span></span>  
 [<span data-ttu-id="5f2ce-133">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="5f2ce-133">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)