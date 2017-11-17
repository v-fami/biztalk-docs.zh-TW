---
title: "開發自訂運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77419e1f-9f01-44ac-bf5b-a393f1d17f61
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e5534f3209cb943fb3e2c2a63a18f9e29928be5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="developing-custom-functoids"></a><span data-ttu-id="1e981-102">開發自訂運算質</span><span class="sxs-lookup"><span data-stu-id="1e981-102">Developing Custom Functoids</span></span>
<span data-ttu-id="1e981-103">雖然 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供許多運算質支援許多不同的作業，仍可能會遇到一些需要不同解決方法的情況。</span><span class="sxs-lookup"><span data-stu-id="1e981-103">Although [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides many functoids to support a range of diverse operations, you will likely encounter a situation that requires a different approach.</span></span> <span data-ttu-id="1e981-104">自訂運算質提供您一個擴充 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 對應環境中之可用作業範圍的方式。</span><span class="sxs-lookup"><span data-stu-id="1e981-104">Custom functoids provide a way for you to extend the range of operations available within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] mapping environment.</span></span> <span data-ttu-id="1e981-105">每個自訂運算質會部署為.NET 組件使用類別衍生自**Microsoft.BizTalk.BaseFunctoids**。</span><span class="sxs-lookup"><span data-stu-id="1e981-105">Each custom functoid is deployed as a .NET assembly using classes derived from **Microsoft.BizTalk.BaseFunctoids**.</span></span> <span data-ttu-id="1e981-106">一個組件可包含一個以上的自訂運算質。</span><span class="sxs-lookup"><span data-stu-id="1e981-106">An assembly can contain more than one custom functoid.</span></span>  
  
 <span data-ttu-id="1e981-107">您應該考慮在下列案例中使用自訂運算質：</span><span class="sxs-lookup"><span data-stu-id="1e981-107">You should consider using a custom functoid in the following scenarios:</span></span>  
  
-   <span data-ttu-id="1e981-108">對於使用只能透過專屬舊版 API 存取之資料的字元程式碼欄位，您具有特殊的驗證和轉換規則。</span><span class="sxs-lookup"><span data-stu-id="1e981-108">You have special validation and conversion rules for a character code field using data that is only accessible through a proprietary legacy API.</span></span>  
  
-   <span data-ttu-id="1e981-109">您需要使用自訂商務邏輯和金鑰管理來加密或解密欄位。</span><span class="sxs-lookup"><span data-stu-id="1e981-109">You need to encrypt or decrypt fields using custom business logic and key management.</span></span>  
  
-   <span data-ttu-id="1e981-110">您需要從部分訊息產生雜湊程式碼，以供在另一個應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="1e981-110">You need to generate a hash code from part of the message for use in another application.</span></span>  
  
-   <span data-ttu-id="1e981-111">訊息傳送至其部門的帳戶處理要求包含依每個產品類型的總銷售額摘要資訊。</span><span class="sxs-lookup"><span data-stu-id="1e981-111">Accounting requests that messages transmitted to their department include summary information about total sales by each product type.</span></span>  
  
-   <span data-ttu-id="1e981-112">您想要組合幾個相關步驟、使用不同的方式，或是使用新的類別庫，來降低對應的複雜性。</span><span class="sxs-lookup"><span data-stu-id="1e981-112">You want to reduce the complexity of a map by combining several related steps, by using a different approach, or by using new class libraries.</span></span>  
  
-   <span data-ttu-id="1e981-113">有一個以上的對應正在使用指令碼運算質中的相同指令碼。</span><span class="sxs-lookup"><span data-stu-id="1e981-113">More than one map is using the same script code in a script functoid.</span></span>  
  
-   <span data-ttu-id="1e981-114">作業失敗時，您需要寫入事件記錄。</span><span class="sxs-lookup"><span data-stu-id="1e981-114">You need to write to the event log when an operation fails.</span></span>  
  
 <span data-ttu-id="1e981-115">自訂運算質可直接使用內嵌程式碼或間接使用部署至全域組件快取之類別庫中的方法參考，整合至方案中。</span><span class="sxs-lookup"><span data-stu-id="1e981-115">Custom functoids can be integrated into a solution directly by using inline code or indirectly by reference to a method in a class library deployed into the global assembly cache.</span></span> <span data-ttu-id="1e981-116">這兩種整合依賴**BizTalk.BaseFunctoid**類別，並遵循一組相同的一般步驟：</span><span class="sxs-lookup"><span data-stu-id="1e981-116">Both types of integration rely on the **BizTalk.BaseFunctoid** class and follow the same set of general steps:</span></span>  
  
