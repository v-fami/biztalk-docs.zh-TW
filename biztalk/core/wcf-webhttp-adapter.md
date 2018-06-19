---
title: Wcf-webhttp 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a353e7-1ba3-427a-8e99-c9b8d83061cb
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 891f636a5380eda7db676559194618915213dc37
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "25976068"
---
# <a name="wcf-webhttp-adapter"></a>WCF-WebHttp 配接器
[!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用**Wcf-webhttp**配接器將訊息傳送至 RESTful 服務。 **Wcf-webhttp** 傳送配接器傳送至服務的 HTTP 訊息的 BizTalk 訊息。 接收位置接收訊息從一種 RESTful 服務。 GET 和 DELETE 要求，配接器所使用的任何內容。 POST 和 PUT 要求，配接器會使用 HTTP 內容/裝載 BizTalk 訊息內文部分。  

本主題說明如何建立接收位置和傳送埠使用 BizTalk 管理。

## <a name="create-a-receive-location"></a>建立接收位置
  
> [!NOTE]
>  之前完成下列程序，您必須已經新增單向接收埠。 請參閱 [如何建立接收埠](../core/how-to-create-a-receive-port.md)。  
  
1.  在 BizTalk Server 管理主控台中，依序展開 [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 **[BizTalk 群組]**、 **[應用程式]**，以及您要在其下建立接收位置的應用程式。  
  
2.  在左窗格中按一下 **[接收埠]** 節點，在右窗格中以滑鼠右鍵按一下您想與新接收位置建立關聯的接收埠，然後按一下 **[屬性]**。  
  
3.  在左窗格中 **接收埠屬性** 對話方塊中，選取 **接收位置**, ，並在右窗格中按一下 **新增** 來建立新的接收位置。  
  
4.  在 [接收位置屬性]  對話方塊的 [傳輸]  區段中，從 [類型]  下拉式清單選取 [WCF-WebHttp]  ，然後按一下 [設定]  ，以設定接收位置的傳輸屬性。  
  
5.  在 **一般** 索引標籤上，設定 REST 介面，從位置接收訊息的端點位址。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**位址 (URI)**|必要。 指定的 URI 上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以接收 HTTP 型 RESTful 訊息。|  
    |**端點身分識別**|選擇性。 指定端點識別。 這些設定可讓端點驗證此接收位置。 在端點與接收位置之間的交握程序中，Windows Communication Foundation (WCF) 基礎結構可確保預期之服務的識別與此元素的值相符。<br /><br /> 預設為空字串。|  
    |**HTTP 方法和 URL 對應**|BTS 作業對應可讓使用者根據傳入的 HTTP 方法和 URL 子路徑，將傳入的 HTTP 要求對應到訊息內容中的 BTS 作業。 傳入的 HTTP 方法和 URL 子路徑會針對一組 HTTP 方法和 URI 範本進行比對。 如果找到相符項目，配接器會以訊息中指定的值，將 **BTS.Operation** 屬性提升至 BizTalk 訊息內容。<br /><br /> 您可以將 HTTP 方法對 URL 的對應指定為單數格式或多對應格式。 多對應格式看起來如下：<br /><br /> `<BtsHttpUrlMapping> <Operation Name = "DelCust" Method="DELETE" Url="/Customer/12345</BtsHttpUrlMapping>`<br /><br /> 在上述程式碼片段中，請注意客戶 ID 以常值 *12345*提供。 不過，可能會有些情況下，客戶 ID 或其他查詢變數必須在執行階段決定。 若要啟用這種情況，您必須在大括號 {} 內提供 URL 的變數元件。 例如在以上片段中，如果您以變數指定客戶 ID，它應該像這樣：<br /><br /> `<BtsHttpUrlMapping> <Operation Name = "DelCust" Method="DELETE" Url="/Customer/{ID}</BtsHttpUrlMapping>`<br /><br /> 在這種情況下，您也必須指定變數 **ID** 的值在執行階段必須從何處取得。 指定的方法是使用 **變數對應**。<br /><br />**附註**<br /> 在 [URL] 欄位中，任何特殊的 XML 字元必須 「 逸出 」。 這可確保特殊 XML 字元的處理，並保留連接埠。 例如， `&` 必須逸出特殊字元，做為 `&amp;`。 <br /><br />From:<br />`Url=”/Customer?{ID}& group=Location”`<br />若要： <br />`Url=”/Customer?{ID}&amp;group=Location”`|  
    |**變數的對應**|如果您指定了 HTTP 方法 URL 對應的變數，您必須指定變數在執行階段對應到的目標。 按一下 [編輯]  按鈕即可啟動 [變數對應]  對話方塊。 在 [變數]  資料行下，對話方塊會列出您為 [HTTP 方法和 URL 對應] 定義的變數。 在 [屬性名稱]  欄位中，您必須指定提供值以和變數相關聯的屬性名稱。 您必須已經在解決方案中定義/提升此屬性。 您也必須在 [屬性命名空間]  欄位中提供屬性的命名空間。|  
  
6.  在 **繫結** 索引標籤上，設定逾時和編碼相關屬性。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**開啟逾時 (hh: mmss)**|指定時間值，表示可供完成通道開啟作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**傳送逾時 (hh: mmss)**|指定時間值，表示可供完成傳送作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。 如果您使用要求-回應接收埠，這個值會指定完成整個互動的時間長度，即使服務傳回很大的訊息也是如此。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**關閉逾時 (hh: mmss)**|指定時間值，表示可供完成通道關閉作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**接收的訊息大小上限 （位元組）**|以位元組為單位，指定可在網路上接收的訊息大小上限 (含標頭)。 訊息的大小受限於配置給每個訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。<br /><br /> WCF-WebHttp 配接器會在緩衝的傳輸模式下，利用 [WebHttpBinding](http://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.aspx) 類別與端點進行通訊。 在緩衝的傳輸模式下， [WebHttpBinding.MaxBufferSize](http://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.maxbuffersize.aspx) 屬性一律等於這個屬性的值。<br /><br /> 預設值：65536<br /><br /> 最大值：2147483647|  
    |**同時呼叫數目上限**|指定對單一服務執行個體的並行呼叫數目。 超出上限的呼叫將排入佇列。 將這個值設定為 0 的效果與設定為 **Int32.MaxValue**相同。<br /><br /> 預設值是 200。|  
  
7.  在 **安全性** 索引標籤上，定義的安全性功能的 Wcf-webhttp 接收位置。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**安全性模式**|指定使用的安全性類型。 有效值包括下列各項：<br /><br /> -                          **無**： 訊息傳輸期間並未受到保護。<br /><br /> - **傳輸**： 使用 HTTPS 傳輸安全性來提供。 使用 HTTPS 來維護 SOAP 訊息的安全。 若要使用這個模式，您必須在 Microsoft Internet Information Services (IIS) 中設定「安全通訊端層」(SSL)。<br /><br /> - **TransportWithMessageCredential**： 完整性、 機密性和服務驗證的 HTTPS 傳輸所提供。 若要使用這個模式，您必須在 Microsoft Internet Information Services (IIS) 中設定「安全通訊端層」(SSL)。<br /><br /> 預設值為 **[傳輸]**。|  
    |**傳輸用戶端認證類型**|指定在執行用戶端驗證時，所要使用的認證類型。 有效值包括下列各項：<br /><br /> - **無**： 無驗證傳輸層級發生。<br /><br /> - **基本**： 基本驗證。 在基本驗證中，會透過網路傳送純文字格式的使用者名稱和密碼。 您必須建立對應到認證的網域或本機使用者帳戶。<br /><br /> - **摘要**： 摘要式驗證。 此驗證方法的運作方式與基本驗證相當類似，例外的一點是密碼會透過網路傳送為雜湊值，以提供額外的安全性。 只有當網域具有執行 Windows Server 作業系統驗證的網域控制站時，才能使用摘要驗證。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。<br /><br /> -                          **Ntlm**: NTLM 驗證。 用戶端可以傳送認證，而不需要傳送密碼給這個接收位置。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。<br /><br /> -                          **Windows**: Windows 整合式的驗證。 Windows Communication Foundation 會交涉 Kerberos 或 NTLM (當有網域存在時，則偏好 Kerberos)。 如果您想要使用 Kerberos，請務必讓用戶端識別具有服務主要名稱 (SPN) 的服務。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。<br /><br /> - **憑證**： 使用用戶端憑證的用戶端驗證。 用戶端 X.509 憑證的 CA 憑證鏈結必須安裝在這部電腦的「信任的根憑證授權單位」憑證存放區中，才可以向這個接收位置驗證用戶端。<br /><br /> **請注意** **傳輸用戶端認證類型** 屬性必須符合驗證結構描述之 iis 虛擬目錄裝載此接收位置。 例如，如果您將此屬性設為 **[Windows]**，您也需要針對裝載它的虛擬目錄啟用 **[整合式 Windows 驗證]** 。 同樣地，如果您將此屬性設為 **[無]**，您必須允許針對裝載此接收位置的虛擬目錄進行匿名存取。<br /><br /> 預設值是 **[Windows]**。|  
    |**服務憑證-指紋**|針對此接收位置指定用戶端用來驗證服務之 X.509 憑證的憑證指紋。 您可以使用 **[瀏覽]** 按鈕瀏覽至 **「目前使用者」** 位置的 **My** 存放區，以選取憑證指紋。<br /><br /> **請注意** 您必須將服務憑證安裝到 **目前使用者** 裝載此接收位置的接收處理常式的使用者帳戶的位置。<br /><br /> 最小長度：00<br /><br /> 最大長度：40<br /><br /> 預設為空字串。|  

8. 在 **行為** 索引標籤上，指定不同的方式，在服務層級，以及端點層級。 這些行為會根據.NET Framework 類別。  
  
    | 使用|動作|  
    |--------------|----------------|  
    | ServiceBehavior | 擴充您的 WCF 服務，服務層級的功能。 您可以新增延伸模組，執行不同的動作，例如定義的安全性設定、 啟用偵錯、 實作節流，以及使用其他.NET 類別。  <br/><br/> 右邊選取 **ServiceBehavior**, ，和 **將延伸加入**。 此清單會顯示可用的.NET 類別。|
    | [Endpointbehavior] | 擴充功能在端點層級收到要求的方式。 您可以新增延伸模組，執行不同的動作，例如從瀏覽器型 ASP.NET AJAX 用戶端接收 HTTP 要求，指定時間間隔上交易，選擇同步或非同步地接收訊息，並使用其他.NET 類別。 <br/><br/> 右邊選取 **EndpointBehavior**, ，和 **將延伸加入**。 此清單會顯示可用的.NET 類別。|

    WCF 自訂接收位置，這是類似的行為組態。 請參閱**Wcf-custom 傳輸屬性對話方塊、 接收、 行為** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
    
9.  在 **訊息** 索引標籤上，指定資料選取範圍 soap **主體** 項目。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**傳出的 HTTP 標頭**|如果有的話，指定回應訊息上加了戳記的 HTTP 標頭。|  
    |**停用失敗的位置**|指定是否停用由於接收管線失敗或路由失敗造成輸入處理失敗的接收位置。<br /><br /> 預設值為清除此核取方塊。|  
    |**擱置失敗的要求訊息**|指定是否擱置因接收管線失敗或路由失敗而造成輸入處理失敗的要求訊息。<br /><br /> 預設值為清除核取方塊。|  
    |**錯誤中包含例外狀況詳細資料**|指定是否要將在錯誤發生時傳回 SOAP 錯誤以方便偵錯。<br /><br /> 預設值為清除核取方塊。|  
  
9. 按一下 **[確定]**。  
  
10. 在 **[接收位置屬性]** 對話方塊中輸入適當的值，以完成接收位置的組態，然後按一下 **[確定]** 儲存設定值。 如需有關資訊 **接收位置屬性** 對話方塊中，請參閱 [如何建立接收位置](../core/how-to-create-a-receive-location.md)。  

## <a name="create-the-send-port"></a>建立傳送埠

1.  在 [BizTalk 管理主控台] 中建立新的傳送埠，或按兩下現有的傳送埠進行修改。 請參閱 [如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 設定所有傳送埠選項，並指定 **Wcf-webhttp** 的 **類型** 選項 **傳輸** 區段 **一般**  索引標籤。  
  
2.  在 **一般** 索引標籤的 **傳輸** 區段中，按一下 **設定**  按鈕。  
  
3.  在 **一般** 索引標籤上，設定要在傳送訊息的 REST 介面的端點位址。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**位址 (URI)**|必要。 指定要在傳送訊息的 REST 介面的 URI。|  
    |**端點身分識別**|選擇性。 指定端點識別。 這些設定可讓端點驗證此傳送埠。 在端點與接收位置之間的交握程序中，Windows Communication Foundation (WCF) 基礎結構可確保預期之服務的識別與此元素的值相符。<br /><br /> 預設為空字串。|  
    |**HTTP 方法和 URL 對應**|BTS 作業對應可讓使用者根據傳入的 HTTP 方法和 URL 子路徑，將傳入的 HTTP 要求對應到訊息內容中的 BTS 作業。 傳入的 HTTP 方法和 URL 子路徑會針對一組 HTTP 方法和 URI 範本進行比對。 如果找到相符項目，配接器會以訊息中指定的值，將 **BTS.Operation** 屬性提升至 BizTalk 訊息內容。<br /><br /> 您可以將 HTTP 方法對 URL 的對應指定為單數格式或多對應格式。 多對應格式看起來如下：<br /><br /> `BtsHttpUrlMapping> <Operation Name = "DelCust" Method="DELETE" Url="/Customer/12345" /> </BtsHttpUrlMapping>`<br /><br /> 在上述程式碼片段中，請注意客戶 ID 以常值 *12345*提供。 不過，可能會有些情況下，客戶 ID 或其他查詢變數必須在執行階段決定。 若要啟用這種情況，您必須在大括號 {} 內提供 URL 的變數元件。 例如在以上片段中，如果您以變數指定客戶 ID，它應該像這樣：<br /><br /> `<BtsHttpUrlMapping> <Operation Name = "DelCust" Method="DELETE" Url="/Customer/{ID}" /> </BtsHttpUrlMapping>`<br /><br /> 在這種情況下，您也必須指定變數 **ID** 的值在執行階段必須從何處取得。 指定的方法是使用 **變數對應**。 <br /><br />**附註**<br /> 在 [URL] 欄位中，任何特殊的 XML 字元必須 「 逸出 」。 這可確保特殊 XML 字元的處理，並保留連接埠。 例如， `&` 必須逸出特殊字元，做為 `&amp;`。 <br /><br />From:<br />`Url=”/Customer?{ID}& group=Location”`<br />若要： <br />`Url=”/Customer?{ID}&amp;group=Location”`|  
    |**變數的對應**|如果您指定了 HTTP 方法 URL 對應的變數，您必須指定變數在執行階段對應到的目標。 按一下 [編輯]  按鈕即可啟動 [變數對應]  對話方塊。 在 [變數]  資料行下，對話方塊會列出您為 [HTTP 方法和 URL 對應] 定義的變數。 在 [屬性名稱]  欄位中，您必須指定提供值以和變數相關聯的屬性名稱。 您必須已經在解決方案中定義/提升此屬性。 您也必須在 [屬性命名空間]  欄位中提供屬性的命名空間。|  
  
4.  在 **繫結** 索引標籤上，設定逾時和編碼相關屬性。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**開啟逾時 (hh: mmss)**|指定時間值，表示可供完成通道開啟作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**傳送逾時 (hh: mmss)**|指定時間值，表示可供完成傳送作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。 如果您使用要求-回應接收埠，這個值會指定完成整個互動的時間長度，即使服務傳回很大的訊息也是如此。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**關閉逾時 (hh: mmss)**|指定時間值，表示可供完成通道關閉作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**接收的訊息大小上限 （位元組）**|以位元組為單位，指定可在網路上接收的訊息大小上限 (含標頭)。 訊息的大小受限於配置給每個訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。<br /><br /> WCF-WebHttp 配接器會在緩衝的傳輸模式下，利用 [WebHttpBinding](http://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.aspx) 類別與端點進行通訊。 在緩衝的傳輸模式下， [WebHttpBinding.MaxBufferSize](http://msdn.microsoft.com/library/system.servicemodel.webhttpbinding.maxbuffersize.aspx) 屬性一律等於這個屬性的值。<br /><br /> 預設值：65536<br /><br /> 最大值：2147483647|  
  
5.  在 **安全性** 索引標籤上，定義 Wcf-webhttp 傳送埠的安全性功能。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**安全性模式**|指定使用的安全性類型。 有效值包括下列各項：<br /><br /> -   **無**： 訊息傳輸期間並未受到保護。<br />-   **傳輸**︰ 使用 HTTPS 傳輸來提供安全性。 使用 HTTPS 來維護 SOAP 訊息的安全。 此服務之 X.509 憑證的 CA 憑證鏈結必須安裝在這部電腦的「信任的根憑證授權單位」憑證存放區中，才可以使用此服務的憑證向傳送埠驗證此服務。<br />-   **TransportWithMessageCredential**: HTTPS 傳輸提供完整性、 機密性和驗證服務。 此服務之 X.509 憑證的 CA 憑證鏈結必須安裝在這部電腦的「信任的根憑證授權單位」憑證存放區中，才可以使用此服務的憑證向傳送埠驗證此服務。 傳送埠驗證是由 SOAP 訊息安全性所提供。<br /><br /> 預設值是 **無**。|  
    |**傳輸用戶端認證類型**|指定在執行用戶端驗證時，所要使用的認證類型。 有效值包括下列各項：<br /><br /> -   **無**： 無驗證傳輸層級發生。<br />-   **基本**︰ 基本驗證。 在基本驗證中，會透過網路傳送純文字格式的使用者名稱和密碼。 您必須建立對應到認證的網域或本機使用者帳戶。<br />-   **摘要**︰ 摘要式驗證。 此驗證方法的運作方式與基本驗證相當類似，例外的一點是密碼會透過網路傳送為雜湊值，以提供額外的安全性。 只有當網域具有執行 Windows Server 作業系統驗證的網域控制站時，才能使用摘要驗證。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。<br />-   **Ntlm**: NTLM 驗證。 用戶端可以傳送認證，而不需要傳送密碼給這個接收位置。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。<br />-   **Windows**: Windows 整合式的驗證。 Windows Communication Foundation 會交涉 Kerberos 或 NTLM (當有網域存在時，則偏好 Kerberos)。 如果您想要使用 Kerberos，請務必讓用戶端識別具有服務主要名稱 (SPN) 的服務。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。<br />-   **憑證**︰ 使用用戶端憑證的用戶端驗證。 用戶端 X.509 憑證的 CA 憑證鏈結必須安裝在這部電腦的「信任的根憑證授權單位」憑證存放區中，才可以向這個接收位置驗證用戶端。 **注意︰**   **傳輸用戶端認證類型** 屬性必須符合驗證結構描述之 iis 虛擬目錄裝載此接收位置。 例如，如果您將此屬性設為 **[Windows]**，您也需要針對裝載它的虛擬目錄啟用 **[整合式 Windows 驗證]** 。 同樣地，如果您將此屬性設為 **[無]**，您必須允許針對裝載此接收位置的虛擬目錄進行匿名存取。 <br /><br /> 預設值是 **[Windows]**。|  
    |**用戶端憑證-憑證指紋**|指定 X.509 憑證來驗證此傳送埠端點的憑證指紋。 您可以瀏覽至選取的憑證指紋 **我** 存放 **目前使用者** 位置 **瀏覽**  按鈕。 **注意︰**  您必須將用戶端憑證安裝到 **目前使用者** 裝載此傳送處理常式的使用者帳戶的位置的傳送埠。 <br /><br /> 最小長度：00<br /><br /> 最大長度：40<br /><br /> 預設為空字串。|  
    |**服務憑證-憑證指紋**|指定 X.509 憑證的指紋，用於驗證此傳送埠傳送訊息至其中的端點。 您可以選取 [瀏覽到憑證指紋 **其他人** 存放 **本機** 位置 **瀏覽** ] 按鈕。<br /><br /> 最小長度：00<br /><br /> 最大長度：40<br /><br /> 預設為空字串。|  
    |**使用者名稱認證**|指定用來傳送訊息的認證。 您可以指定的屬性，即可 **編輯**  按鈕。 您必須設定認證，如果您選取 **Username** 選項 **訊息用戶端認證類型**。<br /><br /> 預設值是 **不會使用單一登入**。|  
    |**使用 ACS 服務身分識別**|適用於[!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]和 BizTalk Server 2013。 <br /><br />選取此核取方塊，然後按一下 **編輯** ，並提供下列值來向服務匯流排。 這是必要的只有當叫用 REST 介面的服務匯流排相關實體。<br /><br /> -   **存取控制服務 STS Uri** – 將此設`https://<Namespace>-sb.accesscontrol.windows.net/`，其中\<命名空間\>是您的服務匯流排命名空間。<br />-   **簽發者名稱** – 指定簽發者名稱。 此值通常設定為擁有者。<br />-   **簽發者金鑰** – 指定簽發者金鑰。|  
    |**服務匯流排連線資訊** | 新開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]。<br/><br/>選擇要使用的共用存取簽章 (SAS) 或存取控制服務 (ACS) 的服務匯流排命名空間。 <br/><br/>選取一個選項，然後選取 **編輯** 輸入索引鍵的資訊︰<br/><br/> - **共用存取簽章**： 輸入存取索引鍵名稱和存取金鑰。 這兩個值會列在 [Azure 入口網站](https://portal.azure.com)。<br/> - **存取控制服務**： 輸入 STS URI (`https://<yourNamespace>-sb.accesscontrol.windows.net/`)，簽發者名稱和簽發者金鑰。 中所述，使用 Windows PowerShell 來擷取這些值， [SB Messaging 配接器](../core/sb-messaging-adapter.md)。 |
  
6.  在 **行為** 索引標籤上，設定此傳送埠的端點行為。 

    |使用|動作|  
    |--------------|----------------|  
    | [Endpointbehavior] | 擴充方式將要求傳送在端點層級的功能。 您可以加入擴充功能，例如執行不同的動作，定義 SOAP 處理行為、 交易、 控制探索功能，在指定時間間隔，以及使用其他.NET 類別。 <br/><br/>右邊選取 **EndpointBehavior**, ，和 **將延伸加入**。 此清單會顯示可用的.NET 類別。 |
    
    這是類似於 Wcf-custom 傳送埠的端點行為組態。 請參閱**Wcf-custom 傳輸屬性對話方塊、 傳送、 行為** 索引標籤[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
7.  在 **Proxy** 索引標籤上，設定的 proxy 設定 Wcf-webhttp 傳送埠。 
  
    |使用|動作|  
    |--------------|----------------|  
    |**使用 傳送處理常式的 proxy 設定**|指定此傳送埠是否要在裝載此傳送埠的傳送處理常式中，使用 Proxy 設定。<br /><br /> 這是預設值。|  
    |**不使用 proxy**|指出這個傳送埠是否要使用 Proxy 伺服器。<br /><br /> 預設值為清除核取方塊。|  
    |**使用 proxy**|指出此傳送埠是否使用指定的 proxy 伺服器 **位址** 屬性。<br /><br /> 預設值為清除核取方塊。|  
    |**地址**|指定 Proxy 伺服器的位址。 使用 **https** 或 **http** 根據安全性組態的配置。 這個位址後面可以加上冒號和連接埠編號， 例如 http://127.0.0.1:8080。<br /><br /> 這個屬性的值才需要 **使用 proxy** 已選取。<br /><br /> 類型：字串<br /><br /> 最大長度：256<br /><br /> 預設為空字串。|  
    |**使用者名稱**|指定要用於驗證的使用者名稱。 若使用整合式驗證，則使用者名稱會包括網域，即「網域\使用者名稱」。 如果使用基本或摘要式驗證，則使用者名稱不包含網域\\。 這個屬性的值才需要 **使用 proxy** 已選取。 **注意︰**  Wcf-webhttp 傳送配接器會使用 proxy 的基本驗證。 <br /><br /> 類型：字串<br /><br /> 최소 길이: 0<br /><br /> 最大長度：256<br /><br /> 預設為空字串。|  
    |**密碼**|指定要用於驗證的密碼。<br /><br /> 這個屬性的值才需要 **使用 proxy** 已選取。<br /><br /> 類型：字串<br /><br /> 최소 길이: 0<br /><br /> 最大長度：256<br /><br /> 預設為空字串。|  
  
8.  在 **訊息** 索引標籤上，指定訊息傳送至 REST 介面的方式。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**傳出的 HTTP 標頭**|如果有的話，指定回應訊息上加了戳記的 HTTP 標頭。|  
    |**隱藏本文指令動詞**|根據您要叫用 REST 端點所使用的動詞命令，或可能不一定需要訊息裝載。 例如，您可能使用 GET 或 DELETE 動詞命令時不需要訊息裝載。 不過，若要觸發呼叫 REST 端點使用的傳送埠，您可以使用空的訊息，其中包含訊息內容。 REST 端點傳送訊息之前，必須移除空的訊息從訊息裝載。 您可以指定的訊息內容必須先移除使用的動詞 **隱藏動詞命令的主體** 屬性。<br /><br /> 例如，如果您想要移除訊息裝載使用 GET 動詞命令時，指定為此屬性的值 `GET`。|  
  
9. 按一下  **確定** 和 **確定** 以儲存設定。  

## <a name="import-wcf-extensions"></a>匯入 WCF 擴充功能

匯入 WCF 擴充功能的接收處理常式或傳送處理常式中︰

1.  中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理、 展開[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理、 展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**.  

2.  選取 **Wcf-webhttp**, ，然後按兩下以選取接收或傳送處理常式。  

3. 在 [一般] 索引標籤中，選取 **屬性**。 

4. 在 **WCF 延伸模組**, ，請選取 **匯入**, ，並瀏覽至 WCF 延伸模組的組態檔。 

  
## <a name="add-a-proxy-to-the-send-handler"></a>將 proxy 加入至傳送處理常式

您可以將 proxy 加入至傳送埠或傳送處理常式。 如果您要新增 proxy 在傳送埠，請略過本節。

1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理、 展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**.  
  
2.  選取 **Wcf-webhttp**, ，然後選取 傳送處理常式。  
  
3.  在 **配接器處理常式屬性**, 上 **一般** 索引標籤上，選取 **屬性**。  
  
4.  在 **Proxy** 索引標籤上，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**使用 proxy**|指出此傳送處理常式是否要使用 proxy 伺服器。<br /><br /> 預設值為清除核取方塊。|  
    |**地址**|指定 Proxy 伺服器的位址。 使用 **https** 或 **http** 根據安全性組態的配置。 這個位址後面可以加上冒號和連接埠編號， 例如 http://127.0.0.1:8080。<br /><br /> 這個屬性的值才需要 **使用 proxy** 已選取。<br /><br /> 類型：字串<br /><br /> 最大長度：256<br /><br /> 預設為空字串。|  
    |**使用者名稱**|指定要用於驗證的使用者名稱。 若使用整合式或基本驗證，則使用者名稱也包括網域，即「網域\使用者名稱」。 如果使用摘要式驗證，則使用者名稱不包含網域\\。<br /><br /> 這個屬性的值才需要 **使用 proxy** 已選取。<br /><br /> 類型：字串<br /><br /> 최소 길이: 0<br /><br /> 最大長度：256<br /><br /> 預設為空字串。|  
    |**密碼**|指定要用於驗證的密碼。<br /><br /> 這個屬性的值才需要 **使用 proxy** 已選取。<br /><br /> 類型：字串<br /><br /> 최소 길이: 0<br /><br /> 最大長度：256<br /><br /> 預設為空字串。|  
  
5.  按一下  **確定** 直到結束所有對話方塊。  
   
## <a name="see-also"></a>另請參閱  
[SB Messaging 配接器](../core/sb-messaging-adapter.md)

[使用配接器](../core/using-adapters.md)

[何謂 WCF 配接器？](../core/what-are-the-wcf-adapters.md)
