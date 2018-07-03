---
title: 如何使用 BizTalk WCF 服務使用精靈來取用 WCF 服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF services, WCF Service Consuming Wizard
- WCF Service Consuming Wizard
- tools, WCF Service Consuming Wizard
- consuming, WCF Service Consuming Wizard
ms.assetid: d5fad2ac-4d98-4720-8026-88ebab78b120
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c626e171135332bca35845c99fc477bbc0e9a60b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009295"
---
# <a name="how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service"></a>如何使用 BizTalk WCF 服務使用精靈以使用 WCF 服務
BizTalk 配接器架構會提供將配接器結構描述和 BizTalk 類型新增至 BizTalk 專案的方法。 BizTalk WCF 服務使用精靈可讓您將 WCF 傳送配接器新增到 BizTalk 專案。 對於 WCF 傳送配接器，您必須針對傳送埠選取現有的中繼資料交換 (MEX) 端點。 然後，您必須輸入用來產生結構描述和類型的資訊。 當精靈完成時，在使用 WCF 服務時所需要的結構描述和類型就會加入到 BizTalk 專案中。  
  
### <a name="to-add-the-schemas-and-types-for-wcf-send-adapters-to-your-project"></a>若要在專案中新增 WCF 傳送配接器適用的結構描述和類型  
  
1. 在您的 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] BizTalk 專案的 [方案總管] 中以滑鼠右鍵按一下您的專案，按一下**新增**，然後按一下**加入產生的項目**。  
  
2. 在 **加入產生的項目- \<** <em>專案名稱</em>**\>** 對話方塊中，於**範本** 區段中，選取 **取用 WCF 服務**，然後按一下**新增**。  
  
3. 在 [**歡迎使用 BizTalk WCF 服務使用精靈**頁面上，按一下**下一步]**。  
  
4. 在 **中繼資料來源**頁面上，選取要匯入，然後按一下 中繼資料的來源**下一步**。  
  
    ![中繼資料來源頁面](../core/media/2478a788-23ff-4ba9-a183-82e533b57f46.gif "2478a788-23ff-4ba9-a183-82e533b57f46")  
  
    若要從執行中服務的中繼資料交換端點下載中繼資料文件，請選取**中繼資料交換 (MEX) 端點**選項。 這能讓我們建立一個傳送埠，在用戶端與 WCF 服務間使用。 若要使用此選項，服務端點必須針對使用 HTTP/GET 或 HTTPS/GET 要求所進行的擷取作業，發佈服務中繼資料。 服務端點也必須允許以使用者名稱和密碼並配合基本驗證配置的形式，透過匿名使用者認證或使用者認證來存取中繼資料。  
  
   > [!NOTE]
   >  使用基本驗證配置時，這些認證是以純文字格式傳送，因此很容易被攔截。 而且此配置沒有對服務傳回的資訊提供任何保護。 因此，您必須使用「安全通訊端層」(SSL) 來加密資料。  
  
    對於任何其他中繼資料文件匯入，請選取**中繼資料檔案 （WSDL 和 XSD）** 從檔案系統匯入中繼資料的選項。  
  
   > [!NOTE]
   >  並非所有的服務都必須發佈中繼資料。 停用中繼資料發佈功能，可減少服務的攻擊面並降低無意間洩漏資訊的風險。  
  
5. 如果您選取**中繼資料交換 (MEX) 端點**選項**中繼資料來源**頁面上，**中繼資料端點**頁面隨即出現。 在 **中繼資料端點**頁面上，指定執行中的服務提供透過 Ws-metadata Exchange 或 Http-get 下載的中繼資料的 URL。 若要從 URL 取得中繼資料文件，請按一下**取得**。 如果執行中的服務需要基本驗證配置的使用者認證，請按一下**編輯**來開啟**BizTalk WCF 服務使用精靈**對話方塊中，您可以在其中提供使用者名稱和若要存取執行服務時使用的密碼。  
  
    ![中繼資料端點 頁面](../core/media/2b17f85a-64d0-4719-99c4-ce61c706f10c.gif "2b17f85a-64d0-4719-99c4-ce61c706f10c")  
  
   > [!NOTE]
   >  若要下載透過 HTTP 或 HTTPS 發佈的 WCF 服務的中繼資料，您無法使用 MEX 端點如http://localhost:8087/CalculatorService/mexfor**中繼資料位址**文字方塊。 對於 WCF 服務，您必須使用 WSDL 中繼資料來下載中繼資料，如下所示：http://localhost:8087/CalculatorService或 http://localhost:8087/CalculatorService?wsdl  
  
