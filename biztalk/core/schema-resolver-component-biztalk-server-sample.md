---
title: 結構描述解析程式元件 （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Flat File Disassembler [pipeline component], examples
- examples, schemas
- schemas, examples
- examples, Flat File Disassembler [pipeline component]
ms.assetid: 9ef68988-c4ee-42d5-83b5-a5c978b2007d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22b59a0606b3cb30827078e28a89d0a51f52c430
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974916"
---
# <a name="schema-resolver-component-biztalk-server-sample"></a>結構描述解析程式元件 （BizTalk Server 範例）
「結構描述解析程式元件」範例會示範如何擴充 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 一般檔案解譯器元件的功能。  
  
 一般檔案解譯器元件通常需要在設計階段定義剖析結構描述。 因此，若您希望在同一個接收位置接收不同的一般檔案文件，通常需要在接收管線加入數個一般檔案解譯器，每個結構描述一個。 在設計階段，會使用管線探查機制選取正確的解譯器元件。 不過，這個方法是高度耗費資源，如果您有多個一般檔案結構描述，因為探查每個對應的解譯器元件會使管線效能降低。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 「結構描述解析程式」元件會示範選取一般檔案解譯器的替代方法。 在此範例中會定義四個結構描述，而每個結構描述訊息的前兩個字元都是唯一的。 會定義唯一的前兩個字元與對應的結構描述之間的對應。 「結構描述解析程式」元件收到輸入訊息時，會讀取前兩個字元，判斷要為對應文件使用哪一個結構描述，再將結構描述資訊儲存於訊息內容，然後呼叫標準一般檔案解譯器元件。 標準一般檔案解譯器元件會從訊息內容讀取結構描述資訊，並用該結構描述剖析文件。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑\>* \Pipelines\SchemaResolverComponent\  
  
 下表顯示此範例所用的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|SchemaResolverSample.sln|執行自訂管線元件的 BizTalk 專案解決方案。|  
|SchemaResolverSample.btproj|執行自訂管線元件的 BizTalk 專案。|  
|SchemaResolverRP.btp|包含自訂元件的接收管線。|  
|PurchaseOrder.xsd, PurchaseRequest.xsd, SalesOrder.xsd, SalesRequest.xsd|一般檔案結構描述。|  
|POInstance.txt, PRInstance.txt, SOInstance.txt, SRInstance.txt|對應的一般檔案文件執行個體。|  
|SchemaResolverFlatFileDasm.sln|管線元件實作的解決方案。|  
|SchemaResolverFlatFileDasm.csproj|管線元件實作的 C# 專案。|  
|SchemaResolverFlatFileDasmComp.cs|管線元件的實作。|  
|SeekableReadOnlyStream.cs|元件所用之可搜尋唯讀資料流的實作。|  
|VirtualStream.cs|管線元件所用之虛擬資料流的實作。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 請使用下列程序，建置和初始化「結構描述解析程式元件」範例。  
  
#### <a name="to-build-and-initialize-this-sample"></a>若要建置並初始化這個範例  
  
1.  在命令視窗中，將目錄變更 (cd) 至下列資料夾：  
  
     *\<範例路徑\>* \Pipelines\SchemaResolverComponent  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   建置元件。  
  
    -   將元件組件複製至 BizTalk \Pipeline 元件資料夾。  
  
    -   建置和部署範例 BizTalk 專案。  
  
    -   設定並啟動接收位置和傳送埠。  
  
    > [!NOTE]
    >  在嘗試執行此範例之前，您應該確認在建置和初始化程序期間沒有報告錯誤。  
  
## <a name="running-this-sample"></a>執行此範例  
 請使用下列程序，執行「結構描述解析程式元件」範例。  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  POInstance.txt、 PRInstance.txt、 SOInstance.txt 和 SRInstance.txt 檔案放入接收位置\<*安裝路徑*\>\SDK\Samples\Pipelines\SchemaResolverComponent\In  
  
2.  觀察寫入的四個.xml 檔案\<Installdir\>\SDK\Samples\Pipelines\SchemaResolverComponent\Out 資料夾。  
  
## <a name="see-also"></a>請參閱  
 [管線 (BizTalk Server Samples 資料夾)](../core/pipelines-biztalk-server-samples-folder.md)