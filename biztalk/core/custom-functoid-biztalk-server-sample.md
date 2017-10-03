---
title: "自訂運算質 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoids, customizing
- examples, functoids
- functoids, examples
- XML tools
- examples, XML tools
ms.assetid: 9f1eb260-ff62-46f5-a517-57f4e9172b35
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5117bed6ea1116047052359eadcd11754e9f85d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="custom-functoid-biztalk-server-sample"></a>自訂運算質 （BizTalk Server 範例）
「自訂運算質」範例示範如何為 BizTalk 對應工具撰寫自訂運算質。 您可以新增至運算質[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱。 BizTalk 對應工具在焦點時，[工具箱] 中會顯示運算質。  
  
 自訂運算質應該存在於 BizTalk 對應工具組件才能辨識它。 您可以用任何 .NET 相容的語言來撰寫自訂運算質，例如 C# 或 Visual Basic。  
  
 另外，自訂運算質必須衍生自 `Microsoft.BizTalk.BaseFunctoids` 類別，而且它必須藉由覆寫某些方法來提供該些方法的實作 (`BaseFunctoid` 類別定義於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所隨附的 Microsoft.BizTalk.BaseFunctoids.dll 組件中)。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 「自訂運算質」範例實作數個運算質，每個都是衍生自 `BaseFunctoid` 類別而且覆寫數個方法。  
  
 實作自訂運算質時，您可以公開其內嵌程式碼。 內嵌程式碼會執行運算質的計算。 BizTalk 對應工具編譯器會從運算質擷取內嵌程式碼，再於建置專案時將它內嵌於編譯的 XSLT。  
  
 若自訂運算質未公開任何內嵌程式碼，BizTalk 對應工具會產生 XSLT (用來呼叫自訂運算質所在之組件)。 因此，您必須確定自訂運算質組件可在全域組件快取 (GAC) 中使用，這樣 XSLT 引擎才找得到它。 自訂運算質也必須具備唯一的 GUID 屬性。 BizTalk 對應工具會使用 GUID 識別要載入的組件。  
  
> [!IMPORTANT]
>  若您重複使用「自訂運算質」範例程式碼實作自己的運算質，務必將 GUID 屬性變更為唯一的屬性。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑 >*\XmlTools\CustomFunctoid  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|AssemblyInfo.cs|組件資訊 C# 原始程式碼。|  
|CBuildArray.bmp|工具箱點陣圖。|  
|CConcat.bmp|工具箱點陣圖。|  
|CExtractArray.bmp|工具箱點陣圖。|  
|Cleanup.bat|用來解除部署組件，將這些組件從全域組件快取 (GAC) 移除，並刪除 CustomFunctoid.dll。|  
|CLongestString.bmp|工具箱點陣圖。|  
|CMultiply.bmp|工具箱點陣圖。|  
|CustomFunctoid.cs|自訂運算質 C# 原始程式碼。|  
|CustomFunctoid.csproj|自訂運算質 C# 專案。|  
|CustomFunctoid.sln|自訂運算質解決方案。|  
|CustomFunctoidResources.resx|自訂運算質資源。|  
|Setup.bat|用來建置、部署及啟動範例。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 請使用下列程序來建置和初始化「自訂運算質」範例。  
  
#### <a name="to-build-and-initialize-this-sample"></a>若要建置並初始化這個範例  
  
1.  在命令視窗中，將目錄變更 (**cd**) 至下列資料夾：  
  
     \<*範例路徑*> \XmlTools\CustomFunctoid  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   建置範例專案。  
  
    -   將產生的組件複製至 Developer Tools\Mapper Extensions 目錄。  
  
    -   將產生的組件加入至 GAC。  
  
        > [!NOTE]
        >  在嘗試執行此範例之前，您應該確認在建置和初始化程序期間沒有報告錯誤。  
  
## <a name="running-this-sample"></a>執行此範例  
 使用下列程序執行「自訂運算質」範例。  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，按一下 **工具**功能表，然後選取**選擇工具箱項目**。  
  
2.  在**[選擇工具箱項目**對話方塊中，選取**BizTalk 對應工具運算質**] 索引標籤。  
  
3.  按一下**重設**，然後按一下 **確定**。  
  
    > [!NOTE]
    >  如果您的自訂運算質未公開任何內嵌程式碼，請確定可以在 GAC 中使用它的組件。  
  
4.  從**檔案**功能表上，選取**結束**關閉[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
5.  啟動**Visual Studio 命令提示字元**。  
  
6.  在命令提示字元中，輸入**devenv /setup**。  
  
7.  啟動**Microsoft Visual Studio**。  
  
     自訂運算質 （自訂串連運算質，最長字串、 組建陣列運算質，並擷取陣列運算質） 會出現在**字串運算質**工具箱和 「 累計乘法 」 運算質索引標籤會出現在**累計運算質** 索引標籤。  
  
## <a name="removing-this-sample"></a>移除此範例  
 使用下列程序移除「自訂運算質」範例。  
  
#### <a name="to-remove-this-sample"></a>若要移除此範例  
  
1.  移除從運算質[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱。  
  
    > [!WARNING]
    >  在執行 Cleanup.bat 之後，如果您仍然在工具箱中看到過時的自訂運算質 (可能是因為 Visual Studio 在內部進行快取)，請遵循下列程序：  
  
    1.  從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，按一下 **工具**功能表，然後選取**選擇工具箱項目**。  
  
    2.  在**[選擇工具箱項目**對話方塊中，選取**BizTalk 對應工具運算質**] 索引標籤。  
  
    3.  在清單中尋找自訂運算質 （自訂串連運算質、 最長字串、 組建陣列運算質、 擷取陣列 」 運算質和累計乘法）。 按一下對應**核取方塊**以移除運算質，然後按一下**確定**。  
  
     如果上述程序無法解決問題，請遵循下列程序。  
  
    1.  從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，按一下 [**工具箱**時編輯對應以顯示工具箱工具板] 索引標籤。  
  
    2.  以滑鼠右鍵按一下工具箱中，選取**選擇項目**。  
  
    3.  在 選擇項目 對話方塊中，按一下 **重設**，然後按一下 **確定**。  
  
    4.  關閉所有執行個體[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
     如果上述程序無法解決問題，請遵循下列程序。  
  
    1.  啟動**Visual Studio 命令提示字元**身為系統管理員。  
  
    2.  關閉所有執行中的 Visual Studio 執行個體。  
  
    3.  執行下列命令：  
  
         `devenv /resetsettings`  
  
         `devenv /setup`  
  
    4.  您可以從工具箱中手動選取不想要的運算質。 以滑鼠右鍵按一下運算質，然後按一下 **刪除**。  
  
     如果上述程序無法解決問題，請遵循下列程序。  
  
    1.  從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]BizTalk 專案中，按一下 [工具箱] 索引標籤編輯對應以顯示工具箱工具板時。  
  
    2.  按一下**累計運算質**群組。  
  
    3.  以滑鼠右鍵按一下您想要移除，然後選擇 運算的質**刪除**或按下 delete 鍵。  
  
    4.  按一下**字串運算質**群組。  
  
    5.  以滑鼠右鍵按一下您想要移除，然後選擇 運算的質**刪除**或按下 delete 鍵。  
  
2.  在命令視窗中，將目錄變更 (**cd**) 至下列資料夾：  
  
     \<*範例路徑*> \XmlTools\CustomFunctoid  
  
3.  執行 Cleanup.bat 檔案，它會執行下列動作：  
  
    -   從 Developer Tools\Mapper Extensions 目錄刪除組件。  
  
    -   從 GAC 移除組件。  
  
## <a name="classes-or-methods-used-in-this-sample"></a>在此範例中使用的類別或方法  
 [Microsoft.BizTalk.BaseFunctoids.BaseFunctoid](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.basefunctoid.aspx)  
  
## <a name="see-also"></a>另請參閱  
 [使用 BaseFunctoid](../core/using-basefunctoid.md)   
 [XML 工具 （BizTalk Server 範例資料夾）](../core/xml-tools-biztalk-server-samples-folder.md)