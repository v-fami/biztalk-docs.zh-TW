---
title: "在 BizTalk Server 中的使用邏輯應用程式配接器 |Microsoft 文件"
description: "安裝和設定邏輯應用程式配接器來建立接收埠、 接收位置，在 BizTalk Server 傳送埠"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72f2a5ac-a1f6-4bdb-8c29-8267ede75b17
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faa43c187df7a8eb9fccd2f02f23f16e86b97ce0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="logic-app-adapter"></a>邏輯應用程式配接器

## <a name="overview"></a>概觀
BizTalk Server 會使用邏輯應用程式配接器接收訊息，從 Azure 邏輯應用程式，或將訊息傳送至 Azure 邏輯應用程式。 

在 Azure 中，我們會建立邏輯應用程式。 此邏輯應用程式會使用 BizTalk 連接器連接至您在 BizTalk Server 建立的接收位置。 本主題假設您已熟悉 Azure 邏輯應用程式。 如果您還不熟悉的 logic apps，我們建議[深入了解它們](https://azure.microsoft.com/documentation/articles/app-service-logic-what-are-logic-apps/)，，甚至[建立您自己的邏輯應用程式](https://azure.microsoft.com/documentation/articles/app-service-logic-create-a-logic-app/)。

本主題中，我們會列出 BizTalk Server 中的訊息接收邏輯應用程式的步驟。 換句話說，邏輯應用程式將訊息傳送至 BizTalk Server。 接收端會在 IIS 中使用應用程式，來處理與 Azure 服務的通訊。 如果 BizTalk Server 在內部部署，您也安裝資料閘道器在 BizTalk 伺服器上，並在 Azure 中建立的閘道。 

如果 BizTalk 伺服器安裝在 Azure 虛擬機器 (VM)，則您可以選擇將 VM 公開為 HTTP 端點 （您會取得 URL），或不要將它公開為 HTTP 端點。 如果您將它公開時，您不需要使用閘道。 您可以在邏輯應用程式中，BizTalk 連接器中輸入您的 URL。 如果您不會讓 VM (URL)，您需要使用閘道。 此主題中列出這些步驟。

我們也示範如何從 BizTalk Server 傳送訊息至 Azure 邏輯應用程式。 邏輯應用程式將另一種方式，從 BizTalk Server 接收訊息。 您會發現本主題中，就相當簡單，傳送端。

您可以使用本主題來建立接收位置和傳送埠使用邏輯應用程式配接器。 您可以使用 LogicApp 中的配接器在內部部署 （加入您的網域） 的 BizTalk Server 中或將執行 BizTalk Server 的 Azure 虛擬機器。 

## <a name="requirements"></a>需求

- Azure 訂用帳戶來登入 Azure 入口網站，並建立邏輯應用程式。
- 選擇性。 若要傳送測試訊息加入至邏輯應用程式，安裝 HTTP 測試的工具，例如[Fiddler](http://www.telerik.com/fiddler)或[郵差](https://www.getpostman.com/)。 如果您使用另一種方法將訊息傳送至邏輯應用程式時，您不需要使用這些工具。 

## <a name="receive-messages-from-a-logic-app"></a>邏輯應用程式中接收訊息

有幾個步驟以便讓 BizTalk Server 邏輯應用程式中接收訊息。 此區段會列出這些步驟。 很可能在使用者介面中 Azure 的變更，因此某些步驟可能無法完全如下所列。 

#### <a name="prerequisites"></a>必要條件

- 如果在內部部署 BizTalk Server，安裝及設定[在內部部署資料閘道](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-install/)Logic apps。 然後，在 Azure 中，[建立資料閘道資源](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-connection/)連接到您的 BizTalk Server。
- 如果 BizTalk Server 上已安裝 Azure VM，且 VM 並未公開為 HTTP 端點，然後安裝並設定[在內部部署資料閘道](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-install/)Logic apps。 然後，在 Azure 中，[建立資料閘道資源](https://azure.microsoft.com/documentation/articles/app-service-logic-gateway-connection/)連接到您的 BizTalk Server。
- 如果 BizTalk Server 上已安裝 Azure VM，且 VM 會公開為 HTTP 端點，然後閘道已不需要或使用。 

### <a name="step-1-install-the-logic-app-adapter"></a>步驟 1： 安裝邏輯應用程式配接器

邏輯應用程式配接器是不同的下載，並不是隨附於 BizTalk Server 安裝。 

> [!IMPORTANT] 
> 若要下載 LogicAppAdapter.iso:
> 
> 1. 移至[Microsoft BizTalk Server Adapter for Logic Apps](https://www.microsoft.com/download/details.aspx?id=54287)，並儲存。 
> 2. 開啟 LogicAppAdapter.iso，並執行**LogicApp Adapter.msi**檔案來安裝。

1. 在 BizTalk 伺服器上，下載並安裝邏輯應用程式配接器。 

2. 雙選取**LogicApp Adapter.msi**安裝。 接受授權合約，以及**安裝**。
3. **完成**安裝、 d 重新啟動**BizTalkServerApplication**和**BizTalkServerIsolatedHost**主控件執行個體。

安裝之後，您有下列項目：

- LogicApp 配接器會新增至 BizTalk 管理。
- 傳送處理常式會建立，並使用 biztalkserverapplication 主控件。
- 接收處理常式為 WCF 服務時，會建立，並使用 biztalkserverisolatedhost 主控件。
- `C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter`資料夾已建立，且包含兩個服務： 管理和 ReceiveService。 

    **管理**BizTalk 連接器邏輯應用程式中用來連接至 BizTalk Server 使用的資料閘道。 此管理服務可讓 BizTalk Server 接收訊息，從 Azure 邏輯應用程式使用的資料閘道。 BizTalk 接收端只會用於此服務。 它不是由傳送端。

    **ReceiveService**輸入接收位置時，由 BizTalk 連接器，在邏輯應用程式。 **ReceiveService**負責從邏輯應用程式傳送訊息。 BizTalk 接收端只會用於此服務。 它不是由傳送端。


### <a name="step-2-create-the-iis-applications"></a>步驟 2： 建立 IIS 應用程式

IIS 應用程式使用的管理和 ReceiveService 服務。

您可以執行使用新的應用程式集區或現有的應用程式集區的 IIS 應用程式。 AppPool 的身分識別會需要執行 BizTalk 服務，例如 「 BizTalk 應用程式使用者 」 和 「 BizTalk 外掛式主控件使用者群組的帳戶相同群組的成員資格。  

> [!TIP] 
> 如果您建立新的應用程式集區，然後保留預設的.NET CLR 版本和受管理的管線。 請記住，選擇已與您的 BizTalk 服務帳戶相同的 BizTalk 群組的成員資格的身分識別 （進階設定）。 

#### <a name="create-the-management-iis-application"></a>建立管理 IIS 應用程式
此 IIS 應用程式的 URL 可由 BizTalk 連接器 （在您的邏輯應用程式） 來使用 BizTalk Server 上的資料閘道。

1. 開啟 Internet Information Services (IIS) 管理員。
2. 以滑鼠右鍵按一下**Default Web Site**，和**新增應用程式**。 在這個新的應用程式： 

    1. 輸入**別名**（名稱） 應用程式，例如**IISLogicApp**。 
    2. **選取**應用程式集區。
    3. 設定**實體路徑**至`C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter\Management`。 
    3. **測試設定**以確認應用程式集區身分識別通過驗證並授權測試。

3. 選取 [確定] 儲存您的變更。
4. 開啟網頁瀏覽器，並移至`http://localhost/YourApplicationAlias/schemas?api-version=2016-10-26`，例如`http://localhost/IISLogicApp/Schemas?api-version=2016-10-26`。 開啟/儲存提示一份結構描述顯示，或是您`schemas.json`。 實際的結果取決於您的 web 瀏覽器。 如果這兩種情況發生，則您的應用程式集區身分識別遺漏的 BizTalk 群組的成員資格。

#### <a name="create-the-biztalk-receiveservice-iis-application"></a>建立 BizTalk ReceiveService IIS 應用程式
此 IIS 應用程式的 URL 由 BizTalk 連接器 （在您的邏輯應用程式） 當您選擇接收位置。 

1. 開啟 Internet Information Services (IIS) 管理員。
2. 以滑鼠右鍵按一下**Default Web Site**，和**新增應用程式**。 在這個新的應用程式： 

    1. 輸入**別名**（名稱） 應用程式，例如**ReceiveWCFService**。 
    2. **選取**與舊版的 IIS 應用程式相同的應用程式集區。
    3. 設定**實體路徑**至`C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter\ReceiveService`。 
    3. **測試設定**以確認應用程式集區身分識別通過驗證並授權測試。

3. 選取 [確定] 儲存您的變更。


### <a name="step-3-create-a-logic-app"></a>步驟 3： 建立邏輯應用程式

1. 在[Azure 入口網站](https://portal.azure.com)，建立新的邏輯應用程式。
2. 新增**收到時的 HTTP 要求**觸發程序。
3. 新增**BizTalk Server-準備從 JSON 訊息**動作。 
4. **選擇性**： 選取**透過在內部部署資料閘道的連線**，並輸入下列命令： 

    | 屬性 | Description |
   | --- | --- |
    | BizTalk Server URL | BizTalk 管理中 IIS 應用程式 URL，請輸入完整的網域名稱 (FQDN)。 例如，輸入`http://BizTalkServerName.corp.contoso.com/IISLogicApp/`。 |
    | 驗證類型 | 選取**Windows**。 |
   | 使用者名稱 | 輸入 IIS 應用程式集區身分的識別。 |
   | 密碼 | 輸入 IIS 應用程式集區的密碼。 |
   | 閘道 | 選取您建立的閘道。 |

    > [!TIP] 
    > 請記住，資料閘道，才需要的如果：
    > - 您使用內部部署 BizTalk Server
    > - 您使用 BizTalk Server 的 Azure 虛擬機器*和*VM 並未公開為 HTTP 端點 (URL)

5. 選取 [建立]。 
6. 設定的動作。 如**主體**，選取 HTTP 主體輸出。 如**結構描述**，選取您想要使用的結構描述。 

    > [!NOTE] 
    > 這個步驟假設您熟悉 biztalk 結構描述，並且知道您想要的結構描述。 如果您不確定，部署 HelloWorld SDK 範例的然後、 可更新其成品，以使用邏輯應用程式配接器，並使用其結構描述和範例的訊息。 

7. 加入新的步驟，並選取**BizTalk Server-傳送訊息**動作。 如**接收位置**、 從下拉式清單中，選取 URL，或輸入 ReceiveService IIS 應用程式 URL 的完整的網域名稱 (FQDN)。 例如，輸入`http://BizTalkServerName.corp.contoso.com/ReceiveWCFService/Service1.svc`。

    > [!TIP] 
    > 當您建立的接收位置時，將也做為接收位置傳輸屬性中輸入此 URL**公用位址**（一般索引標籤）。

    如**主體**，從上一個 BizTalk Server 動作選取主體輸出。 

8. **儲存**您的變更。 

當您儲存時，HTTP 要求的觸發程序會自動建立 URL。 複製這個 URL。您需要在**步驟 5： 將訊息傳送**。

### <a name="step-4-create-a-receive-port-and-a-receive-location"></a>步驟 4： 建立接收埠和接收位置

> [!NOTE] 
> 而不是建立您自己的接收埠和接收位置，您可以部署 HelloWorld SDK 範例。 更新要使用邏輯應用程式配接器的成品。 
 
本節列出的步驟來建立您自己的成品。 

1. 在 BizTalk Server 管理，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開您想要的應用程式執行接收位置。 例如，展開  **BizTalk Application 1**。
2. 右邊選取**接收埠**，選取**新增**，然後選取**單向接收埠**。
3. 在接收埠屬性中，輸入下列內容：  

    | 使用 | 動作 |
    | --- | --- |
    | **名稱** | 輸入接收埠的名稱。 例如，輸入**LAReceivePort**。 |
    | **驗證** | 選項： <br/><ul><li>無驗證： 預設值。 停用驗證。</li><li>驗證失敗時捨棄訊息： 啟用驗證，但若要卸除未驗證的訊息。</li><li>驗證失敗時保留訊息： 按一下此選項以啟用驗證並保留未驗證的訊息。 </li></ul>|
    | **啟用失敗訊息的路由** | 將路由至訂閱應用程式處理失敗的任何訊息 （例如其他接收埠或協調流程排程）。 取消選取此選項以擱置失敗的訊息，並產生負值通知 (NACK)。 預設值為清除核取方塊。 如需詳細資訊，請參閱[如何啟用接收埠的失敗訊息路由](../core/how-to-enable-routing-for-failed-messages-for-a-receive-port.md)。|

4. 選取**接收位置**，然後選取**新增**。 
5. 輸入**名稱**接收位置。 例如，輸入**LAReceiveLoc**。
6. 如**類型**，選取**LogicApp**從清單中，然後選取**設定 按鈕**。 
7. 在**一般**索引標籤上，設定您的邏輯應用程式的端點位址：

    | 使用 | 動作 |
    | --- | --- |
    | **位址 (URI)** | 必要。 輸入 BizTalk ReceiveService IIS 應用程式 URL (`/YourIISApp2Name/Service1.svc`)。 例如，輸入`/ReceiveWCFService/Service1.svc`。 |
    | **公用位址** | 必要。 輸入`http://<your fully qualified machine name>/YourIISApp2Name/Service1.svc`。 例如，輸入`http://btsProd.northamerica.corp.contoso.com/ReceiveWCFService/Service1.svc`。 <br/><br/>此 URL 也會列在接收位置中應用程式邏輯中。|

8. **選擇性**。 在**繫結**索引標籤上，設定任何逾時和編碼相關屬性的基礎 Wcf-webhttp 繫結。 處理大型訊息時，這些屬性就很有幫助。

    | 使用 | 動作 |
    | --- | --- |
    | 開啟逾時 | 輸入會針對要完成通道開啟作業所花費的時間間隔。 這個值應該大於或等於 System.TimeSpan.Zero。 <br/><br/>預設值：00:01:00<br/>最大值： 23:59:59 |
    | 傳送逾時 |輸入應該讓傳送作業完成的時間間隔。 這個值應該大於或等於 System.TimeSpan.Zero。 如果您使用要求-回應接收埠，這個值會指定完成，整個互動的時間長度，即使在用戶端傳回很大的訊息。 <br/><br/>預設值：00:01:00<br/>最大值： 23:59:59|
    | 關閉逾時 | 輸入會針對要完成通道關閉作業所花費的時間間隔。 這個值應該大於或等於 System.TimeSpan.Zero。 <br/><br/>預設值：00:01:00<br/>最大值： 23:59:59 |
    | 接收訊息大小上限 (以位元組為單位) | 輸入的大小上限，以位元組為單位，包括標頭，在網路上接收訊息。 訊息大小受限於配置給各訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。 <br/><br/>預設值：65536<br/>最大值：2147483647|
    | 同時呼叫數目上限 | 輸入的單一服務執行個體的並行呼叫數。 超出上限的呼叫將排入佇列。 將此值設定為 0 相當於將它設定為 Int32.MaxValue。 <br/><br/>預設值是 200。|

9. **選擇性**。 在**安全性**索引標籤上，設定任何安全性內容。 供開發應用程式，您可以選擇一個：

    | 使用 | 以進行此動作 |
    | --- | --- |
    | 安全性模式 | 選項：  <br/><br/><ul><li>None： 不保護訊息傳輸期間。</li><li>傳輸： 使用安全性來提供 HTTPS 傳輸。 使用 HTTPS 來維護 SOAP 訊息的安全。 若要使用此模式中，您必須設定總 Secure Sockets Layer (SSL) 在 網際網路資訊服務 (IIS)。 </li><li>TransportCredentialOnly： 預設值。 </li></ul> |
    | 傳輸用戶端認證類型 | 使用用戶端驗證時，請選擇認證類型。 選項：  <br/><br/><ul><li>None： 無驗證傳輸層級發生。</li><li>Basic： 使用基本驗證透過網路以純文字傳送使用者名稱和密碼。 您必須建立對應到認證的網域或本機使用者帳戶。</li><li>若要透過網路傳送密碼雜湊值的摘要： 使用摘要式驗證。 只能在具有執行 Windows Server 作業系統驗證的網域控制站的網域。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。</li><li>Ntlm： 預設值。 用戶端傳送的認證，而不將密碼傳送至這個接收位置。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。</li><li>Windows: Windows 整合式的驗證會交涉 Kerberos 或 NTLM，如果網域存在，則偏好 Kerberos。 若要使用 Kerberos，請務必讓用戶端與服務主要名稱 (SPN) 識別服務。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。</li><li>憑證： 使用用戶端憑證。 CA 憑證鏈結的用戶端 X.509 憑證必須安裝在這部電腦的受信任的根憑證授權單位憑證存放區，讓用戶端可以驗證這個接收位置。</li><li>InheritedFromHost</li></ul> |
    | 使用單一登入 | |


10. **選擇性**。 在**訊息**索引標籤上，使用**連出 HTTP 標頭**屬性設為加入任何自訂標頭，並使用額外的屬性協助的錯誤： 

    | 使用 | 以進行此動作 |
    | --- | --- |
    |輸出 HTTP 標頭 | 輸入任何您想要在回應訊息上加上戳記的 HTTP 標頭。 | 
    | 失敗時停用位置 | 輸入的處理失敗，因為接收管線失敗或路由失敗時，會停用接收位置。 預設為未選取狀態。|
    | 失敗時擱置的要求訊息 | 輸入的處理失敗，因為接收管線失敗或路由失敗時，暫止的要求訊息。 預設為未選取狀態。|
    | 錯誤中包含例外狀況詳細資料 | 發生錯誤時，會傳回任何的 SOAP 錯誤，以協助偵錯。 預設為未選取狀態。|

[管理接收位置](../core/managing-receive-locations.md)描述其他屬性。 

### <a name="step-5-send-a-message"></a>步驟 5： 傳送訊息

1. 開啟 Fiddler 或郵差 （或您偏好的任何內容）。
2. 貼上要求觸發程序從邏輯應用程式的 URL。 您在步驟 3 中複製這個 URL。 
3. 選取**POST**作為 HTTP 動詞命令，並將**content-type**標頭`application/json`。 在本文中，貼上下列 JSON:  

    ```json
    {“hello”:”world”}
    ```

4. 因為這是 BizTalk 單向呼叫，則結果應該是 HTTP 202。 如果您使用 HelloWorld SDK 範例，請移至您的 BizTalk server。 傳送資料夾中可能是檔案。 


## <a name="send-messages-to-a-logic-app"></a>將訊息傳送至邏輯應用程式

### <a name="step-1-install-the-logic-apps-adapter"></a>步驟 1： 安裝 Logic Apps 配接器

邏輯應用程式配接器是不同的下載，並不是隨附於 BizTalk Server 安裝。

1. 移至[Microsoft BizTalk Server Adapter for Logic Apps](https://www.microsoft.com/download/details.aspx?id=54287)，並儲存。 
2. 開啟 LogicAppAdapter.iso，並執行**LogicApp Adapter.msi**檔案來安裝。
3. **完成**安裝和重新啟動**BizTalkServerApplication**和**BizTalkServerIsolatedHost**主控件執行個體。

安裝之後，您有下列項目：

- LogicApp 配接器新增至 BizTalk 管理
- 傳送處理常式會建立，並使用 biztalkserverapplication 主控件。
- 接收處理常式為 WCF 服務時，會建立，並使用 biztalkserverisolatedhost 主控件。
- `C:\Program Files (x86)\Microsoft BizTalk Server 2016\LogicApp Adapter`資料夾已建立，且包含兩個服務： 管理和 ReceiveService。 這些服務不會將訊息傳送至邏輯應用程式。 


### <a name="step-2-create-a-logic-app"></a>步驟 2： 建立邏輯應用程式

1. 在[Azure 入口網站](https://portal.azure.com)，建立新的邏輯應用程式。
2. 新增**收到時的 HTTP 要求**觸發程序
3. 新增**Office 365 Outlook 的電子郵件傳送**動作。 如**至**位址，請輸入您的 Office 365 地址。 如**主旨**，輸入`Sending from BizTalk`。 如**主體**，選擇*主體*從輸出**收到時的 HTTP 要求**觸發程序。 
4. 邏輯應用程式看起來類似： 

    ![LogicAppExample](../core/media/logicappexample.gif)

5. 複製儲存邏輯應用程式; 時，會自動建立的 HTTP POST URL您需要此 URL 中的下一個步驟。 您可能要關閉並重新開啟邏輯應用程式會看到的 URL。  


### <a name="step-3-create-a-send-port"></a>步驟 3： 建立傳送埠

BizTalk Server 將訊息傳送至邏輯應用程式中，邏輯應用程式必須有**手動**觸發程序，例如**Manual-時的 HTTP 要求收到**。 

1. 在 BizTalk Server 管理，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開您想要的應用程式執行傳送埠。 例如，展開  **BizTalk Application 1**。
2. 右邊選取**傳送埠**，選取**新增**，然後選取**靜態單向傳送埠**。
3. 輸入**名稱**傳送埠。 例如，輸入**LASendPort**。
4. 如**類型**，選取**LogicApp**從清單中，然後選取**設定** 按鈕。 
5. 在**一般**索引標籤上，設定**回呼 URI**的邏輯應用程式觸發程序。 有兩種方式可以執行此動作： 

    **選項 1** ： 貼上您在上一個步驟中複製的 HTTP POST URL**觸發程序 (回呼 URI)**屬性。 您也可以複製的 URI 使用下列步驟：  
  
      1. 在[Azure 入口網站](https://portal.azure.com)，應用程式邏輯在設計師中開啟邏輯應用程式 （編輯模式）。 
      2. 選取**收到時的 HTTP 要求**介面卡，並將複製**URL**。 
      3. 在傳送埠中，貼上此 URL 中的**觸發程序 (回呼 URI)**屬性。

    > [!TIP] 
    > 您也可以使用您的管理應用程式開發介面，以取得此 URI。

    **選項 2** ： 如果您不知道回呼 URI 的觸發程序，選取**設定**，和登入 Azure。 然後，使用下拉式清單選擇您**訂用帳戶**，**資源群組**，**邏輯應用程式**，和**觸發程序**。
 
6. **選擇性**。 在**繫結**索引標籤上，設定任何逾時和編碼相關屬性的基礎 Wcf-webhttp 繫結。 處理大型訊息時，這些屬性就很有幫助。

    | 使用 | 動作 |
    | --- | --- |
    | 開啟逾時 | 輸入會針對要完成通道開啟作業所花費的時間間隔。 這個值應該大於或等於 System.TimeSpan.Zero。 <br/><br/>預設值：00:01:00<br/>最大值： 23:59:59 |
    | 傳送逾時 |輸入應該讓傳送作業完成的時間間隔。 這個值應該大於或等於 System.TimeSpan.Zero。 如果您使用要求-回應接收埠，這個值會指定完成，整個互動的時間長度，即使在用戶端傳回很大的訊息。 <br/><br/>預設值：00:01:00<br/>最大值： 23:59:59|
    | 關閉逾時 | 輸入會針對要完成通道關閉作業所花費的時間間隔。 這個值應該大於或等於 System.TimeSpan.Zero。 <br/><br/>預設值：00:01:00<br/>最大值： 23:59:59 |
    | 接收訊息大小上限 (以位元組為單位) | 輸入的大小上限，以位元組為單位，包括標頭，在網路上接收訊息。 訊息大小受限於配置給各訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。 <br/><br/>邏輯 appa 配接器會利用[WebHttpBinding 類別](https://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.aspx)在緩衝的傳輸模式中與端點進行通訊。 緩衝的傳輸模式下， [WebHttpBinding.MaxBufferSize](https://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.maxbuffersize.aspx)屬性會一律等於這個屬性的值。  <br/><br/>預設值：65536<br/>最大值：2147483647 |


7. **選擇性**。 在**訊息**索引標籤上，使用**連出 HTTP 標頭**將外寄訊息上的任何自訂標頭的屬性。 
8. 選取**確定**來儲存您的設定。 

[管理傳送埠與傳送埠群組](../core/managing-send-ports-and-send-port-groups.md)描述的其他傳送埠屬性。 

### <a name="step-4-send-some-messages"></a>步驟 4： 傳送一些訊息

您可以建立接收埠和接收位置使用 File 配接器。 請務必啟用應用程式邏輯。

1. 建立接收埠，例如*FileSendPort*，
2. 建立接收位置，並設定內容類似：  

    | 屬性 | 輸入範例 |
    | --- | --- |
   | 接收資料夾 | C:\temp\In\ |
   | 檔案遮罩 | *.txt |
   | 管線 | PassThruReceive |

3. 您所建立的傳送埠，在設定**篩選**至：

    | 屬性 | 運算子 | 值 |
    | --- | --- | --- |
    | BTS.ReceivePortName |  == | *FileSendPort* |

4. 建立包含下列文字的文字檔案 (FileName.txt)。 使用此文字檔案做為範例訊息： 

    ```
    <Data>
      <DataID>DataID_0</DataID>
      <DataDetails>DataDetails_0</DataDetails>
    </Data>
    ```

5. 將您的範例訊息 (FileName.txt) 複製到接收資料夾。 傳送埠傳送.txt 檔案的邏輯應用程式使用您輸入的 URI。 邏輯應用程式接收檔案。 如果您使用 Office 365 Outlook 連接器後，您*至*電子郵件地址應該會收到電子郵件的範例訊息。

## <a name="next"></a>下一個
[邏輯應用程式有哪些？](https://azure.microsoft.com/documentation/articles/app-service-logic-what-are-logic-apps/)  

[建立邏輯應用程式](https://azure.microsoft.com/documentation/articles/app-service-logic-create-a-logic-app/)

[BizTalk Server 中使用配接器](../core/using-adapters.md)