1.  <span data-ttu-id="1e981-117">使用您選擇的 .NET 語言建立新的程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="1e981-117">Create a new class library project using the .NET language of your choice.</span></span>  
  
2.  <span data-ttu-id="1e981-118">使用強式命名的公用程式 sn.exe 建立 keyfile，並將它指派至專案。</span><span class="sxs-lookup"><span data-stu-id="1e981-118">Using the strong-naming utility sn.exe, create a keyfile and assign it to the project.</span></span>  
  
3.  <span data-ttu-id="1e981-119">加入參考至 Microsoft.BizTalk.BaseFunctoids.dll。</span><span class="sxs-lookup"><span data-stu-id="1e981-119">Add a reference to Microsoft.BizTalk.BaseFunctoids.dll.</span></span> <span data-ttu-id="1e981-120">這個組件包含**BaseFunctoid**基底類別。</span><span class="sxs-lookup"><span data-stu-id="1e981-120">This assembly contains the **BaseFunctoid** base class.</span></span>  
  
4.  <span data-ttu-id="1e981-121">建立資源檔案，並將它新增至專案。</span><span class="sxs-lookup"><span data-stu-id="1e981-121">Create a resource file and add it to the project.</span></span> <span data-ttu-id="1e981-122">新增運算質名稱、工具提示和描述的字串資源。</span><span class="sxs-lookup"><span data-stu-id="1e981-122">Add string resources for the functoid name, tooltip, and description.</span></span> <span data-ttu-id="1e981-123">新增 16x16 像素的影像資源，以在對應設計師工具板上代表運算質。</span><span class="sxs-lookup"><span data-stu-id="1e981-123">Add a 16x16-pixel image resource to represent the functoid on the map designer palette.</span></span>  
  
5.  <span data-ttu-id="1e981-124">由衍生自實作運算質類別**BaseFunctoid**中建構函式，建立基本參數，然後寫入運算質方法和任何支援的方法。</span><span class="sxs-lookup"><span data-stu-id="1e981-124">Implement the functoid class by deriving from **BaseFunctoid**, establishing basic parameters in the constructor, and then writing the functoid method and any supporting methods.</span></span> <span data-ttu-id="1e981-125">此組件可包含多個自訂運算質。</span><span class="sxs-lookup"><span data-stu-id="1e981-125">The assembly can contain multiple custom functoids.</span></span>  
  
6.  <span data-ttu-id="1e981-126">部署該組件，並確定可從 [工具箱] 工具板取得新的運算質。</span><span class="sxs-lookup"><span data-stu-id="1e981-126">Deploy the assembly and ensure the new functoid is available from the Toolbox palette.</span></span> <span data-ttu-id="1e981-127">請參閱[新增和移除自訂運算質從 Visual Studio 工具箱](../core/adding-and-removing-custom-functoids-from-the-visual-studio-toolbox.md)。</span><span class="sxs-lookup"><span data-stu-id="1e981-127">See [Adding and Removing Custom Functoids from the Visual Studio Toolbox](../core/adding-and-removing-custom-functoids-from-the-visual-studio-toolbox.md).</span></span>  
  
 <span data-ttu-id="1e981-128">下列是 Floor 運算質的圖例。</span><span class="sxs-lookup"><span data-stu-id="1e981-128">The following is an illustration for Floor functoid.</span></span>  
  
