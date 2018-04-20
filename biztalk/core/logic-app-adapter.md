---
title: 在 BizTalk Server 中的使用邏輯應用程式配接器 |Microsoft 文件
description: 安裝和設定邏輯應用程式配接器來建立接收埠、 接收位置，在 BizTalk Server 傳送埠
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
ms.openlocfilehash: faa43c187df7a8eb9fccd2f02f23f16e86b97ce0
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="logic-app-adapter"></a>邏輯應用程式配接器

## <a name="overview"></a>概觀
BizTalk Server 會使用邏輯應用程式配接器接收訊息從 Azure 邏輯應用程式，或將訊息傳送至 Azure 邏輯應用程式。 

在 Azure 中，我們會建立邏輯應用程式。 此邏輯應用程式會使用 BizTalk 連接器來連接到您在 BizTalk Server 建立的接收位置。 本主題假設您已熟悉 Azure 邏輯應用程式。 如果您是新手邏輯應用程式，我們建議您 [深入了解它們](https://azure.microsoft.com/documentation/articles/app-service-logic-what-are-logic-apps/), ，甚至 [建立邏輯應用程式](https://azure.microsoft.com/documentation/articles/app-service-logic-create-a-logic-app/)。

本主題中，我們會列出在 BizTalk Server 接收訊息的邏輯應用程式中的步驟。 換句話說，邏輯應用程式將訊息傳送至 BizTalk Server。 接收端會使用應用程式在 IIS 中處理 Azure 的服務通訊。 如果 BizTalk Server 在內部，您也在 BizTalk 伺服器上安裝資料閘道，並在 Azure 中建立的閘道。 

如果 BizTalk 伺服器安裝在 Azure 虛擬機器 (VM)，則您可以選擇將 VM 公開為 HTTP 端點 （您取得的 URL），或不公開 HTTP 端點。 如果您將它公開時，您不需要使用閘道。 您可以在邏輯應用程式中，BizTalk 連接器中輸入您的 URL。 如果您不要公開 VM (沒有 URL)，您必須使用閘道。 本主題列出這些步驟。

我們也顯示如何從 BizTalk Server 傳送訊息至 Azure 邏輯應用程式。 邏輯應用程式放在另一種方式，從 BizTalk Server 接收訊息。 本主題中，您會發現，就相當簡單，傳送端。

您可以使用本主題來建立接收位置和傳送埠使用邏輯應用程式配接器。 您可以使用 LogicApp 配接器在內部部署 （加入至您的網域） 的 BizTalk Server 中或執行 BizTalk Server 的 Azure 虛擬機器。 

## <a name="requirements"></a>需求

- Azure 訂閱，才能登入 Azure 入口網站，然後建立邏輯應用程式。
- 選擇性。 若要將測試訊息傳送至您的邏輯應用程式，安裝 HTTP 的測試工具，例如 [Fiddler](http://www.telerik.com/fiddler) 或 [Postman](https://www.getpostman.com/)。 如果您使用另一種方法將訊息傳送至邏輯應用程式時，您不必使用這些工具。 

## <a name="receive-messages-from-a-logic-app"></a>從邏輯應用程式接收訊息

有幾個步驟的邏輯應用程式中接收訊息的 BizTalk Server。 此區段會列出這些步驟。 就 Azure 的變更，因此某些步驟中的使用者介面可能無法完全如下所列。 

#### <a name="prerequisites"></a>必要條件

- 如果 BizTalk Server 會在內部，安裝並設定 [內部資料閘道](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-install/) 為邏輯應用程式。 然後，在 Azure 中， [建立資料閘道資源](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-connection/) 連接到您的 BizTalk Server。
- 如果在 Azure VM 上安裝 BizTalk Server VM 不會公開為 HTTP 端點，然後安裝及設定 [內部資料閘道](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-install/) 為邏輯應用程式。 然後，在 Azure 中， [建立資料閘道資源](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-connection/) 連接到您的 BizTalk Server。
- 如果在 Azure VM 上安裝 BizTalk Server，而且 VM 會公開為 HTTP 端點，然後閘道與不需要或使用。 

### <a name="step-1-install-the-logic-app-adapter"></a>步驟 1︰ 安裝邏輯應用程式配接器

邏輯應用程式配接器是不同的下載，並不是隨附於 BizTalk Server 安裝。 

> [!IMPORTANT] 
> 若要下載 LogicAppAdapter.iso:
> 
> 1. 移至 [邏輯應用程式的 Microsoft BizTalk Server 配接器](https://www.microsoft.com/download/details.aspx?id=54287), ，並儲存。 
> 2. 開啟 LogicAppAdapter.iso，並執行 **LogicApp Adapter.msi** 檔案來安裝。

1. BizTalk Server 中，下載並安裝邏輯應用程式配接器。 

2. 按兩下以選取 **LogicApp Adapter.msi** 安裝。 接受授權合約，以及 **安裝**。
3. **完成** 安裝、 d 的重新啟動 **BizTalkServerApplication** 和 **BizTalkServerIsolatedHost** 主控件執行個體。

安裝之後，您具有下列項目︰

- LogicApp 配接器會新增至 BizTalk 管理。
- 傳送處理常式會建立，並使用 biztalkserverapplication 主控件。
- 接收處理常式做為 WCF 服務，會建立，並使用 biztalkserverisolatedhost 主控件。
- `C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter`資料夾已建立，且包含兩個服務： 管理和 ReceiveService。 

    **管理**BizTalk 連接器邏輯應用程式中用來連接至 BizTalk Server 使用的資料閘道。 此管理服務可讓 BizTalk Server 接收訊息從 Azure 邏輯應用程式使用資料閘道。 在 BizTalk 接收端只使用這項服務。 它不是由傳送端。

    **ReceiveService**輸入接收位置時，由 BizTalk 連接器，在邏輯應用程式。 **ReceiveService**負責從邏輯應用程式傳送訊息。 在 BizTalk 接收端只使用這項服務。 它不是由傳送端。


### <a name="step-2-create-the-iis-applications"></a>步驟 2︰ 建立 IIS 應用程式

IIS 應用程式使用的管理和 ReceiveService 服務。

您可以執行使用新的應用程式集區或現有的應用程式集區的 IIS 應用程式。 AppPool 識別需要執行 BizTalk 服務，例如 「 BizTalk 應用程式使用者 」 和 「 BizTalk 外掛式主控件使用者群組的帳戶相同群組的成員資格。  

> [!TIP] 
> 如果您建立新的應用程式集區，那麼請保留預設的.NET CLR 版本，與受管理的管線。 請記住，選擇 身分識別 （進階設定） 具有相同的 BizTalk 群組與 BizTalk 服務帳戶的成員資格。 

#### <a name="create-the-management-iis-application"></a>建立管理 IIS 應用程式
此 IIS 應用程式的 URL 供 BizTalk 中的連接器 （在邏輯應用程式），來使用 BizTalk Server 上的資料閘道。

1. 開啟網際網路資訊服務 (IIS) 管理員。
2. 以滑鼠右鍵按一下 **預設的網站**, ，和 **新增應用程式**。 在這個新的應用程式︰ 

    1. 輸入 **別名** （名稱） 的應用程式，例如 **IISLogicApp**。 
    2. **選取** 應用程式集區。
    3. 設定**實體路徑**至`C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter\Management`。 
    3. **測試設定** 確認應用程式集區身分識別通過驗證，並測試授權。

3. 選取 **確定** 以儲存變更。
4. 開啟網頁瀏覽器，並移至`http://localhost/YourApplicationAlias/schemas?api-version=2016-10-26`，例如`http://localhost/IISLogicApp/Schemas?api-version=2016-10-26`。 可能是結構描述顯示的清單，或提示開啟/儲存 `schemas.json`。 實際的結果取決於您的 web 瀏覽器。 如果發生上述任一種情況，然後 AppPool 識別可能會遺失的 BizTalk 群組的成員資格。

#### <a name="create-the-biztalk-receiveservice-iis-application"></a>建立 BizTalk ReceiveService IIS 應用程式
此 IIS 應用程式的 URL 由 BizTalk 中的連接器 （在邏輯應用程式） 當您選擇接收位置。 

1. 開啟網際網路資訊服務 (IIS) 管理員。
2. 以滑鼠右鍵按一下 **預設的網站**, ，和 **新增應用程式**。 在這個新的應用程式︰ 

    1. 輸入 **別名** （名稱） 的應用程式，例如 **ReceiveWCFService**。 
    2. **選取** 與先前的 IIS 應用程式相同的應用程式集區。
    3. 設定**實體路徑**至`C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter\ReceiveService`。 
    3. **測試設定** 確認應用程式集區身分識別通過驗證，並測試授權。

3. 選取 **確定** 以儲存變更。


### <a name="step-3-create-a-logic-app"></a>步驟 3︰ 建立邏輯應用程式

1. 在 [Azure 入口網站](https://portal.azure.com), ，建立新的邏輯應用程式。
2. 新增 **收到時的 HTTP 要求** 觸發程序。
3. 新增 **BizTalk Server 做為準備從 JSON 訊息** 動作。 
4. **選擇性**︰ 選取 **連線透過內部資料閘道**, ，並輸入下列命令︰ 

    | 屬性 | Description |
   | --- | --- |
    | BizTalk Server URL | BizTalk 管理中 IIS 應用程式 URL，請輸入完整的網域名稱 (FQDN)。 例如，輸入`http://BizTalkServerName.corp.contoso.com/IISLogicApp/`。 |
    | 驗證類型 | 選取 **Windows**。 |
   | 使用者名稱 | 輸入 IIS 應用程式集區識別。 |
   | 密碼 | 輸入 IIS 應用程式集區的密碼。 |
   | 閘道 | 選取您建立的閘道。 |

    > [!TIP] 
    > 請記住，只是資料閘道器才需要︰
    > - 您使用內部部署 BizTalk Server
    > - 您使用 BizTalk Server 的 Azure 虛擬機器 *和* VM 不會公開為 HTTP 端點 (沒有 URL)

5. 選取 [建立]。 
6. 設定動作。 如 **主體**, ，選取 HTTP 主體輸出。 如 **結構描述**, ，選取您想要使用的結構描述。 

    > [!NOTE] 
    > 這個步驟假設您已熟悉 biztalk 結構描述，而且知道您想要的結構描述。 如果您不確定，然後部署 HelloWorld SDK 範例，更新使用邏輯應用程式配接器，其成品和使用其結構描述和範例訊息。 

7. 加入新的步驟，然後選取 **BizTalk Server 做為傳送訊息** 動作。 如**接收位置**、 從下拉式清單中，選取 URL，或輸入 ReceiveService IIS 應用程式 URL 的完整的網域名稱 (FQDN)。 例如，輸入 `http://BizTalkServerName.corp.contoso.com/ReceiveWCFService/Service1.svc`。

    > [!TIP] 
    > 當您建立的接收位置時，將也做為接收位置傳輸屬性中輸入確切的 URL **公用位址** （一般索引標籤）。

    如 **主體**, ，從上一個 BizTalk Server 動作選取主體輸出。 

8. **儲存** 您的變更。 

當您儲存時，HTTP 要求觸發程序會自動建立的 URL。 複製這個 URL。您需要在 **步驟 5︰ 將訊息傳送**。

### <a name="step-4-create-a-receive-port-and-a-receive-location"></a>步驟 4︰ 建立接收埠和接收位置

> [!NOTE] 
> 而不是建立您自己的接收埠和接收位置，您可以部署 HelloWorld SDK 範例。 更新要使用邏輯應用程式配接器的成品。 
 
本節列出的步驟來建立您自己的成品。 

1. 在 BizTalk Server 管理，依序展開 **BizTalk Server 管理**, ，依序展開 **BizTalk 群組**, ，依序展開 **應用程式**, ，然後展開您想要執行的接收位置的應用程式。 例如，展開  **BizTalk Application 1**。
2. 右邊選取 **接收埠**, ，請選取 **新增**, ，然後選取 **單向接收埠**。
3. 在接收埠屬性中，輸入下列資訊︰  

    | 使用 | 動作 |
    | --- | --- |
    | **名稱** | 輸入接收埠的名稱。 例如，輸入 **LAReceivePort**。 |
    | **驗證** | 選項： <br/><ul><li>不需要驗證︰ 預設值。 停用驗證。</li><li>驗證失敗時捨棄訊息︰ 啟用驗證，但若要卸除未驗證的訊息。</li><li>驗證失敗時保留訊息︰ 按一下此選項以啟用驗證並保留未驗證的訊息。 </li></ul>|
    | **啟用失敗訊息的路由** | 將路由至訂閱應用程式的處理失敗的任何訊息 （例如其他接收埠或協調流程排程）。 取消選取此選項以擱置失敗的訊息，並產生負值通知 (NACK)。 預設值為清除核取方塊。 如需詳細資訊，請參閱[如何啟用接收埠的失敗訊息路由](../core/how-to-enable-routing-for-failed-messages-for-a-receive-port.md)。|

4. 選取 **接收位置**, ，然後選取 **新增**。 
5. 輸入 **名稱** 接收位置。 例如，輸入 **LAReceiveLoc**。
6. 如 **類型**, ，請選取 **LogicApp** 從清單中，然後選取 **設定 按鈕**。 
7. 在 **一般** 索引標籤上，設定端點位址，以便在邏輯應用程式︰

    | 使用 | 動作 |
    | --- | --- |
    | **位址 (URI)** | 必要。 輸入 BizTalk ReceiveService IIS 應用程式 URL (`/YourIISApp2Name/Service1.svc`)。 例如，輸入 `/ReceiveWCFService/Service1.svc`。 |
    | **公用位址** | 必要。 輸入 `http://<your fully qualified machine name>/YourIISApp2Name/Service1.svc`。 例如，輸入 `http://btsProd.northamerica.corp.contoso.com/ReceiveWCFService/Service1.svc`。 <br/><br/>確切的 URL 也會列在邏輯應用程式中接收位置。|

8. **選擇性**。 在 **繫結** 索引標籤上，設定任何逾時和編碼相關基礎 Wcf-webhttp 繫結的屬性。 處理大型訊息時，這些屬性是很有幫助。

    | 使用 | 動作 |
    | --- | --- |
    | 開啟逾時 | 輸入應該才會完成通道開啟作業的時間間隔。 這個值應該大於或等於 System.TimeSpan.Zero。 <br/><br/>預設值：00:01:00<br/>最大值︰ 23:59:59 |
    | 傳送逾時 |輸入應該針對完成傳送作業的時間間隔。 這個值應該大於或等於 System.TimeSpan.Zero。 如果您使用要求-回應接收埠，這個值會指定，才能完成整個互動的時間長度，即使在用戶端傳回很大的訊息。 <br/><br/>預設值：00:01:00<br/>最大值︰ 23:59:59|
    | 關閉逾時 | 輸入所需的通道關閉作業完成的時間間隔。 這個值應該大於或等於 System.TimeSpan.Zero。 <br/><br/>預設值：00:01:00<br/>最大值︰ 23:59:59 |
    | 接收訊息大小上限 (以位元組為單位) | 輸入的最大的大小，以位元組為單位，包括標頭，在網路上接收訊息。 訊息大小受限於配置給各訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。 <br/><br/>預設值：65536<br/>最大值：2147483647|
    | 同時呼叫數目上限 | 輸入單一服務執行個體的並行呼叫數。 超出上限的呼叫將排入佇列。 將此值設定為 0 相當於設定為 Int32.MaxValue。 <br/><br/>預設值是 200。|

9. **選擇性**。 在 **安全性** 索引標籤上，設定任何安全性屬性。 為開發用途，您可以選擇 無︰

    | 使用 | 以進行此動作 |
    | --- | --- |
    | 安全性模式 | 選項：  <br/><br/><ul><li>None︰ 不保護訊息傳輸期間。</li><li>傳輸︰ 安全性提供使用 HTTPS 傳輸。 使用 HTTPS 來維護 SOAP 訊息的安全。 若要使用此模式中，您必須設定設定安全通訊端層 (SSL) 在網際網路資訊服務 (IIS)。 </li><li>TransportCredentialOnly︰ 預設值。 </li></ul> |
    | 傳輸用戶端認證類型 | 使用用戶端驗證時，請選擇認證類型。 選項：  <br/><br/><ul><li>None︰ 不需要驗證就會發生在傳輸層級。</li><li>Basic︰ 使用基本驗證透過網路以純文字傳送使用者名稱和密碼。 您必須建立對應到認證的網域或本機使用者帳戶。</li><li>若要透過網路傳送密碼以雜湊值的摘要︰ 使用摘要式驗證。 僅適用於執行 Windows Server 作業系統驗證網域控制站的定義域。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。</li><li>Ntlm︰ 預設值。 用戶端傳送的認證，而不需要密碼傳送至這個接收位置。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。</li><li>Windows: Windows 整合式的驗證會交涉 Kerberos 或 NTLM，如果網域存在，則偏好 Kerberos。 若要使用 Kerberos，是讓用戶端與服務主要名稱 (SPN) 識別服務。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。</li><li>憑證︰ 使用用戶端憑證。 CA 憑證鏈結的用戶端 X.509 憑證必須安裝在這部電腦的受信任的根憑證授權單位憑證存放區，讓用戶端可以驗證此接收位置。</li><li>InheritedFromHost</li></ul> |
    | 使用單一登入 | |


10. **選擇性**。 在 **訊息** 索引標籤上，使用 **傳出的 HTTP 標頭** 屬性加入任何自訂標頭，並使用其他屬性來幫助的錯誤︰ 

    | 使用 | 以進行此動作 |
    | --- | --- |
    |輸出 HTTP 標頭 | 輸入您想要的回應訊息中加上任何 HTTP 標頭。 | 
    | 失敗時停用位置 | 如果輸入的處理失敗，因為接收管線失敗或路由失敗，會停用接收位置。 預設為核取。|
    | 失敗時擱置的要求訊息 | 如果輸入的處理失敗，因為接收管線失敗或路由失敗而，擱置的要求訊息。 預設為核取。|
    | 錯誤中包含例外狀況詳細資料 | 發生錯誤時，會傳回任何 SOAP 錯誤，以協助偵錯。 預設為核取。|

[管理接收位置](../core/managing-receive-locations.md)描述其他屬性。 

### <a name="step-5-send-a-message"></a>步驟 5︰ 將訊息傳送。

1. 開啟 Fiddler 或 Postman （或您偏好的任何內容）。
2. 貼上 URL，從邏輯應用程式的要求觸發程序。 您在步驟 3 中複製此 URL。 
3. 選取 **POST** 做為 HTTP 動詞命令，並將 **content-type** 標頭以 `application/json`。 在本文中，貼上下列 JSON:  

    ```json
    {“hello”:”world”}
    ```

4. 因為這是 BizTalk 的單向呼叫時，結果應該是 HTTP 202。 如果您使用 HelloWorld SDK 範例，請移至您的 BizTalk server。 傳送資料夾中可能是檔案。 


## <a name="send-messages-to-a-logic-app"></a>將訊息傳送至邏輯應用程式

### <a name="step-1-install-the-logic-apps-adapter"></a>步驟 1︰ 安裝邏輯應用程式配接器

邏輯應用程式配接器是不同的下載，並不是隨附於 BizTalk Server 安裝。

1. 移至 [邏輯應用程式的 Microsoft BizTalk Server 配接器](https://www.microsoft.com/download/details.aspx?id=54287), ，並儲存。 
2. 開啟 LogicAppAdapter.iso，並執行 **LogicApp Adapter.msi** 檔案來安裝。
3. **完成** 安裝和重新啟動 **BizTalkServerApplication** 和 **BizTalkServerIsolatedHost** 主控件執行個體。

安裝之後，您具有下列項目︰

- LogicApp 配接器新增至 BizTalk 管理
- 傳送處理常式會建立，並使用 biztalkserverapplication 主控件。
- 接收處理常式做為 WCF 服務，會建立，並使用 biztalkserverisolatedhost 主控件。
- `C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter`資料夾已建立，且包含兩個服務： 管理和 ReceiveService。 這些服務不會用於將訊息傳送至邏輯應用程式。 


### <a name="step-2-create-a-logic-app"></a>步驟 2︰ 建立邏輯應用程式

1. 在 [Azure 入口網站](https://portal.azure.com), ，建立新的邏輯應用程式。
2. 新增 **收到時的 HTTP 要求** 觸發程序
3. 新增 **Office 365 Outlook 的電子郵件傳送** 動作。 如 **至** 位址，請輸入您的 Office 365 地址。 如 **主體**, ，輸入 `Sending from BizTalk`。 如 **主體**, ，選擇  *主體* 輸出從 **收到時的 HTTP 要求** 觸發程序。 
4. 在邏輯應用程式看起來類似︰ 

    ![LogicAppExample](../core/media/logicappexample.gif)

5. 複製儲存在邏輯應用程式中，會自動建立的 HTTP POST URL您需要此 URL 在下一個步驟。 您可能要關閉並重新開啟邏輯應用程式看到的 URL。  


### <a name="step-3-create-a-send-port"></a>步驟 3︰ 建立傳送埠

BizTalk Server 將訊息傳送至邏輯應用程式中，邏輯應用程式必須有 **手動** 觸發，例如 **Manual-時的 HTTP 要求收到**。 

1. 在 BizTalk Server 管理，依序展開 **BizTalk Server 管理**, ，依序展開 **BizTalk 群組**, ，依序展開 **應用程式**, ，然後展開您想要執行的傳送埠的應用程式。 例如，展開  **BizTalk Application 1**。
2. 右邊選取 **傳送埠**, ，請選取 **新增**, ，然後選取 **靜態單向傳送埠**。
3. 輸入 **名稱** 傳送埠。 例如，輸入 **LASendPort**。
4. 如 **類型**, ，請選取 **LogicApp** 從清單中，然後選取 **設定**  按鈕。 
5. 在 **一般** 索引標籤上，設定 **回呼 URI** 的邏輯應用程式觸發程序。 有兩種方式可以執行此動作： 

    **選項 1** ︰ 貼上您在上一個步驟中複製的 HTTP POST URL **觸發程序 (回呼 URI)** 屬性。 您也可以複製 URI 使用下列步驟︰  
  
      1. 在 [Azure 入口網站](https://portal.azure.com), ，在邏輯應用程式設計工具 （編輯模式） 中開啟邏輯應用程式。 
      2. 選取 **收到時的 HTTP 要求** 介面卡，並複製 **URL**。 
      3. 在傳送埠中，貼上此 URL **觸發程序 (回呼 URI)** 屬性。

    > [!TIP] 
    > 您也可以使用管理 Api 來取得這個 URI。

    **選項 2** ︰ 如果您不知道回呼 URI 到觸發程序，選取 **設定**, ，並登入 Azure。 然後，使用下拉式清單選取您 **訂閱**, ，**資源群組**, ，**邏輯應用程式**, ，和 **觸發程序**。
 
6. **選擇性**。 在 **繫結** 索引標籤上，設定任何逾時和編碼相關基礎 Wcf-webhttp 繫結的屬性。 處理大型訊息時，這些屬性是很有幫助。

    | 使用 | 動作 |
    | --- | --- |
    | 開啟逾時 | 輸入應該才會完成通道開啟作業的時間間隔。 這個值應該大於或等於 System.TimeSpan.Zero。 <br/><br/>預設值：00:01:00<br/>最大值︰ 23:59:59 |
    | 傳送逾時 |輸入應該針對完成傳送作業的時間間隔。 這個值應該大於或等於 System.TimeSpan.Zero。 如果您使用要求-回應接收埠，這個值會指定，才能完成整個互動的時間長度，即使在用戶端傳回很大的訊息。 <br/><br/>預設值：00:01:00<br/>最大值︰ 23:59:59|
    | 關閉逾時 | 輸入所需的通道關閉作業完成的時間間隔。 這個值應該大於或等於 System.TimeSpan.Zero。 <br/><br/>預設值：00:01:00<br/>最大值︰ 23:59:59 |
    | 接收訊息大小上限 (以位元組為單位) | 輸入的最大的大小，以位元組為單位，包括標頭，在網路上接收訊息。 訊息大小受限於配置給各訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。 <br/><br/>邏輯 appa 配接器會利用 [WebHttpBinding 類別](https://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.aspx) 處於緩衝的傳輸模式，才能與端點進行通訊。 緩衝的傳輸模式下， [WebHttpBinding.MaxBufferSize](https://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.maxbuffersize.aspx) 屬性會一律等於這個屬性的值。  <br/><br/>預設值：65536<br/>最大值：2147483647 |


7. **選擇性**。 在 **訊息** 索引標籤上，使用 **傳出的 HTTP 標頭** 屬性來加入傳出訊息上的任何自訂標頭。 
8. 選取 **確定** 來儲存組態。 

[管理傳送埠與傳送埠群組](../core/managing-send-ports-and-send-port-groups.md)描述的其他傳送埠屬性。 

### <a name="step-4-send-some-messages"></a>步驟 4︰ 傳送一些訊息

您可以建立接收埠和接收位置使用 File 配接器。 請務必在邏輯應用程式已啟用。

1. 建立接收埠，例如 *FileSendPort*,，
2. 建立接收位置，並設定屬性類似於︰  

    | 屬性 | 範例輸入 |
    | --- | --- |
   | 接收資料夾 | C:\temp\In\ |
   | 檔案遮罩 | *.txt |
   | 管線 | PassThruReceive |

3. 在您所建立的傳送埠，設定 **篩選** 至︰

    | 屬性 | 運算子 | Value |
    | --- | --- | --- |
    | BTS.ReceivePortName |  == | *FileSendPort* |

4. 建立包含下列文字的文字檔案 (FileName.txt)。 使用這個文字檔做為範例訊息︰ 

    ```
    <Data>
      <DataID>DataID_0</DataID>
      <DataDetails>DataDetails_0</DataDetails>
    </Data>
    ```

5. 將您的範例訊息 (FileName.txt) 複製到接收資料夾。 傳送埠會將邏輯應用程式使用您所輸入的 URI 中的.txt 檔案。 在邏輯應用程式接收檔案。 如果您使用 Office 365 的 Outlook 連接器，您 *至* 電子郵件地址應該會收到電子郵件的範例訊息。

## <a name="next"></a>下一個
[什麼是邏輯應用程式](https://azure.microsoft.com/documentation/articles/app-service-logic-what-are-logic-apps/)  

[建立邏輯應用程式](https://azure.microsoft.com/documentation/articles/app-service-logic-create-a-logic-app/)

[BizTalk Server 中使用配接器](../core/using-adapters.md)