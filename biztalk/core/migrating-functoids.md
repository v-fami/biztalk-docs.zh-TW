---
title: "移轉運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fac30a9b884bc769752623003d16e7089b140d4
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="migrating-functoids"></a><span data-ttu-id="12518-102">移轉運算質</span><span class="sxs-lookup"><span data-stu-id="12518-102">Migrating Functoids</span></span>
<span data-ttu-id="12518-103">當您從舊版的 BizTalk Server 移轉對應至 BizTalk Server 時，也會移轉任何包含在對應的運算質。</span><span class="sxs-lookup"><span data-stu-id="12518-103">When you migrate a map from previous versions of BizTalk Server to BizTalk Server, any functoids included in the map are also migrated.</span></span> <span data-ttu-id="12518-104">如果您移轉的運算質未包含**指令碼處理**運算質，沒有其他移轉工作所需。</span><span class="sxs-lookup"><span data-stu-id="12518-104">If the functoids you migrate do not include **Scripting** functoids, no additional migration tasks are required.</span></span> <span data-ttu-id="12518-105">不過如果您的對應包含**指令碼處理**運算質或自訂運算質，您可能必須執行其他步驟。</span><span class="sxs-lookup"><span data-stu-id="12518-105">However if your map includes **Scripting** functoids or custom functoids, you may have additional steps to perform.</span></span>  
  
 <span data-ttu-id="12518-106">在舊版的 BizTalk Server 中，所有的自訂指令碼包含**指令碼處理**寫入內嵌運算質。</span><span class="sxs-lookup"><span data-stu-id="12518-106">In previous versions of BizTalk Server, all custom script included with a **Scripting** functoid was written inline.</span></span> <span data-ttu-id="12518-107">也就是說，當您建立運算質時，運算質在執行階段呼叫的所有指令碼都與運算質一起儲存。</span><span class="sxs-lookup"><span data-stu-id="12518-107">That is, when you created the functoid, all the script the functoid called during run time was stored with the functoid.</span></span> <span data-ttu-id="12518-108">如果您想要使用不同的運算質使用相同的指令碼，您可以複製並貼上它從某個**指令碼處理**到另一個，或者您的運算質重寫從頭指令碼。</span><span class="sxs-lookup"><span data-stu-id="12518-108">If you wanted to use the same script with a different functoid, you either copied and pasted it from one **Scripting** functoid to another, or you rewrote the script from scratch.</span></span>  
  
 <span data-ttu-id="12518-109">在移轉對應時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用運算質複製現有的內嵌指令碼。</span><span class="sxs-lookup"><span data-stu-id="12518-109">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] copies existing inline scripts with the functoids when you migrate a map.</span></span> <span data-ttu-id="12518-110">不過，所有指令碼可能會正常運作。</span><span class="sxs-lookup"><span data-stu-id="12518-110">However, not all of the scripts may function correctly.</span></span> <span data-ttu-id="12518-111">BizTalk Server 會使用 Visual Basic.NET 和 JScript.NET，而不是 VBScript 和 JScript 在舊版中使用。</span><span class="sxs-lookup"><span data-stu-id="12518-111">BizTalk Server uses Visual Basic .NET and JScript .NET rather than the VBScript and JScript used in previous versions.</span></span> <span data-ttu-id="12518-112">語言的 .NET 版本包含部分語法變更。</span><span class="sxs-lookup"><span data-stu-id="12518-112">The .NET versions of the languages include some changes in syntax.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12518-113">務必先測試您**指令碼處理**移轉之後的運算質。</span><span class="sxs-lookup"><span data-stu-id="12518-113">Be sure to test your **Scripting** functoids after migration.</span></span>  
  
 <span data-ttu-id="12518-114">您必須重新撰寫自訂運算質。</span><span class="sxs-lookup"><span data-stu-id="12518-114">You will need to rewrite custom functoids.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="12518-115">預期為使用.NET framework 的自訂運算質。</span><span class="sxs-lookup"><span data-stu-id="12518-115"> expects custom functoids to use the .NET framework.</span></span> <span data-ttu-id="12518-116">它不能使用舊版以 COM 為基礎的自訂運算質。</span><span class="sxs-lookup"><span data-stu-id="12518-116">It cannot use the older, COM-based custom functoids.</span></span> <span data-ttu-id="12518-117">您可以重新撰寫自訂運算質以使用 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="12518-117">Custom functoids can be rewritten to use the .NET framework.</span></span> <span data-ttu-id="12518-118">自訂運算質的範例程式碼，請參閱[自訂運算質 （BizTalk Server 範例）](../core/custom-functoid-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="12518-118">For sample code of a custom functoid, see [Custom Functoid (BizTalk Server Sample)](../core/custom-functoid-biztalk-server-sample.md).</span></span>  
  
 <span data-ttu-id="12518-119">另一個方法是在外部組件中換行功能的自訂運算質呼叫此組件透過**指令碼處理**運算質。</span><span class="sxs-lookup"><span data-stu-id="12518-119">An alternative is to wrap the functionality of the custom functoid in an external assembly and call this assembly through a **Scripting** functoid.</span></span> <span data-ttu-id="12518-120">下節敘述此程序。</span><span class="sxs-lookup"><span data-stu-id="12518-120">The following section describes this process.</span></span>  
  
### <a name="to-migrate-your-custom-functoids"></a><span data-ttu-id="12518-121">移轉自訂運算質</span><span class="sxs-lookup"><span data-stu-id="12518-121">To migrate your custom functoids</span></span>  
  
1.  <span data-ttu-id="12518-122">使用 .NET 語言 (例如，Microsoft Visual Basic .NET、JScript .NET 或 Microsoft Visual C# .NET) 重新建立運算質的功能。</span><span class="sxs-lookup"><span data-stu-id="12518-122">Re-create the functionality of the functoid in a .NET language, such as Microsoft Visual Basic .NET, JScript .NET, or Microsoft Visual C# .NET.</span></span>  
  
2.  <span data-ttu-id="12518-123">建立組件以包含新功能。</span><span class="sxs-lookup"><span data-stu-id="12518-123">Create an assembly to contain the new functionality.</span></span>  
  
3.  <span data-ttu-id="12518-124">在全域組件快取 (GAC) 中註冊組件。</span><span class="sxs-lookup"><span data-stu-id="12518-124">Register the assembly in the global assembly cache (GAC).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="12518-125">若要在全域組件快取中註冊組件，則組件必須以強式名稱命名並簽章。</span><span class="sxs-lookup"><span data-stu-id="12518-125">To register assemblies in the global assembly cache, they must be strong named and signed.</span></span> <span data-ttu-id="12518-126">如需註冊組件的詳細資訊，請參閱《[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 組合集合》中的＜全域組件快取＞。</span><span class="sxs-lookup"><span data-stu-id="12518-126">For more information about registering assemblies, see "Global Assembly Cache" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Combined Collection.</span></span>  
  
4.  <span data-ttu-id="12518-127">之間的對應，包含建立參考**指令碼處理**運算質和組件，其中包含重寫的功能。</span><span class="sxs-lookup"><span data-stu-id="12518-127">Create a reference between the map that contains the **Scripting** functoid and the assembly that contains the rewritten functionality.</span></span>  
  
5.  <span data-ttu-id="12518-128">設定**指令碼**屬性**指令碼處理**運算質。</span><span class="sxs-lookup"><span data-stu-id="12518-128">Configure the **Script** property for the **Scripting** functoid.</span></span> <span data-ttu-id="12518-129">此屬性會決定哪些指令碼**指令碼處理**運算質在執行階段呼叫。</span><span class="sxs-lookup"><span data-stu-id="12518-129">This property determines what script the **Scripting** functoid calls during run time.</span></span> <span data-ttu-id="12518-130">您必須將此屬性的值與自訂指令碼已轉換成的語言比對。</span><span class="sxs-lookup"><span data-stu-id="12518-130">You must match the value of this property to the language into which you converted your custom script.</span></span> <span data-ttu-id="12518-131">如需如何設定 Script 屬性的詳細資訊，請參閱[編輯運算質屬性和輸入參數](../core/editing-functoid-properties-and-input-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="12518-131">For more information about how to configure the Script property, see [Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md).</span></span> <span data-ttu-id="12518-132">另請參閱[指令碼處理運算質](../core/scripting-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="12518-132">Also see [Scripting Functoid](../core/scripting-functoid.md).</span></span>  
  
6.  <span data-ttu-id="12518-133">建置 BizTalk 專案，其中包含地圖**指令碼處理**運算質。</span><span class="sxs-lookup"><span data-stu-id="12518-133">Build the BizTalk project that contains the map with the **Scripting** functoid.</span></span>  
  
7.  <span data-ttu-id="12518-134">驗證並測試對應。</span><span class="sxs-lookup"><span data-stu-id="12518-134">Validate and test the map.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12518-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="12518-135">See Also</span></span>  
 <span data-ttu-id="12518-136">[編輯運算質屬性和輸入的參數](../core/editing-functoid-properties-and-input-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="12518-136">[Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md) </span></span>  
 [<span data-ttu-id="12518-137">指令碼處理運算質</span><span class="sxs-lookup"><span data-stu-id="12518-137">Scripting Functoid</span></span>](../core/scripting-functoid.md)