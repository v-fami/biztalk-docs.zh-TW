---
title: 彙總工具 （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- pipelines, examples
- orchestrations, messages
- examples, pipelines
- messages, correlating to orchestrations
ms.assetid: eb8121df-4f5b-4f36-8228-4b5ad1abfb4e
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 493f4d28214a815aca88f214e5efb9cd883e7192
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="aggregator-biztalk-server-sample"></a>彙總工具 (BizTalk Server 範例)
此範例的目的是要建置使用協調流程和管線的訊息彙總功能。 具體而言，我們將會建立可執行下列作業的協調流程：  
  
1.  接收一組相互關聯的訊息。 訊息會根據從訊息內容擷取的目的地夥伴 URI 資訊來進行相互關聯。  
  
2.  藉由執行 XML 傳送管線，將接收的訊息彙總到單一的交換批次。  
  
3.  每分鐘產生一次 XML 交換訊息，或是在有足夠彙總數量的訊息時立即產生。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑\>*\Pipelines\Aggregator  
  
 下表列出此範例使用的檔案。  
  
|檔案|Description|  
|---------------|-----------------|  
|Aggregator.sln|此範例的 Visual Studio 方案檔案。|  
|AggretatorBinding.xml|此範例的繫結檔案。|  
|Cleanup.bat|用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。 移除傳送埠和接收埠。 視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|Setup.bat|用來建置和初始化此範例。|  
|在 [Aggregate] 資料夾中：<br /><br /> Aggregate.btproj|彙總協調流程所使用的 BizTalk 專案。|  
|在 Aggregator 資料夾中：<br /><br /> Aggregate.odx|協調流程，其可將相互關聯的訊息收集在一起，然後執行傳送管線，將這些訊息組合成單一個交換。|  
|在 [Aggregate] 資料夾中：<br /><br /> SuspendMessage.odx|協調流程，用於擱置無法在彙總協調流程內處理的訊息。|  
|在 PipelinesAndSchemas 資料夾中：<br /><br /> FFReceivePipeline.btp|具有一般檔案解譯器的接收管線|  
|在 PipelinesAndSchemas 資料夾中：<br /><br /> Instance1.txt、Instance2.txt、Instance3.txt、Instance4.txt|此範例的文件執行個體。 Instance1.txt 和 instance2.txt 都應該加入到目的地夥伴交換[ http://www.contoso.com ](http://www.contoso.com/)而 Instance3.txt 和 Instance4.txt 應該加入到目的地夥伴交換[ http://www.northwind.com](http://www.northwind.com/).|  
|在 PipelinesAndSchemas 資料夾中：<br /><br /> Invoice.xsd、InvoiceEnvelope.xsd|輸出交換的文件結構描述和信封結構描述。|  
|在 PipelinesAndSchemas 資料夾中：<br /><br /> PipelinesAndSchemas.btproj|結構描述和管線的 BizTalk 專案。|  
|在 PipelinesAndSchemas 資料夾中：<br /><br /> PropertySchema.xsd|此範例的屬性結構描述。|  
|在 PipelinesAndSchemas 資料夾中：<br /><br /> XMLAggregatingPipeline.btp|傳送管線，其將從協調流程執行，以便將收集到的訊息組合成 XML 交換。|  
  
## <a name="building-and-initializing-the-sample"></a>建置和初始化範例  
 請使用下列程序，建置和初始化此「彙總工具」範例。  
  
#### <a name="to-build-and-initialize-the-aggregator-sample"></a>若要建置和初始化此彙總工具範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<範例路徑\>\Pipelines\Aggregator  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   在此資料夾中建立此範例的輸入 (In) 和輸出 (Out) 資料夾。  
  
         \<範例路徑\>\Pipelines\Aggregator  
  
    -   為此範例編譯 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  
  
    -   建立稱為 "Aggregator Sample" 的新應用程式，並在其中部署此範例組件。  
  
    -   建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。  
  
    -   登錄和啟動協調流程、啟用接收位置，並啟動傳送埠。  
  
         若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 這個金鑰組的用途是簽署產生的組件。  
  
3.  在嘗試執行此範例之前，請確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 未在建置和初始化程序期間報告任何錯誤。  
  
     若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
## <a name="running-the-sample"></a>執行範例  
 請使用下列程序執行「彙總工具」範例。  
  
#### <a name="to-run-the-aggregator-sample"></a>若要執行此彙總工具範例  
  
1.  開啟位於 PipelinesAndSchemas 資料夾中的 Instance1.txt 和 Instance2.txt 檔案，檢查其內容。  
  
     請注意，在檔案的 DestinationPartnerURI 項目包含值http://www.contoso.com 。這個值會用來將這兩個訊息相互關聯，如此它們就可加入到同一個交換中。  
  
     同樣地 Instance3.txt 和 Instance4.txt 檔案具有 DestinationPatnerURI 項目設為http://www.northwind.com 。  
  
     這兩個訊息會一起加入到另一個交換中。  
  
2.  Instance1.txt、 Instance2.txt、 Instance3.txt、 和 Instance4.txt 的文字檔案的複本貼入資料夾中。  
  
3.  彙總協調流程會在收集到 10 則訊息後立即產生輸出交換，或是在 1 分鐘逾時後產生輸出交換。 因此，在 Out 資料夾中的檔案可能會延遲出現。  
  
     若要避免逾時，您可以將四個輸入檔案再貼上四次，以便觸發彙總協調流程產生交換。  
  
4.  觀察在 Out 資料夾中建立的 XML 檔案。其中應該有兩個檔案，也就是每個目的地夥伴 URI 各有一個。  
  
     開啟一個檔案檢查其內容。 該檔案應該包含由一個信封和兩個內部 XML 文件所組成的 XML 交換。  
  
    > [!NOTE]
    >  此範例實作可能會於群組實例中的高負載情況下，造成「已傳遞，未使用訊息」或「完成並有捨棄的訊息」的問題。 每當訊息路由至已經在結束階段的商務程序時，或是每當有未預期的訊息抵達到商務程序時，就會發生這種情況。  
  
## <a name="see-also"></a>另請參閱  
 [管線 (BizTalk Server Samples 資料夾)](../core/pipelines-biztalk-server-samples-folder.md)