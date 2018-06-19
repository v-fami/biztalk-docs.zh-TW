---
title: 如何使用對應精靈 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35b96cea-ead7-43de-8411-62d2c7d6620e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6b016eb0599924d4927868b6a19d3b57389e5c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257358"
---
# <a name="how-to-use-the-mapping-wizard"></a><span data-ttu-id="aff67-102">如何使用對應精靈</span><span class="sxs-lookup"><span data-stu-id="aff67-102">How to Use the Mapping Wizard</span></span>
<span data-ttu-id="aff67-103">此版本的「企業單一登入」包含對應精靈，可讓您輕鬆建立分支機構應用程式的對應。</span><span class="sxs-lookup"><span data-stu-id="aff67-103">This version of Enterprise Single Sign-On includes the Mapping Wizard, which allows you to easily create mappings for affiliate applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aff67-104">您只能在 [外部 UserID] 是以 Windows 網域帳戶為基礎時使用對應精靈。</span><span class="sxs-lookup"><span data-stu-id="aff67-104">You can only use the Mapping Wizard if the External UserID is based on the Windows domain account.</span></span>  
  
### <a name="to-start-the-mapping-wizard"></a><span data-ttu-id="aff67-105">啟動對應精靈</span><span class="sxs-lookup"><span data-stu-id="aff67-105">To start the Mapping Wizard</span></span>  
  
1.  <span data-ttu-id="aff67-106">開啟 [企業單一登入]。</span><span class="sxs-lookup"><span data-stu-id="aff67-106">Open Enterprise Single Sign-On.</span></span>  
  
2.  <span data-ttu-id="aff67-107">在 [領域] 窗格中，按一下**分支機構應用程式**。</span><span class="sxs-lookup"><span data-stu-id="aff67-107">In the scope pane, click **Affiliate Applications**.</span></span>  
  
3.  <span data-ttu-id="aff67-108">以滑鼠右鍵按一下適當的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="aff67-108">Right click the appropriate affiliate application.</span></span>  
  
4.  <span data-ttu-id="aff67-109">按一下**建立對應**。</span><span class="sxs-lookup"><span data-stu-id="aff67-109">Click **Create Mappings**.</span></span> <span data-ttu-id="aff67-110">「對應精靈」隨即出現。</span><span class="sxs-lookup"><span data-stu-id="aff67-110">The Mapping Wizard appears.</span></span>  
  
5.  <span data-ttu-id="aff67-111">**歡迎使用對應精靈**</span><span class="sxs-lookup"><span data-stu-id="aff67-111">**Welcome to the Mapping Wizard**</span></span>  
  
    -   <span data-ttu-id="aff67-112">確認這是正確的分支機構應用程式，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="aff67-112">Verify that this is the correct affiliate application, and click **Next**.</span></span>  
  
6.  <span data-ttu-id="aff67-113">**對應檔案選項**頁面</span><span class="sxs-lookup"><span data-stu-id="aff67-113">**Mappings File Option** page</span></span>  
  
    -   <span data-ttu-id="aff67-114">ENTSSO 會透過 XML 檔管理對應。</span><span class="sxs-lookup"><span data-stu-id="aff67-114">ENTSSO manages mappings through an XML file.</span></span> <span data-ttu-id="aff67-115">您可以選擇建立新檔案或使用現有檔案。</span><span class="sxs-lookup"><span data-stu-id="aff67-115">You can choose to create a new file or use an existing one.</span></span>  
  
7.  <span data-ttu-id="aff67-116">**檔案位置**頁面</span><span class="sxs-lookup"><span data-stu-id="aff67-116">**Files Location** page</span></span>  
  
    -   <span data-ttu-id="aff67-117">選取要使用的檔案。</span><span class="sxs-lookup"><span data-stu-id="aff67-117">Select the files to be used.</span></span>  
  
    -   <span data-ttu-id="aff67-118">您必須按一下**驗證**驗證檔案，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="aff67-118">You must click **Validate** to validate the files before proceeding.</span></span> <span data-ttu-id="aff67-119">驗證狀態會顯示在**狀態**視窗。</span><span class="sxs-lookup"><span data-stu-id="aff67-119">The validation status appears in the **Status** window.</span></span>  
  
8.  <span data-ttu-id="aff67-120">**帳戶**頁面</span><span class="sxs-lookup"><span data-stu-id="aff67-120">**Accounts** page</span></span>  
  
    -   <span data-ttu-id="aff67-121">選擇一或多個帳戶，以產生新的對應檔案，並按一下**驗證**。</span><span class="sxs-lookup"><span data-stu-id="aff67-121">Choose one or more accounts to generate the new mappings file, and click **Validate**.</span></span>  
  
