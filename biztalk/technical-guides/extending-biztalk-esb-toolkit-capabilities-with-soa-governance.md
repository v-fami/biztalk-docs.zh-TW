---
title: "擴充 BizTalk ESB Toolkit 功能與 SOA 控管 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b66a121b-d86f-4f97-a05f-5141ffe719e8
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f872d24c7c792d01f80463da0e3c27f31d76d8ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="extending-biztalk-esb-toolkit-capabilities-with-soa-governance"></a>擴充 BizTalk ESB Toolkit 功能與 SOA 控管
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]隨附於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是工具和擴充的程式庫集合和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]支援鬆散偶合和動態的傳訊架構的功能。 它當做中介軟體，可提供快速中繼服務和其取用者之間的工具。 啟用執行階段的最大的彈性[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]簡化鬆散偶合的組合的服務端點與服務互動的管理。  
  
 Sentinet BizTalk 伺服器擴充功能增強的功能[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]藉由整合與 Sentinet SOA 控管和 API 管理的軟體解決方案，為 Microsoft 平台。 第一 Sentinet 版[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]擴充功能提供[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]SOA 儲存機制解析程式，將與 BizTalk Server 2013 整合[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]，和 Visual Studio 2012。  
  
 此白皮書討論如何 Sentinet SOA 解析程式擴充[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]功能，如何設定 Sentinet SOA 解析程式，以及展示如何使用 Sentinet SOA 解析程式的範例。  
  
## <a name="esb-toolkit-and-sentinet-soa-resolver"></a>ESB Toolkit 和 Sentinet SOA 解析程式  
 在其他方面，ESB Toolkit 解析程式必須提供下列內容：  
  
-   執行階段解析的服務端點和其組態  
  
