---
title: 新增和移除自訂運算質，從 Visual Studio 工具箱 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 28f798cc-da97-4332-a842-ba87ac7b13b8
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a0ddbab8a116369b6edb39623cd73a16362a3db
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013087"
---
# <a name="adding-and-removing-custom-functoids-from-the-visual-studio-toolbox"></a><span data-ttu-id="028a6-102">新增和移除 Visual Studio 工具箱中的自訂運算質</span><span class="sxs-lookup"><span data-stu-id="028a6-102">Adding and Removing Custom Functoids from the Visual Studio Toolbox</span></span>
<span data-ttu-id="028a6-103">本主題描述如何新增自訂運算質和移除自訂運算質從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱。</span><span class="sxs-lookup"><span data-stu-id="028a6-103">This topic describes how to add custom functoids to and remove custom functoids from the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox.</span></span>  
  
## <a name="adding-custom-functoids-to-visual-studio"></a><span data-ttu-id="028a6-104">新增自訂運算質至 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="028a6-104">Adding Custom Functoids to Visual Studio</span></span>  
 <span data-ttu-id="028a6-105">自訂運算質必須新增至[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱，才能在對應中使用。</span><span class="sxs-lookup"><span data-stu-id="028a6-105">Custom functoids must be added to the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox before they can be used in a map.</span></span> <span data-ttu-id="028a6-106">請使用下列程序新增自訂運算質。</span><span class="sxs-lookup"><span data-stu-id="028a6-106">Use the following procedure to add custom functoids.</span></span>  
  
#### <a name="to-add-a-custom-functoid"></a><span data-ttu-id="028a6-107">新增自訂運算質</span><span class="sxs-lookup"><span data-stu-id="028a6-107">To add a custom functoid</span></span>  
  
1. <span data-ttu-id="028a6-108">新增至運算質[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱。</span><span class="sxs-lookup"><span data-stu-id="028a6-108">Add the functoid to the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox.</span></span>  
  
   1. <span data-ttu-id="028a6-109">使用 [Windows 檔案總管] 找出實作自訂運算質的組件。</span><span class="sxs-lookup"><span data-stu-id="028a6-109">Using Windows Explorer, find the assembly that implements your custom functoids.</span></span>  
  
   2. <span data-ttu-id="028a6-110">若要將組件複製\< *BizTalk Server 安裝資料夾*\>**\Developer Tools\Mapper 延伸**目錄。</span><span class="sxs-lookup"><span data-stu-id="028a6-110">Copy the assembly to the \<*BizTalk Server installation folder*\>**\Developer Tools\Mapper Extensions** directory.</span></span> <span data-ttu-id="028a6-111">BizTalk 對應工具會在此位置尋找自訂運算質。</span><span class="sxs-lookup"><span data-stu-id="028a6-111">This is where BizTalk Mapper looks for custom functoids.</span></span>  
  
   3. <span data-ttu-id="028a6-112">從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，在**工具**功能表上，按一下 **選擇工具箱項目**。</span><span class="sxs-lookup"><span data-stu-id="028a6-112">From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, on the **Tools** menu, click **Choose Toolbox Items**.</span></span>  
  
   4. <span data-ttu-id="028a6-113">在 [ **[選擇工具箱項目**] 對話方塊中，按一下**BizTalk 對應工具運算質**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="028a6-113">In the **Choose Toolbox items** dialog box, click the **BizTalk Mapper Functoids** tab.</span></span>  
  
   5. <span data-ttu-id="028a6-114">按一下 **重設**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="028a6-114">Click **Reset**, and then click **OK**.</span></span> <span data-ttu-id="028a6-115">此程序會花一些時間。</span><span class="sxs-lookup"><span data-stu-id="028a6-115">This process may take a few moments.</span></span>  
  
       <span data-ttu-id="028a6-116">您的自訂運算質現在應該出現在符合其類別之索引標籤下的工具箱中。</span><span class="sxs-lookup"><span data-stu-id="028a6-116">Your custom functoids should now appear in the Toolbox under tabs matching their category.</span></span>  
  
      <span data-ttu-id="028a6-117">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="028a6-117">\- OR -</span></span>  
  
   6. <span data-ttu-id="028a6-118">從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，在**工具**功能表上，按一下 **選擇工具箱項目**。</span><span class="sxs-lookup"><span data-stu-id="028a6-118">From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, on the **Tools** menu, click **Choose Toolbox Items**.</span></span>  
  
   7. <span data-ttu-id="028a6-119">在 [ **[選擇工具箱項目**] 對話方塊中，按一下**BizTalk 對應工具運算質**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="028a6-119">In the **Choose Toolbox items** dialog box, click the **BizTalk Mapper Functoids** tab.</span></span>  
  
   8. <span data-ttu-id="028a6-120">按一下 **重設**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="028a6-120">Click **Reset**, and then click **OK**.</span></span>  
  
      > [!NOTE]
      >  <span data-ttu-id="028a6-121">如果您的自訂運算質未公開任何內嵌程式碼，請確定其組件可在全域組件快取中使用。</span><span class="sxs-lookup"><span data-stu-id="028a6-121">If your custom functoid does not expose any inline code, make sure its assembly is made available in the global assembly cache.</span></span>  
  
   9. <span data-ttu-id="028a6-122">在 **檔案**功能表上，按一下**結束**關閉[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="028a6-122">On the **File** menu, click **Exit** to close [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
   10. <span data-ttu-id="028a6-123">開始**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="028a6-123">Start **Visual Studio Command Prompt**.</span></span>  
  
   11. <span data-ttu-id="028a6-124">在命令提示字元中，輸入**devenv /setup**。</span><span class="sxs-lookup"><span data-stu-id="028a6-124">At the command prompt, type **devenv /setup**.</span></span>  
  
   12. <span data-ttu-id="028a6-125">開始**Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="028a6-125">Start **Microsoft Visual Studio**.</span></span>  
  
        <span data-ttu-id="028a6-126">自訂運算質應該會出現在適當的索引標籤中。</span><span class="sxs-lookup"><span data-stu-id="028a6-126">The custom functoid(s) should appear in the appropriate tab.</span></span>  
  
2. <span data-ttu-id="028a6-127">將組件新增至全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="028a6-127">Add the assembly to the global assembly cache.</span></span> <span data-ttu-id="028a6-128">如果您的組件僅包含內嵌運算質，則可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="028a6-128">If your assembly contains only inline functoids, then you can skip this step.</span></span>  
  
   1.  <span data-ttu-id="028a6-129">開始**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="028a6-129">Start **Visual Studio Command Prompt**.</span></span>  
  
   2.  <span data-ttu-id="028a6-130">切換至包含您組件的資料夾。</span><span class="sxs-lookup"><span data-stu-id="028a6-130">Switch to the folder containing your assembly.</span></span>  
  
   3.  <span data-ttu-id="028a6-131">在命令提示字元中，輸入**gacutil /if < assembly_path >**。</span><span class="sxs-lookup"><span data-stu-id="028a6-131">At the command prompt, type **gacutil /if <assembly_path >**.</span></span> <span data-ttu-id="028a6-132">比方說，如果您的組件名稱為 FunctoidLibrary.dll，則請鍵入**gacutil /if FunctoidLibrary.dll**。</span><span class="sxs-lookup"><span data-stu-id="028a6-132">For example, if your assembly name is FunctoidLibrary.dll, then type **gacutil /if FunctoidLibrary.dll**.</span></span>  
  
   4.  <span data-ttu-id="028a6-133">當您完成時，輸入**結束**。</span><span class="sxs-lookup"><span data-stu-id="028a6-133">When you are finished, type **exit**.</span></span>  
  
## <a name="removing-custom-functoids-from-visual-studio"></a><span data-ttu-id="028a6-134">從 Visual Studio 移除自訂運算質</span><span class="sxs-lookup"><span data-stu-id="028a6-134">Removing Custom Functoids from Visual Studio</span></span>  
 <span data-ttu-id="028a6-135">請使用下列程序移除自訂運算質。</span><span class="sxs-lookup"><span data-stu-id="028a6-135">Use the following procedure to remove custom functoids.</span></span>  
  
#### <a name="to-remove-a-custom-functoid"></a><span data-ttu-id="028a6-136">移除自訂運算質</span><span class="sxs-lookup"><span data-stu-id="028a6-136">To remove a custom functoid</span></span>  
  
1. <span data-ttu-id="028a6-137">移除運算質從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱。</span><span class="sxs-lookup"><span data-stu-id="028a6-137">Remove the functoid from the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox.</span></span>  
  
   1. <span data-ttu-id="028a6-138">從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，在**工具**功能表上，按一下 **選擇工具箱項目**。</span><span class="sxs-lookup"><span data-stu-id="028a6-138">From a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, on the **Tools** menu, click **Choose Toolbox Items**.</span></span>  
  
   2. <span data-ttu-id="028a6-139">在 [ **[選擇工具箱項目**] 對話方塊中，按一下**BizTalk 對應工具運算質**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="028a6-139">In the **Choose Toolbox items** dialog box, click the **BizTalk Mapper Functoids** tab.</span></span>  
  
   3. <span data-ttu-id="028a6-140">尋找自訂運算質，在清單中，選取**移除**核取方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="028a6-140">Find the custom functoid in the list, select the **Remove** check box, and then click **OK**.</span></span>  
  
      <span data-ttu-id="028a6-141">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="028a6-141">\- OR -</span></span>  
  
   4. <span data-ttu-id="028a6-142">編輯在對應時[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，按一下**工具箱** 索引標籤以顯示工具箱工具板。</span><span class="sxs-lookup"><span data-stu-id="028a6-142">While editing a map in a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk project, click the **Toolbox** tab to bring up the Toolbox Palette.</span></span>  
  
   5. <span data-ttu-id="028a6-143">按一下包含您自訂運算質的運算質群組。</span><span class="sxs-lookup"><span data-stu-id="028a6-143">Click the functoid group containing your custom functoid.</span></span>  
  
   6. <span data-ttu-id="028a6-144">以滑鼠右鍵按一下您想要移除此項目，然後按一下 運算的質**刪除**或按下 delete 鍵。</span><span class="sxs-lookup"><span data-stu-id="028a6-144">Right-click the functoid you want to remove, and then click **Delete** or press the delete key.</span></span>  
  
2. <span data-ttu-id="028a6-145">移除的運算質組件**Developer Tools\Mapper Extensions**目錄。</span><span class="sxs-lookup"><span data-stu-id="028a6-145">Remove the functoid assembly from the **Developer Tools\Mapper Extensions** directory.</span></span>  
  
   > [!CAUTION]
   >  <span data-ttu-id="028a6-146">如果組件包含作用中的運算質，請不要移除它。</span><span class="sxs-lookup"><span data-stu-id="028a6-146">If an assembly contains active functoids, then do not remove it.</span></span> <span data-ttu-id="028a6-147">這麼做將會中斷其他對應。</span><span class="sxs-lookup"><span data-stu-id="028a6-147">Doing so will break other maps.</span></span>  
  
   1. <span data-ttu-id="028a6-148">啟動 Windows 檔案總管並瀏覽至**Developer Tools\Mapper Extensions**目錄[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="028a6-148">Start Windows Explorer and navigate to the **Developer Tools\Mapper Extensions** directory of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
   2. <span data-ttu-id="028a6-149">以滑鼠右鍵按一下包含 「 移除 」 運算質的組件，然後按一下**刪除**來移除檔案。</span><span class="sxs-lookup"><span data-stu-id="028a6-149">Right-click the assembly containing the removed functoid, and then click **Delete** to remove the file.</span></span>  
  
3. <span data-ttu-id="028a6-150">從全域組件快取中移除運算質組件。</span><span class="sxs-lookup"><span data-stu-id="028a6-150">Remove the functoid assembly from the global assembly cache.</span></span> <span data-ttu-id="028a6-151">如果您的組件僅包含內嵌運算質，則可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="028a6-151">If your assembly contains only inline functoids, then you can skip this step.</span></span>  
  
   > [!CAUTION]
   >  <span data-ttu-id="028a6-152">如果組件包含作用中的運算質，請不要將它從全域組件快取中移除。</span><span class="sxs-lookup"><span data-stu-id="028a6-152">If an assembly contains active functoids, then do not remove it from the global assembly cache.</span></span> <span data-ttu-id="028a6-153">這麼做將會中斷其他對應。</span><span class="sxs-lookup"><span data-stu-id="028a6-153">Doing so will break other maps.</span></span>  
  
   1.  <span data-ttu-id="028a6-154">開始**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="028a6-154">Start **Visual Studio Command Prompt**.</span></span>  
  
   2.  <span data-ttu-id="028a6-155">在命令提示字元中，輸入**gacutil /u < assembly_display_name >**。</span><span class="sxs-lookup"><span data-stu-id="028a6-155">At the command prompt, type **gacutil /u <assembly_display_name>**.</span></span> <span data-ttu-id="028a6-156">比方說，如果您的組件名稱為 FunctoidLibrary.dll，則請鍵入**gacutil /if FunctoidLibrary**。</span><span class="sxs-lookup"><span data-stu-id="028a6-156">For example, if your assembly name is FunctoidLibrary.dll, then type **gacutil /if FunctoidLibrary**.</span></span>  
  
   3.  <span data-ttu-id="028a6-157">當您完成時，輸入**結束**。</span><span class="sxs-lookup"><span data-stu-id="028a6-157">When you are finished, type **exit**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="028a6-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="028a6-158">See Also</span></span>  
 [<span data-ttu-id="028a6-159">開發自訂運算質</span><span class="sxs-lookup"><span data-stu-id="028a6-159">Developing Custom Functoids</span></span>](../core/developing-custom-functoids.md)