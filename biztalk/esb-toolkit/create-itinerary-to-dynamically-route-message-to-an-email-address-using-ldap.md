---
title: 如何： 建立路線以動態方式將訊息路由至電子郵件地址，使用 LDAP 查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d9929dd-5e45-4b0d-90df-52a35e68b0ba
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93a2237b76524488d7a3903468ebb321d19ae623
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987599"
---
# <a name="how-to-create-an-itinerary-to-dynamically-route-a-message-to-an-email-address-using-an-ldap-query"></a>如何： 建立路線以動態方式將訊息路由至電子郵件地址，使用 LDAP 查詢
## <a name="goal"></a>目標  
 本節示範如何建立查詢透過 LDAP （輕量型目錄存取通訊協定） 的電子郵件地址，然後將電子郵件訊息傳送至使用 BizTalk Server SMTP 配接器的解析端點路線。  
  
 在本使用說明主題中，您將完成下列步驟：  
  
-   建立動態路由傳送訊息，使用 LDAP 查詢路線傳閱名單。  
  
-   測試使用路線測試用戶端的範例應用程式的路線。  
  
## <a name="prerequisites"></a>必要條件  
 本使用說明主題中的程序必須完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。  
  
 在其，您將完成本節中的電腦必須有 Microsoft Active Directory 目錄服務已設定並執行 (不需要電腦是網域控制站，但它必須連線到網域)。 此外，SMTP 伺服器必須已設定且正在執行;若要測試本使用說明主題的結果，您必須具有要檢查的 ESB 所傳送的電子郵件的用戶端。  
  
 在本節中的指示會假設有家名 Global Bank 網域為 globalbank.com，為與 Active Directory 組織單位名為 Employees，其中包含使用者 John Evans 名為有效的電子郵件地址，在他的設定檔 （例如johne@globalbank.com). 您不需要複寫這些環境因素;不過，基於重新建立您的環境中的這個實作，請考量下列因素，請視需要的替代項目。  
  
## <a name="steps"></a>步驟  
  
#### <a name="to-create-an-esb-itinerary-domain-specific-language-dsl-model"></a>若要建立的 ESB 路線的特定領域語言 (DSL) 模型  
  
1.  在 Visual Studio 中，開啟 [C:\HowTos\Patterns\Patterns.sln]。  
  
2.  在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新路線**。  
  
3.  在 [**加入新項目**] 對話方塊中，輸入**LdapResolution**中**名稱**方塊，然後再按一下**新增**。  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>若要設定的路線屬性  
  
1.  在 Visual Studio 中，按一下設計介面**LdapResolution.itinerary**。 在 [ **LdapResolution**屬性] 視窗中，設定下列屬性：  
  
    1.  在 **模型匯出工具**下拉式清單中，按一下**XML 路線匯出工具**。  
  
    2.  底下**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性中，按一下省略符號按鈕 （...）。  
  
    3.  在 [**選取 XML 檔案**] 對話方塊中，輸入**C:\HowTos\Itineraries\LdapResolution**中**檔名**方塊，然後再按一下**儲存**。  
  
        > [!NOTE]
        >  此步驟可讓您將匯出為 XML 的路線，到本機檔案的位置。 而不是匯出至本機檔案位置，路線，路線資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。 您將完成此程序，稍後在本使用說明主題。  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>若要定義的路線結構  
  
1. 從 [工具箱] 拖曳**匝道**模型項目到設計介面。 在 [ **OnRamp1**屬性] 視窗中，設定下列屬性：  
  
   1.  按一下 **名稱**屬性，然後按**ReceiveNAOrder**。  
  
   2.  在  **Extender**下拉式清單中，按一下**匝道 ESB Extender**。  
  
   3.  在  **BizTalk 應用程式**下拉式清單中，按一下**Microsoft.Practices.ESB**。  
  
   4.  在 **接收埠**下拉式清單中，按一下**OnRamp.Itinerary**。  
  
2. 從 [工具箱] 拖曳**路線服務**模型項目到設計介面，並再將其放置在右邊**匝道**模型項目。 在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：  
  
   1.  按一下 **名稱**屬性，然後按**RouteMessageEmail**。  
  
   2.  在 **路線服務的擴充項**下拉式清單中，按一下**傳訊 Extender**。  
  
       > [!NOTE]
       >  這個屬性會定義此程序需要 （傳訊） 的管線中的位置。 或者，如果協調流程中的位置時，會進行的程序，設定**路線服務 Extender**屬性設**協調流程 Extender**。  
  
   3.  在 **容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。  
  
   4.  在 **服務名稱**下拉式清單中，按一下**Microsoft.Practices.ESB.Services.Routing**。  
  