```  
/// <summary>  
/// Floor Functoid - finds the floor of input  
/// </summary>  
public class FloorFunctoid : BaseFunctoid  
{  
    public FloorFunctoid()  
        : base()  
    {  
        this.ID = 11001;  
        SetupResourceAssembly("MultipleFunctoids.Resource", Assembly.GetExecutingAssembly());  
  
        SetName("NAME_FLOOR");  
        SetDescription("DESCRIPTION_FLOOR");  
        SetTooltip("DESCRIPTION_FLOOR");  
        SetBitmap("IMAGE_FLOOR");  
  
        SetExternalFunctionName(GetType().Assembly.FullName, " MultipleFunctoids.FloorFunctoid", "MathFloor");  
        this.RequiredGlobalHelperFunctions = InlineGlobalHelperFunction.IsNumeric;  
  
        AddScriptTypeSupport(ScriptType.CSharp);  
        SetMinParams(1);  
        SetMaxParams(1);  
  
        this.Category = FunctoidCategory.Math;  
        this.OutputConnectionType = ConnectionType.AllExceptRecord;  
        AddInputConnectionType(ConnectionType.AllExceptRecord);  
        this.HasSideEffects = false;  
    }  
  
    /// <summary>  
    /// To create the C# function  
    /// </summary>  
    /// <param name="scriptType">Script type</param>  
    /// <param name="numParams">Number of parameters</param>  
    /// <param name="functionNumber">Functoid number</param>  
    /// <returns>C# script</returns>  
    protected override string GetInlineScriptBuffer(ScriptType scriptType, int numParams, int functionNumber)  
    {  
        if (ScriptType.CSharp == scriptType)  
        {  
            StringBuilder builder = new StringBuilder();  
  
            builder.Append("public string MathFloor(string input)\n");  
            builder.Append("{\n");  
            builder.Append("  if(string.IsNullOrEmpty(input))\n");  
            builder.Append("    return string.Empty;\n");  
            builder.Append("double d = 0.0;\n");  
            builder.Append("if (IsNumeric(input, ref d))\n");  
            builder.Append("    return Math.Floor(d).ToString(System.Globalization.CultureInfo.InvariantCulture);\n");  
            builder.Append("else\n");  
            builder.Append("    return string.Empty;\n");  
            builder.Append("}\n");  
  
            return builder.ToString();  
        }  
        else  
        {  
            return string.Empty;  
        }  
    }  
}  
  
```  
  
 <span data-ttu-id="1e981-129">在 C# 專案中使用此範例程式碼時，“Assembly name” 必須設為 “MultipleFunctoids”。</span><span class="sxs-lookup"><span data-stu-id="1e981-129">While using this sample code as part of your C# project, the “Assembly name” must be set to “MultipleFunctoids”.</span></span> <span data-ttu-id="1e981-130">您的 C# 專案 (包含此程式碼) 應該包含 Resource.resx 檔案。</span><span class="sxs-lookup"><span data-stu-id="1e981-130">Your C# project (containing this code) should include a Resource.resx file.</span></span>  
  
