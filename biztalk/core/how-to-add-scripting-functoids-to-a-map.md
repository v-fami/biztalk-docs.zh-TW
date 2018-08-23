---
title: 如何新增指令碼處理運算質至對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.mapper.functiod.script
ms.assetid: eb96814a-b3fb-48f6-a947-ab595a270faa
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e983564b448ef27323879c6db15ccc232d032d8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019136"
---
# <a name="how-to-add-scripting-functoids-to-a-map"></a><span data-ttu-id="cef63-102">如何新增指令碼處理運算質至對應</span><span class="sxs-lookup"><span data-stu-id="cef63-102">How to Add Scripting Functoids to a Map</span></span>
<span data-ttu-id="cef63-103">**指令碼處理**運算質可讓您使用自訂指令碼或程式碼在執行階段來執行無法使用的功能。</span><span class="sxs-lookup"><span data-stu-id="cef63-103">The **Scripting** functoid enables you to use custom script or code at run time to perform functions otherwise not available.</span></span> <span data-ttu-id="cef63-104">例如，您可以在執行階段呼叫 COM 物件使用**指令碼處理**運算質和撰寫您自己自訂的指令碼。</span><span class="sxs-lookup"><span data-stu-id="cef63-104">For example, you can call a COM object at run time by using the **Scripting** functoid and writing your own custom script.</span></span>  
  
 <span data-ttu-id="cef63-105">如需概念性資訊**Scripting**運算質，請參閱[指令碼處理運算質](../core/scripting-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="cef63-105">For conceptual information about the **Scripting** functoid, see [Scripting Functoid](../core/scripting-functoid.md).</span></span>  
  
### <a name="to-add-the-scripting-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="cef63-106">新增指令碼處理運算質至對應並設定</span><span class="sxs-lookup"><span data-stu-id="cef63-106">To add the Scripting functoid to a map and configure it</span></span>  
  
1. <span data-ttu-id="cef63-107">具有[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)][工具箱]，按一下 **進階運算質**来選取該運算質類別索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cef63-107">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
    <span data-ttu-id="cef63-108">顯示所選類別中的進階運算質清單。</span><span class="sxs-lookup"><span data-stu-id="cef63-108">The list of advanced functoids in the chosen category appears.</span></span>  
  
2. <span data-ttu-id="cef63-109">拖曳**Scripting**運算質![](../core/media/bts-tls-scripting.gif "bts_tls_scripting")從工具箱拖曳至格線頁上的適當位置。</span><span class="sxs-lookup"><span data-stu-id="cef63-109">Drag the **Scripting** functoid ![](../core/media/bts-tls-scripting.gif "bts_tls_scripting") from the Toolbox to the appropriate location on a grid page.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="cef63-110">運算質將放置在顯示的格線頁上。</span><span class="sxs-lookup"><span data-stu-id="cef63-110">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="cef63-111">若要將運算質放在其他格線頁上，必須先顯示該格線頁。</span><span class="sxs-lookup"><span data-stu-id="cef63-111">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="cef63-112">若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。</span><span class="sxs-lookup"><span data-stu-id="cef63-112">If you are constructing a map using more than one functoid together, you need to consider their relative left-to-right placement.</span></span> <span data-ttu-id="cef63-113">運算質是由左至右執行。</span><span class="sxs-lookup"><span data-stu-id="cef63-113">Functoids are executed from left to right.</span></span> <span data-ttu-id="cef63-114">某個運算質的輸出，只能是其較右邊另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="cef63-114">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3. <span data-ttu-id="cef63-115">選取 **指令碼處理**您剛新增至顯示的格線頁的運算質。</span><span class="sxs-lookup"><span data-stu-id="cef63-115">Select the **Scripting** functoid that you just added to the displayed grid page.</span></span>  
  
