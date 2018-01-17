---
title: "如何更新對應，使用並行的版本設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b0e377f-92ab-483e-9f3c-222c7b5ac0b1
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d463823a7038e1ead7e2de323da97eda372db76
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-update-a-map-using-side-by-side-versioning"></a><span data-ttu-id="f0e58-102">如何更新對應，使用-並存版本控制</span><span class="sxs-lookup"><span data-stu-id="f0e58-102">How to Update a Map Using Side-by-Side Versioning</span></span>
<span data-ttu-id="f0e58-103">某些 BizTalk 成品，例如對應，選擇完整強式名稱 (FQSN)，在這種情況下的繫結包括使用的版本。</span><span class="sxs-lookup"><span data-stu-id="f0e58-103">Some BizTalk artifacts, such as maps, are chosen by fully-qualified strong name (FQSN), in which case the bindings include the version used.</span></span> <span data-ttu-id="f0e58-104">這可讓以並存方式，並排在兩個或多個對應[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f0e58-104">This allows two or more maps to coexist side by side in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="f0e58-105">如此一來，您可以選取其中一個輸入中的接收位置屬性的對應或輸出對應的對應中的傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="f0e58-105">As a result, you can select one of the maps for inbound mapping in the receive location properties or outbound mapping in the send port properties.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f0e58-106">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="f0e58-106">Prerequisites</span></span>  
 <span data-ttu-id="f0e58-107">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="f0e58-107">To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-add-a-second-map-side-by-side-to-an-existing-map"></a><span data-ttu-id="f0e58-108">將第二個對應以並排方式加入至現有的對應</span><span class="sxs-lookup"><span data-stu-id="f0e58-108">To add a second map side by side to an existing map</span></span>  
  
1.  <span data-ttu-id="f0e58-109">開啟 Visual Studio 中，及包含對應的專案。</span><span class="sxs-lookup"><span data-stu-id="f0e58-109">Open Visual Studio, and then open the project containing the map.</span></span>  
  
2.  <span data-ttu-id="f0e58-110">開啟對應的組件，並進行程式碼變更的對應。</span><span class="sxs-lookup"><span data-stu-id="f0e58-110">Open the map in the assembly, and make a code change to the map.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f0e58-111">如果您從協調流程，呼叫地圖和地圖參考是硬式編碼，您可能需要變更協調流程本身的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f0e58-111">If you call a map from an orchestration, and the map reference is hard-coded, you may need to make code changes to the orchestration itself.</span></span>  
  
3.  <span data-ttu-id="f0e58-112">變更組件的版本號碼：</span><span class="sxs-lookup"><span data-stu-id="f0e58-112">Change the version number of the assembly:</span></span>  
  
    1.  <span data-ttu-id="f0e58-113">在 [方案總管] 中，以滑鼠右鍵按一下 BizTalk 專案，然後**屬性**。</span><span class="sxs-lookup"><span data-stu-id="f0e58-113">In Solution Explorer, right-click the BizTalk project, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="f0e58-114">在**專案設計工具**，按一下 [**應用程式**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f0e58-114">In the **Project Designer**, click the **Application** tab.</span></span>  
  
    3.  <span data-ttu-id="f0e58-115">在右窗格中，按一下 **組件資訊**。</span><span class="sxs-lookup"><span data-stu-id="f0e58-115">In the right pane, click **Assembly Information**.</span></span>  
  
    4.  <span data-ttu-id="f0e58-116">在**組件資訊**對話方塊方塊中，指定的值**組件版本**欄位來變更組件版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f0e58-116">In the **Assembly Information** dialog box, specify values for the **Assembly Version** field to change the assembly version number.</span></span> <span data-ttu-id="f0e58-117">您應該變更只有主要或次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f0e58-117">You should change only the major or minor version number.</span></span> <span data-ttu-id="f0e58-118">主要版本號碼是序列中的第一個數字 (***n***.0.0.0); 的次要版本號碼是序列中的第二位數 (0。***n*** .0.0)。</span><span class="sxs-lookup"><span data-stu-id="f0e58-118">The major version number is the first digit in the sequence (***n***.0.0.0); the minor version number is the second digit in the sequence (0.***n***.0.0).</span></span>  
  
    5.  <span data-ttu-id="f0e58-119">按一下  **確定** 關閉 **組件資訊** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f0e58-119">Click **OK** to close the **Assembly Information** dialog box.</span></span>  
  
4.  <span data-ttu-id="f0e58-120">編譯組件。</span><span class="sxs-lookup"><span data-stu-id="f0e58-120">Compile the assembly.</span></span>  
  
5.  <span data-ttu-id="f0e58-121">將組件部署到群組 （和所有的電腦）。</span><span class="sxs-lookup"><span data-stu-id="f0e58-121">Deploy the assembly to the group (and all computers).</span></span>  
  
## <a name="modifying-a-map-to-reflect-updated-version-numbers"></a><span data-ttu-id="f0e58-122">修改對應，以反映更新的版本號碼</span><span class="sxs-lookup"><span data-stu-id="f0e58-122">Modifying a Map to Reflect Updated Version Numbers</span></span>  
 <span data-ttu-id="f0e58-123">.NET 組件可以叫用從對應中使用指令碼處理運算質。</span><span class="sxs-lookup"><span data-stu-id="f0e58-123">.NET assemblies can be invoked from within a map by using the Scripting functoid.</span></span> <span data-ttu-id="f0e58-124">這個方法可以提供很大的彈性，允許開發人員解決許多不同的自訂對應問題。</span><span class="sxs-lookup"><span data-stu-id="f0e58-124">This provides a great deal of flexibility and enables the developer to solve many different custom mapping problems.</span></span> <span data-ttu-id="f0e58-125">它也給對應賦予獨特的限制，就是它不只必須從內部參考組件類型名稱，同時也必須從內部參考所叫用的完整組件版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f0e58-125">It also imposes a unique constraint on the map—it must internally reference not only the assembly type name but also the full assembly version number being invoked.</span></span> <span data-ttu-id="f0e58-126">如此一來，如果對應所呼叫的組件版本號碼變更了，所有參考該組件的連結也會一併中斷。</span><span class="sxs-lookup"><span data-stu-id="f0e58-126">As a consequence, if the version number of the assembly called by the map changes, all of the links that reference the assembly will break.</span></span>  
  
 <span data-ttu-id="f0e58-127">若要避免這個問題，我們建議如果需要從對應呼叫組件，來容納只對應功能，而這個組件的組件版本號碼固定建立特定的組件。</span><span class="sxs-lookup"><span data-stu-id="f0e58-127">To avoid this issue we recommend that if assemblies are required to be called from a map, a specific assembly is created to hold only map functionality and that the assembly version number of this assembly is fixed.</span></span> <span data-ttu-id="f0e58-128">採用這個方法可讓您在更新其他 helper 函式的組件版本時，維持對應的關係。</span><span class="sxs-lookup"><span data-stu-id="f0e58-128">In this way, other helper functions can have the assembly version updated without breaking the maps.</span></span>  
  
 <span data-ttu-id="f0e58-129">如果對應所參考的組件在對應開發後產生變更，則考慮在「對應編輯器」外更新對應檔來反映更新過的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f0e58-129">If an assembly referenced from a map is changed after map development then consider updating the map file outside of the Map Editor to reflect the updated version numbers.</span></span>  
  
#### <a name="to-modify-a-map-file-to-reflect-updated-version-numbers"></a><span data-ttu-id="f0e58-130">若要修改對應檔，以反映更新的版本號碼</span><span class="sxs-lookup"><span data-stu-id="f0e58-130">To modify a map file to reflect updated version numbers</span></span>  
  
1.  <span data-ttu-id="f0e58-131">使用**啟動**功能表中，開啟**記事本**。</span><span class="sxs-lookup"><span data-stu-id="f0e58-131">Using the **Start** menu, open **Notepad**.</span></span>  
  
2.  <span data-ttu-id="f0e58-132">在**記事本**上**檔案**功能表上，按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="f0e58-132">In **Notepad**, on the **File** menu, click **Open**.</span></span> <span data-ttu-id="f0e58-133">在 **開啟** 對話方塊中，選取對應檔您想来修改，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="f0e58-133">In the **Open** dialog box, select the map file you want to modify, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="f0e58-134">在 [編輯] 功能表上，按一下 [尋找]。</span><span class="sxs-lookup"><span data-stu-id="f0e58-134">On the **Edit** menu, click **Find**.</span></span> <span data-ttu-id="f0e58-135">在 **尋找** ] 對話方塊中，輸入 **組件 =**, ，然後按一下 [ **尋找下一個**。</span><span class="sxs-lookup"><span data-stu-id="f0e58-135">In the **Find** dialog box, enter **Assembly=**, and then click **Find Next**.</span></span>  
  
4.  <span data-ttu-id="f0e58-136">如果某個外部組件含有指令碼參考的話，則「記事本」應該會找到如下列所示的 XML 項目：</span><span class="sxs-lookup"><span data-stu-id="f0e58-136">If there is a script reference to an external assembly, Notepad should find an XML element like the following:</span></span>  
  
    ```  
    <Script Language="ExternalAssembly" Assembly="Contoso.Scripts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=  
    <token>  
    " Class="Contoso.Scripts" Function="CalculateValue" AssemblyPath="Contoso.Scripts.dll"/>  
    ```  
  
5.  <span data-ttu-id="f0e58-137">更新版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f0e58-137">Update the version number.</span></span> <span data-ttu-id="f0e58-138">如果有多個執行個體，請使用 **取代** 上 **編輯** 功能表。</span><span class="sxs-lookup"><span data-stu-id="f0e58-138">If there are multiple instances, use **Replace** on the **Edit** menu.</span></span>  
  
6.  <span data-ttu-id="f0e58-139">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="f0e58-139">Save the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f0e58-140">現在您可以使用「對應編輯器」來開啟對應了。</span><span class="sxs-lookup"><span data-stu-id="f0e58-140">You can now open the map using the Map Editor.</span></span>