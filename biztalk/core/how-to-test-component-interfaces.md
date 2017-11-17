---
title: "如何測試元件介面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing component interfaces
- component interfaces, testing
ms.assetid: d637f76d-170d-4543-a2b2-a4ac4001386b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be50521e5c4421d8ac8902bcf7a414d734c3b9f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-test-component-interfaces"></a><span data-ttu-id="dfcb5-102">如何測試元件介面</span><span class="sxs-lookup"><span data-stu-id="dfcb5-102">How to Test Component Interfaces</span></span>
<span data-ttu-id="dfcb5-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise 使用 PeopleSoft 中繼資料和元件介面；因此，它可以處理新的或已修改的元件介面。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise uses PeopleSoft metadata and component interfaces; therefore, it can handle new or modified component interfaces.</span></span> <span data-ttu-id="dfcb5-104">配接器對元件介面不做任何限制性規定，但是除了元件介面必須符合邏輯且有效。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-104">The adapter makes no assumptions about component interfaces except that they are logical and valid.</span></span> <span data-ttu-id="dfcb5-105">因此，每個元件介面做為配接器的來源之前，都必須先進行測試。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-105">Therefore, each component interface must be tested before it is used as a source for the adapter.</span></span>  
  
 <span data-ttu-id="dfcb5-106">如果因使用者或 PeopleSoft 升級而使得基礎應用程式發生變更，同時這些變更造成元件介面失效，這時使用者必須修復無效的元件介面，才能提供配接器使用。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-106">If changes are made to the underlying application by the user or by a PeopleSoft upgrade, and the changes invalidate a component interface, the user must repair the invalid component interface before the adapter uses it.</span></span>  
  
### <a name="to-test-a-component-interface"></a><span data-ttu-id="dfcb5-107">若要測試元件介面</span><span class="sxs-lookup"><span data-stu-id="dfcb5-107">To test a component interface</span></span>  
  
1.  <span data-ttu-id="dfcb5-108">在 應用程式設計工具上**工具**功能表上，按一下  **Test Component Interface**。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-108">In Application Designer, on the **Tools** menu, click **Test Component Interface**.</span></span>  
  
     ![](../core/media/psadapter-54-ps-testcompinterface1.gif "PSAdapter_54_PS_TestCompInterface1")  
  