4. <span data-ttu-id="cef63-116">在 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性] 視窗中，按一下省略符號 (**...**) 按鈕相關聯**指令碼**屬性。</span><span class="sxs-lookup"><span data-stu-id="cef63-116">In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, click the ellipsis (**...**) button associated with the **Script** property.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="cef63-117">或者，您可以在此運算質，以滑鼠右鍵按一下，然後按一下**設定運算質指令碼**操作功能表中。</span><span class="sxs-lookup"><span data-stu-id="cef63-117">Alternatively, you can right-click the functoid, and then click **Configure Functoid Script** in the context menu.</span></span> <span data-ttu-id="cef63-118">**設定指令碼處理運算質**對話方塊會顯示**指令碼運算質組態**選取的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cef63-118">The **Configure Scripting Functoid** dialog box appears with the **Script Functoid Configuration** tab selected.</span></span>  
  
5. <span data-ttu-id="cef63-119">在 **設定指令碼處理運算質**對話方塊的 **選取指令碼類型**下拉式清單中，選取您的指令碼的類型。</span><span class="sxs-lookup"><span data-stu-id="cef63-119">In the **Configure Scripting Functoid** dialog box, in the **Select script type** drop-down list, select the type of your script.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="cef63-120">視您所選的指令碼類型而定，將會啟用和停用其餘對話方塊欄位的不同子集。</span><span class="sxs-lookup"><span data-stu-id="cef63-120">Depending on your selection of script type, different subsets of the remaining dialog box fields will be enabled and disabled.</span></span>  
  
