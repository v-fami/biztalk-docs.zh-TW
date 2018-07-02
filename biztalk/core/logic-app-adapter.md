---
title: 使用 BizTalk Server 中的邏輯應用程式配接器 |Microsoft Docs
description: 安裝和設定來建立接收埠、 接收位置和傳送埠，BizTalk Server 中的 Logic Apps 配接器
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72f2a5ac-a1f6-4bdb-8c29-8267ede75b17
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e13756fb6310b73f8e7fb88c336bdf2a7bbc1372
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972823"
---
# <a name="logic-app-adapter"></a>Logic Apps 配接器

## <a name="overview"></a>概觀
BizTalk Server 會使用 Logic Apps 配接器接收來自 Azure 邏輯應用程式的訊息，或將訊息傳送至 Azure logic app。 

在 Azure 中，我們會建立邏輯應用程式。 此邏輯應用程式會使用 BizTalk 連接器將連線至您在 BizTalk Server 建立的接收位置。 本主題假設您已熟悉 Azure Logic Apps。 如果您還不熟悉 logic apps，我們建議您[深入了解它們](https://azure.microsoft.com/documentation/articles/app-service-logic-what-are-logic-apps/)，並甚至[建立您自己的邏輯應用程式](https://azure.microsoft.com/documentation/articles/app-service-logic-create-a-logic-app/)。

在本主題中，我們會列出在 BizTalk Server 收到訊息，從邏輯應用程式的步驟。 換句話說，邏輯應用程式可以傳送訊息至 BizTalk Server。 接收端會在 IIS 中使用應用程式，來處理與 Azure 服務之間的通訊。 如果 BizTalk Server 在內部部署環境，您也在 BizTalk 伺服器上，安裝資料閘道，並在 Azure 中建立閘道。 

如果 Azure 的虛擬機器 (VM) 上安裝 BizTalk Server，則您可以選擇將 VM 公開為 HTTP 端點 （您取得的 URL），或不要將它公開為 HTTP 端點。 如果您將它公開時，您不需要使用閘道。 您可以在邏輯應用程式中，BizTalk 連接器中輸入您的 URL。 如果您不會公開 VM (無 URL)，您就需要使用閘道。 本主題列出這些步驟。

我們也示範如何從 BizTalk Server 將訊息傳送至 Azure 的邏輯應用程式。 換句話說，邏輯應用程式可以接收訊息從 BizTalk Server。 您會發現本主題中，是相當直覺，傳送端。

您可以使用本主題來建立接收位置和傳送埠使用 Logic Apps 配接器。 您可以使用內部部署 （已加入至您的網域） 的 BizTalk Server 中或執行 BizTalk Server 的 Azure 虛擬機器的 LogicApp 配接器。 

## <a name="requirements"></a>需求

- Azure 訂用帳戶來登入 Azure 入口網站中，並建立邏輯應用程式。
- 選擇性。 若要將測試訊息傳送至邏輯應用程式中，安裝 HTTP 測試工具，例如[Fiddler](http://www.telerik.com/fiddler)或是[Postman](https://www.getpostman.com/)。 如果您使用另一種方法來將訊息傳送到邏輯應用程式時，您不需要使用這些工具。 

## <a name="receive-messages-from-a-logic-app"></a>從邏輯應用程式接收訊息

有幾個步驟以便讓 BizTalk Server 接收邏輯應用程式中的訊息。 此區段會列出這些步驟。 可以在 Azure 的變更，因此部分一個步驟中的使用者介面可能無法完全依照所列。 

#### <a name="prerequisites"></a>必要條件

- 如果 BizTalk Server 會在內部部署，安裝並設定[內部部署資料閘道](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-install/)適用於 Logic Apps。 然後，在 Azure 中，[建立資料閘道資源](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-connection/)連接到您的 BizTalk Server。
- 如果在 Azure VM 上安裝 BizTalk Server，而且 VM 並未公開為 HTTP 端點，然後安裝並設定[內部部署資料閘道](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-install/)適用於 Logic Apps。 然後，在 Azure 中，[建立資料閘道資源](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-connection/)連接到您的 BizTalk Server。
- 如果在 Azure VM 上安裝 BizTalk Server，VM 會公開為 HTTP 端點，再 gateway 已不需要或使用。 

### <a name="step-1-install-the-logic-app-adapter"></a>步驟 1： 安裝邏輯應用程式配接器

邏輯應用程式配接器是不同的下載，並不會包含在 BizTalk Server 安裝。 

> [!IMPORTANT] 
> 若要下載 LogicAppAdapter.iso:
> 
> 1. 移至[Microsoft BizTalk Server 配接器，適用於 Logic Apps](https://www.microsoft.com/download/details.aspx?id=54287)，並儲存。 
> 2. 開啟 LogicAppAdapter.iso，然後執行**LogicApp Adapter.msi**檔案以進行安裝。

1. 在您的 BizTalk Server 上下載並安裝邏輯應用程式配接器。 

2. 雙精度浮點數，來選取**LogicApp Adapter.msi**安裝。 接受授權合約，並**安裝**。
3. **完成**安裝、 d 重新啟動**BizTalkServerApplication**並**BizTalkServerIsolatedHost**主控件執行個體。

安裝之後，您具備下列項目：

- LogicApp 配接器會新增至 BizTalk 管理。
- 傳送處理常式會建立，並使用 biztalkserverapplication 主控件。
- 接收處理常式為 WCF 服務時，會建立，並使用 biztalkserverisolatedhost 主控件。
- `C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter`資料夾會建立，並包含兩個服務： 管理和 ReceiveService。 

    **管理**BizTalk 連接器在邏輯應用程式中用來連接至 BizTalk Server 使用部署資料閘道。 此管理服務可讓 BizTalk Server 接收訊息，使用部署資料閘道 Azure 邏輯應用程式。 BizTalk 接收端只會用於此服務。 它不會由傳送端使用。

    **ReceiveService**輸入接收位置時，由 BizTalk 連接器在邏輯應用程式。 **ReceiveService**負責從邏輯應用程式傳送的訊息。 BizTalk 接收端只會用於此服務。 它不會由傳送端使用。


### <a name="step-2-create-the-iis-applications"></a>步驟 2： 建立 IIS 應用程式

IIS 應用程式使用 「 管理 」 和 「 ReceiveService 服務。

您可以執行使用新的應用程式集區或現有的應用程式集區的 IIS 應用程式。 應用程式集區的身分識別需要到相同的群組，做為帳戶所執行的 BizTalk 服務，例如 「 BizTalk 應用程式使用者 」 和 「 BizTalk 外掛式主控件使用者群組的成員資格。  

> [!TIP] 
> 如果您建立新的應用程式集區，然後保留預設的.NET CLR 版本和受管理的管線。 請記住，選擇已與您的 BizTalk 服務帳戶相同的 BizTalk 群組的成員資格的身分識別 （進階設定）。 

#### <a name="create-the-management-iis-application"></a>建立管理 IIS 應用程式
此 IIS 應用程式的 URL 供 BizTalk 連接器 （在邏輯應用程式） 中，若要使用 BizTalk Server 上的 部署資料閘道。

1. 開啟 Internet Information Services (IIS) 管理員。
2. 以滑鼠右鍵按一下**Default Web Site**，並**新增應用程式**。 在這個新的應用程式： 

    1. 請輸入**別名**（名稱） 為您的應用程式，例如**IISLogicApp**。 
    2. **選取**應用程式集區。
    3. 設定**實體路徑**至`C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter\Management`。 
    3. **測試設定**以確認應用程式集區身分識別通過驗證並授權測試。

3. 選取 [確定] 儲存您的變更。
4. 開啟網頁瀏覽器，並移至`http://localhost/YourApplicationAlias/schemas?api-version=2016-10-26`，例如`http://localhost/IISLogicApp/Schemas?api-version=2016-10-26`。 是的結構描述顯示的清單，或會提示開啟/儲存`schemas.json`。 實際的結果取決於您的 web 瀏覽器。 如果不是上述兩種情況下，則您的應用程式集區身分識別可能遺失到 BizTalk 群組的成員資格。

#### <a name="create-the-biztalk-receiveservice-iis-application"></a>建立 BizTalk ReceiveService IIS 應用程式
此 IIS 應用程式的 URL 供 BizTalk 連接器 （在邏輯應用程式） 當您選擇的接收位置。 

1. 開啟 Internet Information Services (IIS) 管理員。
2. 以滑鼠右鍵按一下**Default Web Site**，並**新增應用程式**。 在這個新的應用程式： 

    1. 請輸入**別名**（名稱） 為您的應用程式，例如**ReceiveWCFService**。 
    2. **選取**與先前的 IIS 應用程式相同的應用程式集區。
    3. 設定**實體路徑**至`C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter\ReceiveService`。 
    3. **測試設定**以確認應用程式集區身分識別通過驗證並授權測試。

3. 選取 [確定] 儲存您的變更。


### <a name="step-3-create-a-logic-app"></a>步驟 3： 建立邏輯應用程式

1. 在  [Azure 入口網站](https://portal.azure.com)，建立新的邏輯應用程式。
2. 新增**HTTP 要求時收到**觸發程序。
3. 新增**BizTalk Server 做為 JSON 準備訊息**動作。 
4. **選擇性**： 選取 **透過內部部署資料閘道連線**，並輸入下列命令： 

    | 屬性 | 描述 |
   | --- | --- |
    | BizTalk Server URL | BizTalk 管理 IIS 應用程式 URL 中輸入完整的網域名稱 (FQDN)。 例如，輸入`http://BizTalkServerName.corp.contoso.com/IISLogicApp/`。 |
    | 驗證類型 | 選取  **Windows**。 |
   | 使用者名稱 | 輸入 IIS 應用程式集區身分的識別。 |
   | [密碼] | 輸入 IIS 應用程式集區的密碼。 |
   | 閘道 | 選取您建立的閘道。 |

    > [!TIP] 
    > 請記住，部署資料閘道，才需要：
    > - 您使用內部部署 BizTalk Server
    > - 您使用 BizTalk Server 的 Azure 虛擬機器*和*VM 並未公開為 HTTP 端點 (沒有 URL)

5. 選取 [建立]。 
6. 設定動作。 針對**主體**，選取 HTTP 主體輸出。 針對**結構描述**，選取您想要使用的結構描述。 

    > [!NOTE] 
    > 這個步驟假設您熟悉 BizTalk 中的結構描述，並且知道您想要的結構描述。 如果您不確定，部署 HelloWorld SDK > 範例的然後、 可更新以使用邏輯應用程式配接器及其成品，並使用其結構描述和範例的訊息。 

7. 加入新的步驟中，然後選取**BizTalk Server 做為傳送訊息**動作。 針對**接收位置**、 從下拉式清單中，選取 URL，或輸入 ReceiveService IIS 應用程式 URL 的完整的網域名稱 (FQDN)。 例如，輸入`http://BizTalkServerName.corp.contoso.com/ReceiveWCFService/Service1.svc`。

    > [!TIP] 
    > 當您建立的接收位置時，將也做為接收位置傳輸屬性中輸入此的確切 URL**公用位址**（一般索引標籤）。

    針對**主體**，選取從先前的 「 BizTalk Server 」 動作的主體的輸出。 

8. **儲存**您的變更。 

當您儲存時，HTTP 要求觸發程序會自動建立的 URL。 複製這個 URL;您需要在**步驟 5： 將訊息傳送**。

### <a name="step-4-create-a-receive-port-and-a-receive-location"></a>步驟 4： 建立接收埠和接收位置

> [!NOTE] 
> 而不是建立您自己的接收埠和接收位置，您可以部署 HelloWorld SDK > 範例。 更新要使用 Logic Apps 配接器的成品。 
 
本節列出的步驟來建立您自己的構件。 

1. 在 BizTalk Server 管理，依序展開**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，然後展開您想要的應用程式執行接收位置。 例如，依序展開**BizTalk Application 1**。
2. 權限，來選取**接收連接埠**，選取**新增**，然後選取**單向接收埠**。
3. 在接收埠屬性中，輸入下列內容：  

    | 使用 | 以進行此動作 |
    | --- | --- |
    | **名稱** | 輸入接收埠的名稱。 例如，輸入**LAReceivePort**。 |
    | **驗證** | 選項： <br/><ul><li>沒有驗證： 預設值。 停用驗證。</li><li>驗證失敗時捨棄訊息： 啟用驗證，但若要卸除未驗證的訊息。</li><li>驗證失敗時保留訊息： 按一下此選項以啟用驗證並保留未驗證的訊息。 </li></ul>|
    | **啟用失敗訊息的路由** | 將路由傳送至訂閱應用程式的處理失敗的任何訊息 （例如其他接收埠或協調流程排程）。 取消核取此選項以擱置失敗的訊息，並產生負值通知 (NACK)。 預設值為清除核取方塊。 如需詳細資訊，請參閱 <<c0> [ 如何啟用接收埠的失敗訊息路由](../core/how-to-enable-routing-for-failed-messages-for-a-receive-port.md)。|

4. 選取 **接收位置**，然後選取**新增**。 
5. 請輸入**名稱**接收位置。 例如，輸入**LAReceiveLoc**。
6. 針對**型別**，選取**LogicApp**從清單中，選取 **[設定] 按鈕**。 
7. 在 **一般**索引標籤上，設定您的邏輯應用程式的端點位址：

    | 使用 | 以進行此動作 |
    | --- | --- |
    | **位址 (URI)** | 必要。 輸入 BizTalk ReceiveService IIS 應用程式 URL (`/YourIISApp2Name/Service1.svc`)。 例如，輸入`/ReceiveWCFService/Service1.svc`。 |
    | **公用位址** | 必要。 輸入`http://<your fully qualified machine name>/YourIISApp2Name/Service1.svc`。 例如，輸入`http://btsProd.northamerica.corp.contoso.com/ReceiveWCFService/Service1.svc`。 <br/><br/>這個確切的 URL 也會列在 接收位置在邏輯應用程式。|

8. **選擇性**。 在 **繫結**索引標籤上，設定任何逾時和編碼相關的基礎 Wcf-webhttp 繫結的屬性。 處理大型訊息時，這些屬性是很有幫助。

    | 使用 | 以進行此動作 |
    | --- | --- |
    | 開啟逾時 | 輸入會完成通道開啟作業所花費的時間間隔。 此值應該大於或等於 System.TimeSpan.Zero。 <br/><br/>預設值：00:01:00<br/>最大值： 23:59:59 |
    | 傳送等候逾時 |輸入應該需要傳送作業完成的時間間隔。 此值應該大於或等於 System.TimeSpan.Zero。 如果您使用要求-回應接收埠，這個值會指定完成，整個互動的時間長度，即使在用戶端傳回很大的訊息。 <br/><br/>預設值：00:01:00<br/>最大值： 23:59:59|
    | 關閉等候逾時 | 輸入會完成通道關閉作業所花費的時間間隔。 此值應該大於或等於 System.TimeSpan.Zero。 <br/><br/>預設值：00:01:00<br/>最大值： 23:59:59 |
    | 接收訊息大小上限 (以位元組為單位) | 輸入的大小上限，以位元組為單位，包括標頭在網路上接收訊息。 訊息大小受限於配置給每個訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。 <br/><br/>預設值：65536<br/>最大值：2147483647|
    | 同時呼叫數目上限 | 輸入對單一服務執行個體的同時呼叫數目。 超出上限的呼叫將排入佇列。 將此值設定為 0 相當於將它設定為 Int32.MaxValue。 <br/><br/>預設值是 200。|

9. **選擇性**。 在 **安全性**索引標籤上，設定任何安全性屬性。 基於開發目的，您可以選擇無：

    | 使用 | 以進行此動作 |
    | --- | --- |
    | 安全性模式 | 選項：  <br/><br/><ul><li>None： 不保護訊息傳輸期間。</li><li>Transport： 使用安全性來提供 HTTPS 傳輸。 使用 HTTPS 來維護 SOAP 訊息的安全。 若要使用此模式中，您必須設定設定安全通訊端層 (SSL) 在網際網路資訊服務 (IIS)。 </li><li>TransportCredentialOnly： 預設值。 </li></ul> |
    | 傳輸用戶端認證類型 | 使用用戶端驗證時，請選擇認證類型。 選項：  <br/><br/><ul><li>None： 不驗證就會發生在傳輸層級。</li><li>Basic： 使用基本驗證 以透過網路以純文字傳送使用者名稱和密碼。 您必須建立對應到認證的網域或本機使用者帳戶。</li><li>若要透過網路傳送密碼做為雜湊值的摘要： 使用摘要式驗證。 只能在執行 Windows Server 作業系統驗證的網域控制站的網域。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。</li><li>Ntlm： 預設值。 用戶端傳送的認證，而不將密碼傳送至這個接收位置。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。</li><li>Windows: Windows 整合式的驗證會交涉 Kerberos 或 NTLM，如果定義域存在，則偏好 Kerberos。 若要使用 Kerberos，請務必讓用戶端與服務主要名稱 (SPN) 識別服務。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。</li><li>憑證： 使用用戶端憑證。 CA 憑證鏈結的用戶端 X.509 憑證必須安裝在這部電腦的受信任的根憑證授權單位憑證存放區，以便用戶端可以向這個接收位置。</li><li>InheritedFromHost</li></ul> |
    | 使用單一登入 | |


10. **選擇性**。 在 **訊息**索引標籤上，使用**輸出 HTTP 標頭**新增任何自訂標頭，並使用其他屬性來協助進行錯誤的屬性： 

    | 使用 | 以進行此動作 |
    | --- | --- |
    |輸出 HTTP 標頭 | 輸入任何您想要在回應訊息上加上戳記的 HTTP 標頭。 | 
    | 失敗時停用位置 | 如果輸入的處理失敗，因為接收管線失敗或路由失敗，會停用接收位置。 預設為核取。|
    | 失敗時擱置的要求訊息 | 如果輸入的處理失敗，因為接收管線失敗或路由失敗，暫止要求訊息。 預設為核取。|
    | 錯誤中包含例外狀況詳細資料 | 發生錯誤時，會傳回任何 SOAP 錯誤，以協助偵錯。 預設為核取。|

[管理接收位置](../core/managing-receive-locations.md)描述的其他屬性。 

### <a name="step-5-send-a-message"></a>步驟 5： 將訊息傳送

1. 開啟 Fiddler 或 Postman （或您偏好的任何內容）。
2. 貼上從邏輯應用程式的要求觸發程序的 URL。 您在步驟 3 中複製此 URL。 
3. 選取  **POST**作為 HTTP 指令動詞，並將**content-type**標頭`application/json`。 在本文中，貼上下列 JSON:  

    ```json
    {“hello”:”world”}
    ```

4. 因為這是 BizTalk 的單向呼叫時，結果應該是 HTTP 202。 如果您使用 HelloWorld SDK 範例，請移至您的 BizTalk server。 在您的傳送資料夾可能是檔案。 


## <a name="send-messages-to-a-logic-app"></a>將訊息傳送至邏輯應用程式

### <a name="step-1-install-the-logic-apps-adapter"></a>步驟 1： 安裝 Logic Apps 配接器

Logic Apps 配接器是不同的下載，並不會包含在 BizTalk Server 安裝。

1. 移至[Microsoft BizTalk Server 配接器，適用於 Logic Apps](https://www.microsoft.com/download/details.aspx?id=54287)，並儲存。 
2. 開啟 LogicAppAdapter.iso，然後執行**LogicApp Adapter.msi**檔案以進行安裝。
3. **完成**安裝和重新啟動**BizTalkServerApplication**並**BizTalkServerIsolatedHost**主控件執行個體。

安裝之後，您具備下列項目：

- LogicApp 配接器新增至 BizTalk 管理
- 傳送處理常式會建立，並使用 biztalkserverapplication 主控件。
- 接收處理常式為 WCF 服務時，會建立，並使用 biztalkserverisolatedhost 主控件。
- `C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter`資料夾會建立，並包含兩個服務： 管理和 ReceiveService。 這些服務不會將訊息傳送至邏輯應用程式。 


### <a name="step-2-create-a-logic-app"></a>步驟 2： 建立邏輯應用程式

1. 在  [Azure 入口網站](https://portal.azure.com)，建立新的邏輯應用程式。
2. 新增**HTTP 要求時收到**觸發程序
3. 新增**Office 365 Outlook-傳送電子郵件**動作。 針對**至**位址，請輸入您的 Office 365 地址。 針對**主旨**，輸入`Sending from BizTalk`。 針對**主體**，選擇*主體*的輸出**收到 HTTP 要求時**觸發程序。 
4. 邏輯應用程式看起來類似： 

    ![LogicAppExample](../core/media/logicappexample.gif)

5. 複製 HTTP POST URL 會自動建立，當您儲存邏輯應用程式中;您需要在下一個步驟中的此 URL。 您可能必須關閉再重新開啟邏輯應用程式中看到的 URL。  


### <a name="step-3-create-a-send-port"></a>步驟 3： 建立傳送埠

BizTalk server 將訊息傳送至邏輯應用程式，邏輯應用程式必須有**手動**觸發程序，例如**手動-HTTP 要求時收到**。 

1. 在 BizTalk Server 管理，依序展開**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，然後展開您想要的應用程式執行傳送埠。 例如，依序展開**BizTalk Application 1**。
2. 權限，來選取**傳送埠**，選取**新增**，然後選取**靜態單向傳送埠**。
3. 請輸入**名稱**傳送埠。 例如，輸入**LASendPort**。
4. 針對**型別**，選取**LogicApp**從清單中，選取**設定** 按鈕。 
5. 在 **一般**索引標籤上，設定**回呼 URI**的邏輯應用程式觸發程序。 有兩種方式可以執行此動作： 

    **選項 1** ： 貼上您在上一個步驟中複製 HTTP POST URL**觸發程序 (回呼 URI)** 屬性。 您也可以複製 URI 使用下列步驟：  
  
   1. 在  [Azure 入口網站](https://portal.azure.com)，在 Logic Apps 設計工具 （編輯模式） 中開啟邏輯應用程式。 
   2. 選取  **HTTP 要求時收到**卡片，並複製**URL**。 
   3. 在傳送埠中，貼上此 URL**觸發程序 (回呼 URI)** 屬性。

      > [!TIP] 
      > 您也可以使用您的管理 Api 來取得此 URI。

      **選項 2** ： 如果您不知道回呼 URI 觸發程序，選取**設定**，和登入 Azure。 然後，使用下拉式清單選擇您**訂用帳戶**，**資源群組**，**邏輯應用程式**，以及**觸發程序**。
 
6. **選擇性**。 在 **繫結**索引標籤上，設定任何逾時和編碼相關的基礎 Wcf-webhttp 繫結的屬性。 處理大型訊息時，這些屬性是很有幫助。

    | 使用 | 以進行此動作 |
    | --- | --- |
    | 開啟逾時 | 輸入會完成通道開啟作業所花費的時間間隔。 此值應該大於或等於 System.TimeSpan.Zero。 <br/><br/>預設值：00:01:00<br/>最大值： 23:59:59 |
    | 傳送等候逾時 |輸入應該需要傳送作業完成的時間間隔。 此值應該大於或等於 System.TimeSpan.Zero。 如果您使用要求-回應接收埠，這個值會指定完成，整個互動的時間長度，即使在用戶端傳回很大的訊息。 <br/><br/>預設值：00:01:00<br/>最大值： 23:59:59|
    | 關閉等候逾時 | 輸入會完成通道關閉作業所花費的時間間隔。 此值應該大於或等於 System.TimeSpan.Zero。 <br/><br/>預設值：00:01:00<br/>最大值： 23:59:59 |
    | 接收訊息大小上限 (以位元組為單位) | 輸入的大小上限，以位元組為單位，包括標頭在網路上接收訊息。 訊息大小受限於配置給每個訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。 <br/><br/>邏輯 appa 配接器會利用[WebHttpBinding 類別](https://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.aspx)在緩衝的傳輸模式中與端點進行通訊。 緩衝的傳輸模式中， [WebHttpBinding.MaxBufferSize](https://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.maxbuffersize.aspx)屬性會一律等於這個屬性的值。  <br/><br/>預設值：65536<br/>最大值：2147483647 |


7. **選擇性**。 在 **訊息**索引標籤上，使用**輸出 HTTP 標頭**外寄訊息上新增任何自訂標頭的屬性。 
8. 選取 **確定**來儲存您的組態。 

[管理傳送埠與傳送埠群組](../core/managing-send-ports-and-send-port-groups.md)描述的其他傳送埠屬性。 

### <a name="step-4-send-some-messages"></a>步驟 4： 傳送一些訊息

您可以建立接收埠和接收位置使用 File 配接器。 請務必啟用邏輯應用程式。

1. 建立接收埠，例如*FileSendPort*，
2. 建立接收位置，並設定屬性類似於：  

    | 屬性 | 範例輸入 |
    | --- | --- |
   | 接收資料夾 | C:\temp\In\ |
   | 檔案遮罩 | *.txt |
   | 管線 | PassThruReceive |

3. 在您建立傳送埠，將**篩選**來：

    | 屬性 | 運算子 | ReplTest1 |
    | --- | --- | --- |
    | BTS.ReceivePortName |  == | *FileSendPort* |

4. 建立包含下列文字的文字檔案 (FileName.txt)。 使用此文字檔案做為範例訊息： 

    ```
    <Data>
      <DataID>DataID_0</DataID>
      <DataDetails>DataDetails_0</DataDetails>
    </Data>
    ```

5. 將您的範例訊息 (FileName.txt) 複製到接收資料夾中。 傳送埠會將.txt 檔案傳送至邏輯應用程式使用您所輸入的 URI。 邏輯應用程式接收檔案。 如果您使用 Office 365 Outlook 連接器，您*至*電子郵件地址應該會收到電子郵件中的範例訊息。

## <a name="next"></a>下一個
[什麼是 Logic Apps](https://azure.microsoft.com/documentation/articles/app-service-logic-what-are-logic-apps/)  

[建立邏輯應用程式](https://azure.microsoft.com/documentation/articles/app-service-logic-create-a-logic-app/)

[在 BizTalk Server 使用配接器](../core/using-adapters.md)