9. <span data-ttu-id="aff67-122">**外部使用者名稱**頁面</span><span class="sxs-lookup"><span data-stu-id="aff67-122">**External User Name** page</span></span>  
  
    -   <span data-ttu-id="aff67-123">定義如何從 Windows 使用者帳戶產生外部使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="aff67-123">Define how the external user name is generated from the Windows user account.</span></span> <span data-ttu-id="aff67-124">當您在方塊中選取項目，您可以看到的名稱會出現在**範例**方塊。</span><span class="sxs-lookup"><span data-stu-id="aff67-124">As you make selections in the boxes, you can see how the names will appear in the **Example** box.</span></span>  
  
10. <span data-ttu-id="aff67-125">**產生**頁面</span><span class="sxs-lookup"><span data-stu-id="aff67-125">**Generate** page</span></span>  
  
    -   <span data-ttu-id="aff67-126">按一下**啟動**產生對應檔。</span><span class="sxs-lookup"><span data-stu-id="aff67-126">Click **Start** to generate the mappings file.</span></span> <span data-ttu-id="aff67-127">(在建立對應之前，您將能夠在下一頁檢視或視需要編輯檔案)。結果會顯示在下列三個視窗中。</span><span class="sxs-lookup"><span data-stu-id="aff67-127">(You will have an opportunity on the next page to view or edit the file as necessary before mappings are created.) Results are displayed in the three windows below.</span></span>  
  
    -   <span data-ttu-id="aff67-128">**數目**中選取帳戶的對應是近似值，因為帳戶可能巢狀方式置於 其他帳戶。</span><span class="sxs-lookup"><span data-stu-id="aff67-128">The **Number** of mappings in selected accounts is an approximation, because accounts may be nested in other accounts.</span></span>  
  
    -   <span data-ttu-id="aff67-129">按一下**檢視記錄檔**檢查任何錯誤或警告可能發生的。</span><span class="sxs-lookup"><span data-stu-id="aff67-129">Click **View Log File** to examine any errors or warnings that might have occurred.</span></span>  
  
11. <span data-ttu-id="aff67-130">**選項**頁面</span><span class="sxs-lookup"><span data-stu-id="aff67-130">**Options** page</span></span>  
  
    -   <span data-ttu-id="aff67-131">您的檔案已建立完成。</span><span class="sxs-lookup"><span data-stu-id="aff67-131">Your file has been created.</span></span> <span data-ttu-id="aff67-132">按一下**檢視/編輯對應檔案**視。</span><span class="sxs-lookup"><span data-stu-id="aff67-132">Click **View/Edit Mappings File** if desired.</span></span>  
  
    -   <span data-ttu-id="aff67-133">按一下**啟用對應**如果您想要自動啟用對應。</span><span class="sxs-lookup"><span data-stu-id="aff67-133">Click **Enable mappings** if you want the mappings to be automatically enabled.</span></span> <span data-ttu-id="aff67-134">如果您未按一下此選項，則必須手動啟用對應。</span><span class="sxs-lookup"><span data-stu-id="aff67-134">(If you do not click this, you will have to enable them manually.)</span></span>  
  
    -   <span data-ttu-id="aff67-135">按一下**設定密碼**以自動設定這些對應的密碼。</span><span class="sxs-lookup"><span data-stu-id="aff67-135">Click **Set Password** to automatically set the password for these mappings.</span></span>  
  
12. <span data-ttu-id="aff67-136">**建立**頁面</span><span class="sxs-lookup"><span data-stu-id="aff67-136">**Create** page</span></span>  
  
    -   <span data-ttu-id="aff67-137">建立對應之前, 按一下**檢視對應檔**視。</span><span class="sxs-lookup"><span data-stu-id="aff67-137">Before creating the mappings, click **View Mappings File** if desired.</span></span>  
  
    -   <span data-ttu-id="aff67-138">當您準備好時，按一下 **啟動**執行對應作業。</span><span class="sxs-lookup"><span data-stu-id="aff67-138">When you are ready, click **Start** to perform the mapping operation.</span></span> <span data-ttu-id="aff67-139">您的狀態會在下列三個方塊中顯示。</span><span class="sxs-lookup"><span data-stu-id="aff67-139">Your status is displayed in the three boxes below.</span></span>  
  
    -   <span data-ttu-id="aff67-140">按一下**檢視記錄檔**檢查任何錯誤或警告可能發生的。</span><span class="sxs-lookup"><span data-stu-id="aff67-140">Click **View Log File** to examine any errors or warnings that might have occurred.</span></span>  
  
13. <span data-ttu-id="aff67-141">**完成對應精靈畫面**</span><span class="sxs-lookup"><span data-stu-id="aff67-141">**Completing the Mapping Wizard screen**</span></span>  
  
14. <span data-ttu-id="aff67-142">選取任何需要的選項，然後再按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="aff67-142">Select any options desired, and then click **Finish**.</span></span>