---
title: "開發自訂內嵌運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4533f09f-b62d-4b09-b7de-44541c6cf053
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a742e6a53b5fb81d92922ff94e7754239f723ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-custom-inline-functoid"></a><span data-ttu-id="1a512-102">開發自訂內嵌運算質</span><span class="sxs-lookup"><span data-stu-id="1a512-102">Developing a Custom Inline Functoid</span></span>
<span data-ttu-id="1a512-103">自訂內嵌運算質藉由直接複製實作程式碼到對應中，以提供功能，而不是像自訂參考運算質一樣參考組件、類別和方法名稱。</span><span class="sxs-lookup"><span data-stu-id="1a512-103">Custom inline functoids provide functionality by copying implementation code directly into a map and not by referencing an assembly, class, and method name like a custom referenced functoid.</span></span>  
  
## <a name="building-inline-script"></a><span data-ttu-id="1a512-104">建置內嵌指令碼</span><span class="sxs-lookup"><span data-stu-id="1a512-104">Building Inline Script</span></span>  
 <span data-ttu-id="1a512-105">有兩種方式可以提供指令碼包含在對應中。</span><span class="sxs-lookup"><span data-stu-id="1a512-105">There are two ways to provide script for inclusion into the map.</span></span> <span data-ttu-id="1a512-106">根據您的自訂運算質是否可支援不同數量的參數，從下列方法選擇：</span><span class="sxs-lookup"><span data-stu-id="1a512-106">Choose from the following methods, based on whether your custom functoid supports a variable number of parameters:</span></span>  
  
-   <span data-ttu-id="1a512-107">覆寫**GetInlineScriptBuffer**當您自訂運算質接受多個輸入參數，而且您已經將**HasVariableInputs**屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="1a512-107">Override **GetInlineScriptBuffer** when your custom functoid accepts a variable number of input parameters and you have set the **HasVariableInputs** property to `true`.</span></span> <span data-ttu-id="1a512-108">例如，若您要串連不同數量的字串或尋找一組值中的最大值，即可使用此方法。</span><span class="sxs-lookup"><span data-stu-id="1a512-108">For example, use this method if you want to concatenate a variable number of strings or find the largest value in a set of values.</span></span>  
  
-   <span data-ttu-id="1a512-109">使用**SetScriptBuffer**時不需要支援多個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="1a512-109">Use **SetScriptBuffer** when you do not need to support a variable number of input parameters.</span></span> <span data-ttu-id="1a512-110">您還是可以使用選擇性的參數，但參數的總數是固定的。</span><span class="sxs-lookup"><span data-stu-id="1a512-110">You can still use optional parameters, but the total number of parameters is fixed.</span></span>  
  
 <span data-ttu-id="1a512-111">這兩種方法需要不同的實作。</span><span class="sxs-lookup"><span data-stu-id="1a512-111">These two methods require different implementations.</span></span>  
  
### <a name="providing-inline-code-with-setscriptbuffer"></a><span data-ttu-id="1a512-112">提供具有 SetScriptBuffer 的內嵌程式碼</span><span class="sxs-lookup"><span data-stu-id="1a512-112">Providing Inline Code with SetScriptBuffer</span></span>  
 <span data-ttu-id="1a512-113">將您的自訂運算質設定為使用內嵌指令碼：</span><span class="sxs-lookup"><span data-stu-id="1a512-113">To configure your custom functoid to use inline script:</span></span>  
  
1.  <span data-ttu-id="1a512-114">呼叫**AddScriptTypeSupport**與[Microsoft.BizTalk.BaseFunctoids.ScriptType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx)以啟用內嵌程式碼並設定支援的指令碼類型。</span><span class="sxs-lookup"><span data-stu-id="1a512-114">Call **AddScriptTypeSupport** with [Microsoft.BizTalk.BaseFunctoids.ScriptType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx) to enable inline code and set the supported script type.</span></span>  
  
