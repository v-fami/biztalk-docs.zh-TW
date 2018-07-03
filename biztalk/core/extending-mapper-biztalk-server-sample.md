---
title: 擴充對應工具 （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Mapper, examples
- XML tools
- BizTalk Mapper, extending
- examples, BizTalk Mapper
- examples, XML tools
ms.assetid: 6010a13f-b715-4766-ad91-5aa9b98589e3
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff0cf33f00688b5b609123a644a5d2a298ecaf01
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995807"
---
# <a name="extending-mapper-biztalk-server-sample"></a>擴充對應工具 （BizTalk Server 範例）
「擴充對應工具」範例會示範如何使用和擴充「BizTalk 對應工具」。 此範例包含數個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 對應檔案 (.btm)，每個檔案都代表「BizTalk 對應工具」的不同功能。  

## <a name="what-this-sample-does"></a>此範例的用途  
 「擴充對應工具」範例會使用根據訊息內容決定路由 (CBR)，而且不會使用協調流程。 藉由對範例傳送埠指定篩選條件，它會直接連接至範例接收埠。 此外，還會對傳送埠指定對應，以套用到處理過的文件。  

## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑\>* \XmlTools\ExtendingMapper  

 下表顯示此範例中的檔案，並描述其用途。  


|                                                                             檔案                                                                             |                                                         描述                                                          |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| MapperClassLibrary\AssemblyInfo.cs、MapperClassLibrary\MapperClassLibrary.csproj、MapperClassLibrary\MapperHelper.cs、MapperClassLibrary\MapperClassLibrary.sln | Microsoft?[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]® 專案檔和 Visual C#® 原始程式檔。 |
|                                                                           Cleanup.bat                                                                           |                      用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。                       |
|                                                                         Destination.xsd                                                                         |                                                         結構描述檔案。                                                         |
|                                                           ExtendingMapper.btproj、ExtendingMapper.sln                                                           |                                     此範例的 BizTalk 專案和方案檔。                                      |
|                                                                       ExtendingMapper.xml                                                                       |                                                         來源 XML。                                                          |
|                                                                   ExtendingMapperBinding.xml                                                                    |                                                         繫結 XML。                                                         |
|                                                                      ExternalAssembly.xml                                                                       |                                                    外部組件 XML。                                                    |
|                                                                      OverridingMapXslt.btm                                                                      |                                                          對應檔案。                                                           |
|                                                                      OverridingMapXslt.xml                                                                      |                                                     覆寫對應 XML。                                                      |
|                                                                     OverridingMapXslt.xslt                                                                      |                                                 覆寫對應樣式表。                                                  |
|                                                                Scriptor_CallExternalAssembly.btm                                                                |                                                       範例對應檔案。                                                       |
|                                                            Scriptor_GlobalVariableInInlineScript.btm                                                            |                                                       範例對應檔案。                                                       |
|                                                                   Scriptor_InlineScripts.btm                                                                    |                                                       範例對應檔案。                                                       |
|                                                                     Scriptor_InlineXslt.btm                                                                     |                                                       範例對應檔案。                                                       |
|                                                         Scriptor_InlineXsltCallingExternalAssembly.btm                                                          |                                                       範例對應檔案。                                                       |
|                                                                  Scriptor_XsltCalltemplate.btm                                                                  |                                                       範例對應檔案。                                                       |
|                                                                            Setup.bat                                                                            |                                           用來建置和初始化範例。                                           |
|                                                                           Source.xsd                                                                            |                                                         結構描述檔案。                                                         |

## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 請使用下列程序，建置和初始化「擴充對應工具」範例。  

#### <a name="to-build-and-initialize-this-sample"></a>若要建置並初始化這個範例  

1. 在命令視窗中，將目錄變更 (**cd**) 至下列資料夾：  

    *\<範例路徑\>* \XmlTools\ExtendingMapper  