-   BizTalk ESB 鬆散偶合的傳訊解決方案。  
  
 Sentinet 提供的強大且完整[SOA 儲存機制](http://www.nevatech.com/sentinet/soa-repository)SOA 整合解決方案，以及進階的 SOA 控管和執行階段可提供管理功能。 結合 Sentinet SOA 儲存機制，提供 Sentinet SOA 解析程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]ESB 架構進階且容易使用 ESB 設定、 動態訊息路由和訊息安全性實作的功能。  
  
 高層級圖顯示 Sentinet SOA 解決器如何納入[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]架構。  
  
 ![使用 BizTalk ESB Toolkit Sentinet](../technical-guides/media/sentinetwp-arch.png "SentinetWP_Arch")  
  
 在執行階段，**端點解析和路由**元件上圖中 （即 ESB Toolkit 解析程式架構的一部分） 使用 （在 Visual Studio 路線設計工具中建立） 的行程文件具現化特定的解析程式，並要求提供服務端點和其設定的解析程式。 行程本身可使用之服務端點參考，來設定，以便解析程式可以使用這個參考來登錄或儲存機制中尋找要求的端點。 在設計階段 （建立路線） 時，不知道服務端點的實際實體位址，且兩者都不是服務所需的安全性原則。 階段，執行階段會使用 ESB Toolkit 解析以設定匝道動態傳送埠的訊息傳送至具有所需的服務安全性設定的實際實體服務位址的服務端點。 如果服務端點位址、 通訊協定或安全性需求的變更僅使用儲存機制登錄/組態已更新。 ESB 或 BizTalk Server 成品的執行階段組態不需要更新。  
  
## <a name="how-does-the-sentinet-resolver-add-value-to-an-esb-toolkit-application"></a>如何沒有 Sentinet 解析程式將值加入至 ESB Toolkit 應用程式？  
 SOA 儲存機制以及使用 Sentinet 解析程式的兩個主要優點為：  
  
-   將用戶端識別指派給已解析的外部服務端點 – 大部分的情況下，解析的 ESB 端點需要特定的用戶端識別來呼叫外部服務 （例如使用者名稱/密碼、 特定的 Windows 帳戶認證或特定的 X.509憑證）。 這是很常見的安全性需求不會適當地處理由其他 ESB 解析程式/登錄它。  
  
-   安全性資訊 – 若要解決先前的限制，限制存取其他解決器可能會使用之 Tmodel 的手動設定，包括複雜的 XML 加上必要的安全性身分識別。 不過，登錄/儲存機制的一部分儲存的安全性資訊不正確的方法。 這會提供服務的安全性詳細資料，例如使用者名稱、 密碼等來存取服務的取用者輕鬆存取。  
  
 Sentinet 解析器和 Sentinet SOA 儲存機制以彈性的方式提供的功能，並安全地將任何特定的用戶端識別指派給已解析的 ESB 端點，透過標準或自訂 WCF 端點行為。 Sentinet 的做法是設定 Sentinet 解析程式，並不 Sentinet SOA 儲存機制的安全性資訊。 使用 Sentinet 解析程式所設定的所有用戶端認證會以加密格式儲存。  
  
 此外，以下是一些使用 Sentinet 解析器和 Sentinet SOA 儲存機制的其他優點。  
  
-   提供完整的 SOA 儲存機制。 儲存機制提供內容的服務中繼資料、 服務身分識別和存取原則，服務版本等等的支援。  
  
-   實體的服務註冊 Sentinet 登錄中上, 傳服務 WSDL 的簡化。  
  
-   完整且容易使用 Sentinet 系統管理主控台。 主控台提供管理服務的所有中繼資料的存取，並與簡單的使用者介面來存取服務作業和其資料結構描述、 服務端點、 安全性原則等相關聯的成品。  
  
-   管理和設定已解析的端點的自訂行為。 Sentinet 解析程式會提供解決端點可完全自訂並可輕鬆地設定端點行為。  
  
-   Sentinet 解析程式設定為不同的搜尋準則的選項。 不但可以定義指派給服務端點，任何關鍵字，或使用服務的路徑指向儲存機制的服務階層架構中的服務。  
  
-   測試功能的進階解析程式。 直接從 Visual Studio 路線設計工具，就可以測試 Sentinet 解析程式設定。 雖然其他的解析程式可以只提供端點的基本屬性的相關資訊，Sentinet 解析程式會提供有關解決端點延伸的資訊。 端點的基本內容，除了 Sentinet 解析程式會顯示之屬性的識別解析 Sentinet 儲存機制中的服務與端點的位置。 路線設計工具可以測試 Sentinet 解析程式和其不同的搜尋準則影響解析結果之前路線本身在執行階段使用。  
  
## <a name="installing-the-sentinet-biztalk-server-extensions"></a>安裝 Sentinet BizTalk 伺服器擴充功能  
 您可以下載並安裝 Sentinet BizTalk 擴充功能，從[這裡](http://www.nevatech.com/download)。 ESB Toolkit、 文件，以及如何使用擴充功能的範例會安裝此擴充功能安裝 Sentinet 解析程式。  
  
 詳細說明如何安裝及設定 Sentinet BizTalk Server 擴充的文件可做為產品下載的一部分。  
  
## <a name="using-the-sentinet-biztalk-server-extensions"></a>使用 Sentinet BizTalk 伺服器擴充功能  
 在本節中，我們看看如何使用 Sentinet BizTalk Server 擴充功能和展示上面提到的功能。  
  
### <a name="prerequisites"></a>必要條件  
 本白皮書中的指示假設您已安裝並設定下列：  
  
-   Visual Studio 2012。  
  
-   BizTalk Server 2013。 如需指示，請參閱[安裝 BizTalk Server 2013](http://msdn.microsoft.com/library/jj248688\(v=bts.80\).aspx)。  
  
-   BizTalk Server ESB Toolkit。 如需指示，請參閱[安裝和設定 Microsoft BizTalk ESB Toolkit](http://msdn.microsoft.com/library/jj684558\(v=bts.80\).aspx)。  
  
-   Sentinet BizTalk Server Extensions。 如需指示，請參閱提供的文件一部分的產品下載[這裡](http://www.nevatech.com/download)。  
  
### <a name="register-a-web-service"></a>註冊 web 服務  
 Sentinet 基礎結構所管理的 web 服務必須登錄儲存機制中。 本白皮書會將所隨附的 WCF 客戶搜尋範例服務使用 Sentinet 安裝套件。  
  
1.  啟動**客戶搜尋**範例 Sentinet 安裝封裝所安裝的服務。 啟動系統管理員身分的客戶搜尋範例中，選取原則的繫結 (例如**wsHttpBinding**)，然後按一下 **啟動**。  
  
2.  一旦服務執行中，按一下 **檢視 Wsdl**連結以瀏覽器開啟的服務中繼資料 URL 與服務 WSDL。 從瀏覽器網址列中複製的中繼資料 URL。  
  
3.  開啟瀏覽器並輸入 URL (`https://[computer-name]/sentinet`) 來啟動 Sentinet 管理主控台。 登入，然後選取**儲存機制**中的根項目**儲存機制**檢視面板。 以滑鼠右鍵按一下**儲存機制**根項目，然後按一下**新增 > 服務 > SOAP**功能表選項。  
  
4.  在**加入服務**對話方塊中，針對**URL 從 WSDL**選項、 貼上您先前複製的服務中繼資料 URL，然後再按一下**下一步**。  
  
     ![新增服務 URL](../technical-guides/media/sentinetwp-addserviceurl.png "SentinetWP_AddServiceURL")  
  
5.  精靈會啟動下載服務中繼資料。 下載完成之後，精靈會顯示 Web 服務樹狀結構。 提供服務的名稱，然後按一下 **完成**上載至 Sentinet 儲存機制的服務中繼資料。  
  
     ![Web 服務結構](../technical-guides/media/sentinetwp-servicestructure.png "SentinetWP_ServiceStructure")  
  
6.  服務會匯入至儲存機制，做為第 1 版。 選取版本，然後選取 結束點。 在**端點詳細資料**] 窗格底部，按一下 [**附件**索引標籤，然後再按一下**修改**。  
  
     ![修改服務端點](../technical-guides/media/sentinetwp-serviceendpoint.png "SentinetWP_ServiceEndpoint")  
  
7.  在端點詳細資料] 索引標籤中，按一下 (**+**) 針對登入**關鍵字**，輸入要與端點相關聯的關鍵字 (例如， **TestKeyword**)，和然後按一下 [**儲存**。 為端點標記 （或識別碼） 使用關鍵字，SOA 儲存機制中。  
  
     ![指定關鍵字](../technical-guides/media/sentinetwp-enterkeyword.png "SentinetWP_EnterKeyword")  
  
 重複上述步驟，以加入新版本的**CustomerSearch**服務，但具有不同的繫結，例如**basicHttpBinding**。 稍後在本白皮書中，我們將示範如何 Sentinet 解決器可以解析為不同的服務 （或相同服務的不同版本） 只要將搜尋關鍵字，服務端點產生關聯。  
  
### <a name="configure-sentinet-resolver"></a>設定 Sentinet 解析程式  
 本節說明如何在簡單的 BizTalk ESB 路線設計師專案中，設定 Sentinet 解析程式，以及如何特別唯一解析之服務端點使用的關鍵字。 本章節也會示範如何測試而不傳送任何 ESB 訊息本身，Visual Studio 中的解決器。  
  
1.  啟動 Visual Studio 並建立**BizTalk ESB 路線設計師**專案。  
  
2.  在 [方案總管] 中，連按兩下路線在路線設計工具中開啟它。  
  
3.  從 [工具箱] 拖曳和卸除**路線服務**圖形設計工具介面上的。  
  
4.  選取**路線服務**圖形，並變更**路線服務的擴充項**屬性**傳訊 Extender**從下拉式清單。  
  
     ![設定訊息擴充項屬性](../technical-guides/media/sentinetwp-setmessageextender.png "SentinetWP_SetMessageExtender")  
  
5.  以滑鼠右鍵按一下**解析程式**中的項目**路線服務**圖形，並按一下**加入新的解析程式**。  
  
     ![加入新的解析程式](../technical-guides/media/sentinetwp-addnewresolver.png "SentinetWP_AddNewResolver")  
  
6.  選取新的解析程式項目、 將它重新命名 (例如**MyResolver**)，而針對**解析程式實作**屬性選取**Sentinet 解析程式擴充功能**。  
  
     ![設定解析程式實作](../technical-guides/media/sentinetwp-addresolverimplementation.png "SentinetWP_AddResolverImplementation")  
  
7.  指定**動作**和**關鍵字**Sentinet 解析程式擴充功能屬性。 若要解決唯一我們稍早加入 Sentinet 儲存機制的服務，我們會使用這些屬性。 沒有其他內容，您可以指定 Sentinet 解析程式擴充功能。 若要了解有關這些屬性的詳細資訊，請參閱 Sentinet BizTalk 延伸模組使用者指南。  
  
    |屬性|Description|  
    |--------------|-----------------|  
    |動作|可唯一識別服務作業呼叫的訊息動作標頭。 此動作標頭是服務 WSDL 的一部分，而且可以找到服務的 WSDL，或從 Sentinet 系統管理主控台使用者介面 （在作業的要求訊息屬性。|  
    |關鍵字|提供的關鍵字 (例如**TestKeyword**) 您指派給 Sentinet 系統管理主控台中的服務。|  
  
     下列螢幕擷取畫面會顯示為指定的動作和關鍵字屬性**MyResolver**組態。  
  
     ![Sentinet Resolvery 組態](../technical-guides/media/sentinetwp-resolverconfig.png "SentinetWP_ResolverConfig")  
  
8.  儲存組態變更。  
  
#### <a name="advanced-resolver-configuration"></a>進階的解析程式組態  
 Sentinet BizTalk 延伸模組組態應用程式修改**Sentinet.BizTalk.config**封裝安裝資料夾的根目錄中找到的檔案 (預設位置是`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Sentinet.BizTalk.config`)。 檔案可以修改外部**Sentinet BizTalk 延伸模組組態**應用程式以提供進階的組態選項。 比方說，在許多實用的 ESB 案例中已解決的端點有不只包含服務端點位址和繫結，但也與特定用戶端身分識別 （使用者名稱/密碼、 特定 Windows 帳戶認證或 X.509 用戶端提供憑證）。 沒有適當的用戶端識別，無法呼叫外部服務 ESB 匝道傳送埠。 Sentinet 解析程式可讓指派提供適當的用戶端端點身分識別的特定端點行為的行程開發人員。 多個端點行為可以是預先設定為在標準的 WCF 端點行為**Sentinet.BizTalk.config**參考檔案，並接著指定的端點行為路線從 Sentinet 解析程式組態，藉由指定的行為名稱**解析端點行為**屬性。  
  
### <a name="test-the-resolver-configuration"></a>測試解析程式設定  
 藉由指定相關的屬性值設定 Sentinet 解析程式之後，您可以測試從 Visual Studio 本身的解析程式。  
  
1.  從設計介面，以滑鼠右鍵按一下您加入 Sentinet 解析程式**路線服務**圖形，，然後按一下**測試解析程式組態**。  
  
     [輸出] 窗格會顯示測試結果，其中的摘錄是類似如下所示：  
  
    ```  
    ***** Resolved Service Endpoint *****  
  
    Service Path and Name          : /CustomerSearch  
    Service Id                     : 2b6d686a-cae1-4b7b-93da-99affef98478  
    Service Version                : 1  
    Endpoint Name                  : WSHttpBinding_ICustomerSearch  
    Endpoint Address               : http://btscloudcar/CustomerSearch/1  
    ```  
  
     請注意，解析程式傳回的端點**CustomerSearch**服務**第 1 版**的搜尋準則 (**TestKeyword**) 連接。  
  
2.  移除**TestKeyword**聯**第 1 版**的**CustomerSearch**服務，並將它與服務的第二個版本的端點產生關聯。  
  
    1.  開啟 Sentinet 系統管理主控台中，按一下**第 1 版**下**CustomerSearch**服務中，按一下 wsHttpBinding 端點，然後按一下**附件**索引標籤，然後再按一下**修改**。  
  
         ![CustomerSearch 服務中移除關鍵字](../technical-guides/media/sentinetwp-removekeyword.png "SentinetWP_RemoveKeyword")  
  
    2.  按一下 針對關鍵字之前刪除的關鍵字，請按一下 輸入 按鈕**是**在訊息方塊，然後按一下**儲存**。  
  
         ![CustomerSearch 服務中移除關鍵字](../technical-guides/media/sentinetwp-removekeyword-2.png "SentinetWP_RemoveKeyword_2")  
  
    3.  現在，將指派相同的關鍵字 (**TestKeyword**) 至**basicHttpBinding**端點**第 2 版**相同服務。  
  
3.  返回 Visual Studio，並測試的解析程式設定一次。 以滑鼠右鍵按一下 加入至 Sentinet 解析程式**路線服務**圖形，，然後按一下**測試解析程式組態**。  
  
     [輸出] 窗格會顯示測試結果，其中的摘錄是類似如下所示：  
  
    ```  
    ***** Resolved Service Endpoint *****  
  
    Service Path and Name          : /CustomerSearch  
    Service Id                     : 5b9e5878-7016-44ab-9f0e-5282a8c3e508  
    Service Version                : 2  
    Endpoint Name                  : BasicHttpBinding_ICustomerSearch  
    Endpoint Address               : http://btscloudcar/CustomerSearch/2  
    ```  
  
4.  請注意如何解決器現在會傳回的詳細資料**第 2 版**的服務即使您沒有變更 ESB 行程應用程式中的任何項目。  
  
 將指定的關鍵字 (**TestKeyword**) 回至第 1 版服務 (與**WSHttpBinding**端點)。  
  
## <a name="using-the-sentinet-biztalk-server-extensions"></a>使用 Sentinet BizTalk 伺服器擴充功能  
 在本節中，我們將探討如何 Sentinet BizTalk 延伸模組，以及 ESB 解析程式，可用來唯一識別服務和服務或用戶端傳送的訊息路由傳送訊息至該服務，以最少或沒有變更。 我們將會測試兩個案例：  
  
-   範例訊息傳送至服務登錄 Sentinet 儲存機制中 （加上附加關鍵字）。 然後變更使用 Sentinet 系統管理主控台之服務的原則繫結傳送另一個範例訊息。 這個案例示範如何變更服務的安全性原則不會影響用戶端應用程式，也不 ESB 行程。  
  
-   範例訊息傳送到服務端點向 Sentinet 儲存機制中 （附加關鍵字）。 然後，將相同的關鍵字附加至另一個版本的相同的服務，並再次傳送訊息。 這個案例示範如何自動附加至不同的服務版本的關鍵字將訊息路由傳送至新的服務版本。  
  
 若要測試這些案例，我們將使用下列的範例：  
  
-   **客戶搜尋服務**隨附 Sentinet 安裝程式。 從 [開始] 功能表可以啟動此服務。  
  
-   **Nevatech.Vsb.BizTalk.Samples** Sentinet 安裝程式所提供的方案。 此範例位於`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples`。  
  
-   ESB。Itinerary.Test 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。 這將會位於`<install drive>:\Program Files (x86)\Microsoft BizTalk ESB Toolkit\ESBSource.zip\Source\Samples\Itinerary\Source\ESB.Itinerary.Test`和用來測試客戶搜尋服務的範例訊息。  
  
#### <a name="to-test-the-sentinet-resolver-by-changing-the-service-policy-binding"></a>若要變更服務原則繫結測試 Sentinet 解析程式  
  
1.  請確定**CustomerSearch**您部署使用 wsHttpBinding 的服務正在執行。  
  
2.  從**Nevatech.Vsb.BizTalk.Samples**範例中，開啟**CustomerSearch.Search.itinerary**，選取**解決服務端點**下**訊息Extender**內**郵件路由**圖形，以及**關鍵字**屬性，指定關鍵字，例如**TestKeyword**。  
  
     ![指派關鍵字](../technical-guides/media/sentinetwp-assignkeyword.png "SentinetWP_AssignKeyword")  
  
3.  將變更儲存至路線，並將模型匯出。 在路線設計工具介面上按一下滑鼠右鍵，並按一下**匯出模型**。  
  
4.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**Microsoft.Practices.ESB**應用程式中，按一下 匯入，然後按一下 繫結。 ESB 解析程式的範例位置，在瀏覽`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver`，並開啟**BizTalk.Bindings.xml**檔案。 這會建立**Sentinet 請求-回應**和**Sentinet 單向**傳送範例行程所需的連接埠。  
  
     此外，請確定所有傳送埠和接收位置的**Microsoft.Practices.ESB** BizTalk 應用程式會登錄並啟動。  
  
5.  開啟**ESB。Itinerary.Test**應用程式，建置它，並執行它。 在啟動路線測試用戶端，執行下列步驟：  
  
    1.  在路線測試用戶端，在**Web 服務選項**，清除**使用 WCF 服務**，然後選取**兩個方式服務**。  
  
    2.  從**服務類型**下拉式清單中，選取**傳訊**。  
  
    3.  按一下**負載路線**並瀏覽至**CustomerSearch.Search.Itinerary.xml**檔案位於範例專案**ExportedItineraries**資料夾`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver\ExportedItineraries`.  
  
    4.  按一下省略符號按鈕 (**..**) 下**載入訊息**群組，並瀏覽至**CustomerSearch.Search.Request.xml**位於專案的**SampleMessages** 資料夾`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver\SampleMessages`.  
  
    5.  按一下**送出要求**和確認收到的回應。  
  
6.  在**CustomerSearch**對話方塊中，請注意，此計數器都會增加一個。  
  
7.  在 Sentinet 系統管理主控台中，更新端點詳細資料，以使用 basicHttpBinding，而不是 wsHttpBinding。  
  
    1.  選取服務端點，請按一下**詳細資料**索引標籤，然後再按一下**修改**。  
  
    2.  在**詳細資料**索引標籤上，按一下省略符號 (**...**) 中**原則**區段中，以啟動**修改原則**精靈。  
  
         ![啟動 修改原則精靈](../technical-guides/media/sentinetwp-modifypolicy-1.png "SentinetWP_ModifyPolicy_1")  
  
    3.  在第一個頁面上，保留 原則類型，做為**私人**，然後按一下 **下一步**。  
  
    4.  在第二個頁面上，變更**wsHttpBinding** XML 項目來**basicHttpBinding** （區分大小寫），然後按一下 **完成**。  
  
         ![更新原則的繫結](../technical-guides/media/sentinetwp-modifypolicy-2.png "SentinetWP_ModifyPolicy_2")  
  
    5.  按一下**儲存**將變更儲存到端點詳細資料。  
  
8.  停止**CustomerSearch**服務，變更從繫結**wsHttpBinding**至**basicHttpBinding**，然後再次啟動服務。  
  
     ![重新啟動服務不同的繫結](../technical-guides/media/sentinetwp-restartcustservice.png "SentinetWP_RestartCustService")  
  
9. 從**測試路線用戶端**，客戶搜尋服務再次傳送測試訊息。 請注意，客戶搜尋服務 對話方塊中的計數器一次都會遞增 1。  
  
     一旦成功接收訊息，從 Sentinet 管理主控台中，變更的原則的詳細資料將會回到**wsHttpBinding**。 同樣地，停止**客戶搜尋**服務，請將原則變更回 wsHttpBinding 並啟動服務。  
  
 這示範了如何 Sentinet 儲存機制中的服務詳細資料可以更新目標已更新的服務端點必須立即轉換而不需要變更路線或用戶端。  
  
#### <a name="to-test-the-sentinet-resolver-by-changing-keyword-assignments"></a>若要藉由變更關鍵字指派測試 Sentinet 解析程式  
  
1.  請確定兩個執行個體**CustomerSearch** basicHttpBinding wsHttpBinding 與您部署的服務正在執行。  
  
2.  從**Nevatech.Vsb.BizTalk.Samples**範例中，開啟**CustomerSearch.Search.itinerary**，選取**解決服務端點**下**訊息Extender**內**郵件路由**圖形，以及**關鍵字**屬性，指定關鍵字，例如**TestKeyword**。  
  
     ![指派關鍵字](../technical-guides/media/sentinetwp-assignkeyword.png "SentinetWP_AssignKeyword")  
  
3.  將變更儲存至路線，並將模型匯出。 在路線設計工具介面上按一下滑鼠右鍵，並按一下**匯出模型**。  
  
4.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**Microsoft.Practices.ESB**應用程式中，按一下 匯入，然後按一下 繫結。 ESB 解析程式的範例位置，在瀏覽`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver`，並開啟**BizTalk.Bindings.xml**檔案。 這會建立**Sentinet 請求-回應**和**Sentinet 單向**傳送範例行程所需的連接埠。  
  
     此外，請確定所有傳送埠和接收位置的**Microsoft.Practices.ESB** BizTalk 應用程式會登錄並啟動。  
  
5.  開啟**ESB。Itinerary.Test**應用程式，建置它，並執行它。 在啟動路線測試用戶端，執行下列步驟：  
  
    1.  在路線測試用戶端，在**Web 服務選項**，清除**使用 WCF 服務**，然後選取**兩個方式服務**。  
  
    2.  從**服務類型**下拉式清單中，選取**傳訊**。  
  
    3.  按一下**負載路線**並瀏覽至**CustomerSearch.Search.Itinerary.xml**檔案位於範例專案**ExportedItineraries**資料夾`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver\ExportedItineraries`.  
  
    4.  按一下省略符號按鈕 (**..**) 下**載入訊息**群組，並瀏覽至**CustomerSearch.Search.Request.xml**位於專案的**SampleMessages** 資料夾`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver\SampleMessages`.  
  
    5.  按一下**送出要求**和確認收到的回應。  
  
6.  在**CustomerSearch**對話方塊中，請注意，此計數器都會增加一個。  
  
7.  從 Sentinet 管理主控台中，移除**TestKeyword**聯**第 1 版**的**CustomerSearch**服務，並將它與關聯**第 2 版**的服務。  
  
    1.  開啟 Sentinet 系統管理主控台中，按一下**第 1 版**下**CustomerSearch**服務中，按一下 wsHttpBinding 端點，然後按一下**附件**索引標籤，然後再按一下**修改**。  
  
         ![CustomerSearch 服務中移除關鍵字](../technical-guides/media/sentinetwp-removekeyword.png "SentinetWP_RemoveKeyword")  
  
    2.  按一下 針對關鍵字之前刪除的關鍵字，請按一下 輸入 按鈕**是**在訊息方塊，然後按一下**儲存**。  
  
         ![CustomerSearch 服務中移除關鍵字](../technical-guides/media/sentinetwp-removekeyword-2.png "SentinetWP_RemoveKeyword_2")  
  
    3.  現在，將指派相同的關鍵字 (**TestKeyword**) 至**basicHttpBinding**端點**第 2 版**相同服務。  
  
8.  傳送測試訊息一次從**測試路線用戶端**並請注意，這次，此計數器會遞增在對話方塊中，表示第 2 版服務的 basicHttpBinding 與部署。