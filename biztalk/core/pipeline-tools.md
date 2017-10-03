---
title: "管線工具 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline tools, XMLAsm.exe
- pipeline tools, FFDasm.exe
- Pipeline.exe
- FFDasm.exe
- pipeline tools, XMLDasm.exe
- pipeline tools
- XMLAsm.exe
- pipeline tools, DSDump.exe
- FFAsm.exe
- pipeline tools, FFAsm.exe
- pipeline tools, how to
- pipeline tools, about pipeline tools
- pipeline tools, Pipeline.exe
- utilities, pipeline tools
- XMLDasm.exe
ms.assetid: ca4d053a-1473-4d40-8cd0-1ed3a3af988a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c64b61c1c96b0ad6f9185ccd511d00f6dae2251
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="pipeline-tools"></a>管線工具
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 軟體開發套件 (SDK) 所提供的管線工具可以讓您驗證管線是否正常運作，而不需要設定 BizTalk Server 環境，例如傳送埠/接收埠。 您也可以使用管線工具執行下列工作：  
  
-   對伺服器環境外部的協力廠商管線元件進行偵錯。  
  
-   診斷剖析引擎錯誤訊息。  
  
-   嘗試各種不同的結構描述，同時免除編譯、部署、解除部署和重新編譯的負擔。  
  
-   瀏覽一般檔案和 XML 組合器/解譯器的行為。  
  
-   檢視解譯器輸出，並探索已升級的訊息內容屬性以及這些屬性的值。  
  
-   執行沒有解譯器及組合器元件的傳送/接收管線 (例如，您可以檢視 S/MIME 解碼器的輸出)。  
  
-   僅單獨對管線進行精細的效能測量 (而非整個傳訊子系統)。  
  
## <a name="location-in-sdk"></a>SDK 中的位置  
 \<*安裝路徑*> \SDK\Utilities\PipelineTools  
  
 您可以使用管線工具來執行、偵錯及分析管線以及管線元件 (亦即一般檔案和 XML 組合器/解譯器元件)。  
  
## <a name="file-inventory"></a>檔案庫存  
 下表列出管線工具檔案並說明其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|DSDump.exe|可讓您傾印文件結構描述結構，也就是一或多個 XSD 結構描述在記憶體中的輕量型表示法 (不論是否有一般檔案註解)。 當您發生剖析引擎錯誤 (例如 $Root$0$3$2) 且需要將錯誤解碼時，這個工具就很有用。 $ 後面的數字代表出現在文件結構描述中以 0 為基礎的索引或記錄。|  
|FFAsm.exe|執行一般檔案組合器元件，並透過模擬傳送管線直接叫用該元件，讓您能夠查看它如何將使用者的 XML 文件序列化或組合成一般檔案文件。|  
|FFDasm.exe|執行一般檔案解譯器元件，並透過模擬接收管線直接叫用該元件，讓您能夠查看它如何剖析或是將使用者的一般檔案文件解譯成一或多個 XML 文件。|  
|Pipeline.exe|執行傳送管線或接收管線；接受一或多份輸入文件及其組件、XSD 結構描述和相關資訊；以及在管線執行之後產生輸出文件。 Pipeline.exe 不會存取 BizTalk Server 資料庫，因此可能無法支援內含會存取 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫之 BizTalk Framework 組合器及解譯器元件的管線。|  
|XMLAsm.exe|執行 XML 組合器元件，並透過模擬傳送管線直接叫用該元件，讓您能夠查看它如何將使用者的 XML 文件序列化、組合或封裝成輸出 XML 文件。|  
|XMLDasm.exe|執行 XML 解譯器元件，並透過模擬接收管線直接叫用該元件，讓您能夠查看它如何將使用者的 XML 文件剖析、解譯或解除封裝成一或多份 XML 文件。|  
  
## <a name="usage"></a>使用方式  
 下列各節提供每個檔案的詳細描述。  
  
### <a name="dsdumpexe"></a>DSDump.exe  
 DSDump.exe 可讓您傾印文件結構描述結構，也就是一或多個 XSD 結構描述在記憶體中的輕量型表示法 (不論是否有一般檔案註解)。  
  
 DSDump.exe (文件結構描述傾印工具) 支援下列命令列參數：  
  
```  
DSDump.exe schemaFileName  
```  
  
 如果成功，DSDump 便會將文件結構描述列印至主控台。  
  
### <a name="ffasmexe"></a>FFAsm.exe  
 FFAsm.exe (一般檔案組合器) 支援下列命令列參數：  
  