6. 如果您選取**中繼資料檔案 （WSDL 和 XSD）** 選項**中繼資料來源**頁面上，**中繼資料端點**頁面隨即出現。 在 **中繼資料端點**頁面上，指定要匯入中繼資料檔案。 按一下 **新增**將中繼資料檔案匯入**中繼資料檔案**檢視。 這會開啟**加入中繼資料檔案**對話方塊中，您可以在其中搜尋的中繼資料檔案的磁碟位置。  
  
    在 **加入中繼資料檔案**對話方塊方塊中，選取要用於中繼資料的一組完整的 WSDL 和 XSD 檔案。 您可以在命令提示字元中，輸入下列命令來產生這些中繼資料檔案：  
  
    **svcutil.exe /t http://localhost/service.svc/mex**  
  
    按一下 **移除**移除中繼資料檔案中選取**中繼資料檔案**檢視。  
  
    ![中繼資料檔案頁面](../core/media/445bccd1-88b0-41ad-b91d-e899e7d5902d.gif "445bccd1-88b0-41ad-b91d-e899e7d5902d")  
  
   > [!NOTE]
   >  SvcUtil.exe 包含在 Windows Vista 和 .NET Framework 執行階段元件的 Microsoft Windows 軟體開發套件 (SDK) 中。  
  
   > [!NOTE]
   >  以不安全的方式擷取服務中繼資料時，可能會遭到竄改或偽造。 遭竄改的中繼資料可能會將您的用戶端重新導向到惡意服務、包含損毀的安全性設定或包含惡意的 XML 結構。 中繼資料文件可能會非常大，而且經常儲存到檔案系統。 您必須確定中繼資料檔案未遭到竄改。  
  
7. 在 **匯入 WCF 服務中繼資料摘要**頁面上，檢閱您的設定。 您可以按一下**回**進行任何變更。 然後按一下**匯入**建立的 BizTalk 成品和用於使用 WCF 服務的型別。  
  
8. 在 **完成 BizTalk WCF 服務使用精靈**頁面上，按一下**完成**。 如果您想要再次執行此精靈，請選取**再次執行此精靈**選項，然後再按一下**完成**。  
  
    [BizTalk WCF 服務使用精靈] 會在 BizTalk 專案中，建立使用 WCF 服務時所需要的 BizTalk 結構描述和類型。 BizTalk 類型 (例如連接埠類型和多部分訊息類型) 會由協調流程建立。 我們建議您不要修改精靈所建立的協調流程。 而是依照您的目的，將新的協調流程加入到 BizTalk 專案。 BizTalk WCF 服務使用精靈也會建立兩個繫結檔案， **BizTalkServiceInstance.BindingInfo.xml**並**BizTalkServiceInstance_Custom.BindingInfo.xml**。 **BizTalkServiceInstance.BindingInfo.xml** ，可以藉由開發命令列工具或精靈來設定標準繫結 WCF 配接器的傳送埠匯入這個 BizTalk 繫結檔案，例如 Wcf-netmsmq 和 Wcf-wshttp配接器。 **BizTalkServiceInstance.BindingInfo.xml** ，可以藉由開發命令列工具或精靈來設定 Wcf-custom 配接器的傳送埠匯入這個 BizTalk 繫結檔案。  
  
    當您匯入產生的繫結檔案時，它會填入**WCF。動作**以動作對應格式的屬性。 若要查看此屬性的設定方式，看看**動作**上的文字方塊**一般**WCF 傳送埠傳輸屬性對話方塊在 BizTalk 管理主控台中的索引標籤。  
  
    您可以指定**WCF。動作**兩種不同方式的屬性： 單一動作格式和動作對應格式。 如果您在設定此屬性的單一動作格式-例如， http://contoso.com/Svc/Op1 - **SOAPAction**標頭外寄訊息一定會設定這個屬性中指定的值。 如果您設定此屬性以動作對應格式外, 寄**SOAPAction**標頭會由**BTS。作業**內容屬性。 例如，如果此屬性設定為下列 XML 格式和**BTS。作業**屬性設定為**Op1**，WCF 傳送配接器會使用http://contoso.com/Svc/Op1針對外寄**SOAPAction**標頭。  
  
    `<BtsActionMapping>`  
  
    `<Operation Name="Op1" Action="http://contoso.com/Svc/Op1" />`  
  
    `<Operation Name="Op2" Action="http://contoso.com/Svc/Op2" />`  
  
    `</BtsActionMapping>`  
  
    協調流程執行個體如果外寄訊息來自於協調流程連接埠，以動態方式設定**BTS。作業**與連接埠的作業名稱的屬性。 如果外寄訊息會路由傳送，以內容為基礎的路由，您可以設定**BTS。作業**管線元件中的屬性。 BizTalk WCF 使用精靈所產生的連接埠有其名稱符合的作業**名稱**中的屬性**<BtsActionMapping>** 項目。 您沒有明確設定**BTS。作業**透過精靈所產生的連接埠傳送訊息時的協調流程中的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [如何使用 BizTalk WCF 服務發佈精靈協調流程發佈為 WCF 服務](../core/publish-orchestrations-as-wcf-services--biztalk-wcf-service-publishing-wizard.md)   
 [如何使用 BizTalk WCF 服務發佈精靈發佈為 WCF 服務的結構描述](../core/publish-schemas-as-wcf-services--use-the-biztalk-wcf-service-publishing-wizard.md)