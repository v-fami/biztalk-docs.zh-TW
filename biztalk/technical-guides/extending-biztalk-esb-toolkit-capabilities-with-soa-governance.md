---
title: 擴充 BizTalk ESB Toolkit 功能使用 SOA 控管 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b66a121b-d86f-4f97-a05f-5141ffe719e8
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a770599e082d2f25062588247acfeb6a0449b974
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977503"
---
# <a name="extending-biztalk-esb-toolkit-capabilities-with-soa-governance"></a>使用 SOA 控管擴充 BizTalk ESB Toolkit 功能
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]隨附[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]且為工具和擴充的程式庫集合[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]支援鬆散偶合和動態的訊息架構的功能。 它是做為提供工具讓您快速中繼服務和其取用者之間的中介軟體。 在執行階段，啟用最大的彈性[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]簡化了鬆散偶合的服務端點的撰寫和管理服務的互動。  
  
 Sentinet BizTalk Server 擴充功能增強的功能[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]藉由整合使用 Sentinet SOA 控管和 API 管理軟體解決方案，適用於 Microsoft 平台。 Sentinet 初版[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]延伸模組供應項目[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]SOA 存放庫解析程式與 BizTalk Server 2013，整合[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]，和 Visual Studio 2012。  
  
 此白皮書會討論如何 Sentinet SOA 解析程式擴充[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]功能，如何設定 Sentinet SOA 解析程式，以及最後的範例，示範如何使用 Sentinet SOA 解析程式。  
  
## <a name="esb-toolkit-and-sentinet-soa-resolver"></a>ESB 工具組和 Sentinet SOA 解析程式  
 除此之外，ESB Toolkit 解析程式必須提供下列各項：  
  
- 執行階段解析服務端點和其組態  
  