3. 以滑鼠右鍵按一下**解析**的集合**RouteMessageEmail**模型項目，然後按一下**加入新的解析程式**。 在 [ **Resolver1**屬性] 視窗中，設定下列屬性：  
  
   1.  按一下 **名稱**屬性，然後按**LdapResolver**。  
  
   2.  在 **解析程式實作**下拉式清單中，按一下**LDAP 解析程式擴充功能**。  
  
   3.  在 **傳輸名稱**下拉式清單中，按一下**SMTP**。  
  
   4.  按一下 **傳輸位置**屬性，然後按 **{郵件}**  
  
   5.  按一下  **SearchRoot**屬性，然後按**ou = Employees，dc = globalbank，dc = com**  
  
       > [!NOTE]
       >  如果您不具有設定您的環境，根據規格，< 先決條件 > 一節中，取代先前的屬性中的值適用於您環境的。  
  
   6.  按一下 **篩選條件**屬性，然後將值變更為 **(&(objectClass=User) (&#124;(givenName = john)))**  
  
       > [!NOTE]
       >  輸入上述的值來取代現有的文字。  
  
   7.  在  **ThrowErrorIfNotFound**下拉式清單中，按一下 **，則為 True**。  
  
4. 在 [屬性] 視窗中，按一下**端點組態**屬性，然後按一下省略符號按鈕 （...）。  
  
   1. 在 [**端點組態**] 對話方塊中，按一下**EmailBodyText**屬性，然後按**訂單已就緒可供處理**。  
  
   2. 按一下 **從**屬性，然後按<strong>orders@globalbank.com</strong>。  
  
   3. 按一下  **MessagePartsAttachment**屬性，然後按**2**。  
  
   4. 按一下 **主旨**屬性，然後按**順序 {givenName}**。  
  
   5. 設定**SMTPAuthentication SMTPHost、 使用者名稱**並**密碼**為您的本機環境中使用的連接資訊的屬性。  
  
   6. 按一下 [ **[確定]** 以關閉**端點組態**] 對話方塊。  
  
5. 以滑鼠右鍵按一下**LdapResolver**解析程式，然後再按一下**測試解析程式組態**。  
  
6. 在 輸出 視窗中，確認 已解析中的主體**端點組態**值是**john 順序**，然後確認已解析**傳輸位置**是電子郵件地址與 Active Directory 中的使用者帳戶相關聯 (例如johne@globalbank.com)。  
  
7. 在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**ReceiveNAOrder**模型項目**RouteMessageEmail**模型項目。  
  
8. 從 [工具箱] 拖曳**出口匝**模型項目到設計介面，並再將其放置在右邊**RouteMessageEmail**模型項目。 在 [ **OffRamp1**屬性] 視窗中，設定下列屬性：  
  
   1.  按一下 **名稱**屬性，然後按**EmailNAOrderDoc**。  
  
   2.  在  **Extender**下拉式清單中，按一下**出口匝 ESB Extender**。  
  
   3.  在  **BizTalk 應用程式**下拉式清單中，按一下**GlobalBank.ESB**。  
  
   4.  在 **傳送埠**下拉式清單中，按一下**DynamicResolutionOneWay**。  
  
9. 從 [工具箱] 拖曳**路線服務**模型項目到設計介面，並將其之間放置**RouteMessageEmail**模型項目和**EmailNAOrderDoc**模型項目。 在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：  
  
    1.  按一下 **名稱**屬性，然後按**SendPortFilter**。  
  
    2.  在 **路線服務的擴充項**下拉式清單中，按一下**出口匝 Extender**。  
  
    3.  在 **出口匝**下拉式清單中，展開**EmailNAOrderDoc**，然後按一下 **傳送處理常式**。  
  
10. 在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**RouteMessageEmail**模型項目**SendPortFilter**模型項目。  
  
11. 在 [工具箱] 中，按一下**連接器**。 拖曳連接，以從**SendPortFilter**模型項目**EmailNAOrderDoc**模型項目。  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>若要匯出使用路線測試用戶端使用的模型  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面**LdapResolution**路線，，然後按一下**匯出模型**。  
  
    > [!NOTE]
    >  在 Visual Studio 中，開啟路線的 XML 版本。  
  
2.  儲存專案的所有成品。  
  
3.  在 Windows 檔案總管中，瀏覽至 C:\HowTos\Itineraries 並注意您的路線 XML (LdapResolution.xml) 建立。  
  
#### <a name="to-test-the-itinerary"></a>若要測試的路線  
  
1.  開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。  
  
2.  在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後按一下**負載路線**。  
  
3.  在 [**開啟路線檔案**] 對話方塊中，瀏覽至 C:\HowTos\Itineraries。 選取  **LdapResolution.xml**，然後按一下**開啟**載入路線。  
  
4.  按一下  **確定**清除**路線成功載入**訊息。  
  
5.  在路線測試用戶端中，按一下 [旁的省略符號按鈕 （...）**載入訊息**] 方塊中。  
  
6.  在 [**選取要載入的 XML 文件**] 對話方塊中，瀏覽至 C:\HowTos。 選取  **NAOrderDoc.xml**，然後按一下**開啟**載入測試訊息。  
  
7.  按一下 [**送出要求**] 按鈕。 測試完成時，按一下**確定**關閉顯示的確認。  
  
8.  開啟 Microsoft Outlook Express （或您選擇的郵件用戶端），並確認訊息傳送到 John Evans 的電子郵件。  
  
## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  
  
-   [開發活動](../esb-toolkit/development-activities.md)  
  
-   [使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)