```  
usage: ffasm document... [-dm documentMask...]-bs bodySchema [ -hs headerSchema ] [ -ts trailerSchema ] [ -c ] [ -d ] [ -sb ] [ -m filenamemask ] [ -en encoding ] [ -v ]  
  
where:  
  document           XML document(s)  
  documentMask       XML document(s) file mask, e.g., c:\\documents\\*.xml  
  bodySchema         Flat File body schema  
  headerSchema       Flat File header schema  
  trailerSchema      Flat File trailer schema  
  -c                 Display assembled FF message on the console  
  -d                 Demote properties  
  -sb                Set body schema(s) as design-time property  
  -m                 Output file name mask (default is %MessageID%)  
  encoding           Output message encoding name (e.g. windows-1252) or   
                         code page (e.g. 936)  
  -v                 Verbose mode  
  
file name macros:  
  %MessageID%        FF message identifier (Guid)  
  %MessagePartID%    FF message part identifier (Guid)  
  
```  
  
 例如，如果您想使用標頭和屬性降級，將三份輸入 XML 文件組合成單一的一般檔案文件，請使用下列命令：  
  
```  
FFAsm.exe file_in1.xml file_in2.xml file_in3.xml –hs myHeaderSchema.xsd –bs myBodySchema.xsd -d  
```  
  
### <a name="ffdasmexe"></a>FFDasm.exe  
 FFDasm.exe (一般檔案解譯器) 支援下列命令列參數：  
  
```  
usage: ffdasm document -bs bodySchema [ -hs headerSchema ] [ -ts trailerSchema ] [ -s ] [ -c ] [ -p ] [ -m filenamemask ] [ -en encoding ] [ -v ]  
  
where:  
  document           Flat File document  
  bodySchema         Flat File body schema  
  headerSchema       Flat File header schema  
  trailerSchema      Flat File trailer schema  
  -s                 Validate document structure  
  -c                 Display disassembled XML message on the console  
  -p                 Display promoted properties on the console  
  encoding           Input message body part encoding name (e.g. windows-1252) or code page (e.g., 396)  
  -m                 Output file name mask (default is %MessageID%)  
  -v                 Verbous mode  
  
file name macros:  
  %MessageID%        XML message identifier (Guid)  
  %MessagePartID%    XML message part identifier (Guid)  
  
```  
  
 例如，如果您想解譯具有標頭、內文和結尾的一般檔案文件，並在主控台上顯示結果，請使用下列命令：  
  
```  
FFDasm.exe file_in.txt –hs myHeaderSchema.xsd –bs myBodySchema.xsd –ts myTrailerSchema.xsd –c  
```  
  
### <a name="pipelineexe"></a>Pipeline.exe  
 Pipeline.exe (管線工具) 支援下列命令列參數：  
  
```  
usage: pipeline ( pipeline[.btp] | -pt pipelineTypeName [ -an assemblyName ] ) -d document... [ -part part... ] [ -s schema[.xsd][:namespace.type]... ] [ -proj project[.btproj] ] [ -p ] [ -c ] [ -t ] [ -m filenamemask ] [ -pm partfilenamemask ] [ -en encoding ] [ -v ]  
  
where:  
  pipeline                Pipeline file name  
  pipelineTypeName     Compiled pipeline assembly qualified type name (e.g.   
"MyPipelines.ReceivePipeline, MyPipelines,   
Version=1.0.0.0, Culture=neutral,   
PublicKeyToken=e03965cb5971ad66" or full name (e.g.   
"MyPipelines.ReceivePipeline") if assembly name is   
specified  
  assemblyName         Compiled pipeline assembly file name (e.g.   
MyPipelines.dll) or name (e.g. "MyPipelines,   
Version=1.0.0.0, Culture=neutral,   
PublicKeyToken=e03965cb5971ad66")  
  document             Input document(s)  
  part                 Input document's part  
  schema               Schema file name  
  namespace            Schema namespace (as in BizTalk project system)  
  type                 Schema type (as in BizTalk project system)  
  project              BizTalk project file  
  -p                   Display promoted context properties for receive and   
send pipelines, and promote context properties for   
send pipelines  
  -c                      Display output document on the console  
  -t                      Display elapsed time of components execution  
  filenamemask         Output message file name mask (default is   
Message_%MessageID%.out)  
  partfilenamemask     Output part file name mask (default is   
Part_%MessagePartID%.out)  
  encoding             Output message encoding name (e.g. windows-1252)   
or code page (e.g. 936)  
  -v                   Verbous mode  
  
note:  
You can specify namespace and type for schemas either using namespace.type notation in schema file reference or by using BizTalk project file.  
  
file name macros:  
  %MessageID%           Message identifier (Guid)  
  %MessagePartID%       Message part identifier (Guid)  
  %MessageNumber%       Message number  
  
```  
  
 例如，如果您想使用 mySchema.xsd 從 ReceivePipeline.btp 檔 (其具有 XML 解譯器和 XML 驗證器元件) 執行接收管線，並將結果顯示在主控台中，請使用下列命令：  
  
```  
Pipeline.exe ReceivePipeline.btp –d file_in.xml –s MySchema.xsd:MyProject.MySchema -c  
  
```  
  
 \-或者-  
  
