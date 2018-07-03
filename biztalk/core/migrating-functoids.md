---
title: 移轉運算質 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- functoids, migrating
- migrating, maps
- Migrating functoids, about Migrating functoids
- Migrating functoids
- Scripting functoids
- migrating, functoids
- migrating, Scripting functoids
ms.assetid: fc5b3ac9-28c6-41df-b779-15a8c3188528
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b01f37551b9d4c1aef13786be7094504f8cee08
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020500"
---
# <a name="migrating-functoids"></a><span data-ttu-id="10088-102">移轉運算質</span><span class="sxs-lookup"><span data-stu-id="10088-102">Migrating Functoids</span></span>
<span data-ttu-id="10088-103">當您從舊版的 BizTalk Server 移轉對應至 BizTalk Server 時，對應中包含的任何運算質也會移轉。</span><span class="sxs-lookup"><span data-stu-id="10088-103">When you migrate a map from previous versions of BizTalk Server to BizTalk Server, any functoids included in the map are also migrated.</span></span> <span data-ttu-id="10088-104">如果未包含您所移轉的運算質**指令碼處理**運算質，沒有其他移轉工作所需。</span><span class="sxs-lookup"><span data-stu-id="10088-104">If the functoids you migrate do not include **Scripting** functoids, no additional migration tasks are required.</span></span> <span data-ttu-id="10088-105">不過如果您的對應包含**指令碼處理**運算質或自訂運算質，您可能必須執行其他步驟。</span><span class="sxs-lookup"><span data-stu-id="10088-105">However if your map includes **Scripting** functoids or custom functoids, you may have additional steps to perform.</span></span>  
  
 <span data-ttu-id="10088-106">在舊版的 BizTalk Server 中，所有的自訂指令碼隨附**指令碼處理**運算質以內嵌方式撰寫。</span><span class="sxs-lookup"><span data-stu-id="10088-106">In previous versions of BizTalk Server, all custom script included with a **Scripting** functoid was written inline.</span></span> <span data-ttu-id="10088-107">也就是說，當您建立運算質時，運算質在執行階段呼叫的所有指令碼都與運算質一起儲存。</span><span class="sxs-lookup"><span data-stu-id="10088-107">That is, when you created the functoid, all the script the functoid called during run time was stored with the functoid.</span></span> <span data-ttu-id="10088-108">如果您想要使用不同的運算質使用相同的指令碼，您可以複製並貼上它從某個**指令碼處理**到另一個，或者您的運算質重寫指令碼從零開始。</span><span class="sxs-lookup"><span data-stu-id="10088-108">If you wanted to use the same script with a different functoid, you either copied and pasted it from one **Scripting** functoid to another, or you rewrote the script from scratch.</span></span>  
  
 <span data-ttu-id="10088-109">在移轉對應時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用運算質複製現有的內嵌指令碼。</span><span class="sxs-lookup"><span data-stu-id="10088-109">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] copies existing inline scripts with the functoids when you migrate a map.</span></span> <span data-ttu-id="10088-110">不過，並非所有的指令碼可能會正常運作。</span><span class="sxs-lookup"><span data-stu-id="10088-110">However, not all of the scripts may function correctly.</span></span> <span data-ttu-id="10088-111">BizTalk Server 會使用 Visual Basic.NET 和 JScript.NET，而不是 VBScript 和 JScript 先前版本中使用。</span><span class="sxs-lookup"><span data-stu-id="10088-111">BizTalk Server uses Visual Basic .NET and JScript .NET rather than the VBScript and JScript used in previous versions.</span></span> <span data-ttu-id="10088-112">語言的 .NET 版本包含部分語法變更。</span><span class="sxs-lookup"><span data-stu-id="10088-112">The .NET versions of the languages include some changes in syntax.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10088-113">請務必測試您**指令碼處理**移轉後的運算質。</span><span class="sxs-lookup"><span data-stu-id="10088-113">Be sure to test your **Scripting** functoids after migration.</span></span>  
  
 <span data-ttu-id="10088-114">您必須重新撰寫自訂運算質。</span><span class="sxs-lookup"><span data-stu-id="10088-114">You will need to rewrite custom functoids.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="10088-115"> 需要使用.NET framework 的自訂運算質。</span><span class="sxs-lookup"><span data-stu-id="10088-115"> expects custom functoids to use the .NET framework.</span></span> <span data-ttu-id="10088-116">它不能使用舊版以 COM 為基礎的自訂運算質。</span><span class="sxs-lookup"><span data-stu-id="10088-116">It cannot use the older, COM-based custom functoids.</span></span> <span data-ttu-id="10088-117">您可以重新撰寫自訂運算質以使用 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="10088-117">Custom functoids can be rewritten to use the .NET framework.</span></span> <span data-ttu-id="10088-118">自訂運算質的範例程式碼，請參閱[自訂運算質 （BizTalk Server 範例）](../core/custom-functoid-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="10088-118">For sample code of a custom functoid, see [Custom Functoid (BizTalk Server Sample)](../core/custom-functoid-biztalk-server-sample.md).</span></span>  
  
 <span data-ttu-id="10088-119">替代方式是在外部組件中包裝自訂運算質的功能，並呼叫透過這個組件**指令碼處理**運算質。</span><span class="sxs-lookup"><span data-stu-id="10088-119">An alternative is to wrap the functionality of the custom functoid in an external assembly and call this assembly through a **Scripting** functoid.</span></span> <span data-ttu-id="10088-120">下節敘述此程序。</span><span class="sxs-lookup"><span data-stu-id="10088-120">The following section describes this process.</span></span>  
  
### <a name="to-migrate-your-custom-functoids"></a><span data-ttu-id="10088-121">移轉自訂運算質</span><span class="sxs-lookup"><span data-stu-id="10088-121">To migrate your custom functoids</span></span>  
  
1. <span data-ttu-id="10088-122">使用 .NET 語言 (例如，Microsoft Visual Basic .NET、JScript .NET 或 Microsoft Visual C# .NET) 重新建立運算質的功能。</span><span class="sxs-lookup"><span data-stu-id="10088-122">Re-create the functionality of the functoid in a .NET language, such as Microsoft Visual Basic .NET, JScript .NET, or Microsoft Visual C# .NET.</span></span>  
  
2. <span data-ttu-id="10088-123">建立組件以包含新功能。</span><span class="sxs-lookup"><span data-stu-id="10088-123">Create an assembly to contain the new functionality.</span></span>  
  
3. <span data-ttu-id="10088-124">在全域組件快取 (GAC) 中註冊組件。</span><span class="sxs-lookup"><span data-stu-id="10088-124">Register the assembly in the global assembly cache (GAC).</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="10088-125">若要在全域組件快取中註冊組件，則組件必須以強式名稱命名並簽章。</span><span class="sxs-lookup"><span data-stu-id="10088-125">To register assemblies in the global assembly cache, they must be strong named and signed.</span></span> <span data-ttu-id="10088-126">如需註冊組件的詳細資訊，請參閱《[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 組合集合》中的＜全域組件快取＞。</span><span class="sxs-lookup"><span data-stu-id="10088-126">For more information about registering assemblies, see "Global Assembly Cache" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Combined Collection.</span></span>  
  
4. <span data-ttu-id="10088-127">之間的對應，包含建立參考**指令碼處理**運算質和組件，其中包含重寫的功能。</span><span class="sxs-lookup"><span data-stu-id="10088-127">Create a reference between the map that contains the **Scripting** functoid and the assembly that contains the rewritten functionality.</span></span>  
  
5. <span data-ttu-id="10088-128">設定**指令碼**屬性**指令碼處理**運算質。</span><span class="sxs-lookup"><span data-stu-id="10088-128">Configure the **Script** property for the **Scripting** functoid.</span></span> <span data-ttu-id="10088-129">此屬性會決定哪些指令碼**指令碼處理**運算質在執行階段期間的呼叫。</span><span class="sxs-lookup"><span data-stu-id="10088-129">This property determines what script the **Scripting** functoid calls during run time.</span></span> <span data-ttu-id="10088-130">您必須將此屬性的值與自訂指令碼已轉換成的語言比對。</span><span class="sxs-lookup"><span data-stu-id="10088-130">You must match the value of this property to the language into which you converted your custom script.</span></span> <span data-ttu-id="10088-131">如需如何設定 Script 屬性的詳細資訊，請參閱[編輯運算質屬性和輸入參數](../core/editing-functoid-properties-and-input-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="10088-131">For more information about how to configure the Script property, see [Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md).</span></span> <span data-ttu-id="10088-132">另請參閱[指令碼處理運算質](../core/scripting-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="10088-132">Also see [Scripting Functoid](../core/scripting-functoid.md).</span></span>  
  
6. <span data-ttu-id="10088-133">建置 BizTalk 專案，其中包含地圖**指令碼處理**運算質。</span><span class="sxs-lookup"><span data-stu-id="10088-133">Build the BizTalk project that contains the map with the **Scripting** functoid.</span></span>  
  
7. <span data-ttu-id="10088-134">驗證並測試對應。</span><span class="sxs-lookup"><span data-stu-id="10088-134">Validate and test the map.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10088-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10088-135">See Also</span></span>  
 <span data-ttu-id="10088-136">[編輯運算質屬性和輸入的參數](../core/editing-functoid-properties-and-input-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="10088-136">[Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md) </span></span>  
 [<span data-ttu-id="10088-137">指令碼處理運算質</span><span class="sxs-lookup"><span data-stu-id="10088-137">Scripting Functoid</span></span>](../core/scripting-functoid.md)