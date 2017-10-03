---
title: "MIME （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send pipelines, MIME/SMIME Encoder [pipeline component]
- examples, send pipelines
- MIME/SMIME Encoder [pipeline component], send pipelines
- MIME/SMIME Encoder [pipeline component], examples
- examples, MIME/SMIME Encoder [pipeline component]
ms.assetid: f76c720d-3798-4f15-a5f9-885ddf421d57
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e948aeca31d3eb9908d6933f5ac375bce206761
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mime-biztalk-server-sample"></a>MIME （BizTalk Server 範例）
MIME 範例會示範如何在傳送管線內執行 MIME 編碼。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例會將 MIMEIn 資料夾設定為接收位置。 將檔案 (例如範例檔案 ImageInput.gif) 放置於此資料夾時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用下列步驟處理此檔案中的訊息：  
  
1.  從接收位置資料夾 MIMEIn 擷取訊息檔案。  
  
2.  在接收管線中，將訊息維持不變傳遞通過。  
  
3.  在 MessageBox 資料庫中，將訊息路由至傳送管線。  
  
4.  在傳送管線中，執行 MIME 編碼，並將檔案放到傳送配接器資料夾 MIMEOut 中。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*範例路徑*> \Pipelines\MIME\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|Cleanup.bat|用來解除部署組件，並將這些組件從全域組件快取 (GAC) 移除。 移除傳送埠和接收埠。 視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|ImageInput.GIF|範例輸入檔案。|  
|SampleMimeEncoding.btproj<br /><br /> SampleMimeEncoding.sln|這個範例的專案及解決方案檔案。|  
|SampleMimeEncodingBinding.xml|用於自動化設定，例如連接埠繫結。|  
|SendMimePipeline.btp|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會以 MIME 編碼器元件來傳送管線檔案。|  
|Setup.bat|用來建置和初始化此範例。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 請使用下列程序，建置和初始化 MIME 範例。  
  
#### <a name="to-build-and-initialize-this-sample"></a>若要建置並初始化這個範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*> \Pipelines\MIME  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   在此資料夾中建立此範例的輸入 (MIMEIn) 和輸出 (MIMEOut) 資料夾。  
  
         \<*範例路徑*> \Pipelines\MIME  
  
    -   為此範例編譯 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  
  
    -   建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。  
  
        > [!NOTE]
        >  此範例會在建立和繫結連接埠時顯示警告，如下所示：  
  
        > [!NOTE]
        >  `Warning: Receive handler not specified for receive location "MIMEReceiveLocation"; updating with first receive handler with matching transport type.`  
  
        > [!NOTE]
        >  您可以安全地忽略這些警告。 (繫結檔案已省略主控件名稱與接收處理常式，以配合使用者安裝中可能的命名差異)。  
  
    -   啟用接收位置並啟動傳送埠。  
  
> [!NOTE]
>  如果您從安裝位置以外的位置執行這個範例中，您必須先新增參考**Microsoft.BizTalk.Pipeline.Components**組件。  
  
> [!NOTE]
>  在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。  
  
> [!NOTE]
>  如果您在此範例中選擇開啟並建置專案，而不執行檔案 Setup.bat，必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 請使用這個金鑰組來簽署產生的組件。 若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
## <a name="running-this-sample"></a>執行此範例  
 請使用下列程序來執行 MIME 範例。  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  將檔案 ImageInput.gif 的複本放到 MIMEIn 資料夾中。  
  
2.  請注意在 MIMEOut 資料夾中建立的文字檔。 這個文字檔的名稱是以訊息識別碼 GUID 為根據。 這個檔案包含輸入檔 ImageInput.gif 的 MIME 編碼內容。  
  
## <a name="see-also"></a>另請參閱  
 [管線 （BizTalk Server 範例資料夾）](../core/pipelines-biztalk-server-samples-folder.md)