2.  <span data-ttu-id="1a512-115">叫用**SetScriptBuffer**設定要用於自訂運算質程式碼。</span><span class="sxs-lookup"><span data-stu-id="1a512-115">Invoke **SetScriptBuffer** to set the code to use for the custom functoid.</span></span> <span data-ttu-id="1a512-116">您將以 `functionNumber` 參數，為自訂累計運算質呼叫此函式三次，並為自訂非累計運算質呼叫此函式一次。</span><span class="sxs-lookup"><span data-stu-id="1a512-116">You will call this function three times with the `functionNumber` parameter for custom cumulative functoids and once for custom noncumulative functoids.</span></span>  
  
3.  <span data-ttu-id="1a512-117">使用**[setscriptglobalbuffer]**以宣告您的內嵌程式碼會使用任何全域變數。</span><span class="sxs-lookup"><span data-stu-id="1a512-117">Use **SetScriptGlobalBuffer** to declare any global variables that your inline code uses.</span></span>  
  
4.  <span data-ttu-id="1a512-118">使用**RequiredGlobalHelperFunctions**表示您的自訂內嵌運算質所需要的 helper 函式。</span><span class="sxs-lookup"><span data-stu-id="1a512-118">Use **RequiredGlobalHelperFunctions** to indicate the helper functions that your custom inline functoid requires.</span></span>  
  
 <span data-ttu-id="1a512-119">您可以使用 StringBuilder 或常數建置您的指令碼。</span><span class="sxs-lookup"><span data-stu-id="1a512-119">You can build your script by using StringBuilder or constants.</span></span> <span data-ttu-id="1a512-120">撰寫指令碼的一個方法是先撰寫自訂參考運算質，排除所有錯誤之後，複製您的運算質到字串常數，以將它轉換為內嵌。</span><span class="sxs-lookup"><span data-stu-id="1a512-120">One approach to writing script code is to write a custom referenced functoid first and, when all bugs are eliminated, convert it to inline by copying your functions into string constants.</span></span>  
  
### <a name="providing-inline-code-with-getinlinescriptbuffer"></a><span data-ttu-id="1a512-121">提供具有 GetInlineScriptBuffer 的內嵌程式碼</span><span class="sxs-lookup"><span data-stu-id="1a512-121">Providing Inline Code with GetInlineScriptBuffer</span></span>  
 <span data-ttu-id="1a512-122">如果您的自訂內嵌運算質可支援不同數量的參數，您將會覆寫**GetInlineScriptBuffer**。</span><span class="sxs-lookup"><span data-stu-id="1a512-122">If your custom inline functoid supports a variable number of parameters, you will override **GetInlineScriptBuffer**.</span></span> <span data-ttu-id="1a512-123">將您的自訂運算質設定為使用內嵌指令碼：</span><span class="sxs-lookup"><span data-stu-id="1a512-123">To configure your custom functoid to use inline script:</span></span>  
  
1.  <span data-ttu-id="1a512-124">在建構函式，宣告您的自訂運算質有變數輸入，藉由設定**HasVariableInputs**至`true`。</span><span class="sxs-lookup"><span data-stu-id="1a512-124">In the constructor, declare that your custom functoid has variable inputs by setting **HasVariableInputs** to `true`.</span></span>  
  
2.  <span data-ttu-id="1a512-125">在建構函式，呼叫**AddScriptTypeSupport**與[Microsoft.BizTalk.BaseFunctoids.ScriptType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx)以啟用內嵌程式碼並設定支援的指令碼類型。</span><span class="sxs-lookup"><span data-stu-id="1a512-125">In the constructor, call **AddScriptTypeSupport** with [Microsoft.BizTalk.BaseFunctoids.ScriptType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx) to enable inline code and set the supported script type.</span></span>  
  
