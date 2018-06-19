---
title: 如何： 建立以動態方式將訊息路由傳送電子郵件地址，使用 LDAP 查詢行程 |Microsoft 文件
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
ms.openlocfilehash: 751eaf381b762372652bb77ddf6f00ffe43971c2
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010111"
---
# <a name="how-to-create-an-itinerary-to-dynamically-route-a-message-to-an-email-address-using-an-ldap-query"></a>如何： 建立以動態方式將訊息路由傳送電子郵件地址，使用 LDAP 查詢的行程
## <a name="goal"></a>目標  
 本節示範如何建立查詢透過 LDAP （輕量型目錄存取通訊協定） 的電子郵件地址，然後再將電子郵件訊息傳送至已解決的端點使用 BizTalk Server SMTP 配接器的行程。  
  
 在此 「 如何 」 主題，您將完成下列步驟：  
  
-   建立動態路由傳送訊息，使用 LDAP 查詢計劃的路由受控滑動。  
  
-   測試使用路線測試用戶端範例應用程式的路線。  
  
## <a name="prerequisites"></a>必要條件  
 在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。  
  
 您將在其完成本節的電腦必須有 Microsoft Active Directory 目錄服務設定且正在執行 (不需要電腦是網域控制站，但必須連線到網域)。 此外，SMTP 伺服器必須設定並執行。若要測試此 「 如何 」 主題的結果，您必須用來檢查 ESB 所傳送的電子郵件用戶端。  
  
 本節中的指示會假設名為 Active Directory 組織單位名為 Employees 包含名為 John Evans 且有效的電子郵件位址 （例如他設定檔中的使用者與全域銀行globalbank.com，網域的組織johne@globalbank.com). 不需要複寫這些環境的因素。不過，基於重新建立這項實作您的環境中，請考慮這些因素，請視需要的替代項目。  
  
## <a name="steps"></a>步驟  
  
#### <a name="to-create-an-esb-itinerary-domain-specific-language-dsl-model"></a>若要建立 ESB 路線網域特定領域語言 (DSL) 模型  
  
1.  在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。  
  
2.  在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下 **新的行程**。  
  
3.  在**加入新項目** 對話方塊中，輸入**LdapResolution**中**名稱**方塊，然後再按一下**新增**。  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a>若要設定的路線屬性  
  
1.  在 Visual Studio 中，按一下設計介面的**LdapResolution.itinerary**。 在**LdapResolution**屬性 視窗中，設定下列屬性：  
  
    1.  在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。  
  
    2.  下**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性中，按一下省略符號按鈕 （...）。  
  
    3.  在**選取 XML 檔案** 對話方塊中，輸入**C:\HowTos\Itineraries\LdapResolution**中**檔案名稱**方塊，然後再按一下**儲存**。  
  
        > [!NOTE]
        >  這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。 藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。 您將完成此程序，稍後在本使用說明主題。  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a>若要定義路線結構  
  
1.  從 [工具箱] 拖曳**上手**至設計介面的模型項目。 在**OnRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。  
  
    2.  在**Extender**下拉式清單中，按一下 **上手 ESB Extender**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。  
  
    4.  在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。  
  
2.  從 [工具箱] 拖曳**路線服務**模型項目至設計介面，然後再將它放右邊的**上手**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**RouteMessageEmail**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。  
  
        > [!NOTE]
        >  這個屬性會定義程序將需要 (messaging) 在管線中的位置。 或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程 Extender**。  
  
    3.  在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。  
  
    4.  在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**。  
  