```  
Pipeline.exe ReceivePipeline.btp –d file_in.xml –s MySchema.xsd –proj MyProject.btproj -c  
  
```  
  
 在第一個範例中，限定的類型名稱 (**MyProject.MySchema**) 的結構描述就會包含做為命令列引數。 在第二個範中，則是從指定的 BizTalk 專案檔案取得結構描述。  
  
 您也可以從已編譯的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案檔案執行管線，如下列範例所示 (此範例使用組件限定類型名稱來參照管線)：  
  
```  
Pipeline.exe -pt "TestBtsProject.ReceivePipeline, TestBtsProject, Version=1.0.0.0, Culture=neutral, PublicKeyToken=e03965cb5971ad66" -d in.xml -s PO.xsd -proj TestBtsProject.btproj –c  
```  
  
 在下列範例中，管線分別由其類型名稱和組件檔案名稱參考：  
  
```  
Pipeline.exe -pt TestBtsProject.ReceivePipeline –an TestBtsProject.dll -d in.xml -s PO.xsd -proj TestBtsProject.btproj –c   
```  
  
 下列範例顯示由其組件名稱所參考的管線：  
  
```  
Pipeline.exe -pt TestBtsProject.ReceivePipeline –an "TestBtsProject, Version=1.0.0.0, Culture=neutral, PublicKeyToken=e03965cb5971ad66" -d in.xml -s PO.xsd -proj TestBtsProject.btproj –c  
```  
  
 Pipeline.exe 會以您用來啟動它的任何認證來執行。 它不會使用一般 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件執行個體執行時所使用的帳戶，因此您可能無法執行內含需要資料庫存取之元件的管線。 請確定您是以擁有所有必要權限的帳戶執行 Pipeline.exe。  
  
 您只能使用 Pipeline.exe 來驗證不含協力廠商自訂元件的自訂管線。 如果您使用 pipeline.exe 來驗證具有協力廠商自訂元件的自訂管線，Pipeline.exe 仍會產生所需的輸出。 但是，如果您部署具有協力廠商自訂元件的同一個自訂管線，在接收埠或傳送埠中使用該管線，然後使用 Pipeline.exe 將訊息提交至管線，則管線將會失敗，BizTalk Server 也會傳回錯誤。  
  
### <a name="xmlasmexe"></a>XMLAsm.exe  
 XMLAsm.exe  (XML 組合器工具) 支援下列命令列參數：  
  
```  
usage: xmlasm document...[-dm documentmask...] -ds documentSchema... [ -es envelopeSchema... ] [ -c ] [ -d ] [ -sd ] [ -m filenamemask ] [ -v ]  
  
where:  
  document           XML document(s)  
  documentMask       XML document(s) file mask, e.g., c:\\documents\\*.xml  
  documentSchema     XML document schema(s)  
  envelopeSchema     XML envelope schema(s)  
  -c                 Display assembled XML message on the console  
  -d                 Demote properties  
  -sd                Set document schema(s) as design-time property  
  -d                 Demote properties  
  -m                 Output file name mask (default is %MessageID%)  
  -v                 Verbous mode  
  
file name macros:  
  %MessageID%        XML message identifier (Guid)  
  %MessagePartID%    XML message part identifier (Guid)  
  
```  
  
 例如，如果您想使用信封，將兩份輸入 XML 文件組合成單一 XML 文件，並在主控台上顯示結果，請使用下列命令：  
  
```  
FFAsm.exe file_in1.xml file_in2.xml–es myEnvelopeSchema.xsd –ds myBodySchema.xsd –c  
```  
  
### <a name="xmldasmexe"></a>XMLDasm.exe  
 XMLDasm.exe 支援下列命令列參數：  
  
```  
usage: xmldasm document -ds documentSchema... [ -es envelopeSchema... ] [ -s ] [ -c ] [ -p ] [ -sd ] [ -se ] [ -m filenamemask ] [ -en encoding ] [ -v ]  
  
where:  
  document           XML document  
  documentSchema     XML document schema(s)  
  envelopeSchema     XML envelope schema(s)  
  -s                 Validate document structure  
  -c                 Display disassembled XML message on the console  
  -p                 Display promoted properties on the console  
  -sd                Set document schema(s) as design-time property  
  -se                Set envelope schema(s) as design-time property  
  -m                 Output file name mask (default is %MessageID%)  
  encoding           Input message body part encoding name (e.g., windows-1252) or code page (e.g., 936)  
  -v                 Verbous mode  
  
file name macros:  
  %MessageID%        XML message identifier (Guid)  
  %MessagePartID%    XML message part identifier (Guid)  
  %MessageNumber%    XML message number  
  
```  
  
 例如，如果您想解譯具有兩個巢狀信封的 XML 文件，並在主控台上顯示結果，請使用下列命令：  
  
```  
XmlDasm.exe file_in.txt –ds myDocumentSchema.xsd –es myEnvelopeSchema1.xsd –es myEnvelopeSchema2.xsd –c  
```  
  
## <a name="see-also"></a>另請參閱  
 [在 SDK 中的公用程式](../core/utilities-in-the-sdk.md)