6. <span data-ttu-id="cef63-121">如果您選取**外部組件**做為指令碼類型，使用**指令碼組件**，**指令碼類別**，以及**指令碼方法**下拉式清單清單中的，依序選取組件、 類別和方法，分別將與這個**指令碼處理**運算質。</span><span class="sxs-lookup"><span data-stu-id="cef63-121">If you selected **External Assembly** as the script type, use the **Script assembly**, **Script class**, and **Script method** drop-down lists, in that order, to select the assembly, class, and method, respectively, to associate with this **Scripting** functoid.</span></span>  
  
   > [!WARNING]
   >  <span data-ttu-id="cef63-122">外部組件中的程式碼必須是安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="cef63-122">The code in the external assembly must be thread-safe.</span></span> <span data-ttu-id="cef63-123">在負荷條件下，對應的多個執行個體可能會同時執行。</span><span class="sxs-lookup"><span data-stu-id="cef63-123">Under stress conditions, multiple instances of a map may be running concurrently.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="cef63-124">選取組件之後,**指令碼類別**下拉式清單將填入該組件中的類別。</span><span class="sxs-lookup"><span data-stu-id="cef63-124">After you have selected an assembly, the **Script class** drop-down list will be populated with the classes in that assembly.</span></span> <span data-ttu-id="cef63-125">同樣地，之後您已選取類別**指令碼方法**下拉式清單將填入該類別中的方法。</span><span class="sxs-lookup"><span data-stu-id="cef63-125">Likewise, after you have selected a class, the **Script method** drop-down list will be populated with the methods in that class.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="cef63-126">**內嵌指令碼**文字方塊中已停用，當您選取**外部組件**的指令碼類型。</span><span class="sxs-lookup"><span data-stu-id="cef63-126">The **Inline script** text box is disabled when you select **External Assembly** as the script type.</span></span>  
  
    <span data-ttu-id="cef63-127">如果您選取的項目以外**外部組件**做為指令碼類型 （其中一個內嵌選擇），使用**內嵌指令碼**文字方塊中輸入您的指令碼中您選取的語言。</span><span class="sxs-lookup"><span data-stu-id="cef63-127">If you selected something other than **External Assembly** as the script type (one of the inline choices), use the **Inline script** text box to enter your script in the language you selected.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="cef63-128">內嵌語言選擇**指令碼處理**運算質包含 C#.NET、 jscript.net、 Visual Basic.NET、 XSLT 和 XSLT 呼叫範本。</span><span class="sxs-lookup"><span data-stu-id="cef63-128">The inline language choices for the **Scripting** functoid include C# .NET, JScript.NET, Visual Basic .NET, XSLT, and XSLT Call Template.</span></span>  
  
    <span data-ttu-id="cef63-129">使用 C# 的指令碼不允許 "using" 陳述式。</span><span class="sxs-lookup"><span data-stu-id="cef63-129">Scripting using C# does not allow "using" statements.</span></span> <span data-ttu-id="cef63-130">如果指令碼需要使用任何特殊 .Net 類別，則您應該將對應的組件及其相依組件新增至 BizTalk 專案的 [參考]，且指令碼應該使用完整名稱。</span><span class="sxs-lookup"><span data-stu-id="cef63-130">If the script needs to use any special .Net classes, then the corresponding assemblies and their dependent assemblies should be added to "References" in the BizTalk project, and the script code should use fully qualified names.</span></span> <span data-ttu-id="cef63-131">如果您撰寫指令碼來執行區分文化特性的小寫轉換，應該撰寫如下的對應程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="cef63-131">If you write a script to perform culture-sensitive lowercase conversion, the corresponding code fragment should be written as below.</span></span> <span data-ttu-id="cef63-132">所有支援的指令碼語言都受到類似的限制。</span><span class="sxs-lookup"><span data-stu-id="cef63-132">Similar limitations apply to all supported scripting languages.</span></span>  
  
   ```  
   string x = y.ToLower(System.Globalization.CultureInfo.CurrentCulture);  
   ```  
  
    <span data-ttu-id="cef63-133">在指令碼中，若要使用任何組件中的類別，請確定您將對應的組件及其相依組件新增至您的對應所在之 BizTalk 專案中的 [參考]。</span><span class="sxs-lookup"><span data-stu-id="cef63-133">In the script, to use classes from any assembly, ensure you add the corresponding assembly and its dependent assemblies to “References” in the BizTalk project containing your map.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="cef63-134">您可以建立自訂指令碼中直接**內嵌指令碼**文字方塊中，或者您可以建立您的指令碼中其他位置，並將它貼到**內嵌指令碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="cef63-134">You can create your custom script directly in the **Inline script** text box, or you can create your script elsewhere, and paste it into the **Inline script** text box.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="cef63-135">**指令碼組件**，**指令碼類別**，並**指令碼方法**下拉式清單會停用，當您選取其中一個內嵌選擇 (項目以外**外部組件**) 的指令碼類型。</span><span class="sxs-lookup"><span data-stu-id="cef63-135">The **Script assembly**, **Script class**, and **Script method** drop-down lists are disabled when you select one of the inline choices (something other than **External Assembly**) as the script type.</span></span>  
  
   > [!IMPORTANT]
   >  <span data-ttu-id="cef63-136">若您建立包含多個函式的指令碼，則第一個函式將被視為主要函式；只有在執行主要函式時，才會呼叫其他函式。</span><span class="sxs-lookup"><span data-stu-id="cef63-136">If you create a script containing multiple functions, the first function will be treated as the main or primary function; other functions are only called if they are called in the execution of the primary function.</span></span>  
  
    <span data-ttu-id="cef63-137">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="cef63-137">Click **OK**.</span></span>  
  
7. <span data-ttu-id="cef63-138">若外部組件中的指令碼或關聯的方法需要輸入參數，則如同您建立基本運算質一樣地建立適當的輸入連結數目與類型。</span><span class="sxs-lookup"><span data-stu-id="cef63-138">If your script or the associated method in an external assembly requires input parameters, create the appropriate number and type of input links as you would for a basic functoid.</span></span>  
  
8. <span data-ttu-id="cef63-139">在大部分情況下，您**指令碼處理**運算質將產生輸出值，用於填入目的結構描述中的欄位，或做為另一個運算質的輸入，在大部分相同方式基本運算質執行。</span><span class="sxs-lookup"><span data-stu-id="cef63-139">In most circumstances, your **Scripting** functoid will produce an output value used to populate a field in the destination schema, or as input to another functoid, in much the same way that basic functoids do.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cef63-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cef63-140">See Also</span></span>  
 [<span data-ttu-id="cef63-141">將進階運算質新增至對應</span><span class="sxs-lookup"><span data-stu-id="cef63-141">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)