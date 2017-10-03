---
title: "HTTPRequestResponse |Microsoft 文件"
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
ms.assetid: 81c66f61-d86c-49cf-8d24-21c67c68bc5a
caps.latest.revision: "35"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fad45e80cac2a398507b4288c9ac6f35c887e71b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="httprequestresponse"></a>HTTPRequestResponse
HTTPRequestResponse 範例會示範如何使用 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 網際網路伺服器應用程式發展介面 (Internet Server Application Programming Interface，ISAPI) 篩選器，讓 ASP.NET 應用程式與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程進行通訊。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 在此範例中，ASP.NET 應用程式會提交要求至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ISAPI 篩選器。 協調流程接著會取用此訊息，並使用同步回應將其傳回 ASP.NET 應用程式。 達到之間的整合[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協調流程與 ASP.NET 應用程式利用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]ISAPI 篩選器。  
  
 在此範例中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 ASP.NET 應用程式交換訂單 (po) 和 PO 通知訊息，使用下列步驟：  
  
1.  ASP.NET 應用程式，使用 HTTP 要求，提交 XML PO 訊息到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
2.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]收到 XML PO 訊息建構 XML PO 通知訊息，並再將該訊息傳送至 HTTP 回應中的 ASP.NET 應用程式。  
  
 ASP.NET 應用程式收到 XML PO 通知回應後，會使用從回應中擷取的狀態資訊來重新整理 Web 表單。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 *\<範例路徑 >*\AdaptersUsage\HTTPRequestResponse\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|Cleanup.bat|從全域組件快取 (GAC) 解除部署並移除組件；移除傳送和接收埠；視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。|  