3.  <span data-ttu-id="1a512-126">覆寫**GetInlineScriptBuffer**建構及傳回自訂運算質的對應中所使用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1a512-126">Override **GetInlineScriptBuffer** to construct and return the code to use in the map for your custom functoid.</span></span> <span data-ttu-id="1a512-127">檢查 `scriptType` 和 `numParams`，以使用參數建置正確的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1a512-127">Use the parameters to build the correct code by checking the `scriptType` and `numParams`.</span></span> <span data-ttu-id="1a512-128">最後一個參數， `functionNumber`，應該是 0。</span><span class="sxs-lookup"><span data-stu-id="1a512-128">The final parameter, `functionNumber`, should be 0.</span></span> <span data-ttu-id="1a512-129">這是因為累計函式有固定的數目的輸入，而且不會使用這個機制。</span><span class="sxs-lookup"><span data-stu-id="1a512-129">This is because cumulative functions have a fixed number of inputs and do not use this mechanism.</span></span>  
  
4.  <span data-ttu-id="1a512-130">使用**[setscriptglobalbuffer]**以宣告您的內嵌程式碼使用全域變數。</span><span class="sxs-lookup"><span data-stu-id="1a512-130">Use **SetScriptGlobalBuffer** to declare global variables that your inline code uses.</span></span>  
  
5.  <span data-ttu-id="1a512-131">使用**RequiredGlobalHelperFunctions**表示您的自訂內嵌運算質所需要的 helper 函式。</span><span class="sxs-lookup"><span data-stu-id="1a512-131">Use **RequiredGlobalHelperFunctions** to indicate the helper functions that your custom inline functoid requires.</span></span>  
  
 <span data-ttu-id="1a512-132">下列程式碼片段建置的 C# 函式有傳入 `numParams` 的參數數目，但沒有函式主體。</span><span class="sxs-lookup"><span data-stu-id="1a512-132">The following code fragment builds a C# function with the number of parameters passed in `numParams` but with no function body.</span></span> <span data-ttu-id="1a512-133">若要使用此程式碼片段，可將範例複製到您的解決方案，再新增程式碼以參數執行動作並傳回值。</span><span class="sxs-lookup"><span data-stu-id="1a512-133">To use this code fragment, copy the example to your solution and add code to do something with the parameters and return a value.</span></span>  
  
```  
// Override GetInlineScriptBuffer  
protected override string GetInlineScriptBuffer(ScriptType scriptType, int numParams, int functionNumber)  
{  
    // Is this one of the supported script types?  
    if(ScriptType.CSharp == scriptType)  
    {  
        // Assume functionNumber == 0  
        StringBuilder builder = new StringBuilder();  
        // Function declaration   
        builder.Append("public string MyFunction("  
        // Declare parameters using numParams  
        for(int i=0; i<numParams; i++)  
        {  
            // Separate params with a comma  
            if(i > 0)  
                builder.Append(", ");  
            // Declare parameters, param0 to paramNUMPARAM  
            builder.Append("string param" + i.ToString());  
        }  
        builder.Append(")\n");  
        // Function body; process params as needed  
        builder.Append("{\n");  
        builder.Append("}\n");  
        // Return script  
        return builder.ToString();  
    }  
    // scriptType is unsupported  
    return string.Empty;  
}  
```  
  
## <a name="testing-an-inline-script"></a><span data-ttu-id="1a512-134">測試內嵌指令碼</span><span class="sxs-lookup"><span data-stu-id="1a512-134">Testing an Inline Script</span></span>  
 <span data-ttu-id="1a512-135">測試在所有開發工作中都是重要的考量。</span><span class="sxs-lookup"><span data-stu-id="1a512-135">Testing is an important consideration in any development effort.</span></span> <span data-ttu-id="1a512-136">自訂內嵌運算質可接受測試。</span><span class="sxs-lookup"><span data-stu-id="1a512-136">Custom inline functoids can be challenging to test.</span></span> <span data-ttu-id="1a512-137">若要簡化此程序，可使用下列的一種或兩種技術：</span><span class="sxs-lookup"><span data-stu-id="1a512-137">To simplify the process, use one or both of the following techniques:</span></span>  
  
-   <span data-ttu-id="1a512-138">檢查使用自訂內嵌運算質的對應之 XSLT。</span><span class="sxs-lookup"><span data-stu-id="1a512-138">Examine the XSLT of a map that uses the custom inline functoid.</span></span>  
  
