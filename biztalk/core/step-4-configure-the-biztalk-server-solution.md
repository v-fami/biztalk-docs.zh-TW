---
title: 步驟 4： 設定 BizTalk Server 解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d60e6a82-51af-41e5-a755-5f337492ba2f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e65c3cf64045378b0f69b6980b98cdec88f175d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013879"
---
# <a name="step-4-configure-the-biztalk-server-solution"></a>步驟 4： 設定 BizTalk Server 解決方案
在上一個步驟中，您需要建立並部署[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式以接收到的 Salesforce 通知[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]並插入內部部署 SQL Server 資料庫的詳細資料。 在此步驟中，我們將設定中的應用程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 主要設定應用程式，牽涉到建立實體連接埠對應至我們在協調流程中建立的邏輯連接埠。 它還包含繫結至邏輯連接埠的實體連接埠。 我們會執行下列步驟來設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式：  
  
- 設定要求-回應 Wcf-basichttprelay 接收位置，以接收來自 Salesforce 商機通知。  
  
- 設定要求-回應 Wcf-webhttp 傳送埠以傳送至 Salesforce 的查詢，擷取已接收的商機通知相關的產品詳細資料。 此傳送埠也會收到來自 Salesforce 的查詢回應。  
  
- 設定要從 Salesforce 的查詢回應插入內部部署 SQL Server 資料庫的單向 WCF SQL 傳送埠。  
  
- 設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式的關聯中所建立的實體連接埠至協調流程中的邏輯連接埠[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
### <a name="to-configure-the-wcf-basichttprelay-receive-location"></a>若要設定 Wcf-basichttprelay 接收位置  
  
1. 開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 展開 [應用程式] 節點，並尋找**SalesforceIntegration**應用程式。 您在部署時，會建立此應用程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]從 Visual Studio 的專案。  
  
2. 依序展開**SalesforceIntegration**應用程式，以滑鼠右鍵按一下**接收埠**，指向**新增**，然後按一下 **要求-回應接收埠**. 將連接埠名稱指定為`ReceiveOppNotification`，然後從左窗格中，按一下**接收位置**。  
  
3. 在 [接收位置屬性] 對話方塊中，指定下列值：  
  
   |||  
   |-|-|  
   |[屬性]|輸入`ReceiveOppNotification`。|  
   |類型|選取**Wcf-basichttprelay**|  
   |接收處理常式|選取**BizTalkServerApplication**|  
   |接收管線|選取**XMLReceive**|  
   |傳送管線|選取**PassThruTransmit**|  
  
    按一下 **設定**針對連接埠類型。  
  
4. 在 [Wcf-basichttprelay 傳輸屬性] 對話方塊中，指定下列值：  
  
   1. 在 **一般**索引標籤上，如**位址 (URI)**，輸入`https://btssalesforce.servicebus.windows.net/notifications/opportunity`。 在這裡， **btssalesforce**是您在中建立的命名空間[步驟 1： 建立服務匯流排命名空間](../core/step-1-create-a-service-bus-namespace.md)。 您可以指定以下是在 Salesforce 中建立工作流程時指定的相同 URL 的 URL[步驟 2： 設定 Salesforce 系統](../core/step-2-set-up-the-salesforce-system.md)。 您設定工作流程中每次有機會的階段設為 Closed Won，Salesforce 會傳送通知至 URL *<https://btssalesforce.servicebus.windows.net/notifications/opportunity>*。 我們會指定相同的 URL 為屬於這個接收位置組態。 啟用接收位置時，會在 URL 所指定的轉送端點[!INCLUDE[winazure](../includes/winazure-md.md)]。  
  
   2. 在 **安全性**索引標籤上，指定下列項目：  
  
      -   針對**安全性模式**，選取**傳輸**至於**轉送用戶端驗證類型**，選取**無**。  
  
      -   選取 **啟用服務探索**核取方塊，以發佈中的服務行為[服務登錄](http://msdn.microsoft.com/library/windowsazure/dd582704.aspx)。 指定**顯示名稱**表示與服務發行至登錄的名稱。 您可以設定**探索模式**至公用或私人。 本教學課程中，將**顯示名稱**來`SF Outbound Notification`並**探索模式**來**公用**。  
  
      -   在存取控制服務方塊中，按一下**編輯**。 針對**存取控制服務 STS Uri**，輸入`https://btssalesforce-sb.accesscontrol.windows.net/`。 針對**簽發者名稱**並**簽發者金鑰**，輸入您在中儲存的值[步驟 1： 建立服務匯流排命名空間](../core/step-1-create-a-service-bus-namespace.md)如**預設使用者**和**預設金鑰**欄位。  
  
   3. 按一下 **確定**直到結束所有開啟的對話方塊。  
  
### <a name="to-configure-the-wcf-webhttp-send-port"></a>若要設定 Wcf-webhttp 傳送埠  
  
1. 依序展開**SalesforceIntegration**應用程式，以滑鼠右鍵按一下**傳送連接埠**，指向**新增**，然後按一下 **靜態請求-回應傳送埠**.  
  
2. 在傳送埠屬性 對話方塊中，指定下列值：  
  
   |||  
   |-|-|  
   |[屬性]|輸入`SalesforceREST`。|  
   |類型|選取**Wcf-webhttp**|  
   |傳送處理常式|選取**BizTalkServerApplication**|  
   |傳送管線|選取**PassThruTransmit**|  
   |接收管線|選取  **AddNamespace** ，然後按一下省略符號按鈕，針對來設定管線的管線。<br /><br /> -底下**第 1 階段： 解碼**，如**NamespaceBase**，輸入`http://BtsSalesforceIntegration.QueryResult`。 這是您在建立 QueryResult.xsd 結構描述的命名空間[步驟 3b： 使用 Wcf-webhttp 配接器從 Salesforce 擷取機會詳細資料](../core/step-3b-retrieve-opportunities-from-salesforce-using-the-wcf-webhttp-adapter.md)。 當**AddNamespace**接收管線從 Salesforce 收到回應時，它將此命名空間加入至回應訊息。 根據預設，來自 Salesforce 的回應訊息不包含任何命名空間。<br />     針對**NamespacePrefix**，輸入`sf`。<br />-底下**階段 2： 解譯**，接受預設值，然後按一下**確定**。|  
  
    在 傳送埠屬性 對話方塊中，按一下 **設定**針對連接埠類型。  
  
3. 在 [Wcf-webhttp 傳輸屬性] 對話方塊中，指定下列值：  
  
   1. 在 [一般] 索引標籤上，執行下列動作：  
  
      - 針對**位址 (URI)**，輸入`https://<Salesforce_instance_name>.salesforce.com/services/data/v24.0`。 您可以藉由複製的文字會與 https:// Salesforce.com 上有開啟的 Salesforce.com 入口網站的網址列中擷取的 Salesforce 執行個體名稱。 例如，如果在 Salesforce 入口網站的 URL 是否*https://*<em>na15</em>*.salesforce.com/home/home.jsp*，Salesforce 執行個體名稱是**na15**.  
  
      - 底下**HTTP 方法和 URL 對應**方塊中，指定下列項目：  
  
        ```  
        <BtsHttpUrlMapping>  
        <Operation Method="GET" Url="/query?q={VAR}" />  
        </BtsHttpUrlMapping>  
        ```  
  
         以下是如何使用這項設定 — 若要查詢 Salesforce 擷取機會通知的詳細資訊，我們必須執行 「 取得 」 作業在 Salesforce REST 端點上的 (在指定**位址**欄位) 和附加若要擷取機會詳細資料的查詢。 因此，URL 看起來應該類似：  
  
        ```  
        https://na15.salesforce.com/services/data/v24.0/query?q=<query_string>  
        ```  
  
         我們已經有 Salesforce REST 端點的一部分**位址 (URI)** 欄位。 因此，部分**HTTP 方法和 URL 對應** 屬性中，我們會指定使用 GET 方法，並附加 **{VAR}** 做為變數。  
  
      - 在 **變數對應**方塊中，按一下**編輯**。 在此方塊中指定方式的值 **{VAR}** 變數在執行階段推算。  
  
         在 [步驟 3b： 使用 Wcf-webhttp 配接器從 Salesforce 擷取機會詳細資料](../core/step-3b-retrieve-opportunities-from-salesforce-using-the-wcf-webhttp-adapter.md)，我們已升級查詢屬性，這會導致建立**PropertySchema.xsd**。 我們將使用**查詢**該結構描述將由該元素對應至在 URL 中的 {VAR} 變數的查詢字串中的項目。  
  
         在 [變數對應] 對話方塊中，**變數**欄會列出您稍早指定，例如，變數的名稱**VAR**。 在 [**屬性名稱**] 欄中，指定要傳給變數的查詢字串之升級屬性的名稱。 在本教學課程中，該屬性名稱就**查詢**。 最後，針對**屬性的命名空間**，指定的命名空間**PropertySchema.xsd**，這是`https://BtsSalesforceIntegration.PropertySchema`。 按一下 [確定] 。  
  
         ![WCF 的一般 索引標籤&#45;WebHttp 配接器](../core/media/bts-sf-webhttp-general.jpg "BTS_SF_WebHttp_General")  
  
   2. 在上**安全性**索引標籤上，如**安全性模式**，選取**傳輸**。  
  
   3. 在上**行為**索引標籤上，使用您在中建立的自訂行為[步驟 3d： 讓 BizTalk Server 傳送和接收的訊息，從 Salesforce](../core/step-3d-enabling-biztalk-server-to-send-and-receive-messages-from-salesforce.md)向 Salesforce。 若要使用的行為，請執行下列作業：  
  
      -   以滑鼠右鍵按一下**Servicebehavior** ，然後選取**新增擴充功能**。  
  
      -   在 [**選取行為延伸模組**] 對話方塊中，選取**Microsoft.BizTalk.Adapter.Behaviors.Demo.Salesforce**。 我們將行為加入至 machine.config 時使用此行為的名稱。  
  
      -   選取新加入的行為，然後指定下列值：  
  
          |||  
          |-|-|  
          |consumerKey （必要）|指定您的 Salesforce 帳戶的取用者索引鍵。 您可以移至您在建立連線的 Salesforce 應用程式，以擷取取用者索引鍵[步驟 2： 設定 Salesforce 系統](../core/step-2-set-up-the-salesforce-system.md)。|  
          |consumerSecret （必要）|取用者祕密從 Salesforce 連線應用程式中建立的擷取[步驟 2： 設定 Salesforce 系統](../core/step-2-set-up-the-salesforce-system.md)。|  
          |密碼 （必要）|指定的 Salesforce 帳戶的密碼。 若要從協力廠商應用程式連接到 Salesforce，您必須指定密碼格式密碼後面的安全性權杖中。 比方說，如果密碼**密碼**語彙基元，而且**XXXXXX**，您必須輸入`passwordXXXXXX`。|  
          |sessionTimeout|這有預設值為 300。|  
          |使用者名稱 （必要）|指定 Salesforce 開發人員登入帳戶。|  
  
           ![WCF 的 [行為] 索引標籤&#45;WebHttp 配接器](../core/media/bts-sf-webhttp-behavior.jpg "BTS_SF_WebHttp_Behavior")  
  
   4. 上**訊息**索引標籤之下**輸出訊息** 方塊中，如**動詞的隱藏主體**，輸入`GET`。 GET 方法，這可確保沒有任何訊息內容中的要求傳送至 Salesforce。  
  
   5. 按一下 **確定**直到結束所有開啟的對話方塊。  
  
### <a name="to-configure-the-wcf-sql-send-port"></a>若要設定 WCF SQL 傳送埠  
  
1.  依序展開**SalesforceIntegration**應用程式，以滑鼠右鍵按一下**傳送連接埠**，指向**新增**，然後按一下 **靜態的單向傳送埠**.  
  
2.  在傳送埠屬性 對話方塊中，指定下列值：  
  
    |||  
    |-|-|  
    |[屬性]|輸入`SendToSQL`。|  
    |類型|選取**WCF-SQL**|  
    |傳送處理常式|選取**BizTalkServerApplication**|  
    |傳送管線|選取**XMLTransmit**|  
  
     在 傳送埠屬性 對話方塊中，按一下 **設定**針對連接埠類型。  
  
3.  在 [WCF-SQL 傳輸屬性] 對話方塊中，指定下列值：  
  
    1.  在 [一般] 索引標籤上，執行下列動作：  
  
        -   底下`Endpoint Address`，按一下**設定**。 針對**InitialCatalog**屬性，指定包含必須在其中輸入將資料從 Salesforce 回應之資料表的資料庫名稱。 在本教學課程中，輸入此值作為`Orders`。 針對**Server**屬性中，輸入安裝 SQL Server 資料庫的伺服器名稱。  
  
        -   底下**SOAP 動作標頭**，指定要用於插入動作**OrderDetails**資料表。 您必須輸入`TableOp/Insert/dbo/OrderDetails`。  
  
    2.  在 [認證] 索引標籤中，如果所有項目空白配接器使用 Windows 驗證來連接到 SQL Server 資料庫。 如果您想要使用任何其他形式的驗證，您可以指定相關的值。  
  
    3.  按一下 **確定**直到結束所有開啟的對話方塊。  
  
### <a name="to-configure-the-biztalk-server-application"></a>若要設定 BizTalk Server 應用程式  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**SalesforceIntegration**應用程式，，然後按一下**設定**。  
  
2. 在 [設定應用程式] 對話方塊中，選取**NotificationServiceClient**協調流程，以及從右窗格中，執行下列動作：  
  
   1. 針對主機上，選取**BizTalkServerApplication**。  
  
   2. 對應的邏輯接收埠**SalesforceNotificationPort**實體接收埠， **ReceiveOppNotification**。  
  
   3. 邏輯傳送連接埠對應**SalesforceRESTInterface**至實體傳送埠， **SalesforceREST**。  
  
   4. 邏輯傳送連接埠對應**SendToSQL**至實體傳送埠， **SendToSQL**。  
  
      按一下 [確定] 。  
  
3. 以滑鼠右鍵按一下**SalesforceIntegration**應用程式，然後按一下**開始**。 這會啟動**NotificationServiceClient**協調流程中，啟用接收位置，並啟動傳送埠。  
  
   本主題中，我們完成設定中的解決方案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，關聯的實體連接埠至協調流程中的邏輯連接埠。