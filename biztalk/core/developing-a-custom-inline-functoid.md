---
title: 開發自訂內嵌運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4533f09f-b62d-4b09-b7de-44541c6cf053
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a742e6a53b5fb81d92922ff94e7754239f723ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22242014"
---
# <a name="developing-a-custom-inline-functoid"></a>開發自訂內嵌運算質
自訂內嵌運算質藉由直接複製實作程式碼到對應中，以提供功能，而不是像自訂參考運算質一樣參考組件、類別和方法名稱。  
  
## <a name="building-inline-script"></a>建置內嵌指令碼  
 有兩種方式可以提供指令碼包含在對應中。 根據您的自訂運算質是否可支援不同數量的參數，從下列方法選擇：  
  
-   覆寫**GetInlineScriptBuffer**當您自訂運算質接受多個輸入參數，而且您已經將**HasVariableInputs**屬性`true`。 例如，若您要串連不同數量的字串或尋找一組值中的最大值，即可使用此方法。  
  
-   使用**SetScriptBuffer**時不需要支援多個輸入參數。 您還是可以使用選擇性的參數，但參數的總數是固定的。  
  
 這兩種方法需要不同的實作。  
  
### <a name="providing-inline-code-with-setscriptbuffer"></a>提供具有 SetScriptBuffer 的內嵌程式碼  
 將您的自訂運算質設定為使用內嵌指令碼：  
  
1.  呼叫**AddScriptTypeSupport**與[Microsoft.BizTalk.BaseFunctoids.ScriptType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx)以啟用內嵌程式碼並設定支援的指令碼類型。  
  
2.  叫用**SetScriptBuffer**設定要用於自訂運算質程式碼。 您將以 `functionNumber` 參數，為自訂累計運算質呼叫此函式三次，並為自訂非累計運算質呼叫此函式一次。  
  
3.  使用 **[setscriptglobalbuffer]** 以宣告您的內嵌程式碼會使用任何全域變數。  
  
4.  使用**RequiredGlobalHelperFunctions**表示您的自訂內嵌運算質所需要的 helper 函式。  
  
 您可以使用 StringBuilder 或常數建置您的指令碼。 撰寫指令碼的一個方法是先撰寫自訂參考運算質，排除所有錯誤之後，複製您的運算質到字串常數，以將它轉換為內嵌。  
  
### <a name="providing-inline-code-with-getinlinescriptbuffer"></a>提供具有 GetInlineScriptBuffer 的內嵌程式碼  
 如果您的自訂內嵌運算質可支援不同數量的參數，您將會覆寫**GetInlineScriptBuffer**。 將您的自訂運算質設定為使用內嵌指令碼：  
  
1.  在建構函式，宣告您的自訂運算質有變數輸入，藉由設定**HasVariableInputs**至`true`。  
  
2.  在建構函式，呼叫**AddScriptTypeSupport**與[Microsoft.BizTalk.BaseFunctoids.ScriptType](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.scripttype.aspx)以啟用內嵌程式碼並設定支援的指令碼類型。  
  
3.  覆寫**GetInlineScriptBuffer**建構及傳回自訂運算質的對應中所使用的程式碼。 檢查 `scriptType` 和 `numParams`，以使用參數建置正確的程式碼。 最後一個參數， `functionNumber`，應該是 0。 這是因為累計函式有固定的數目的輸入，而且不會使用這個機制。  
  
4.  使用 **[setscriptglobalbuffer]** 以宣告您的內嵌程式碼使用全域變數。  
  
5.  使用**RequiredGlobalHelperFunctions**表示您的自訂內嵌運算質所需要的 helper 函式。  
  
 下列程式碼片段建置的 C# 函式有傳入 `numParams` 的參數數目，但沒有函式主體。 若要使用此程式碼片段，可將範例複製到您的解決方案，再新增程式碼以參數執行動作並傳回值。  
  
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
  
## <a name="testing-an-inline-script"></a>測試內嵌指令碼  
 測試在所有開發工作中都是重要的考量。 自訂內嵌運算質可接受測試。 若要簡化此程序，可使用下列的一種或兩種技術：  
  
-   檢查使用自訂內嵌運算質的對應之 XSLT。  
  
-   驗證使用自訂內嵌運算質的對應之輸入和輸出。  
  
### <a name="examine-the-xslt-of-a-map-that-uses-the-custom-inline-functoid"></a>檢查使用自訂內嵌運算質的對應之 XSLT  
 此技術通常可以發現邏輯問題或較容易忽略的語法問題。 也可以協助您瞭解對應中所發生的事。  
  
 檢視對應的 XSLT：  
  
1.  在 Visual Studio BizTalk 專案中，按一下 [**方案總管] 中**索引標籤上，以滑鼠右鍵按一下使用您的自訂內嵌運算質的對應，然後按一下**驗證對應**。  
  
2.  捲動至 [輸出] 視窗，以尋找 XSLT 檔案的 URL。 按 CTRL 再按一下 URL，以檢視檔案。  
  
> [!NOTE]
>  請記住，對 XSLT 檔案所做的任何變更都不會反映在您的自訂運算質中。  
  
### <a name="test-a-map-that-uses-the-custom-inline-functoid"></a>測試使用自訂內嵌運算質的對應  
 這會測試對應和自訂內嵌運算質是否如預期運作。  
  
 測試對應：  
  
1.  在 Visual Studio BizTalk 專案中，按一下 [**方案總管] 中**索引標籤上，以滑鼠右鍵按一下使用您的自訂內嵌運算質的對應，然後按一下**測試對應**。  
  
2.  捲動至 [輸出] 視窗，以尋找輸出檔案的 URL。 按 CTRL 再按一下 URL，以檢視檔案。  
  
 您可以檢查輸入和輸出值，以驗證對應是否如預期運作。  
  
## <a name="example"></a>範例  
 下列範例說明如何建立自訂內嵌運算質以供串連兩個字串。 它依賴包含三個字串資源以及一個 16x16 像素點陣圖資源的資源檔案。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [使用 BaseFunctoid](../core/using-basefunctoid.md)   
 [開發自訂參考運算質](../core/developing-a-custom-referenced-functoid.md)   
 [自訂運算質 （BizTalk Server 範例）](../core/custom-functoid-biztalk-server-sample.md)