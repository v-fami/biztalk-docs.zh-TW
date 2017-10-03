---
title: "HTTPSolicitResponse |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- examples, HTTP adapters
ms.assetid: b149544e-3279-4ac9-b31f-fff3e41ec8e7
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59f5c2821af02fb87727a4096f4b6e586bfd5b4f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="httpsolicitresponse"></a>HTTPSolicitResponse
HTTPSolicitResponse 範例會示範如何建立 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程，以運用 ASP.NET 應用程式協助處理協調流程資料。 在此範例中，協調流程會利用要求/回應埠，將訊息傳送至 ASP.NET 應用程式並擷取回應。 藉由使用 HTTP 配接器，便能整合 BizTalk Server 協調流程與 ASP.NET 應用程式。 如需詳細資訊，請參閱[HTTP 配接器](../core/http-adapter.md)。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 此範例由 BizTalk Server 協調流程組成，它會接收一個包含兩個要相乘之數字的要求，並透過下列步驟順序滿足該要求：  
  
1.  BizTalk Server 協調流程會從特定資料夾接收 .xml 輸入檔。  
  
2.  協調流程會使用 HTTP 要求，將 XML 從檔案轉寄至乘法運算器 ASP.NET 應用程式。  
  
3.  乘法運算器 ASP.NET 應用程式會執行乘法運算，並且傳回 XML 格式的結果，以回應 HTTP 要求。  
  
4.  協調流程會接收 HTTP 回應中 XML 格式的結果，並將該結果寫入特定資料夾的 .xml 檔案中。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 \<*範例路徑*> \AdaptersUsage\HTTPSolicitResponse  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|Cleanup.bat|從全域組件快取 (GAC) 解除部署並移除組件；移除傳送和接收埠；視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|HttpSolicitResponse.btproj、HttpSolicitResponse.sln|為包含協調流程 (會使用乘法運算器 ASP.NET 應用程式、相關結構描述等) 的 BizTalk 專案，提供專案和原始程式檔。|  
|HttpSolicitResponseBinding.xml|提供例如連接埠繫結等自動設定的功能。|  
|MultiplyRequest.xsd、MultiplyResponse.xsd|為乘法運算要求和回應 XML 訊息分別提供結構描述。|  
|MultiplyTwoIntegers.odx|提供 BizTalk Server 協調流程，它會接收要求乘法運算的 .xml 檔案、將該要求轉寄至乘法運算器 ASP.NET 應用程式，並將其回應寫入檔案。|  
|request_in.xml|範例輸入檔案。|  
|Setup.bat|建置並初始化此範例。|  
|在 \Multiplier 資料夾中：<br /><br /> Multiplier.aspx、 Multiplier.aspx.cs、 Multiplier.sln|包含構成實作乘法運算器服務之 ASP.NET 應用程式的檔案，其中包括專案和方案檔、ASPX 檔案、Microsoft Visual C# .NET 原始程式檔等等。|  
  
## <a name="building-and-initializing-the-sample"></a>建置和初始化範例  
 請使用下列程序，建置和初始化 HTTPSolicitResponse 範例。  
  
> [!NOTE]
>  如果接收位置包含任何大寫字元，這個範例便無法運作。  
  
#### <a name="to-build-and-initialize-the-sample"></a>建置和初始化範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*> \AdaptersUsage\HTTPSolicitResponse  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   為此範例建立輸入和輸出資料夾：  
  
         \<*範例路徑*> \AdaptersUsage\HttpSolicitResponse\HttpSolicitResponseInput  
  
         \<*範例路徑*> \AdaptersUsage\HttpSolicitResponse\HttpSolicitResponseOutput  
  
    -   編譯及設定此範例所使用的乘法運算器 ASP.NET 應用程式。  
  
        > [!NOTE]
        >  在 IIS 管理員中建立應用程式集區，設定**DefaultAppPool**以.NET Framework 版本**.Net Framework v4.0**。  
  
    -   編譯及部署此範例中所使用的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。  
  
    -   建立並繫結必要的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置和連接埠。  
  
        > [!NOTE]
        >  此範例會在建立和繫結連接埠時顯示下列警告：  
  
        > [!NOTE]
        >  `Warning: Receive handler not specified for receive location "HttpSolicitResponseReceiveLocation"; updating with first receive handler with matching transport type.`  
  
        > [!NOTE]
        >  `Warning: Host not specified for orchestration "Microsoft.Samples.BizTalk.HttpSolicitResponse.MultiplyTwoIntegers"; updating with first available host.`  
  
    -   啟用接收位置並啟動傳送埠。  
  
        > [!NOTE]
        >  在這個範例中，協調流程會使用雙向連接埠透過 HTTP 與 ASP.NET 應用程式互動。  
  
        > [!NOTE]
        >  在嘗試執行此範例之前，您必須確認 BizTalk 沒有在建置和初始化的程序中報告任何錯誤。  
  
        > [!NOTE]
        >  若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 使用此金鑰組簽署所產生的組件。  
  
        > [!NOTE]
        >  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
## <a name="running-the-sample"></a>執行範例  
 請依照下列程序執行 HTTPSolicitResponse 範例。  
  
#### <a name="to-run-the-sample"></a>執行範例  
  
1.  將 request_in.xml 檔案複本貼入資料夾 HttpSolicitResponseInput。  
  
2.  觀察資料夾 HttpSolicitResponseOutput 中建立的 .xml 檔案。 這個 .xml 檔案的名稱是根據訊息識別碼 GUID 為基礎。 這個檔案包含乘法運算的 XML 格式結果。  
  
    > [!NOTE]
    >  您可以變更輸入檔中的運算元值，執行不同的乘法運算。  
  
## <a name="comments"></a>註解  
 您可以調整這個範例，以便與公開 HTTP 介面的不同外部系統通訊。  
  
 MultiplyRequest.xsd 和 MultiplyResponse.xsd 檔案都是 XML 結構描述，會分別針對乘法運算器 ASP.NET 應用程式定義輸入和輸出資料。 協調流程會使用這些檔案來定義要求和回應訊息類型。  
  
## <a name="see-also"></a>另請參閱  
 [HTTP 配接器範例](../core/http-adapter-samples.md)