-   <span data-ttu-id="1a512-139">驗證使用自訂內嵌運算質的對應之輸入和輸出。</span><span class="sxs-lookup"><span data-stu-id="1a512-139">Verify the input and output of a map that uses the custom inline functoid.</span></span>  
  
### <a name="examine-the-xslt-of-a-map-that-uses-the-custom-inline-functoid"></a><span data-ttu-id="1a512-140">檢查使用自訂內嵌運算質的對應之 XSLT</span><span class="sxs-lookup"><span data-stu-id="1a512-140">Examine the XSLT of a Map That Uses the Custom Inline Functoid</span></span>  
 <span data-ttu-id="1a512-141">此技術通常可以發現邏輯問題或較容易忽略的語法問題。</span><span class="sxs-lookup"><span data-stu-id="1a512-141">This technique often reveals problems with logic or subtle syntax issues.</span></span> <span data-ttu-id="1a512-142">也可以協助您瞭解對應中所發生的事。</span><span class="sxs-lookup"><span data-stu-id="1a512-142">It also helps you to understand what happens in the map.</span></span>  
  
 <span data-ttu-id="1a512-143">檢視對應的 XSLT：</span><span class="sxs-lookup"><span data-stu-id="1a512-143">To view the XSLT for a map:</span></span>  
  
1.  <span data-ttu-id="1a512-144">在 Visual Studio BizTalk 專案中，按一下 [**方案總管] 中**索引標籤上，以滑鼠右鍵按一下使用您的自訂內嵌運算質的對應，然後按一下**驗證對應**。</span><span class="sxs-lookup"><span data-stu-id="1a512-144">From a Visual Studio BizTalk project, click the **Solution Explorer** tab, right-click a map that uses your custom inline functoid, and then click **Validate Map**.</span></span>  
  
2.  <span data-ttu-id="1a512-145">捲動至 [輸出] 視窗，以尋找 XSLT 檔案的 URL。</span><span class="sxs-lookup"><span data-stu-id="1a512-145">Scroll the Output window to find the URL for the XSLT file.</span></span> <span data-ttu-id="1a512-146">按 CTRL 再按一下 URL，以檢視檔案。</span><span class="sxs-lookup"><span data-stu-id="1a512-146">Press CTRL and click the URL to view the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a512-147">請記住，對 XSLT 檔案所做的任何變更都不會反映在您的自訂運算質中。</span><span class="sxs-lookup"><span data-stu-id="1a512-147">Remember that any changes made to the XSLT file will not be reflected in your custom functoid.</span></span>  
  
### <a name="test-a-map-that-uses-the-custom-inline-functoid"></a><span data-ttu-id="1a512-148">測試使用自訂內嵌運算質的對應</span><span class="sxs-lookup"><span data-stu-id="1a512-148">Test a Map That Uses the Custom Inline Functoid</span></span>  
 <span data-ttu-id="1a512-149">這會測試對應和自訂內嵌運算質是否如預期運作。</span><span class="sxs-lookup"><span data-stu-id="1a512-149">This tests whether the map and custom inline functoid work as expected.</span></span>  
  
 <span data-ttu-id="1a512-150">測試對應：</span><span class="sxs-lookup"><span data-stu-id="1a512-150">To test a map:</span></span>  
  
1.  <span data-ttu-id="1a512-151">在 Visual Studio BizTalk 專案中，按一下 [**方案總管] 中**索引標籤上，以滑鼠右鍵按一下使用您的自訂內嵌運算質的對應，然後按一下**測試對應**。</span><span class="sxs-lookup"><span data-stu-id="1a512-151">From a Visual Studio BizTalk project, click the **Solution Explorer** tab, right-click a map that uses your custom inline functoid, and then click **Test Map**.</span></span>  
  