3.  以滑鼠右鍵按一下**解析程式**集合**RouteMessageEmail**模型項目，然後按一下**加入新的解析程式**。 在**Resolver1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**LdapResolver**。  
  
    2.  在**解析程式實作**下拉式清單中，按一下  **LDAP 解析程式擴充功能**。  
  
    3.  在**傳輸名稱**下拉式清單中，按一下  **SMTP**。  
  
    4.  按一下**傳輸位置**屬性，，然後輸入 **{mail}**  
  
    5.  按一下**SearchRoot**屬性，，然後輸入**ou = 員工，dc = globalbank，dc = com**  
  
        > [!NOTE]
        >  如果您尚未在 < 先決條件 > 一節中設定您的環境，根據規格，取代先前的屬性中的值適用於您的環境。  
  
    6.  按一下**篩選**屬性，然後將變更的值 **(&(objectClass=User) (&#124;(givenName=john)))**  
  
        > [!NOTE]
        >  輸入上面的值來取代現有的文字。  
  
    7.  在**ThrowErrorIfNotFound**下拉式清單中，按一下  **True**。  
  
4.  在 [屬性] 視窗中，按一下**端點組態**屬性，然後按一下省略符號按鈕 （...）。  
  
    1.  在**端點組態**對話方塊中，按一下  **EmailBodyText**屬性，，然後輸入**順序已準備好處理**。  
  
    2.  按一下**從**屬性，，然後輸入 **orders@globalbank.com** 。  
  
    3.  按一下**MessagePartsAttachment**屬性，，然後輸入**2**。  
  
    4.  按一下**主旨**屬性，，然後輸入**順序 {givenName}**。  
  
    5.  設定**SMTPAuthentication、 SMTPHost、 使用者名稱、** 和**密碼**屬性的本機環境中使用的連接資訊。  
  
    6.  按一下**確定**關閉**端點組態** 對話方塊。  
  
5.  以滑鼠右鍵按一下**LdapResolver**解析程式，然後再按一下**測試解析程式組態**。  
  
6.  在 輸出 視窗中，確認 已解析中的主體**端點組態**值是**john 順序**，然後確認已解析**傳輸位置**是電子郵件地址與 Active Directory 中使用者的帳戶相關聯 (例如， johne@globalbank.com)。  
  
7.  在工具箱中，按一下 **連接器**。 拖曳連接**ReceiveNAOrder**模型項目的**RouteMessageEmail**模型項目。  
  
8.  從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**RouteMessageEmail**模型項目。 在**OffRamp1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**EmailNAOrderDoc**。  
  
    2.  在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。  
  
    3.  在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。  
  
    4.  在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。  
  
9. 從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**RouteMessageEmail**模型項目和**EmailNAOrderDoc**模型項目。 在**ItineraryService1**屬性 視窗中，設定下列屬性：  
  
    1.  按一下**名稱**屬性，，然後輸入**SendPortFilter**。  
  
    2.  在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。  
  
    3.  在**匝道**下拉式清單中，展開**EmailNAOrderDoc**，然後按一下 **傳送處理常式**。  
  
10. 在工具箱中，按一下 **連接器**。 拖曳連接**RouteMessageEmail**模型項目的**SendPortFilter**模型項目。  
  
11. 在工具箱中，按一下 **連接器**。 拖曳連接**SendPortFilter**模型項目的**EmailNAOrderDoc**模型項目。  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a>若要匯出的行程測試用戶端使用的模型  
  
1.  在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**LdapResolution**路線，然後再按一下**匯出模型**。  
  
    > [!NOTE]
    >  在 Visual Studio 中，開啟路線的 XML 版本。  
  
2.  儲存專案的所有成品。  
  
3.  在 Windows 檔案總管，瀏覽至 C:\HowTos\Itineraries 並注意您路線 XML (LdapResolution.xml) 建立。  
  
#### <a name="to-test-the-itinerary"></a>若要測試路線  
  
1.  開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。  
  
2.  在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後**負載路線**。  
  
3.  在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。 選取**LdapResolution.xml**，然後按一下 **開啟**載入路線。  
  
4.  按一下**確定**清除**路線成功載入**訊息。  
  
5.  在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。  
  
6.  在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\HowTos。 選取**NAOrderDoc.xml**，然後按一下 **開啟**載入測試訊息。  
  
7.  按一下**送出要求** 按鈕。 測試完成時，按一下**確定**解除顯示的確認。  
  
8.  開啟 Microsoft Outlook Express （或您選擇的郵件用戶端），並確認 John Evans 的電子郵件訊息的傳遞。  
  
## <a name="additional-resources"></a>其他資源  
 如需詳細資訊，請參閱下列相關主題：  
  
-   [開發活動](../esb-toolkit/development-activities.md)  
  
-   [使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)