2.  <span data-ttu-id="dfcb5-109">在**Component Interface Tester**對話方塊方塊中，使用下列方法測試元件介面。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-109">In the **Component Interface Tester** dialog box, test the component interface by using one the following methods.</span></span> <span data-ttu-id="dfcb5-110">完成變更之後，以滑鼠右鍵按一下窗格中最上方的項目。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-110">After you finish making changes, right-click the top item in the pane.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dfcb5-111">若有必要，請按一下該對話方塊使其顯示於前景。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-111">If required, click the dialog box to bring it to the foreground.</span></span>  
  
    -   <span data-ttu-id="dfcb5-112">若要測試元件介面使用 Find 方法，請按一下**尋找**。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-112">To test the component interface using the Find method, click **Find**.</span></span>  
  
         <span data-ttu-id="dfcb5-113">**Component Interface Tester-尋找結果** 對話方塊隨即開啟，顯示基礎元件的所有可能的項目。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-113">The **Component Interface Tester - Find Results** dialog box opens, displaying all the possible entries for the underlying component.</span></span> <span data-ttu-id="dfcb5-114">如果有超過 300 個項目，則會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-114">If there are more than 300 entries, a message appears.</span></span>  
  
         <span data-ttu-id="dfcb5-115">a.</span><span class="sxs-lookup"><span data-stu-id="dfcb5-115">a.</span></span> <span data-ttu-id="dfcb5-116">在左窗格中**尋找結果**對話方塊中，選取一個欄位。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-116">In the left pane of the **Find Results** dialog box, select a field.</span></span>  
  
         <span data-ttu-id="dfcb5-117">b.</span><span class="sxs-lookup"><span data-stu-id="dfcb5-117">b.</span></span> <span data-ttu-id="dfcb5-118">若要顯示該特定欄位的相關資料，請按一下**Get Selected**。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-118">To display the relevant data for that particular field, click **Get Selected**.</span></span>  
  
         <span data-ttu-id="dfcb5-119">下列畫面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-119">The following screen appears.</span></span>  
  
         ![](../core/media/psadapter-55-ps-testcompinterface2.gif "PSAdapter_55_PS_TestCompInterface2")  
  
         <span data-ttu-id="dfcb5-120">如果安全性設定允許的話，您可以變更個別欄位中的值。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-120">If the security settings allow, you can change the values in the individual fields.</span></span>  
  
         <span data-ttu-id="dfcb5-121">下列對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-121">The following dialog box opens.</span></span>  
  
         ![](../core/media/psadapter-56-ps-testcompinterface3.gif "PSAdapter_56_PS_TestCompInterface3")  
  
    -   <span data-ttu-id="dfcb5-122">若要使用 `Get` 方法測試元件介面：</span><span class="sxs-lookup"><span data-stu-id="dfcb5-122">To test the component interface using the `Get` method:</span></span>  
  
         <span data-ttu-id="dfcb5-123">a.</span><span class="sxs-lookup"><span data-stu-id="dfcb5-123">a.</span></span> <span data-ttu-id="dfcb5-124">輸入現有金鑰。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-124">Enter the existing key(s).</span></span>  
  
         <span data-ttu-id="dfcb5-125">b.</span><span class="sxs-lookup"><span data-stu-id="dfcb5-125">b.</span></span> <span data-ttu-id="dfcb5-126">按一下**取得現有**。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-126">Click **Get Existing**.</span></span>  
  
         <span data-ttu-id="dfcb5-127">這會傳回所輸入金鑰的已公開屬性。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-127">This returns the exposed properties for the key that you entered.</span></span>  
  
         <span data-ttu-id="dfcb5-128">您可以變更值，如果**更新存取**指定。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-128">You can change values if **Update access** was specified.</span></span>  
  
         <span data-ttu-id="dfcb5-129">或者，您可以使用 `Create` 方法進行測試。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-129">Alternatively, you can test using the `Create` method.</span></span>  
  
         ![](../core/media/psadapter-57-ps-testcompinterface4.gif "PSAdapter_57_PS_TestCompInterface4")  
  
    -   <span data-ttu-id="dfcb5-130">若要使用 `Create` 方法測試元件介面：</span><span class="sxs-lookup"><span data-stu-id="dfcb5-130">To test the component interface using the `Create` method:</span></span>  
  
         <span data-ttu-id="dfcb5-131">a.</span><span class="sxs-lookup"><span data-stu-id="dfcb5-131">a.</span></span> <span data-ttu-id="dfcb5-132">輸入所有必要的金鑰值。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-132">Enter all required key values.</span></span>  
  
         <span data-ttu-id="dfcb5-133">b.</span><span class="sxs-lookup"><span data-stu-id="dfcb5-133">b.</span></span> <span data-ttu-id="dfcb5-134">按一下**建立新**。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-134">Click **Create New**.</span></span>  
  
         <span data-ttu-id="dfcb5-135">當您輸入有效的值**建立金鑰**，顯示 JOBCODE 資料 窗格會開啟預設的資料，就地展開資料表名稱之後。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-135">When you enter valid values in **Create keys**, a pane that displays the JOBCODE data opens after the Table name is expanded with default data in place.</span></span>  
  
         <span data-ttu-id="dfcb5-136">現在您可以變更欄位。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-136">You can change fields now.</span></span>  
  
         ![](../core/media/psadapter-58-ps-testcompinterface5.gif "PSAdapter_58_PS_TestCompInterface5")  
  
         <span data-ttu-id="dfcb5-137">此作業會針對元件的基礎商務邏輯來驗證變更。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-137">Changes are validated against the component's underlying business logic.</span></span>  
  
3.  <span data-ttu-id="dfcb5-138">若要儲存您的變更，請按一下**儲存**圖示。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-138">To save your changes, click the **Save** icon.</span></span>  
  
     <span data-ttu-id="dfcb5-139">用來建立記錄的金鑰可以與 Get 方法搭配使用，以檢視資料。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-139">The keys used to create the record can be used with the Get method for viewing data.</span></span> <span data-ttu-id="dfcb5-140">所加入的資料可從 PeopleSoft 元件進行檢視，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-140">The data that was added can be viewed in the PeopleSoft Component as shown in the following example.</span></span>  
  
     ![](../core/media/psadapter-59-ps-testcompinterface6.gif "PSAdapter_59_PS_TestCompInterface6")  
  
     <span data-ttu-id="dfcb5-141">**生效日期**是其中一個預設值。</span><span class="sxs-lookup"><span data-stu-id="dfcb5-141">**Effective Date** is one of the default values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfcb5-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfcb5-142">See Also</span></span>  
 <span data-ttu-id="dfcb5-143">[附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md) </span><span class="sxs-lookup"><span data-stu-id="dfcb5-143">[Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md) </span></span>  
 [<span data-ttu-id="dfcb5-144">附錄 c： 使用元件介面</span><span class="sxs-lookup"><span data-stu-id="dfcb5-144">Appendix C: Using Component Interfaces</span></span>](../core/appendix-c-using-component-interfaces.md)