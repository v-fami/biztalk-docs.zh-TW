---
title: 如何使用 BizTalk Web 服務發佈精靈發佈為 Web 服務的協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Web services, publishing
- BizTalk Web Services Publishing Wizard, publishing
- BizTalk Web Services Publishing Wizard
- Web services, orchestrations
- BizTalk Web Services Publishing Wizard, orchestrations
- BizTalk Web Services Publishing Wizard, about BizTalk Web Services Publishing Wizard
- orchestrations, publishing
ms.assetid: d990f8e4-88ce-4718-8a94-63796b8d92dc
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d8c86721091b9a0c9e8436b42a7489e228dbb7e0
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-use-the-biztalk-web-services-publishing-wizard-to-publish-an-orchestration-as-a-web-service"></a>如何使用 BizTalk Web 服務發佈精靈發佈為 Web 服務的協調流程
您可以使用 [BizTalk Web 服務發佈精靈] 將協調流程發佈為 Web 服務。  
  
> [!NOTE]
>  您必須先建置自己的 BizTalk 專案，才可以執行 [BizTalk Web 服務發佈精靈]。  
  
> [!NOTE]
>  您也可以使用命令列工具 BTSWebSvcPub.exe，將協調流程發佈為 Web 服務。 如需詳細資訊，請參閱[BTSWebSvcPub 命令列參照](../core/btswebsvcpub-command-line-reference.md)。  
  
### <a name="to-publish-an-orchestration-as-a-web-service"></a>若要將協調流程發佈為 Web 服務  
  
1.  按一下  **啟動**, ，指向  **所有程式**, ，指向  **Microsoft BizTalk Server**, ，然後按一下  **BizTalk Web 服務發佈精靈**。  
  
2.  在 **歡迎使用 BizTalk Web 服務發佈精靈** 頁面上，按一下 **下一步**。  
  
3.  在 **建立 Web 服務** 頁面上，選取 **BizTalk 協調流程發佈為 web 服務**, ，然後按一下  **下一步**。  
  
4.  在 **BizTalk 組件**  頁面上，BizTalk 組件檔 (\*.dll) 文字方塊中，輸入 BizTalk 組件檔案的名稱，或按一下 **瀏覽** 瀏覽至包含協調流程来發佈組件，然後按一下  **下一步**。  
  
    > [!NOTE]
    >  選擇 BizTalk 組件檔案之前，請將所有相依的組件複製到與 BizTalk 組件相同的資料夾中，或將這些相依組件安裝至「全域組件快取」(GAC)。  
  
    > [!NOTE]
    >  如果您安裝到 GAC 的 BizTalk 組件檔案，請確定在 GAC 中的組件，您會在選取的組件已經更新 **BizTalk 組件** 對話方塊。 如果 GAC 具有相同的完整格式名稱，[BizTalk Web 服務發佈精靈] 就會使用 GAC 中的組件檔案，而非您所選取的檔案。  
  
    > [!NOTE]
    >  如果在包含協調流程的 Visual Studio 中開啟 [BizTalk Web 服務發佈精靈]，BizTalk 組件檔中會填入包含此協調流程的組件。  
  
    > [!NOTE]
    >  長度超過 260 個字元的路徑可能會導致路徑太長的錯誤訊息出現。  
  
5.  在 **協調流程和連接埠** 頁面上，按一下加號展開樹狀節點，每個組件和協調流程。 透過核取對應樹狀節點的核取方塊，選取要發佈的協調流程和連接埠。 如果您想要建立一個 Web 服務 (.asmx) 的所有選取的接收埠，而不是一個 Web 服務，每個接收埠，請選取 **所有選取的連接埠合併成單一 web 服務** 選項，然後再按一下 **下一步**。  
  
    > [!NOTE]
    >  當您將所有選取的連接埠合併成單一 Web 服務時，所有選取的連接埠都會具有相同的連接埠類型，而且這些連接埠中的作業名稱都是唯一的。  
  
