---
title: 開發自訂運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77419e1f-9f01-44ac-bf5b-a393f1d17f61
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e5534f3209cb943fb3e2c2a63a18f9e29928be5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22242046"
---
# <a name="developing-custom-functoids"></a>開發自訂運算質
雖然 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供許多運算質支援許多不同的作業，仍可能會遇到一些需要不同解決方法的情況。 自訂運算質提供您一個擴充 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 對應環境中之可用作業範圍的方式。 每個自訂運算質會部署為.NET 組件使用類別衍生自**Microsoft.BizTalk.BaseFunctoids**。 一個組件可包含一個以上的自訂運算質。  
  
 您應該考慮在下列案例中使用自訂運算質：  
  
-   對於使用只能透過專屬舊版 API 存取之資料的字元程式碼欄位，您具有特殊的驗證和轉換規則。  
  
-   您需要使用自訂商務邏輯和金鑰管理來加密或解密欄位。  
  
-   您需要從部分訊息產生雜湊程式碼，以供在另一個應用程式中使用。  
  
-   訊息傳送至其部門的帳戶處理要求包含依每個產品類型的總銷售額摘要資訊。  
  
-   您想要組合幾個相關步驟、使用不同的方式，或是使用新的類別庫，來降低對應的複雜性。  
  
-   有一個以上的對應正在使用指令碼運算質中的相同指令碼。  
  
-   作業失敗時，您需要寫入事件記錄。  
  
 自訂運算質可直接使用內嵌程式碼或間接使用部署至全域組件快取之類別庫中的方法參考，整合至方案中。 這兩種整合依賴**BizTalk.BaseFunctoid**類別，並遵循一組相同的一般步驟：  
  
1.  使用您選擇的 .NET 語言建立新的程式庫專案。  
  
2.  使用強式命名的公用程式 sn.exe 建立 keyfile，並將它指派至專案。  
  
3.  加入參考至 Microsoft.BizTalk.BaseFunctoids.dll。 這個組件包含**BaseFunctoid**基底類別。  
  
4.  建立資源檔案，並將它新增至專案。 新增運算質名稱、工具提示和描述的字串資源。 新增 16x16 像素的影像資源，以在對應設計師工具板上代表運算質。  
  
5.  由衍生自實作運算質類別**BaseFunctoid**中建構函式，建立基本參數，然後寫入運算質方法和任何支援的方法。 此組件可包含多個自訂運算質。  
  
6.  部署該組件，並確定可從 [工具箱] 工具板取得新的運算質。 請參閱[新增和移除自訂運算質從 Visual Studio 工具箱](../core/adding-and-removing-custom-functoids-from-the-visual-studio-toolbox.md)。  
  
 下列是 Floor 運算質的圖例。  
  
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
  
 在 C# 專案中使用此範例程式碼時，“Assembly name” 必須設為 “MultipleFunctoids”。 您的 C# 專案 (包含此程式碼) 應該包含 Resource.resx 檔案。  
  
```  
SetName("NAME_FLOOR");  
SetDescription("DESCRIPTION_FLOOR");  
SetTooltip("DESCRIPTION_FLOOR");  
SetBitmap("IMAGE_FLOOR");  
  
```  
  
 在上述程式碼中，“NAME_FLOOR”、“DESCRIPTION_FLOOR” 和 “DESCRIPTION_FLOOR” 這些值是 Resource.resx 檔案中內嵌的資源字串的「識別碼」。 “IMAGE_FLOOR” 是 Resource.resx 檔案中內嵌的影像的名稱。 此映像做為運算質的圖示。  
  
 如果您未指定適當的資源索引鍵，或如果您刪除 SetName 方法，則沒有名稱的自訂運算質會建立，這不是很好的作法。 SetDescription 和 SetTooltip 方法也是一樣。 請務必正確地使用這些方法，以避免任何不必要的無用行為。 不過，如果您沒有任何適合的影像可做為運算質圖示，您可以略過 SetBitmap 方法。 在此情況下，自訂運算質會使用預設圖示，此舉並沒有害處 (除非有多個無圖示的運算質)。  
  
 如需如何建立自訂運算質的詳細資訊，請參閱[自訂運算質 （BizTalk Server 範例）](../core/custom-functoid-biztalk-server-sample.md)。  
  
> [!IMPORTANT]
>  標準/內建對應工具運算質會保留特定運算質識別碼。 通常，標準的對應工具運算質會使用從 1 到 10000 的識別碼。 在建立自訂運算質時，請勿使用識別碼小於 10000 的運算質。  
  
## <a name="in-this-section"></a>本節內容  
 此部分包含：  
  
-   [使用 BaseFunctoid](../core/using-basefunctoid.md)  
  
-   [開發自訂參考運算質](../core/developing-a-custom-referenced-functoid.md)  
  
-   [開發自訂內嵌運算質](../core/developing-a-custom-inline-functoid.md)  
  
-   [開發自訂累計運算質](../core/developing-a-custom-cumulative-functoid.md)  
  
-   [加入和移除自訂運算質從 Visual Studio 工具箱](../core/adding-and-removing-custom-functoids-from-the-visual-studio-toolbox.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用運算質建立更複雜的對應](../core/using-functoids-to-create-more-complex-mappings.md)