```  
SetName("NAME_FLOOR");  
SetDescription("DESCRIPTION_FLOOR");  
SetTooltip("DESCRIPTION_FLOOR");  
SetBitmap("IMAGE_FLOOR");  
  
```  
  
 <span data-ttu-id="1e981-131">在上述程式碼中，“NAME_FLOOR”、“DESCRIPTION_FLOOR” 和 “DESCRIPTION_FLOOR” 這些值是 Resource.resx 檔案中內嵌的資源字串的「識別碼」。</span><span class="sxs-lookup"><span data-stu-id="1e981-131">In the above code, the values “NAME_FLOOR”, “DESCRIPTION_FLOOR”, and “DESCRIPTION_FLOOR” are the “keys” of resource strings embedded in Resource.resx file.</span></span> <span data-ttu-id="1e981-132">“IMAGE_FLOOR” 是 Resource.resx 檔案中內嵌的影像的名稱。</span><span class="sxs-lookup"><span data-stu-id="1e981-132">And, “IMAGE_FLOOR” is the name of an image embedded in the Resource.resx file.</span></span> <span data-ttu-id="1e981-133">此映像做為運算質的圖示。</span><span class="sxs-lookup"><span data-stu-id="1e981-133">This image will act as an icon for the functoid.</span></span>  
  
 <span data-ttu-id="1e981-134">如果您未指定適當的資源索引鍵，或如果您刪除 SetName 方法，則沒有名稱的自訂運算質會建立，這不是很好的作法。</span><span class="sxs-lookup"><span data-stu-id="1e981-134">If you do not specify proper resource keys, or if you delete the SetName method, then a nameless custom functoid is created, which is not a good practice.</span></span> <span data-ttu-id="1e981-135">SetDescription 和 SetTooltip 方法也是一樣。</span><span class="sxs-lookup"><span data-stu-id="1e981-135">Same holds true for SetDescription and SetTooltip methods.</span></span> <span data-ttu-id="1e981-136">請務必正確地使用這些方法，以避免任何不必要的無用行為。</span><span class="sxs-lookup"><span data-stu-id="1e981-136">Always use these methods properly to avoid any unwanted garbage behavior.</span></span> <span data-ttu-id="1e981-137">不過，如果您沒有任何適合的影像可做為運算質圖示，您可以略過 SetBitmap 方法。</span><span class="sxs-lookup"><span data-stu-id="1e981-137">However, you may skip the SetBitmap method if you do not have any suitable images to be used as functoid icons.</span></span> <span data-ttu-id="1e981-138">在此情況下，自訂運算質會使用預設圖示，此舉並沒有害處 (除非有多個無圖示的運算質)。</span><span class="sxs-lookup"><span data-stu-id="1e981-138">In such a case, a default icon is used by the custom functoid, which is harmless (unless there are multiple icon-less functoids).</span></span>  
  
 <span data-ttu-id="1e981-139">如需如何建立自訂運算質的詳細資訊，請參閱[自訂運算質 （BizTalk Server 範例）](../core/custom-functoid-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="1e981-139">For more information about how to create a custom functoid, see [Custom Functoid (BizTalk Server Sample)](../core/custom-functoid-biztalk-server-sample.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1e981-140">標準/內建對應工具運算質會保留特定運算質識別碼。</span><span class="sxs-lookup"><span data-stu-id="1e981-140">Certain functoid IDs are reserved by standard/inbuilt Mapper functoids.</span></span> <span data-ttu-id="1e981-141">通常，標準的對應工具運算質會使用從 1 到 10000 的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1e981-141">Usually, the standard Mapper functoids use the IDs from 1 to 10000.</span></span> <span data-ttu-id="1e981-142">在建立自訂運算質時，請勿使用識別碼小於 10000 的運算質。</span><span class="sxs-lookup"><span data-stu-id="1e981-142">While creating custom functoids, do not use the functoid IDs less than 10000.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1e981-143">本節內容</span><span class="sxs-lookup"><span data-stu-id="1e981-143">In This Section</span></span>  
 <span data-ttu-id="1e981-144">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="1e981-144">This section contains:</span></span>  
  
-   [<span data-ttu-id="1e981-145">使用 BaseFunctoid</span><span class="sxs-lookup"><span data-stu-id="1e981-145">Using BaseFunctoid</span></span>](../core/using-basefunctoid.md)  
  
-   [<span data-ttu-id="1e981-146">開發自訂參考運算質</span><span class="sxs-lookup"><span data-stu-id="1e981-146">Developing a Custom Referenced Functoid</span></span>](../core/developing-a-custom-referenced-functoid.md)  
  
-   [<span data-ttu-id="1e981-147">開發自訂內嵌運算質</span><span class="sxs-lookup"><span data-stu-id="1e981-147">Developing a Custom Inline Functoid</span></span>](../core/developing-a-custom-inline-functoid.md)  
  
-   [<span data-ttu-id="1e981-148">開發自訂累計運算質</span><span class="sxs-lookup"><span data-stu-id="1e981-148">Developing a Custom Cumulative Functoid</span></span>](../core/developing-a-custom-cumulative-functoid.md)  
  
-   [<span data-ttu-id="1e981-149">加入和移除自訂運算質從 Visual Studio 工具箱</span><span class="sxs-lookup"><span data-stu-id="1e981-149">Adding and Removing Custom Functoids from the Visual Studio Toolbox</span></span>](../core/adding-and-removing-custom-functoids-from-the-visual-studio-toolbox.md)  
  
## <a name="see-also"></a><span data-ttu-id="1e981-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e981-150">See Also</span></span>  
 [<span data-ttu-id="1e981-151">使用運算質建立更複雜的對應</span><span class="sxs-lookup"><span data-stu-id="1e981-151">Using Functoids to Create More Complex Mappings</span></span>](../core/using-functoids-to-create-more-complex-mappings.md)