6.  在 **Web 服務屬性** 頁面上，於 **web 服務的目標命名空間** 方塊中，輸入 Web 服務的目標命名空間中，選取適當的方塊，以指定精靈應該如何處理 SOAP 標頭和 Web 服務的 SharePoint Portal Server 2007 單一登入 (SSO) 支援。 如果您想要進一步自訂 Web 服務實作中，按一下 [ **進階** ] 按鈕。 如此將顯示更多可用的選項：  
  
    |選項|值|Description|  
    |------------|-----------|-----------------|  
    |SOAP 參數樣式|預設值|這個選項會指定參數在 SOAP 訊息中格式化的方式。 如需詳細資訊，請參閱 < SoapParameterStyle 列舉 >，網址[ http://go.microsoft.com/fwlink/?LinkId=62259 ](http://go.microsoft.com/fwlink/?LinkId=62259)。|  
    |SOAP 參數樣式|Bare|這個選項會指定參數在 SOAP 訊息中格式化的方式。 如需詳細資訊，請參閱 < SoapParameterStyle 列舉 >，網址[ http://go.microsoft.com/fwlink/?LinkId=62259 ](http://go.microsoft.com/fwlink/?LinkId=62259)。|  
    |SOAP 參數樣式|Wrapped|這個選項會指定參數在 SOAP 訊息中格式化的方式。 如需詳細資訊，請參閱 < SoapParameterStyle 列舉 >，網址[ http://go.microsoft.com/fwlink/?LinkId=62259 ](http://go.microsoft.com/fwlink/?LinkId=62259)。|  
    |相容主張|無|這個選項會指定繫結主張所遵詢的「Web 服務互通性」(WSI) 規格。 如需詳細資訊，請參閱 < WebServiceBindingAttribute.ConformsTo 屬性[ http://go.microsoft.com/fwlink/?LinkId=193064 ](http://go.microsoft.com/fwlink/?LinkId=193064)。|  
    |相容主張|WS-I 基本設定檔 1.1|這個選項會指定繫結主張所遵詢的「Web 服務互通性」(WSI) 規格。 如需詳細資訊，請參閱 < WebServiceBindingAttribute.ConformsTo 屬性[ http://go.microsoft.com/fwlink/?LinkId=193064 ](http://go.microsoft.com/fwlink/?LinkId=193064)。|  
    |強制要求回應|[預設]|這個選項會指定單向 BizTalk 作業是否應該公開為要求-回應的 Web 方法。 預設是不強制單向旗標。|  
    |強制要求回應|否|這個選項會指定單向 BizTalk 作業是否應該公開為要求-回應的 Web 方法。 預設是不強制單向旗標。|  
    |強制要求回應|是|這個選項會指定單向 BizTalk 作業是否應該公開為要求-回應的 Web 方法。 預設是不強制單向旗標。|  
  
7.  在 **Web 服務屬性** 頁面上，按一下 **下一步**。  
  
    > [!NOTE]
    >  所有選取的 SOAP 標頭選項，都會全域套用至執行這個精靈執行個體時所建立的所有 Web 服務和 Web 方法。  
  
8.  如果您選取 **新增其他 SOAP 標頭** 選項， **要求 SOAP 標頭** 和 **回應 SOAP 標頭** 頁面會出現。 您可以新增和移除要求和回應 SOAP 標頭，使用 **新增** 和 **移除** 下列對話方塊中的按鈕︰  
  
    -   若要新增 SOAP 標頭，請按一下  **新增**。 在 **BizTalk 組件檔案 (\*.dll)** 文字方塊中，輸入或瀏覽包含 SOAP 標頭結構描述之組件。 **可用的結構描述型別** 清單檢視會顯示結構描述的每個根項目。 選取要新增為要求或回應 SOAP 標頭的根節點。 若要選取多個項目，按住 CTRL 鍵，然後按一下 **確定**。  
  
    -   若要從清單移除的 SOAP 標頭，從已加入的 SOAP 標頭的清單中選取，然後按一下  **移除**。  
  
    -   按一下  **下一步** 每 **SOAP 標頭** 頁面，即可繼續執行精靈。  
  
    > [!NOTE]
    >  目標命名空間和根項目名稱會定義 SOAP 標頭。  
  
    > [!NOTE]
    >  如果目標命名空間/根項目名稱的相同組合新增為要求和回應 SOAP 標頭，它將不會被視為輸入/輸出標頭。 您必須在協調流程內部，手動將內送標頭複製到外寄標頭。  
  
    > [!NOTE]
    >  目標命名空間/根項目名稱的相同組合只能新增為要求 SOAP 標頭和回應 SOAP 標頭各一次。  
  
9. 在 **Web 服務專案** 頁面上，於 **專案名稱** 文字中，輸入專案名稱。 您可以接受預設位置 (http://localhost/<*project_name*>)，輸入中的專案位置**專案位置**文字方塊中或按一下**瀏覽**和選取 Web 目錄。 接著，選取下列任何一個選項：  
  
    -   **覆寫現有的專案。** 這個選項只有在專案位置已經存在時才能使用。 您只能在這個選項已選取時，才能夠發佈至相同的位置。 否則，您必須輸入不同的專案位置。  
  
    -   **允許匿名存取 web 服務。** 這個選項會新增已建立之虛擬目錄的匿名存取。 根據預設，虛擬目錄會從其父虛擬目錄或網站 (如果它是最上層虛擬目錄的話) 繼承存取權限。  
  
    -   **建立 BizTalk 接收位置。** 這個選項會自動建立對應於每個產生之 .asmx 檔案的 SOAP 配接器接收埠和位置。 如果接收位置已經存在，則不會取代該接收位置。 SOAP 配接器會使用格式來解析的接收位置 /\<*虛擬目錄名稱*\>/\<*namespace_typename_portname 協調流程* \>.asmx。 選取這個選項之後，再選擇將產生接收埠和位置的應用程式。  
  
        > [!NOTE]
        >  專案位置可以存在不同的伺服器上。 若要發行到不同的伺服器的 Web 服務，輸入專案名稱，做為**http://&lt*servername*>/<*project_name*>**。  
  
        > [!NOTE]
        >  專案位置可以存在非預設的網站上。 發佈至非預設的網站時，請在 URL 中加入網站的連接埠編號。 例如， http://localhost:8080/< *project_name*>。  
  
        > [!NOTE]
        >  在使用精靈建立接收位置時，精靈會使用預設值來建立接收位置。 接收管線的預設值是 **Microsoft.BizTalk.DefaultPipelines.PassThruReceive** 管線。 如果透過已發佈的 Web 服務收到的訊息需要任何特殊管線處理 (例如驗證、 相互關聯 / 屬性升級或輸入/輸出對應)，則您應該設定接收管線 **Microsoft.BizTalk.DefaultPipelines.XMLReceive**, ，或自訂管線。  
  
        > [!NOTE]
        >  當您從協調流程使用 (呼叫) Web 服務時，SOAP 配接器只支援通過型傳送管線。 您可以使用自訂傳送管線，但它不能包含會修改訊息內文部分的元件。 這些元件包括 XML 組合器和任何編碼元件。  
  
        > [!NOTE]
        >  當您到達此頁面，而您選擇來選擇備份 **結構描述發佈為 web 服務** 選項，請在 **Web 服務** 頁面上，您可能會看到 **Web 服務描述** 顯示從 BizTalk 組件之前您之前選取的服務和方法名稱從回 **BizTalk 協調流程發佈為 web 服務** 選項。 這是因為發佈方法變更時，記憶體中的 Web 服務描述並未清除。  
  
10. 按一下  **下一步** 檢閱您的 ASP.NET Web 服務專案設定。  
  
11. 按一下  **建立** 來建立 ASP.NET Web 服務。  
  
12. 按一下  **完成** 完成 BizTalk Web 服務發佈精靈。  
  
> [!NOTE]
>  如果要在 Windows Vista 上將某個協調流程發佈為 Web 服務，您必須更新裝載服務的虛擬目錄。 若要這樣做，請發出下列命令，從命令提示字元，取代\<vdir\>虛擬目錄的名稱： **%systemroot%\system32\inetsrv\appcmd。EXE 移轉設定"Default Web Site /\<vdir 名稱\>"**。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程發佈為 Web 服務](../core/publishing-an-orchestration-as-a-web-service.md)   
 [如何將協調流程對應至 Web 服務](../core/how-to-map-orchestrations-to-web-services.md)