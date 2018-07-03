---
title: 步驟 1： 設定應用程式集區身分識別 |Microsoft Docs
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
ms.openlocfilehash: 61cdbc019b2e36ea8c50d97ff03597374cb07253
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988487"
---
# <a name="step-1-configure-application-pool-identity"></a><span data-ttu-id="a0bc1-102">步驟 1： 設定應用程式集區識別</span><span class="sxs-lookup"><span data-stu-id="a0bc1-102">Step 1: Configure Application Pool Identity</span></span>
<span data-ttu-id="a0bc1-103">在本教學課程中，您可以使用 應用程式集區中 Microsoft Internet Information Services (IIS) 來處理協調流程，您將發佈為 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-103">In this tutorial, you use an application pool in Microsoft Internet Information Services (IIS) to process the orchestration, which you publish as a Web service.</span></span> <span data-ttu-id="a0bc1-104">應用程式集區是由背景工作處理序的一或多個 Url 群組。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-104">An application pool is a grouping of one or more URLs served by a worker process.</span></span>  

 <span data-ttu-id="a0bc1-105">應用程式集區的識別是應用程式集區的工作者處理序所執行的服務帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-105">The identity of an application pool is the name of the service account under which the worker process of the application pool runs.</span></span> <span data-ttu-id="a0bc1-106">根據預設，應用程式集區會在 Network Service 使用者帳戶，擁有低層級的使用者存取權限，並不足以執行本教學課程中函式下作業。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-106">By default, application pools operate under the Network Service user account, which has low-level user-access rights and is insufficient for this tutorial to function.</span></span> <span data-ttu-id="a0bc1-107">基於安全性理由，您想要設定給使用者帳戶的應用程式集區識別的絕對最低權限，但在寫入組態資料庫 (也稱為 BizTalk 與 MessageBox 資料庫 (BizTalkMsgBoxDb) 的最低權限管理資料庫或 BizTalkMgmtDb）。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-107">For security reasons, you want to configure the application pool identity to a user account with the absolute minimum permissions, but at least permissions to write to the MessageBox database (BizTalkMsgBoxDb) and Configuration database (also known as the BizTalk Management database, or BizTalkMgmtDb).</span></span>  

### <a name="to-change-the-service-account-under-which-an-application-pool-runs"></a><span data-ttu-id="a0bc1-108">若要變更應用程式集區所執行的服務帳戶</span><span class="sxs-lookup"><span data-stu-id="a0bc1-108">To change the service account under which an application pool runs</span></span>  

1. <span data-ttu-id="a0bc1-109">按一下 **開始**，指向**程式**，指向**系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="a0bc1-109">Click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  

2. <span data-ttu-id="a0bc1-110">在 [Internet Information Services (IIS) 管理員] 中，展開 [本機電腦]，然後展開**應用程式集區**。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-110">In Internet Information Services (IIS) Manager, expand the local computer, and expand **Application Pools**.</span></span>  

3. <span data-ttu-id="a0bc1-111">以滑鼠右鍵按一下您想要設定應用程式集區 (根據預設，本教學課程中會執行**DefaultAppPool**)，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-111">Right-click the application pool you want to configure (by default, this tutorial runs under the **DefaultAppPool**), and then click **Properties**.</span></span>  

4. <span data-ttu-id="a0bc1-112">在 [Defaultapppool] 對話方塊中，在**識別**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a0bc1-112">In the DefaultAppPool Properties dialog box, on the **Identity** tab, do the following:</span></span>  


   |     <span data-ttu-id="a0bc1-113">使用</span><span class="sxs-lookup"><span data-stu-id="a0bc1-113">Use this</span></span>     |                                                                                                                                                                                                                                                                     <span data-ttu-id="a0bc1-114">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="a0bc1-114">To do this</span></span>                                                                                                                                                                                                                                                                      |
   |------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |  <span data-ttu-id="a0bc1-115">**預先定義的**</span><span class="sxs-lookup"><span data-stu-id="a0bc1-115">**Predefined**</span></span>  | <span data-ttu-id="a0bc1-116">取消選取**預先定義的**。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-116">Deselect **Predefined**.</span></span> <span data-ttu-id="a0bc1-117">**預先定義的**指的是標準的服務帳戶，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a0bc1-117">**Predefined** refers to standard service accounts, such as the following:</span></span><br /><br /> <span data-ttu-id="a0bc1-118">-   **網路服務**（預設值），其中包含可用來在遠端電腦上的資源的存取權的低層級的使用者存取權限。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-118">-   **Network Service** (the default), which has low-level user access rights that can be used for access to resources on remote computers.</span></span><br /><span data-ttu-id="a0bc1-119">-   **本機服務**，其具有低層級的存取權限。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-119">-   **Local Service**, which has low-level access rights.</span></span> <span data-ttu-id="a0bc1-120">您不需要在遠端電腦上的資源的存取權的情況下使用此設定。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-120">You use this setting for situations that do not require access to resources on remote computers.</span></span><br /><span data-ttu-id="a0bc1-121">-   **本機系統**，這是具有多個與 Network Service 或 Local Service 帳戶的使用者權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-121">-   **Local System**, which is an account with more user rights than the Network Service or Local Service account.</span></span> |
   | <span data-ttu-id="a0bc1-122">**可設定**</span><span class="sxs-lookup"><span data-stu-id="a0bc1-122">**Configurable**</span></span> |                                                                                                                                                                                                                                     <span data-ttu-id="a0bc1-123">選取 **可設定**。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-123">Select **Configurable**.</span></span> <span data-ttu-id="a0bc1-124">**可設定**指的是已註冊的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-124">**Configurable** refers to registered user names.</span></span>                                                                                                                                                                                                                                      |
   |  <span data-ttu-id="a0bc1-125">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="a0bc1-125">**User name**</span></span>   |                                                                                                                                                                                                                                <span data-ttu-id="a0bc1-126">輸入想要操作的工作者處理序帳戶的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-126">Type the user name of the account under which you want the worker process to operate.</span></span>                                                                                                                                                                                                                                |
   |   <span data-ttu-id="a0bc1-127">**密碼**</span><span class="sxs-lookup"><span data-stu-id="a0bc1-127">**Password**</span></span>   |                                                                                                                                                                                                                                                                 <span data-ttu-id="a0bc1-128">輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-128">Type the password.</span></span>                                                                                                                                                                                                                                                                  |


5. <span data-ttu-id="a0bc1-129">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-129">Click **OK**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="a0bc1-130">或者，為了提高安全性，您可以建立全新的應用程式集區會在您建立專供本教學課程中的權限的自訂身分識別下執行。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-130">Alternatively, for increased security, you could create an entirely new application pool that runs under a custom identity that you create with permissions tailored for this tutorial.</span></span>  

   <span data-ttu-id="a0bc1-131">請繼續進行[步驟 2： 建立新的專案](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md)。</span><span class="sxs-lookup"><span data-stu-id="a0bc1-131">Proceed to [Step 2: Create a New Project](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="a0bc1-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0bc1-132">See Also</span></span>  
 [<span data-ttu-id="a0bc1-133">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="a0bc1-133">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)