2.  <span data-ttu-id="1a512-152">捲動至 [輸出] 視窗，以尋找輸出檔案的 URL。</span><span class="sxs-lookup"><span data-stu-id="1a512-152">Scroll the Output window to find the URL for the output file.</span></span> <span data-ttu-id="1a512-153">按 CTRL 再按一下 URL，以檢視檔案。</span><span class="sxs-lookup"><span data-stu-id="1a512-153">Press CTRL and click the URL to view the file.</span></span>  
  
 <span data-ttu-id="1a512-154">您可以檢查輸入和輸出值，以驗證對應是否如預期運作。</span><span class="sxs-lookup"><span data-stu-id="1a512-154">You can check input and output values to verify that the map behaved as expected.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a512-155">範例</span><span class="sxs-lookup"><span data-stu-id="1a512-155">Example</span></span>  
 <span data-ttu-id="1a512-156">下列範例說明如何建立自訂內嵌運算質以供串連兩個字串。</span><span class="sxs-lookup"><span data-stu-id="1a512-156">The following example illustrates how to create a custom inline functoid for concatenating two strings.</span></span> <span data-ttu-id="1a512-157">它依賴包含三個字串資源以及一個 16x16 像素點陣圖資源的資源檔案。</span><span class="sxs-lookup"><span data-stu-id="1a512-157">It relies on a resource file containing three string resources and a 16x16-pixel bitmap resource.</span></span>  
  
```  
using System;  
using Microsoft.BizTalk.BaseFunctoids;  
using System.Reflection;  
using System.Text;  
  
namespace Microsoft.Samples.BizTalk.CustomFunctoid  
{  
    /// <summary>  
    /// Performs a string concatenation using inline code.  
    /// </summary>  
    public class CustomStringConcatFunctoid : BaseFunctoid  
    {  
        public CustomStringConcatFunctoid()  
            : base()  
        {  
            //ID for this functoid  
            this.ID = 6001;  
  
            // Resource assembly must be ProjectName.ResourceName if building with VS.Net  
            SetupResourceAssembly("Microsoft.Samples.BizTalk.CustomFunctoid.CustomFunctoidResources", Assembly.GetExecutingAssembly());  
  
            // Pass the resource ID names for functoid name, tooltip  
            // description and the 16x16 bitmap for the Map palette  
            SetName("IDS_CUSTOMSTRINGCONCATFUNCTOID_NAME");  
            SetTooltip("IDS_CUSTOMSTRINGCONCATFUNCTOID_TOOLTIP");  
            SetDescription("IDS_CUSTOMSTRINGCONCATFUNCTOID_DESCRIPTION");  
            SetBitmap("IDB_CUSTOMSTRINGCONCATFUNCTOID_BITMAP");  
  
            // Put this string handling function under the String   
            // Functoid tab in the Visual Studio toolbox for functoids  
            this.Category = FunctoidCategory.String;  
  
            // 2 required parameters, no optional parameters  
            this.SetMinParams(2);  
            this.SetMaxParams(2);  
  
            // Functoid accepts two inputs  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
  
            // Set the output connection type  
            this.OutputConnectionType = ConnectionType.AllExceptRecord;  
  
            // Declare support for CSharp inline function and  
            // pass the method implementation to the buffer  
            AddScriptTypeSupport(ScriptType.CSharp);  
            SetScriptBuffer(ScriptType.CSharp, GetCSharpBuffer());  
        }  
  
        private string GetCSharpBuffer()  
        {  
            StringBuilder builder = new StringBuilder();  
  
            builder.Append("public string ConCatStrings(string val1, string val2)\n");  
            builder.Append("{\n");  
            builder.Append("    return val2+val1;\n");  
            builder.Append("}\n");  
  
            return builder.ToString();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a512-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a512-158">See Also</span></span>  
 <span data-ttu-id="1a512-159">[使用 BaseFunctoid](../core/using-basefunctoid.md) </span><span class="sxs-lookup"><span data-stu-id="1a512-159">[Using BaseFunctoid](../core/using-basefunctoid.md) </span></span>  
 <span data-ttu-id="1a512-160">[開發自訂參考運算質](../core/developing-a-custom-referenced-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="1a512-160">[Developing a Custom Referenced Functoid](../core/developing-a-custom-referenced-functoid.md) </span></span>  
 [<span data-ttu-id="1a512-161">自訂運算質 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="1a512-161">Custom Functoid (BizTalk Server Sample)</span></span>](../core/custom-functoid-biztalk-server-sample.md)