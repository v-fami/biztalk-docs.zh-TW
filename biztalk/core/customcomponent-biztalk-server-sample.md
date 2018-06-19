---
title: CustomComponent （BizTalk Server 範例） |Microsoft 文件
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
- messages, streamed
- pipeline components [custom], configuring
ms.assetid: ed0da9f5-8cc7-4528-be8c-35b80744fd38
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fd774848dec1ae54541e749a0cc551bf7c42d49
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969732"
---
# <a name="customcomponent-biztalk-server-sample"></a>CustomComponent （BizTalk Server 範例）
此 CustomComponent 範例會示範如何建立和使用會修改資料流處理訊息的自訂管線元件。 這個範例也會示範使用「管線設計師」對自訂管線元件的設定。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 這個範例會實作自訂管線元件，該元件可以在輸入訊息之前加上字串或是附加字串。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理資料流處理模式中，這表示整個訊息永遠不會載入記憶體中的訊息。 自訂管線元件的示範會依下列步驟順序進行：  
  
1.  BizTalk 從特定資料夾中的檔案擷取文字訊息。  
  
2.  該文字訊息會透過包含 FixMsg 自訂管線元件的接收管線來傳送。 您會設定這個元件，將字串插入到訊息的開頭。  
  
3.  您會使用 FixMsg 自訂管線元件，透過傳送管線來傳送產生的文字訊息。 您會將這個元件設定成將字串附加到訊息的結尾。  
  
4.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會將產生的文字訊息寫入到特定資料夾中的檔案。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*範例路徑*\>\Pipelines\CustomComponent\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|Cleanup.bat|用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。 移除傳送埠和接收埠。 視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|Input.txt|範例輸入檔案。|  
|Setup.bat|用來建置和初始化此範例。|  
|在 \FixMsg 資料夾中：<br /><br /> AssemblyInfo.cs、FixMsg.csproj、FixMsg.sln|此範例之自訂管線元件部分的專案、方案及組件資訊檔案。|  
|在 \FixMsg 資料夾中：<br /><br /> FixMsg.cs|實作管線元件介面。|  
|在 \FixMsg 資料夾中：<br /><br /> FixMsgStream.cs|實作的包裝函式**System.IO.Stream**類別，讓資料流處理資料的程序。|  
|在 \FixMsg 資料夾中：<br /><br /> FixMsgDescription.cs|提供方法來存取和轉譯管線設計師 」 中的元件 UI 資源。|  
|在 \FixMsg 資料夾中：<br /><br /> FixMsg.resx|包含屬性描述、圖示及錯誤訊息。|  
|在 \PipelineComponentSample 資料夾中：<br /><br /> PipelineComponentSample.btproj、PipelineComponentSample.sln|此範例之 BizTalk 專案部分的專案和方案檔案。|  
|在 \PipelineComponentSample 資料夾中：<br /><br /> PipelineComponentSampleBinding.xml|用於自動化設定，例如連接埠繫結。|  
|在 \PipelineComponentSample 資料夾中：<br /><br /> FixMsgReceivePipeline.btp、FixMsgSendPipeline.btp|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管線 (內含 FixMsg 自訂管線元件)，分別代表接收管線和傳送管線。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
  
#### <a name="to-build-and-initialize-the-customcomponent-sample"></a>若要建置和初始化此 CustomComponent 範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*\>\Pipelines\CustomComponent  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   在此資料夾中建立此範例的輸入 (In) 和輸出 (Out) 資料夾。  
  
         \<*範例路徑*\>\Pipelines\CustomComponent  
  
    -   為這個範例編譯和部署 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  
  
    -   建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。  
  
        > [!NOTE]
        >  此範例會在建立和繫結連接埠時顯示下列警告：  
        >   
        >  `Warning: Receive handler not specified for receive location "PCReceiveLocation"; updating with first receive handler with matching transport type.`  
        >   
        >  `Warning: Host not specified for orchestration "CustomComponent"; updating with first available host.`  
        >   
        >  您可以安全地忽略這些警告。 (繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。  
  
    -   啟用接收位置並啟動傳送埠。  
  
> [!NOTE]
>  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。  
  
> [!NOTE]
>  若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 這個金鑰組的用途是簽署產生的組件。  
  
> [!NOTE]
>  若要復原 Setup.bat 所進行的變更，必須先從 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理] MMC 主控台停止並重新啟動主控件執行個體。 接著，執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
## <a name="running-this-sample"></a>執行此範例  
  
#### <a name="to-run-the-customcomponent-sample"></a>若要執行此 CustomComponent 範例  
  
1.  請將文字檔 Input.txt 的複本貼到 In 資料夾中。  
  
2.  請觀察建立於 Out 資料夾中的文字檔。這個檔案所包含的內容，就是開頭由接收管線插入和結尾由傳送管線插入其他文字之 Input.txt 檔案的內容。 這個檔案的名稱的格式是\< *MessageID*\>.xml，其中 *\<MessageID\>* 產生來唯一識別訊息的 GUID.  
  
## <a name="comments"></a>註解  
 您可以依照以下步驟執行，使用 [管線設計師] 來檢視事先設定的管線：  
  
1.  在 [方案總管] 中，按兩下 ReceivePipeline.btp，以便在 [管線設計師] 中開啟接收管線。 觀察 FixMsg 元件會放置在**驗證**接收管線階段。  
  
2.  按一下該 FixMsg 元件，在**驗證**階段設計介面上的。 您可以在 [屬性] 視窗中，查看該管線元件的組態屬性。 觀察**PrependData**屬性設定為**接收管線字串加到前面的資料**。  
  
3.  在 [方案總管] 中，按兩下 SendPipeline.btp，以便在 [管線設計師] 中開啟傳送管線。 觀察 FixMsg 元件會放置在**預先組合**傳送管線階段。  
  
4.  按一下該 FixMsg 元件，在**預先組合**階段設計介面上的。 請注意， **AppendData**屬性設定為**資料在傳送管線字串**。  
  
## <a name="see-also"></a>請參閱  
 [管線 (BizTalk Server Samples 資料夾)](../core/pipelines-biztalk-server-samples-folder.md)