- BizTalk ESB 鬆散偶合的傳訊解決方案。  
  
  Sentinet 提供的穩固且全面性[SOA 存放庫](http://www.nevatech.com/sentinet/soa-repository)SOA 整合解決方案，以及進階的 SOA 控管和執行階段，提供管理功能。 結合 Sentinet SOA 存放庫，則 Sentinet SOA 解決程式會提供[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]ESB 架構與進階且容易使用 ESB 組態、 動態的訊息路由和訊息安全性實作的功能。  
  
  高層級圖顯示如何將 Sentinet SOA 解析程式放入[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]架構。  
  
  ![使用 BizTalk ESB 工具組 Sentinet](../technical-guides/media/sentinetwp-arch.png "SentinetWP_Arch")  
  
  在執行階段**端點解析和路由**上圖中 （也就是 ESB Toolkit 解析程式架構的一部分） 的元件會使用路線文件 （在 Visual Studio 路線設計工具中建立） 來具現化特定的解析程式，並要求提供服務端點和其組態的解析程式。 路線本身可使用的參考服務端點，來設定，以便解析程式可以使用這個參考來登錄或儲存機制中找到要求的端點。 在設計階段 （建立路線） 時，不知道服務端點的實際實體位址，並不是服務所需的安全性原則。 在後面的階段中，執行階段會使用 ESB Toolkit 會解析服務端點，以設定出口匝動態傳送埠的訊息傳送至具有必要的服務安全性設定的實際實體的服務位址。 如果服務端點位址、 通訊協定或安全性需求變更只有登錄/存放庫組態已更新。 ESB 或 BizTalk Server 成品的執行階段組態不需要更新。  
  
## <a name="how-does-the-sentinet-resolver-add-value-to-an-esb-toolkit-application"></a>如何沒有 Sentinet 解析程式增加價值至 ESB Toolkit 應用程式？  
 使用 Sentinet 解析程式以及 SOA 存放庫的兩個主要優點如下：  
  
- 將用戶端身分識別指派給已解析的外部服務端點，而大部分的情況下，解決的 ESB 端點都需要特定的用戶端身分識別來呼叫外部服務 （例如使用者名稱/密碼、 特定的 Windows 帳戶認證或特定的 X.509憑證）。 這是很常見的安全性需求不會適當地處理由其他 ESB 解析程式/登錄它。  
  
- 安全性資訊 – 若要解決先前的限制，限制存取其他的解析程式可能會包含所需的安全性身分識別的複雜 XML 中使用 Tmodel 的手動的組態。 不過，登錄/存放庫的一部分儲存安全性資訊不正確的方法。 這會提供服務的安全性詳細資料，例如使用者名稱、 密碼等，以存取服務的取用者輕鬆存取。  
  
  Sentinet 解析器和 Sentinet SOA 存放庫有彈性地提供的功能，並安全地將任何特定的用戶端身分識別指派給已解析的 ESB 端點，透過標準或自訂的 WCF 端點行為。 Sentinet 的做法是設定 Sentinet 解析程式和非 Sentinet SOA 存放庫的安全性資訊。 使用 Sentinet 解析程式設定的所有用戶端認證會以加密形式儲存。  
  
  除了這個以外，以下是一些使用 Sentinet 解析程式和 Sentinet SOA 存放庫的其他優點。  
  
- 提供完整的 SOA 儲存機制。 儲存機制提供存取內容的服務中繼資料、 服務身分識別和原則，適用於服務版本等等的支援。  
  
- 註冊 Sentinet 登錄中的實體服務上傳服務 WSDL 的簡化。  
  
- 完整且方便使用 Sentinet 系統管理主控台。 在主控台提供管理存取所有的服務中繼資料和簡單的使用者介面來存取服務作業和其資料結構描述、 服務端點、 安全性原則等相關聯的成品。  
  
- 管理和設定用於解析端點的自訂行為。 Sentinet 解析程式解析端點，提供可完全自訂，而且可以輕鬆設定的端點行為。  
  
- 若要使用各種不同的搜尋準則設定 Sentinet 解析程式的選項。 路線可以定義指派給服務端點，任何關鍵字，或使用服務的路徑，指向 儲存機制的服務階層架構中的服務。  
  
- 進階測試功能的解析程式。 您可以測試 Sentinet 解析程式設定，直接從 Visual Studio 路線設計工具。 雖然其他的解析程式可以只提供端點的基本屬性的相關資訊，Sentinet 解析程式會提供解決端點的擴充的資訊。 端點的基本內容，除了 Sentinet 解析程式會顯示屬性來識別已解析的服務和端點 Sentinet 存放庫中的位置。 路線設計工具可以測試 Sentinet 解析程式和其不同的搜尋準則影響的方式解析結果之前路線本身在執行階段使用。  
  
## <a name="installing-the-sentinet-biztalk-server-extensions"></a>安裝 Sentinet BizTalk Server 擴充功能  
 您可以下載並安裝 Sentinet BizTalk 延伸模組，從[此處](http://www.nevatech.com/download)。 安裝延伸模組會安裝 Sentinet 解析程式 ESB 工具組、 文件，以及如何使用擴充功能的範例。  
  
 文件詳細說明如何安裝和設定 Sentinet BizTalk Server 延伸模組是可用的產品下載的一部分。  
  
## <a name="using-the-sentinet-biztalk-server-extensions"></a>使用 Sentinet BizTalk Server 擴充功能  
 在本節中，我們看看如何使用 Sentinet BizTalk Server 擴充功能，並展示先前所述的功能。  
  
### <a name="prerequisites"></a>先決條件  
 在本白皮書中的指示假設您已安裝並設定下列：  
  
-   Visual Studio 2012。  
  
-   BizTalk Server 2013。 如需相關指示，請參閱 <<c0> [ 安裝 BizTalk Server 2013](http://msdn.microsoft.com/library/jj248688\(v=bts.80\).aspx)。  
  
-   BizTalk Server ESB 工具組。 如需相關指示，請參閱 <<c0> [ 安裝和設定 Microsoft BizTalk ESB Toolkit](http://msdn.microsoft.com/library/jj684558\(v=bts.80\).aspx)。  
  
-   Sentinet BizTalk Server 擴充功能。 如需指示，請參閱提供的文件作為可用的產品下載的一部分[此處](http://www.nevatech.com/download)。  
  
### <a name="register-a-web-service"></a>註冊 web 服務  
 Sentinet 基礎結構所管理的 web 服務必須在存放庫中註冊。 本白皮書中會使用 Sentinet 安裝套件中隨附的 WCF 客戶搜尋範例服務。  
  
1. 開始**客戶搜尋**範例 Sentinet 安裝套件會安裝的服務。 啟動系統管理員身分的客戶搜尋範例，請選取原則繫結 (例如**wsHttpBinding**)，然後按一下**開始**。  
  
2. 當服務執行時，按一下**檢視 Wsdl**連結以開啟瀏覽器使用服務中繼資料 URL 」 及 「 服務 WSDL。 從瀏覽器網址列中複製的中繼資料 URL。  
  
3. 開啟瀏覽器並輸入 URL (`https://[computer-name]/sentinet`) 來啟動 Sentinet 管理主控台。 登入，然後選取**儲存機制**中的根項目**存放庫**檢視面板。 以滑鼠右鍵按一下**儲存機制**根項目，然後按一下**新增 > 服務 > SOAP**功能表選項。  
  
4. 在**新增服務** 對話方塊中，如**URL 從 WSDL**選項、 貼上您在稍早所複製的服務中繼資料 URL，然後按一下**下一步**。  
  
    ![新增服務 URL](../technical-guides/media/sentinetwp-addserviceurl.png "SentinetWP_AddServiceURL")  
  
5. 精靈會啟動下載服務中繼資料。 下載完成之後，精靈會顯示 Web 服務樹狀結構。 提供服務的名稱，然後按**完成**上傳至 Sentinet 存放庫的服務中繼資料。  
  
    ![Web 服務結構](../technical-guides/media/sentinetwp-servicestructure.png "SentinetWP_ServiceStructure")  
  
6. 服務會匯入至儲存機制，為第 1 版。 選取的版本，，然後選取 結束點。 在 **端點詳細資料** 窗格底部，按一下 **附件**索引標籤，然後再按**修改**。  
  
    ![修改服務端點](../technical-guides/media/sentinetwp-serviceendpoint.png "SentinetWP_ServiceEndpoint")  
  
7. 在端點詳細資料] 索引標籤中，按一下 [(**+**) 針對登入**關鍵字**，輸入要與端點相關聯的關鍵字 (例如**TestKeyword**)，和然後按一下**儲存**。 關鍵字在 SOA 儲存機制中用作為端點標記 （或識別項）。  
  
    ![指定關鍵字](../technical-guides/media/sentinetwp-enterkeyword.png "SentinetWP_EnterKeyword")  
  
   重複上述步驟，以加入新的版本**CustomerSearch**服務，但使用不同的繫結，例如**basicHttpBinding**。 稍後在本白皮書中，我們將示範如何 Sentinet 解析程式可以解析為不同的服務 （或不同版本的相同服務） 只是藉由關聯的服務端點以搜尋關鍵字。  
  
### <a name="configure-sentinet-resolver"></a>設定 Sentinet 解析程式  
 本節說明如何在簡單的 BizTalk ESB 路線設計師專案中，設定 Sentinet 解析程式，尤其是如何使用關鍵字來解析服務端點為唯一。 本章節也會示範如何測試 Visual Studio 本身，而不傳送任何 ESB 訊息中的解決器。  
  
1.  啟動 Visual Studio，建立**BizTalk ESB 路線設計師**專案。  
  
2.  在 [方案總管] 中，按兩下路線，路線設計工具中開啟它。  
  
3.  從 [工具箱] 拖**路線服務**圖形設計工具介面上的。  
  
4.  選取 **路線服務**圖形，並變更**路線服務的擴充項**屬性設**訊息的擴充項**從下拉式清單。  
  
     ![設定訊息的擴充性屬性](../technical-guides/media/sentinetwp-setmessageextender.png "SentinetWP_SetMessageExtender")  
  
5.  以滑鼠右鍵按一下**解析**中的項目**路線服務**圖形，然後按一下**加入新的解析程式**。  
  
     ![加入新的解析程式](../technical-guides/media/sentinetwp-addnewresolver.png "SentinetWP_AddNewResolver")  
  
6.  選取新的解析程式項目，將它重新命名 (例如**MyResolver**)，並針對**解析程式實作**屬性中，選取**Sentinet 解析程式擴充功能**。  
  
     ![設定解析程式實作](../technical-guides/media/sentinetwp-addresolverimplementation.png "SentinetWP_AddResolverImplementation")  
  
7.  指定**動作**並**關鍵字**Sentinet 解析程式擴充功能的屬性。 若要解決唯一我們稍早新增至 Sentinet 存放庫的服務，我們將使用這些屬性。 有其他屬性，您可以指定 Sentinet 解析程式擴充功能。 若要深入了解這些屬性，請參閱 Sentinet BizTalk 延伸模組使用者指南。  
  
    |屬性|描述|  
    |--------------|-----------------|  
    |動作|可唯一識別服務作業，會呼叫訊息動作標頭。 此動作標頭是服務 WSDL 的一部分，而且可在服務 WSDL，或從 Sentinet 系統管理主控台使用者介面 （在下作業的要求訊息屬性。|  
    |關鍵字|提供的關鍵字 (例如**TestKeyword**)，您指派給 Sentinet 系統管理主控台中的服務。|  
  
     下列螢幕擷取畫面會顯示為指定的動作和關鍵字屬性**MyResolver**組態。  
  
     ![Sentinet Resolvery configuration](../technical-guides/media/sentinetwp-resolverconfig.png "SentinetWP_ResolverConfig")  
  
8.  儲存組態變更。  
  
#### <a name="advanced-resolver-configuration"></a>進階的解析程式組態  
 Sentinet BizTalk 延伸模組組態應用程式修改**Sentinet.BizTalk.config**套件安裝資料夾的根目錄中找到的檔案 (預設位置是`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Sentinet.BizTalk.config`)。 可以修改檔案，之外**Sentinet BizTalk 延伸模組組態**應用程式提供進階的組態選項。 例如，在許多實用的 ESB 案例中解析的端點有不只與服務端點位址和繫結，但也與特定用戶端身分識別 （使用者名稱/密碼、 特定 Windows 帳戶認證或 X.509 用戶端提供憑證）。 沒有適當的用戶端身分識別，ESB 出口匝傳送連接埠失敗呼叫外部服務。 Sentinet 解析程式可讓您指派特定的端點行為，提供適當的用戶端端點身分識別的路線開發人員。 多個端點行為可以預先設定為在標準的 WCF 端點行為**Sentinet.BizTalk.config**參考檔案，並接著指定的端點行為 Sentinet 解析程式從路線藉由指定的行為名稱的組態**解析端點行為**屬性。  
  
### <a name="test-the-resolver-configuration"></a>測試的解析程式設定  
 藉由指定相關的屬性值設定 Sentinet 解析程式之後，您可以測試從 Visual Studio 本身的解析程式。  
  
1. 從設計介面，以滑鼠右鍵按一下您加入 Sentinet 解析程式**路線服務**圖形，，然後按一下**測試解析程式組態**。  
  
    [輸出] 窗格會顯示測試結果，其中摘錄是類似於如下所示：  
  
   ```  
   ***** Resolved Service Endpoint *****  
  
   Service Path and Name          : /CustomerSearch  
   Service Id                     : 2b6d686a-cae1-4b7b-93da-99affef98478  
   Service Version                : 1  
   Endpoint Name                  : WSHttpBinding_ICustomerSearch  
   Endpoint Address               : http://btscloudcar/CustomerSearch/1  
   ```  
  
    請注意，解析程式傳回的端點**CustomerSearch**服務**第 1 版**的搜尋準則 (**TestKeyword**) 連結。  
  
2. 移除**TestKeyword**聯**第 1 版**的**CustomerSearch**服務，並將它與服務的第二個版本的端點產生關聯。  
  
   1.  開啟 Sentinet 系統管理主控台中，按一下**第 1 版**下方**CustomerSearch**服務，按一下 wsHttpBinding 端點，然後按一下**附件**索引標籤，然後再按一下**修改**。  
  
        ![移除 CustomerSearch 服務中的關鍵字](../technical-guides/media/sentinetwp-removekeyword.png "SentinetWP_RemoveKeyword")  
  
   2.  按一下 針對關鍵字之前刪除的關鍵字，請按一下 輸入 按鈕**是**在訊息方塊，然後按一下**儲存**。  
  
        ![移除 CustomerSearch 服務中的關鍵字](../technical-guides/media/sentinetwp-removekeyword-2.png "SentinetWP_RemoveKeyword_2")  
  
   3.  現在，將指派相同的關鍵字 (**TestKeyword**) 來**basicHttpBinding**端點**第 2 版**相同的服務。  
  
3. 返回 Visual Studio，並測試的解析程式設定一次。 以滑鼠右鍵按一下您加入 Sentinet 解析程式**路線服務**圖形，，然後按一下**測試解析程式組態**。  
  
    [輸出] 窗格會顯示測試結果，其中摘錄是類似於如下所示：  
  
   ```  
   ***** Resolved Service Endpoint *****  
  
   Service Path and Name          : /CustomerSearch  
   Service Id                     : 5b9e5878-7016-44ab-9f0e-5282a8c3e508  
   Service Version                : 2  
   Endpoint Name                  : BasicHttpBinding_ICustomerSearch  
   Endpoint Address               : http://btscloudcar/CustomerSearch/2  
   ```  
  
4. 請注意如何解決器現在會傳回的詳細資料**第 2 版**的服務即使您沒有變更在 ESB 路線應用程式中的任何項目。  
  
   將指定的關鍵字 (**TestKeyword**) 回到第 1 版的服務 (與**WSHttpBinding**端點)。  
  
## <a name="using-the-sentinet-biztalk-server-extensions"></a>使用 Sentinet BizTalk Server 擴充功能  
 在本節中，我們將探討如何 Sentinet BizTalk 延伸模組，ESB 解析程式，以及可用來唯一識別服務和路由的訊息，該服務，搭配最低限度或完全不變更傳送至服務或用戶端傳送訊息。 我們會測試兩個案例：  
  
- 傳送範例訊息至服務，向 Sentinet 存放庫中 （附加的關鍵字）。 然後，變更服務使用 Sentinet 系統管理主控台原則繫結，並將另一個範例訊息傳送。 這個案例示範如何變更服務的安全性原則都不會影響用戶端應用程式，也不 ESB 路線。  
  
- 將範例訊息傳送到服務端點 （使用附加的關鍵字） Sentinet 存放庫中註冊。 然後，將相同的關鍵字附加至另一個版本的相同的服務，並重新傳送訊息。 這個案例示範如何自動附加至不同的服務版本的關鍵字將訊息路由傳送至新的服務版本。  
  
  若要測試這些情況下，我們將使用下列範例：  
  
- **客戶搜尋服務**隨附 Sentinet 安裝程式。 這項服務可以從 [開始] 功能表啟動。  
  
- **Nevatech.Vsb.BizTalk.Samples** Sentinet 安裝程式隨附的解決方案。 此範例位於`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples`。  
  
- ESB。Itinerary.Test 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。 這可從`<install drive>:\Program Files (x86)\Microsoft BizTalk ESB Toolkit\ESBSource.zip\Source\Samples\Itinerary\Source\ESB.Itinerary.Test`，並用來測試客戶搜尋服務的範例訊息。  
  
#### <a name="to-test-the-sentinet-resolver-by-changing-the-service-policy-binding"></a>若要變更服務原則繫結測試 Sentinet 解析程式  
  
1. 請確定**CustomerSearch**您部署使用 wsHttpBinding 的服務正在執行。  
  
2. 從**Nevatech.Vsb.BizTalk.Samples**範例中，開啟**CustomerSearch.Search.itinerary**，選取**解決服務端點**下**訊息Extender**內**郵件路由**圖形，並針對**關鍵字**屬性，指定關鍵字，例如**TestKeyword**。  
  
    ![指派關鍵字](../technical-guides/media/sentinetwp-assignkeyword.png "SentinetWP_AssignKeyword")  
  
3. 將變更儲存至路線，並將模型匯出。 以滑鼠右鍵按一下在路線設計工具介面上的任何位置，並按一下**匯出模型**。  
  
4. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**Microsoft.Practices.ESB**應用程式中，按一下 匯入，然後按一下 繫結。 瀏覽至 ESB 解析程式範例位置`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver`，然後開啟**BizTalk.Bindings.xml**檔案。 這會建立**Sentinet 請求-回應**並**Sentinet 單向**傳送範例路線所需的連接埠。  
  
    此外，請確定所有傳送埠和接收位置的**Microsoft.Practices.ESB** BizTalk 應用程式會登錄並啟動。  
  
5. 開啟**ESB。Itinerary.Test**應用程式，建置它，並執行它。 在啟動路線測試用戶端，執行下列步驟：  
  
   1.  在路線測試用戶端，底下**Web 服務選項**，清除**使用 WCF 服務**，然後選取**兩個方式服務**。  
  
   2.  從**服務型別**下拉式清單中，選取**Messaging**。  
  
   3.  按一下 **負載路線**並瀏覽至**CustomerSearch.Search.Itinerary.xml**範例專案中的檔案**ExportedItineraries**資料夾`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver\ExportedItineraries`.  
  
   4.  按一下省略符號按鈕 (**...**) 底下**載入訊息**分組，並瀏覽至**CustomerSearch.Search.Request.xml**位於專案的**SampleMessages** 資料夾`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver\SampleMessages`.  
  
   5.  按一下 **送出要求**和確認收到的回應。  
  
6. 在  **CustomerSearch**對話方塊中，請注意，此計數器增加一個。  
  
7. 在 Sentinet 系統管理主控台中，更新端點詳細資料，以使用 basicHttpBinding 而非 wsHttpBinding。  
  
   1.  選取服務端點，然後按一下**詳細資料**索引標籤，然後再按一下**修改**。  
  
   2.  在 **詳細資料**索引標籤上，按一下省略符號 (**...**) 中**原則**區段中，以啟動**修改原則**精靈。  
  
        ![啟動 [修改原則精靈]](../technical-guides/media/sentinetwp-modifypolicy-1.png "SentinetWP_ModifyPolicy_1")  
  
   3.  在第一個頁面上，保留 [做為原則型別**私人**，然後按一下**下一步]**。  
  
   4.  在第二個頁面上，變更**wsHttpBinding** XML 項目**basicHttpBinding** （區分大小寫），然後按一下**完成**。  
  
        ![更新原則繫結](../technical-guides/media/sentinetwp-modifypolicy-2.png "SentinetWP_ModifyPolicy_2")  
  
   5.  按一下 **儲存**將變更儲存至端點的詳細資料。  
  
8. 停止**CustomerSearch**服務，將變更從繫結**wsHttpBinding**來**basicHttpBinding**，然後重新啟動服務。  
  
    ![重新啟動服務，使用不同的繫結](../technical-guides/media/sentinetwp-restartcustservice.png "SentinetWP_RestartCustService")  
  
9. 從**測試路線用戶端**，客戶搜尋服務再次傳送測試訊息。 請注意客戶搜尋服務 對話方塊中的計數器再加 1。  
  
     一旦成功接收訊息，從 Sentinet 管理主控台中，變更的原則的詳細資料將會回到**wsHttpBinding**。 同樣地，停止**客戶搜尋**服務、 將原則變更回 wsHttpBinding 和啟動服務。  
  
   這示範了如何 Sentinet 存放庫中的服務詳細資料可以即時更新至更新的服務端點的目標而不需要變更路線或用戶端。  
  
#### <a name="to-test-the-sentinet-resolver-by-changing-keyword-assignments"></a>若要藉由變更關鍵字指派測試 Sentinet 解析程式  
  
1.  請確定兩個執行個體**CustomerSearch**您部署使用 basicHttpBinding 與 wsHttpBinding 的服務正在執行。  
  
2.  從**Nevatech.Vsb.BizTalk.Samples**範例中，開啟**CustomerSearch.Search.itinerary**，選取**解決服務端點**下**訊息Extender**內**郵件路由**圖形，並針對**關鍵字**屬性，指定關鍵字，例如**TestKeyword**。  
  
     ![指派關鍵字](../technical-guides/media/sentinetwp-assignkeyword.png "SentinetWP_AssignKeyword")  
  
3.  將變更儲存至路線，並將模型匯出。 以滑鼠右鍵按一下在路線設計工具介面上的任何位置，並按一下**匯出模型**。  
  
4.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**Microsoft.Practices.ESB**應用程式中，按一下 匯入，然後按一下 繫結。 瀏覽至 ESB 解析程式範例位置`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver`，然後開啟**BizTalk.Bindings.xml**檔案。 這會建立**Sentinet 請求-回應**並**Sentinet 單向**傳送範例路線所需的連接埠。  
  
     此外，請確定所有傳送埠和接收位置的**Microsoft.Practices.ESB** BizTalk 應用程式會登錄並啟動。  
  
5.  開啟**ESB。Itinerary.Test**應用程式，建置它，並執行它。 在啟動路線測試用戶端，執行下列步驟：  
  
    1.  在路線測試用戶端，底下**Web 服務選項**，清除**使用 WCF 服務**，然後選取**兩個方式服務**。  
  
    2.  從**服務型別**下拉式清單中，選取**Messaging**。  
  
    3.  按一下 **負載路線**並瀏覽至**CustomerSearch.Search.Itinerary.xml**範例專案中的檔案**ExportedItineraries**資料夾`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver\ExportedItineraries`.  
  
    4.  按一下省略符號按鈕 (**...**) 底下**載入訊息**分組，並瀏覽至**CustomerSearch.Search.Request.xml**位於專案的**SampleMessages** 資料夾`<installation drive>:\Program Files\Nevatech\Sentinet BizTalk Extensions\Samples\ESB Resolver\SampleMessages`.  
  
    5.  按一下 **送出要求**和確認收到的回應。  
  
6.  在  **CustomerSearch**對話方塊中，請注意，此計數器增加一個。  
  
7.  從 Sentinet 管理主控台中，移除**TestKeyword**聯**第 1 版**的**CustomerSearch**服務和其關聯**第 2 版**的服務。  
  
    1.  開啟 Sentinet 系統管理主控台中，按一下**第 1 版**下方**CustomerSearch**服務，按一下 wsHttpBinding 端點，然後按一下**附件**索引標籤，然後再按一下**修改**。  
  
         ![移除 CustomerSearch 服務中的關鍵字](../technical-guides/media/sentinetwp-removekeyword.png "SentinetWP_RemoveKeyword")  
  
    2.  按一下 針對關鍵字之前刪除的關鍵字，請按一下 輸入 按鈕**是**在訊息方塊，然後按一下**儲存**。  
  
         ![移除 CustomerSearch 服務中的關鍵字](../technical-guides/media/sentinetwp-removekeyword-2.png "SentinetWP_RemoveKeyword_2")  
  
    3.  現在，將指派相同的關鍵字 (**TestKeyword**) 來**basicHttpBinding**端點**第 2 版**相同的服務。  
  
8.  傳送測試訊息從再次**測試路線用戶端**並請注意，此期間，此計數器會遞增在對話方塊中，表示第 2 版的服務，使用 basicHttpBinding 部署。