|HTTPRequestResponse.btproj、HTTPRequestResponse.sln|提供 BizTalk 專案的專案和原始程式檔，此專案可以接收 HTTP 要求、處理 PO 訊息，以及發出回應。|  
|HTTPRequestResponseBinding.xml|提供例如連接埠繫結等自動設定的功能。|  
|POAck.xsd、POSchema.xsd|分別提供 PO 通知和 PO .xml 檔案的結構描述。|  
|POReceiveOrchestration.odx|提供[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收 PO 的協調流程加以處理，以及發出 PO 通知。|  
|Setup.bat|建置並初始化此範例。|  
|在 \RequestResponse 資料夾中：<br /><br /> AssemblyInfo.cs、default.aspx、default.aspx.cs、Global.asax、Global.asax.cs、RequestResponse.csproj、RequestResponse.csproj.webinfo、RequestResponse.sln、Web.config|所包含的檔案，構成在本範例中當做驅動程式使用的 ASP.NET 應用程式，其中包括專案和方案檔案、ASPX 檔案、Microsoft Visual C# .NET 原始程式檔等等。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 請使用下列程序，建置和初始化 HTTPRequestResponse 範例。  
  
#### <a name="to-build-and-initialize-this-sample"></a>若要建置並初始化這個範例  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     \<*範例路徑*> \AdaptersUsage\HTTPRequestResponse  
  
2.  執行檔案 Setup.bat，這會執行下列動作：  
  
    -   編譯及設定用來驅動此範例的 ASP.NET 應用程式。  
  
        > [!NOTE]
        >  在 IIS 管理員中建立應用程式集區，設定**DefaultAppPool**以.NET Framework 版本**.Net Framework v4.0**。  
  
    -   編譯及部署此範例中所使用的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。  
  
    -   為這個範例編譯和部署 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。  
  
    -   建立並繫結必要[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]連接埠。  
  
    -   啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程。  
  
        > [!IMPORTANT]
        >  您必須變更實作 Web 應用程式的範例程式碼 (Default.aspx.cs) 以反映您的環境：  
        >   
        >  http://\<*伺服器名稱*>/\<*虛擬 dir*> /BTSHTTPReceive.dll 其中`<servername>`與Web伺服器，您張貼的名稱`<`*虛擬 dir* `>`是這個檔案所在的虛擬目錄。  
  
        > [!NOTE]
        >  在嘗試執行此範例之前，您必須確認 BizTalk 沒有在建置和初始化的程序中報告任何錯誤。  
  
        > [!NOTE]
        >  若您選擇不執行 Setup.bat 檔案就開啟和建置此範例中的專案，您必須先使用 .NET Framework Strong Name Utility (sn.exe) 建立強式名稱金鑰組。 使用此金鑰組簽署所產生的組件。 在嘗試建置專案前，您還必須從 RequestResponse.csproj 檔案中手動移除 default.aspx.resx 和 Global.asax.resx 的參考。  
  
        > [!NOTE]
        >  若要復原 Setup.bat 所進行的變更，請執行 Cleanup.bat。 您必須先執行 Cleanup.bat 才能再度執行 Setup.bat。  
  
        > [!NOTE]
        >  您必須設定和啟用 IIS 才能使用 HTTP 接收配接器。 如需詳細資訊，請參閱[如何設定 HTTP 接收位置的 IIS](../core/how-to-configure-iis-for-an-http-receive-location.md)。  
  
3.  setup.bat 檔會設定此範例的虛擬目錄，以在與預設網站關聯的 IIS 應用程式集區中執行。  若要設定讓此範例中的使用者內容下執行的虛擬目錄**BizTalk Isolated Host Users**和**「 iis_iurs 」**使用者群組，您應該設定執行新的虛擬目錄IIS 應用程式集區。 請依照下列步驟執行，將虛擬目錄設定為在新的 IIS 應用程式集區中執行：  
  
    > [!NOTE]
    >  如果您已經為其他 SDK 範例建立新的應用程式集區，則可以繼續執行下面最後一項步驟。  
  
    1.  按一下**啟動**，指向 **所有程式**，指向 **系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**.  
  
    2.  在**網際網路資訊服務 (IIS) 管理員**，瀏覽至**應用程式集區**資料夾。  
  
    3.  以滑鼠右鍵按一下**應用程式集區**資料夾，然後按一下**新增**，**應用程式集區...**  
  
    4.  輸入的名稱**應用程式集區識別碼：** （例如 biztalksdksamples），確認**新應用程式集區使用預設設定**選項已選取，然後按一下**確定**至建立新的應用程式集區。  
  
    5.  以滑鼠右鍵按一下新的應用程式集區，然後按一下 **屬性**。  
  
    6.  按一下**識別** 索引標籤的 屬性 對話方塊並變更這個應用程式集區執行使用者為成員的身分識別**BizTalk Isolated Host Users**使用者群組。  此使用者也應該屬於本機**「 iis_iurs 」**使用者群組。  
  
    7.  設定這個 SDK 範例的虛擬目錄為在新的應用程式集區下執行。 **應用程式集區**設定位在**虛擬目錄**] 索引標籤的 [虛擬目錄的 [內容] 對話方塊。 為此範例所建立的虛擬目錄為 HttpRequestResponseSample。  
  
## <a name="running-this-sample"></a>執行此範例  
 請使用下列程序執行 HTTPRequestResponse 範例。  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  在 Internet Explorer 中瀏覽至 http://localhost/RequestResponse/。  
  
2.  完成 Web 表單中的必要欄位，然後按一下**訂購**提交訂單。  
  
3.  在收到回應後重新整理 Web 表單時，觀察您的訂單狀態。  
  
## <a name="comments"></a>註解  
 **BTSHTTPReceiveISAPI**延伸此範例中使用設定為在單一電腦預設安裝上運作。 若要擴充此範例以額外的組態，請參閱[HTTP 配接器](../core/http-adapter.md)。  
  
 您可將此範例擴充至一般需透過 Web 表單或 HTTP 提交資料給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的應用程式。 透過擴充此範例的 ASP.NET 應用程式部分，您可以查詢更多資訊，以及在提交資料給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 前先執行其他前置處理。  
  
## <a name="see-also"></a>另請參閱  
 [HTTP 配接器範例](../core/http-adapter-samples.md)