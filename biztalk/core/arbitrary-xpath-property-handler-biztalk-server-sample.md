---
title: 任意 XPath 屬性處理常式 （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], examples
- examples, pipeline components [custom]
ms.assetid: 4eb26c38-5ece-42b0-a28e-73214df1dc41
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f2f59ce48a3d46ebf33889e31a55f9aa452fd17
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="arbitrary-xpath-property-handler-biztalk-server-sample"></a>任意 XPath 屬性處理常式 （BizTalk Server 範例）
「任意 XPath 屬性處理常式」([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 範例) 示範如何撰寫自訂管線元件，以針對提交給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 XML 文件升級特定屬性。 您可以使用範例中包含的功能來建立自訂規則、組合器和解譯器元件，以評估 XPath 運算式。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例包含要進行處理的訂單 (PO) XML 文件 DocInstance.xml， 並且會使用下列步驟來處理 DocInstance.xml：  
  
1.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收埠擷取 DocInstance.xml，再由名為「任意 XPath 屬性處理常式」的自訂管線元件處理。  
  
2.  任意 XPath 屬性處理常式元件會升級所有\<價格\>和\<數量\>PO 結構描述中定義具有任意的 XPath 運算式做為項目。 這個 XPath 運算式也包含位置建構，可搭配 PO 文件根項目的模稜兩可子項目使用。  
  
3.  任意 XPath 屬性處理常式元件判斷訊息類型，並將它升級為訊息內容。  
  
4.  該元件接著將 XML 文件以及升級後的項目傳送至協調流程進一步處理。  
  
5.  協調流程存取 PO 文件中的已升級項目，然後計算 PO 中的項目總數。  
  
6.  協調流程建立新的 PO 文件，其中包含原始 PO 的資訊以及已更新的總計。  
  
7.  將新的 PO 文件寫入至 \Output 目錄中的檔案。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑\>*\Pipelines\ArbitraryXPathPropertyHandler  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|파일|Description|  
|---------------|-----------------|  
|ArbitraryXPathPropertyHandler.sln|自訂管線元件解決方案檔案。|  
|ArbitraryXPathPropertyHandler.resX|資源檔。|  
|ArbitraryXPathPropertyHandlerComp.cs|主要元件實作。|  
|AssemblyInfo.cs|組件資訊。|  
|Cleanup.bat|範例清除檔。|  
|PromotingMap.cs|做為原生 CLR 型別對應實作的屬性升級。|  
|PropertyAttributes.cs|自訂屬性 (Attribute)、屬性 (Property) 描述元和 ICustomTypePropertyDescriptor 實作。|  
|SchemaMap.cs|從訊息類型到 IDocumentSpec 的結構描述對應，以解析結構描述模稜兩可的情形。|  
|Setup.bat|建置和安裝範例管線元件。|  
|VirtualStream.cs|虛擬資料流實作。|  
|SeekableReadOnlyStream.cs|可搜尋的唯讀資料流實作。|  
|ArbitraryXPathSample.sln|範例協調流程解決方案檔案。|  
|CalculateTotalAmount.odx|範例協調流程。|  
|PODocument.xsd|訂單結構描述。|  
|DocInstance.xml|範例訂單執行個體。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 此範例需在同時安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 與 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 的電腦上執行。 如果您的環境不符合此組態，則必須修改「任意 XPath 屬性處理常式」([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 範例)，以指向正確的 SQL Server 電腦。  
  
> [!IMPORTANT]
>  Setup.bat 會假設您的 Microsoft Windows 安裝目錄為 C:\Windows。 如果您的 Windows 安裝在其他目錄，則必須修改 ArbitraryXPathPropertyHandler.csproj 檔案，以在全域組件快取中反映 Microsoft.BizTalk.Component.Utilities 組件的位置。 在 Reference 項目中，變更\<SYSTEMROOT\>至已安裝 Windows 的位置 (例如，C:\WINNT\\)。  
  
```  
<Reference  
  Name = "Microsoft.BizTalk.Component.Utilities"  
  AssemblyName = "Microsoft.BizTalk.Component.Utilities"  
  HintPath = "<SYSTEMROOT>\assembly\GAC\Microsoft.BizTalk.Component.Utilities\3.0.1.0__31bf3856ad364e35\Microsoft.BizTalk.Component.Utilities.dll"  
/>  
```  
  
 請使用下列程序，建置並初始化「任意 XPath 屬性處理常式」([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 範例)。  
  
#### <a name="to-build-and-initialize-this-sample"></a>若要建置並初始化這個範例  
  
1.  在命令視窗中，將目錄變更 (**cd**) 至下列資料夾︰  
  
     *\<範例路徑\>*\Pipelines\ArbitraryXPathPropertyHandler  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   建置「任意 XPath 屬性處理常式」管線元件。  
  
    -   複本建立管線元件來*\<安裝路徑\>*\Pipeline Components 目錄。  
  
    -   建立傳送埠和接收埠。  
  
    -   建立在範例中使用的輸入和輸出目錄。  
  
    -   安裝範例 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程 ArbitraryXPathSample。  
  
    -   將連接埠繫結至範例協調流程。  
  
    -   啟動協調流程。  
  
    > [!NOTE]
    >  建置和初始化期間應不會出現任何錯誤。 如果發生錯誤，請確定您已安裝所有必要軟體，而且 Microsoft 建置工具也位於路徑上。  
  
    > [!NOTE]
    >  若要復原 Setup.bat 所做的變更，必須先從 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理] 主控台停止並重新啟動主控件執行個體。 接著，執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
## <a name="running-this-sample"></a>執行此範例  
 請使用下列程序，執行「任意 XPath 屬性處理常式」([!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 範例)。  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  將訂單 (PO) 檔案 DocInstance.xml 複製到 \Input 目錄。 接收埠會取用這個 PO 檔案，然後將 XML 資料傳送到「任意 XPath 屬性處理常式」管線元件。  
  
2.  檢視 \Output 目錄中的內容。 請注意，這時會建立新的檔案，其中包含您先前複製到 \Input 目錄之 DocInstance.xml 檔案的所有資訊。 在檔案中的差異在於現在\<TotalAmount\>項目已填入了 po 的總容量。  
  
## <a name="comments"></a>註解  
 標準 XPath 運算式是簡單運算式，例如"/ * [local-name =' 項目名稱 'and ='http://MyUri.org'] /\*[local-name =' 項目名稱 '] / @\*[區域名稱 =' 屬性名稱']"。  
  
 任意 XPath 運算式則可以複雜如 "//element-name//*[local-name()='element-name' and position()=2]"。 事實上，如果您的結構描述在 XPath 主體或 XPath 屬性中使用非標準 XPath，便會收到執行階段錯誤，指出 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不支援非標準 XPath 運算式。 要支援任意 XPath 運算式，解決方法是建立自訂解譯器和組合器元件，以支援任意 XPath 主體和任意 XPath 屬性運算式。  
  
 這個範例會使用自訂管線元件中的下列一連串步驟時 **IComponent.Execute** 實作︰  
  
1.  透過輸入訊息內文部分資料流建立虛擬可搜尋資料流 (由於輸入訊息可能很大而且資料流可能無法搜尋，因此它應該只佔用少量的記憶體，而且能夠變更資料流位置)。  
  
2.  建立新的外寄訊息並為其建立新的內文部分、指派虛擬資料流給新的內文部分、複製內文部分屬性以及複製訊息內容。  
  
3.  取得輸入訊息的結構描述，或根據設計階段指定的結構描述。  
  
4.  載入的執行個體中的資料流 **System.Xml.XmlDocument**。  
  
5.  逐一查看升級後的屬性和辨別欄位，再將它們升級或寫入至外寄訊息的訊息內容中。  
  
6.  傳回外寄訊息。  
  
7.  將外寄訊息寫入檔案。  
  
## <a name="see-also"></a>另請參閱  
 [管線 (BizTalk Server Samples 資料夾)](../core/pipelines-biztalk-server-samples-folder.md)