2. 執行檔案 Setup.bat，這會執行下列動作：  

   - 建立此範例的輸入 (\In) 和輸出 (\Out) 資料夾。  

   - 為這個範例編譯和部署 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  

   - 建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。  

     如果您要使用 Scriptor_CallExternalAssembly.btm 或 Scriptor_InlineXsltCallingExternalAssembly.btm 對應，請在 Visual Studio 中開啟 ExtendingMapper.sln，然後進行下列修改 (否則請移至步驟 3)：  

   1. 在 [方案總管] 中，開啟 Scriptor_CallExternalAssembly.btm。  

   2. 在對應工具方格中，選取 [指令碼處理] 運算質。  

   3. 在屬性方格中，選取**指令碼**屬性，然後按一下省略符號 （...） 按鈕來設定運算質指令碼。  

   4. 在 **設定指令碼處理運算質**對話方塊中，選取**指令碼運算質組態**，並指定下列項目：  


      |      設定此項       |                           為此值                            |
      |---------------------|--------------------------------------------------------------|
      |   **指令碼類型**   |                      外部組件                       |
      | **指令碼組件** | Microsoft.Samples.BizTalk.ExtendingMapper.MapperClassLibrary |
      |  **指令碼類別**   |    Microsoft.Samples.BizTalk.ExtendingMapper.MapperHelper    |
      |  **指令碼方法**  |                           MyConcat                           |


   5. 從[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]**檔案**功能表上，選擇 **儲存**對應檔案，儲存變更並關閉方案。  

3. 按任何鍵繼續執行 Setup.bat。  

   > [!IMPORTANT]
   >  如果您要使用 Scriptor_InlineXsltCallingExternalAssembly.btm，則必須編輯 ExternalAssembly.xml 檔案。 BizTalk 會使用 ExternalAssembly.xml，將對應工具延伸模組物件註冊命名空間對應至 .NET 組件。 由於參考相依組件時是根據其完整格式名稱 (包括自動產生的公開金鑰 Token)，所以您必須更新此值。 如果您不要使用 Scriptor_InlineXsltCallingExternalAssembly.btm，則不需要完成步驟 a 至 e。  

4. 在 Windows 檔案總管中，瀏覽至\<Windows 資料夾\>\assembly\\。  

   1. 以滑鼠右鍵按一下 **[microsoft.samples.biztalk.extendingmapper.mapperclasslibrary]** ，然後選取**屬性**。  

   2. 複製公開金鑰 Token 值。  

   3. 在文字編輯器中，開啟*\<範例路徑\>* \XML Tools\ExtendingMapper\ExternalAssembly.xml。  

   4. 選取  <strong>Assemblyname，version=1.0.0.0，Culture = neutral，PublicKeyToken = 68496d20c737d84b 」</strong>屬性，並取代**PublicKeyToken**值與公開金鑰語彙基元值，但您複製在步驟 c。  

   5. 儲存並關閉 ExternalAssembly.xml。  

   > [!NOTE]
   >  在嘗試執行此範例之前，您應該確認在建置和初始化程序期間沒有報告錯誤。  

#### <a name="to-configure-enlist-and-start-the-send-port"></a>若要設定、登錄和啟動傳送埠  

1. 按一下 **開始**，選取**所有程式**，選取**Microsoft BizTalk Server**，然後選取**BizTalk Server 管理**。  

2. 在 BizTalk Server 管理主控台中，按一下以展開**BizTalk Server 管理**，按一下以展開**BizTalk 群組 [\<servername\>:\<管理資料庫\>]**，然後按一下以展開**應用程式**。  

3. 按一下以展開**ExtendingMapperApplication**，然後按一下**傳送連接埠**。  

4. 在右窗格中，以滑鼠右鍵按一下**傳送埠**，然後按一下**屬性**。  

5. 在  **extendingmappersp – 傳送埠屬性** 對話方塊中，按一下**輸出對應**頁面。  

    在 **地圖**資料行中，從下拉式清單中，選取所需的對應，然後按一下**確定**。 下表說明對應。  


   |                                 要套用的對應屬性                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            描述                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
   |---------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |       Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_CallExternalAssembly        |                                                                                                                                                                                                                                                                                                                                       示範如何呼叫外部.NET 組件中的函式**指令碼處理**」 運算質在對應中，根據這個運算質的輸入參數。 這有助於將任何處理邏輯與對應檔案清楚劃分開來。 此對應檔案會使用本範例隨附的 MapperClassLibrary.dll 組件。                                                                                                                                                                                                                                                                                                                                       |
   |           Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_InlineScripts           |                                                                                                                                                                                                                                                                                                                                                                                                                 示範如何撰寫簡單的內嵌指令碼內**指令碼處理**運算質在對應檔中使用.NET 語言，例如 C#、 Visual Basic.NET 和 jscript.net。                                                                                                                                                                                                                                                                                                                                                                                                                  |
   |   Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_GlobalVariableInInlineScript    |                                                                                                                                                                                                                                                                                                                                                                                        示範如何內嵌指令碼中使用全域變數**指令碼處理**運算質。 全域變數通常用來維護跨不同的對應檔中的狀態資訊**指令碼處理**運算質。                                                                                                                                                                                                                                                                                                                                                                                         |
   |            Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_InlineXslt             |                                                                                                                                                                                                                                                                                                                                   示範如何建構中使用原始內嵌 XSLT 的目的文件結構內**指令碼處理**」 運算質在對應中的。 您可以建構目的文件使用的某些部分**指令碼處理**包含內嵌 XSLT，每當它是不可能這樣做，在使用其他運算質的 BizTalk 對應工具運算質。                                                                                                                                                                                                                                                                                                                                   |
   |         Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_XsltCalltemplate          |                                                                                                                                                                                                                                示範如何使用 XSLT 呼叫範本內的目的地文件中建立結構**指令碼處理**」 運算質在對應中的。 「 XSLT 呼叫範本優於內嵌 XSLT 呼叫範本可以使用參數，因此您可以建立結構會根據輸入參數**指令碼處理**運算質。 您可以建構目的文件使用的某些部分**指令碼處理**包含內嵌 XSLT，每當它是不可能這樣做，在使用其他運算質的 BizTalk 對應工具運算質。                                                                                                                                                                                                                                 |
   | Microsoft.Samples.BizTalk.ExtendingMapper. Scriptor_InlineXsltCallingExternalAssembly |                                                                                                                                                                                                                           示範如何呼叫外部.NET 組件中的內嵌 XSLT 的**指令碼處理**」 運算質在對應中的。 說明您如何可以覆寫**自訂延伸模組 XML**自訂延伸模組檔案 ExternalAssembly_extxml.xml，其中包含要叫用之外部.NET 組件的詳細資料與 BizTalk 對應工具 」 方格的屬性。 您可以建構目的文件使用的某些部分**指令碼處理**運算質包含內嵌 XSLT，當您無法使用其他運算質的對應工具 UI 中這麼做。                                                                                                                                                                                                                           |
   |             Microsoft.Samples.BizTalk.ExtendingMapper. OverridingMapXslt              | 示範如何使用自訂 XSLT 檔案完全覆寫「BizTalk 對應工具」檔案的已編譯 XSLT。 您可以藉由覆寫**自訂 XSL 路徑**屬性並選擇性地**自訂延伸模組 XML** BizTalk 對應工具 」 方格的屬性。 您提供的自訂 XSLT 檔案會包含在執行階段要使用之專案的已編譯 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件中。 在這種情況下，對應檔案 (.btm) 的內容會被忽略。 此對應檔案使用 OverridingMapXslt.xslt 和 overridingmapxslt.xml 做為**自訂 XSL 路徑**並**自訂延伸模組 XML**屬性，分別。<br /><br /> 您可以在 [方案總管] 中驗證對應檔案。 您可以為範本檔，您可以編輯，並使用，然後使用它**自訂 XSL 路徑**BizTalk 對應工具 」 方格的屬性。 只要無法使用「BizTalk 對應工具」產生此 XSLT，您便可尋求這種解決方式。 |

## <a name="running-this-sample"></a>執行此範例  
 請使用下列程序執行「擴充對應工具」範例。  

#### <a name="to-run-this-sample"></a>執行此範例  

1.  輸入檔 extendingmapper.xml 複製到在輸入資料夾的複本*\<範例路徑\>* \XmlTools\ExtendingMapper\In。  

2.  請注意檔案如何轉換和路由傳送至*\<範例路徑\>* \XmlTools\ExtendingMapper\Out 資料夾。 這裡執行的轉換是根據您所套用的對應而來。  

## <a name="see-also"></a>另請參閱  
 [XML 工具 (BizTalk Server Samples 資料夾)](../core/xml-tools-biztalk-server-samples-folder.md)