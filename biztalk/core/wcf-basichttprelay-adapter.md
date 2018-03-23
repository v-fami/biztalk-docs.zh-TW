---
title: Wcf-basichttprelay 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 22eefde6-80f5-4d45-80cf-55f743ff9d45
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72a72129a9b0ee48969d528374c2a06497aa3311
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="wcf-basichttprelay-adapter"></a>WCF-BasicHttpRelay 配接器
[!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用**Wcf-basichttprelay**配接器來接收和傳送 WCF 服務要求，透過[BasicHttpRelayBinding 類別](https://msdn.microsoft.com/library/azure/microsoft.servicebus.basichttprelaybinding.aspx)。 **Wcf-basichttprelay**配接器會使用服務匯流排轉接端點使用**BasicHttpRelayBinding**。  

## <a name="before-you-begin"></a>開始之前

從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]，此配接器可以使用存取控制服務 (ACS) 或共用存取簽章 (SAS) athenticate 至服務匯流排。 我們建議使用服務匯流排進行驗證時使用共用存取簽章 (SAS)。 

當您建立服務匯流排命名空間時，不會自動建立存取控制 (ACS) 命名空間。 如果您使用 ACS 驗證，您可能需要建立新的 ACS 命名空間。 請參閱[SB Messaging 配接器](../core/sb-messaging-adapter.md)如需詳細資訊，包括擷取 ACS 索引鍵值的步驟。
  
## <a name="create-the-receive-location"></a>建立接收位置
  
> [!NOTE]
>  之前完成下列程序，您必須已經新增單向接收埠。 請參閱 [如何建立接收埠](../core/how-to-create-a-receive-port.md)。  
  
1.  在 BizTalk Server 管理主控台中，依序展開 [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 **[BizTalk 群組]**、 **[應用程式]**，以及您要在其下建立接收位置的應用程式。  
  
2.  在左窗格中按一下 **[接收埠]** 節點，在右窗格中以滑鼠右鍵按一下您想與新接收位置建立關聯的接收埠，然後按一下 **[屬性]**。  
  
3.  在左窗格中 **接收埠屬性** 對話方塊中，選取 **接收位置**, ，並在右窗格中按一下 **新增** 來建立新的接收位置。  
  
4.  在**接收位置屬性**對話方塊中，於**傳輸**區段中，選取**Wcf-basichttprelay**從**類型**下拉式清單，然後按一下**設定**設定接收位置的傳輸屬性。  
  
5.  在**Wcf-basichttprelay 傳輸屬性**對話方塊**一般**索引標籤上，設定裝載服務匯流排轉接端點的端點位址和服務識別Wcf-basichttprelay 接收位置。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**位址 (URI)**|必要。 指定已部署服務匯流排轉接端點的 URI。|  
    |**端點身分識別**|選擇性。 指定端點識別。 這些設定可讓端點驗證此接收位置。 在端點與接收位置之間的交握程序中，Windows Communication Foundation (WCF) 基礎結構可確保預期之服務的識別與此元素的值相符。<br /><br /> 預設為空字串。|  
  
6.  在**Wcf-basichttprelay 傳輸屬性**對話方塊**繫結**索引標籤上，設定逾時和編碼相關屬性。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**開啟逾時 (hh: mmss)**|指定時間值，表示可供完成通道開啟作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**傳送逾時 (hh: mmss)**|指定時間值，表示可供完成傳送作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。 如果您使用要求-回應接收埠，這個值會指定完成整個互動的時間長度，即使服務傳回很大的訊息也是如此。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**關閉逾時 (hh: mmss)**|指定時間值，表示可供完成通道關閉作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**接收的訊息大小上限 （位元組）**|以位元組為單位，指定可在網路上接收的訊息大小上限 (含標頭)。 訊息的大小受限於配置給每個訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。<br /><br /> Wcf-basichttprelay 配接器會利用[BasicHttpRelayBinding](http://msdn.microsoft.com/library/windowsazure/microsoft.servicebus.basichttprelaybinding.aspx)類別與端點進行通訊的緩衝的傳輸模式中。 緩衝的傳輸模式下， [BasicHttpRelayBinding.MaxBufferSize](http://msdn.microsoft.com/library/windowsazure/microsoft.servicebus.basichttprelaybinding.maxbuffersize.aspx)屬性會一律等於這個屬性的值。<br /><br /> 預設值：65536<br /><br /> 最大值：2147483647|  
    |**訊息編碼**|指定用來為 SOAP 訊息編碼的編碼器。 有效值包括下列各項：<br /><br /> -   **文字**： 使用文字訊息編碼器。<br />-   **Mtom**︰ 使用訊息傳輸 Organization Mechanism 1.0 (MTOM) 編碼器。<br /><br /> 預設值是 **文字**。|  
    |**文字編碼**|指定字元集的編碼方式來繫結上發出訊息時 **訊息編碼** 屬性設定為 **文字**。 有效值包括下列各項：<br /><br /> -   **utf 16BE (unicodeFFFE)**: Unicode BigEndian 編碼方式。<br />-   **utf-16**: 16 位元編碼方式。<br />-   **utf-8**: 8 位元編碼方式<br /><br /> 預設值是 **utf-8**。|  
    |**同時呼叫數目上限**|指定對單一服務執行個體的並行呼叫數目。 超出上限的呼叫將排入佇列。 將這個值設定為 0 的效果與設定為 **Int32.MaxValue**相同。<br /><br /> 預設值是 200。|  
  
7.  在**Wcf-basichttprelay 傳輸屬性**對話方塊**安全性**索引標籤上，定義的安全性功能的 Wcf-basichttprelay 接收位置。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**安全性模式**|指定使用的安全性類型。 有效值包括下列各項：<br /><br /> -   **無**： 訊息傳輸期間並未受到保護。<br />-   **傳輸**︰ 使用 HTTPS 傳輸來提供安全性。 使用 HTTPS 來維護 SOAP 訊息的安全。 若要使用這個模式，您必須在 Microsoft Internet Information Services (IIS) 中設定「安全通訊端層」(SSL)。<br />-   **訊息**︰ 使用透過 HTTP 傳輸的 SOAP 訊息安全性來提供安全性。 根據預設，SOAP **Body** 會進行加密及簽署。 唯一有效 **訊息用戶端認證類型** 配接器是 WCF 基本 **憑證**。 這種模式需要使用 HTTP 傳輸。 使用此安全性模式時，服務憑證，這個接收位置必須可透過提供 **服務憑證-憑證指紋** 屬性。<br />-   **TransportWithMessageCredential**: HTTPS 傳輸提供完整性、 機密性和驗證服務。 若要使用這個模式，您必須在 Microsoft Internet Information Services (IIS) 中設定「安全通訊端層」(SSL)。<br /><br /> 預設值為 **[傳輸]**。|  
    |**訊息用戶端認證類型**|指定的訊息層級安全性選項，只有當您設定**安全性模式**上方以**訊息**或**TransportWithMessageCredential**。 有效值包括下列各項：<br /><br /> -   **使用者名稱**： 可讓這個接收位置要求來驗證用戶端使用**UserName**認證。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。<br />-   **憑證**︰ 用戶端驗證此接收位置使用用戶端憑證。 用戶端 X.509 憑證的 CA 憑證鏈結必須安裝在這部電腦的「信任的根憑證授權單位」憑證存放區中，才可以向這個接收位置驗證用戶端。<br /><br /> 預設值是 **UserName**。|  
    |**演算法套件**|指定訊息加密和金鑰包裝演算法，只有當您設定**安全性模式**模式上方**訊息**或**TransportWithMessageCredential**。 這不是適用於您設定**安全性模式**至**無**或**傳輸**。<br /><br /> 這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。 可能的值為：<br /><br /> -   **Basic128**： 使用 Aes128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br />-   **Basic128Rsa15**︰ 使用 aes128 代表訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br />-   **Basic128Sha256**︰ 使用 aes256 代表訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br />-   **Basic128Sha256Rsa15**︰ 使用 aes128 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br />-   **Basic192**︰ 使用 Aes192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br />-   **Basic192Rsa15**︰ 使用 aes192 代表訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br />-   **Basic192Sha256**︰ 使用 aes192 代表訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br />-   **Basic192Sha256Rsa15**︰ 使用 aes192 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br />-   **Basic256**︰ 使用 Aes256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br />-   **Basic256Rsa15**︰ 使用 aes256 代表訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br />-   **Basic256Sha256**︰ 使用 aes256 代表訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br />-   **Basic256Sha256Rsa15**︰ 使用 aes256 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br />-   **TripleDes**︰ 使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br />-   **TripleDesRsa15**︰ 使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br />-   **TripleDesSha256**︰ 使用 tripledes 代表訊息加密，Sha256 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br />-   **TripleDesSha256Rsa15**︰ 使用 tripledes 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> 預設值為 **[Basic256]**。|  
    |**服務憑證-指紋**|針對此接收位置指定用戶端用來驗證服務之 X.509 憑證的憑證指紋。 您可以使用 **[瀏覽]** 按鈕瀏覽至 **「目前使用者」** 位置的 **My** 存放區，以選取憑證指紋。 **注意：**您必須設定此屬性，只有當您設定**安全性模式**模式上方**訊息**或**TransportWithMessageCredential**。 這不是適用於您設定**安全性模式**至**無**或**傳輸**。 **注意︰**  您必須將服務憑證安裝到 **目前使用者** 裝載此接收位置的接收處理常式的使用者帳戶的位置。 <br /><br /> 最小長度：00<br /><br /> 最大長度：40<br /><br /> 預設為空字串。|  
    |**轉送用戶端驗證類型**|指定用於驗證接收訊息之服務匯流排轉接端點的選項。 有效值包括下列各項：<br /><br /> -   **無**： 都不需要驗證。<br />-   **RelayAccessToken**： 指定此選項可使用授權與服務匯流排轉接端點的安全性權杖。<br /><br /> 預設值為 **RelayAccessToken**。|  
    |**啟用服務探索**|選取此核取方塊，指定是否在服務登錄中發佈此服務的行為。<br /><br /> -   **顯示名稱**– 指定與服務發行至服務登錄的名稱。<br />-   **探索模式**– 設定服務登錄中發佈服務的探索模式。 如需探索模式的詳細資訊，請參閱[ http://msdn.microsoft.com/library/microsoft.servicebus.discoverytype.aspx ](http://msdn.microsoft.com/library/microsoft.servicebus.discoverytype.aspx)。|  
    |**存取控制服務**|適用於[!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]2013年。<br/><br/>如果將 **[轉接用戶端驗證類型]** 設定為 **[RelayAccessToke]**，請按一下 **[編輯]** 按鈕並指定下列詳細資料：<br /><br /> -   **存取控制服務 STS Uri** – 將此設`https://<Namespace>-sb.accesscontrol.windows.net/`，其中\<命名空間\>是您的服務匯流排命名空間。<br />-   **簽發者名稱** – 指定簽發者名稱。 此值通常設定為擁有者。<br />-   **簽發者金鑰** – 指定簽發者金鑰。|  
    |**服務匯流排連線資訊** | 新開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]。<br/><br/>選擇要使用的共用存取簽章 (SAS) 或存取控制服務 (ACS) 的服務匯流排命名空間。 <br/><br/>選取一個選項，然後選取 **編輯** 輸入索引鍵的資訊︰<br/><br/> - **共用存取簽章**： 輸入存取索引鍵名稱和存取金鑰。 這兩個值會列在 [Azure 入口網站](https://portal.azure.com)。<br/> - **存取控制服務**： 輸入 STS URI (`https://<yourNamespace>-sb.accesscontrol.windows.net/`)，簽發者名稱和簽發者金鑰。 中所述，使用 Windows PowerShell 來擷取這些值， [SB Messaging 配接器](../core/sb-messaging-adapter.md)。 |
  
8.  在**Wcf-basichttprelay 傳輸屬性**對話方塊**訊息**索引標籤上，指定 SOAP 資料選取範圍**主體**項目。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**信封--整個\<p: Envelope>\>**|從內送訊息的整個 SOAP **信封** 建立 BizTalk 訊息內文部分。<br /><br /> 預設值為清除核取方塊。|  
    |**內文--內容\<soap: Body\>項目**|使用內送訊息的 SOAP **Body** 元素內容來建立 BizTalk 訊息內文部分。 如果 **Body** 元素有一個以上的子元素，則只有第一個元素會成為 BizTalk 訊息內文部分。<br /><br /> 這是預設值。|  
    |**路徑--內容由內文路徑定位**|使用 **[內文路徑運算式]** 文字方塊中的內文路徑運算式，建立 BizTalk 訊息內文部分。 內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子元素來進行評估。<br /><br /> 預設值為清除核取方塊。|  
    |**內文路徑運算式**|輸入內文路徑運算式，以識別用來建立 BizTalk 訊息內文部分的內送訊息特定部分。 這個內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子項目來進行評估。 如果此內文路徑運算式傳回一個以上的節點，則只會為 BizTalk 訊息內文部分選擇第一個節點。 如果選取了 **[路徑 -- 內容由內文路徑定位]** 選項，就需要此屬性。<br /><br /> 類型：字串<br /><br /> 最小長度：00<br /><br /> 最大長度：32767<br /><br /> 預設為空字串。|  
    |**節點編碼**|指定的編碼 Wcf-basichttprelay 接收配接器，用來解碼的內文路徑運算式所識別的節點類型**內文路徑運算式**文字方塊。<br /><br /> 如果選取了 **[路徑 -- 內容由內文路徑定位]** 選項，就需要此屬性。 有效值包括下列各項：<br /><br /> -   **Base64**: Base64 編碼方式。<br />-   **Hex**︰ 十六進位編碼方式。<br />-   **字串**︰ 文字編碼-utf-8<br />-   **XML**: WCF 配接器建立 BizTalk 訊息內文中的內文路徑運算式所選取之節點外部 xml **內文路徑運算式** 文字方塊。<br /><br /> 預設值是 **[XML]**。|  
    |**內文--BizTalk 回應訊息內文**|使用 BizTalk 訊息內文部分建立外寄回應訊息的 SOAP **內文** 元素內容。 此屬性只適用於要求-回應接收位置。<br /><br /> 這是預設值。|  
    |**範本--由範本指定的內容**|使用 [XML]  文字方塊中提供的範本來建立外寄訊息的 SOAP **內文** 元素內容。 此屬性只適用於要求-回應接收位置。<br /><br /> 預設值為清除核取方塊。|  
    |**XML**|針對外寄訊息的 SOAP **內文** 元素內容，輸入 XML 格式的範本。 如果選取了 **[範本 -- BizTalk 回應訊息本文]** 選項，就需要此屬性。 此屬性只適用於要求-回應接收位置。<br /><br /> 類型：字串<br /><br /> 最小長度：00<br /><br /> 最大長度：32767<br /><br /> 預設值是 **\<bts 訊息主體 xmlns ="http://www.microsoft.com/schemas/bts2007"編碼方式 ="xml"\>**。|  
    |**擱置失敗的要求訊息**|指定是否擱置因接收管線失敗或路由失敗而造成輸入處理失敗的要求訊息。<br /><br /> 預設值為清除核取方塊。|  
    |**錯誤中包含例外狀況詳細資料**|指定是否要將在錯誤發生時傳回 SOAP 錯誤以方便偵錯。<br /><br /> 預設值為清除核取方塊。|  
  
9. 按一下 **[確定]**。  
  
10. 在 **[接收位置屬性]** 對話方塊中輸入適當的值，以完成接收位置的組態，然後按一下 **[確定]** 儲存設定值。 如需有關資訊 **接收位置屬性** 對話方塊中，請參閱 [如何建立接收位置](../core/how-to-create-a-receive-location.md)。  

## <a name="create-the-send-port"></a>建立傳送埠

1.  在 [BizTalk 管理主控台] 中建立新的傳送埠，或按兩下現有的傳送埠進行修改。 請參閱 [如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 設定所有傳送埠選項，並指定**Wcf-basichttprelay**如**類型**選項**傳輸**區段**一般** 索引標籤。  
  
2.  在 **一般** 索引標籤的 **傳輸** 區段中，按一下 **設定**  按鈕。  
  
3.  在**Wcf-basichttprelay 傳輸屬性**對話方塊**一般**索引標籤上，指定下列項目：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**位址 (URI)**|必要。 服務匯流排上指定部署的轉送端點所在的 URL。 URL 通常會使用下列格式：<br /><br /> `https://<namespace>.servicebus.windows.net/`|  
    |**端點身分識別**|選擇性。 指定端點識別。 這些設定可讓與端點驗證此傳送埠。 在結束點和傳送埠之間的交握程序，Windows Communication Foundation (WCF) 基礎結構可確保端點身分識別符合此項目的值。<br /><br /> 預設值為清除核取方塊。|  
    |**動作**|指定 **SOAPAction** 外寄訊息的 HTTP 標頭欄位。 這個屬性也可以透過訊息內容屬性設定 **WCF。動作** 管線或協調流程中。 您可以將這個值指定兩個不同的方式︰ 單一動作格式和動作對應格式。 如果您在設定此屬性的單一動作格式-例如， `http://contoso.com/Svc/Op1`- **SOAPAction**標頭外寄訊息一定會設定這個屬性中指定的值。<br /><br /> 如果您設定此屬性以動作對應格式傳出 **SOAPAction** 標頭由 **BTS。作業** 內容屬性。 例如，如果此屬性設定為下列 XML 格式和**BTS。作業**屬性設定為 Op1，WCF 傳送配接器會使用`http://contoso.com/Svc/Op1`針對外寄**SOAPAction**標頭。<br /><br /> `<BtsActionMapping> <Operation Name="Op1" Action="http://contoso.com/Svc/Op1" /> <Operation Name="Op2" Action="http://contoso.com/Svc/Op2" /> </BtsActionMapping>`<br /><br /> 協調流程執行個體如果外寄訊息是來自協調流程連接埠，以動態方式設定 **BTS。作業** 與連接埠的作業名稱的屬性。 如果外寄訊息會路由傳送，以內容為基礎的路由，您可以設定 **BTS。作業** 管線元件中的屬性。<br /><br /> 重要事項：<br /><br /> [!INCLUDE[sb](../includes/sb-md.md)] 要求 SOAP 動作，將訊息傳送至轉送端點時設定。<br /><br /> 최소 길이: 0<br /><br /> 最大長度：32767<br /><br /> 預設為空字串。|  
  
4.  在**Wcf-basichttprelay 傳輸屬性**對話方塊**繫結**索引標籤上，設定逾時和編碼屬性。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**開啟逾時 (hh: mmss)**|指定時間值，表示可供完成通道開啟作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**傳送逾時 (hh: mmss)**|指定時間值，表示可供完成傳送作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。 如果您使用請求-回應傳送埠，這個值會指定完成整個互動的時間長度，即使服務傳回很大的訊息也是如此。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**關閉逾時 (hh: mmss)**|指定時間值，表示可供完成通道關閉作業的時間間隔。 這個值應該大於或等於 **System.TimeSpan.Zero**。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**接收的訊息大小上限 （位元組）**|以位元組為單位，指定可在網路上接收的訊息大小上限 (含標頭)。 訊息的大小受限於配置給每個訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。<br /><br /> Wcf-basichttprelay 配接器會利用[BasicHttpBinding](http://go.microsoft.com/fwlink/?LinkId=81086)類別與端點進行通訊的緩衝的傳輸模式中。 緩衝的傳輸模式下， [BasicHttpBinding.MaxBufferSize](http://go.microsoft.com/fwlink/?LinkId=80659) 屬性會一律等於這個屬性的值。<br /><br /> 預設值：65536<br /><br /> 最大值：2147483647|  
    |**訊息編碼**|指定用來為 SOAP 訊息編碼的編碼器。 有效值包括下列各項：<br /><br /> -                         **文字**： 使用文字訊息編碼器。<br /><br /> -                         **Mtom**： 使用訊息傳輸 Organization Mechanism 1.0 (MTOM) 編碼器。<br /><br /> 預設值︰ **文字**|  
    |**文字編碼**|指定字元集的編碼方式來繫結上發出訊息時 **訊息編碼** 屬性設定為 **文字**。 有效值包括下列各項：<br /><br /> -                         **utf 16BE (unicodeFFFE)**: Unicode BigEndian 編碼方式。<br /><br /> -                         **utf-16**: 16 位元編碼方式。<br /><br /> -                         **utf-8**: 8 位元編碼<br /><br /> 預設值︰ **utf-8**|  
  
5.  在**Wcf-basichttprelay 傳輸屬性**對話方塊**安全性**索引標籤上，定義 Wcf-basichttprelay 傳送埠的安全性功能。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**安全性模式**|指定使用的安全性類型。 有效值包括下列各項：<br /><br /> -                         **無**： 訊息傳輸期間並未受到保護。<br /><br /> -                         **傳輸**： 使用 HTTPS 傳輸安全性來提供。 使用 HTTPS 來維護 SOAP 訊息的安全。 此服務之 X.509 憑證的 CA 憑證鏈結必須安裝在這部電腦的「信任的根憑證授權單位」憑證存放區中，才可以使用此服務的憑證向傳送埠驗證此服務。<br /><br /> -                         **訊息**： 使用 SOAP 訊息安全性來提供安全性。 根據預設，SOAP **主體** 加密且簽署項目。 唯一有效**訊息用戶端認證類型**Wcf-basichttprelay 傳送配接器是**憑證**。 這種模式需要使用 HTTP 傳輸。<br /><br /> -                         **TransportWithMessageCredential**： 完整性、 機密性和服務驗證的 HTTPS 傳輸所提供。 此服務之 X.509 憑證的 CA 憑證鏈結必須安裝在這部電腦的「信任的根憑證授權單位」憑證存放區中，才可以使用此服務的憑證向傳送埠驗證此服務。 傳送埠驗證是由 SOAP 訊息安全性所提供。<br /><br /> 預設值是 **無**。|  
    |**訊息用戶端認證類型**|指定的訊息層級安全性選項，只有當您設定**安全性模式**上方以**訊息**或**TransportWithMessageCredential**。 有效值包括下列各項：<br /><br /> -                         **使用者名稱**： 通過此傳送埠的端點**UserName**認證。 Wcf-basichttprelay 傳送配接器，這不是支援。<br /><br /> -                         **憑證**： 此傳送埠會使用透過所指定的用戶端憑證的端點進行驗證**用戶端憑證-憑證指紋**屬性。 此外，使用這個認證類型時，服務憑證必須透過提供 **服務憑證-憑證指紋** 屬性。<br /><br /> 預設值是 **UserName**。|  
    |**演算法套件**|指定訊息加密和 Key Wrap 演算法。 這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。 可能的值為：<br /><br /> -                         **Basic128**： 使用 Aes128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                         **Basic128Rsa15**： 使用 aes128 代表訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> -                         **Basic128Sha256**： 使用 aes256 代表訊息加密，Sha256 用於訊息摘要，並 Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                         **Basic128Sha256Rsa15**： 使用 aes128 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> -                         **Basic192**： 使用 Aes192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                         **Basic192Rsa15**： 使用 aes192 代表訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> -                         **Basic192Sha256**： 使用 aes192 代表訊息加密，Sha256 用於訊息摘要，並 Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                         **Basic192Sha256Rsa15**： 使用 aes192 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> -                         **Basic256**： 使用 Aes256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                         **Basic256Rsa15**： 使用 aes256 代表訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> -                         **Basic256Sha256**： 使用 aes256 代表訊息加密，Sha256 用於訊息摘要，並 Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                         **Basic256Sha256Rsa15**： 使用 aes256 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> -                         **TripleDes**： 使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                         **TripleDesRsa15**： 使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> -                         **TripleDesSha256**： 使用 TripleDes 代表訊息加密，Sha256 用於訊息摘要，並 Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                         **TripleDesSha256Rsa15**： 使用 TripleDes 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> 預設值為 **[Basic256]**。|  
    |**用戶端憑證-憑證指紋**|指定 X.509 憑證來驗證此傳送埠端點的憑證指紋。 您可以瀏覽至選取的憑證指紋 **我** 存放 **目前使用者** 位置 **瀏覽**  按鈕。<br /><br /> 注意：<br /><br /> 您必須將用戶端憑證安裝到**目前使用者**裝載此傳送處理常式的使用者帳戶的位置的傳送埠。<br /><br /> 최소 길이: 0<br /><br /> 最大長度：40<br /><br /> 預設為空字串。|  
    |**服務憑證-憑證指紋**|指定 X.509 憑證的指紋，用於驗證此傳送埠傳送訊息至其中的端點。 您可以選取 [瀏覽到憑證指紋 **其他人** 存放 **本機** 位置 **瀏覽** ] 按鈕。<br /><br /> 最小長度：00<br /><br /> 最大長度：40<br /><br /> 預設為空字串。|  
    |**使用者名稱認證**|指定用來傳送訊息的認證。 您可以指定的屬性，即可 **編輯**  按鈕。 您必須設定認證，如果您選取 **Username** 選項 **訊息用戶端認證類型**。<br /><br /> 預設值是 **不會使用單一登入**。|  
    |**使用 ACS 服務身分識別**|適用於[!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]2013年。<br/><br/>選取此核取方塊，然後按一下 **編輯** ，並提供下列值來向服務匯流排。<br /><br /> -                         **存取控制服務 STS Uri** – 將此設`https://<Namespace>-sb.accesscontrol.windows.net/`，其中\<命名空間\>是您的服務匯流排命名空間。<br /><br /> -                         **簽發者名稱**– 指定簽發者名稱。 此值通常設定為擁有者。<br /><br /> -                         **簽發者金鑰**– 指定簽發者金鑰。|  
    |**服務匯流排連線資訊** | 新開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]。<br/><br/>選擇要使用的共用存取簽章 (SAS) 或存取控制服務 (ACS) 的服務匯流排命名空間。 <br/><br/>選取一個選項，然後選取 **編輯** 輸入索引鍵的資訊︰<br/><br/> - **共用存取簽章**： 輸入存取索引鍵名稱和存取金鑰。 這兩個值會列在 [Azure 入口網站](https://portal.azure.com)。<br/> - **存取控制服務**： 輸入 STS URI (`https://<yourNamespace>-sb.accesscontrol.windows.net/`)，簽發者名稱和簽發者金鑰。 中所述，使用 Windows PowerShell 來擷取這些值， [SB Messaging 配接器](../core/sb-messaging-adapter.md)。 |
  
6.  在**Wcf-basichttprelay 傳輸屬性**對話方塊**Proxy**索引標籤上，設定的 proxy 設定 Wcf-basichttprelay 傳送埠。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**使用傳送處理常式的 proxy 設定**|指定此傳送埠是否要在裝載此傳送埠的傳送處理常式中，使用 Proxy 設定。<br /><br /> 這是預設值。|  
    |**不使用 proxy**|指出這個傳送埠是否要使用 Proxy 伺服器。<br /><br /> 預設值為清除核取方塊。|  
    |**使用 proxy**|指出此傳送埠是否使用指定的 proxy 伺服器 **位址** 屬性。<br /><br /> 預設值為清除核取方塊。|  
    |**地址**|指定 Proxy 伺服器的位址。 使用 **https** 或 **http** 根據安全性組態的配置。 這個位址後面可以加上冒號和連接埠編號， 例如 http://127.0.0.1:8080。<br /><br /> 這個屬性的值才需要 **使用 proxy** 已選取。<br /><br /> 類型：字串<br /><br /> 最大長度：256<br /><br /> 預設為空字串。|  
    |**使用者名稱**|指定要用於驗證的使用者名稱。 若使用整合式驗證，則使用者名稱會包括網域，即「網域\使用者名稱」。 如果使用基本或摘要式驗證，則使用者名稱不包含網域\\。 這個屬性的值才需要 **使用 proxy** 已選取。<br /><br /> 注意：<br /><br /> Wcf-basichttprelay 傳送配接器會使用 proxy 的基本驗證。<br /><br /> 유형: 문자열<br /><br /> 최소 길이: 0<br /><br /> 最大長度：256<br /><br /> 預設為空字串。|  
    |**密碼**|指定要用於驗證的密碼。<br /><br /> 這個屬性的值才需要 **使用 proxy** 已選取。<br /><br /> 類型：字串<br /><br /> 최소 길이: 0<br /><br /> 最大長度：256<br /><br /> 預設為空字串。|  
  
7.  在**Wcf-basichttprelay 傳輸屬性**對話方塊**訊息**索引標籤上，指定 SOAP 資料選取範圍**主體**項目。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**內文--BizTalk 要求訊息內文**|使用 BizTalk 訊息內文部分建立內容的 soap **主體** 外寄訊息的項目。<br /><br /> 這是預設值。|  
    |**範本--由範本指定的內容**|使用 [XML]  文字方塊中提供的範本來建立外寄訊息的 SOAP **內文** 元素內容。<br /><br /> 預設值為清除核取方塊。|  
    |**XML**|輸入 XML 格式的範本內容的 SOAP **ody**外寄訊息的項目。 如果選取了 **[範本 -- BizTalk 回應訊息本文]** 選項，就需要此屬性。<br /><br /> 類型：字串<br /><br /> 最小長度：00<br /><br /> 最大長度：32767<br /><br /> 預設值為 `<bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/>`。|  
    |**信封--整個\<p: Envelope>\>**|從內送訊息的整個 SOAP **信封** 建立 BizTalk 訊息內文部分。 此屬性只對請求-回應連接埠有效。<br /><br /> 預設值為清除核取方塊。|  
    |**內文--內容\<soap: Body\>項目**|使用內送訊息的 SOAP **Body** 元素內容來建立 BizTalk 訊息內文部分。 如果 **Body** 元素有一個以上的子元素，則只有第一個元素會成為 BizTalk 訊息內文部分。 此屬性只對請求-回應連接埠有效。<br /><br /> 這是預設值。|  
    |**路徑--內容由內文路徑定位**|使用 **[內文路徑運算式]** 文字方塊中的內文路徑運算式，建立 BizTalk 訊息內文部分。 內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子元素來進行評估。 此屬性只對請求-回應連接埠有效。<br /><br /> 預設值為清除核取方塊。|  
    |**內文路徑運算式**|輸入內文路徑運算式，以識別用來建立 BizTalk 訊息內文部分的內送訊息特定部分。 此內文路徑運算式評估的 soap 的直系子項目 **主體** 內送訊息的節點。 如果此內文路徑運算式傳回一個以上的節點，則只會為 BizTalk 訊息內文部分選擇第一個節點。 如果選取了 **[路徑 -- 內容由內文路徑定位]** 選項，就需要此屬性。 此屬性只對請求-回應連接埠有效。<br /><br /> 類型：字串<br /><br /> 最小長度：00<br /><br /> 最大長度：32767<br /><br /> 預設為空字串。|  
    |**節點編碼**|指定 Wcf-basichttprelay 傳送配接器的內文路徑運算式所識別的節點用來解碼的編碼類型**內文路徑運算式**文字方塊。 如果選取了 **[路徑 -- 內容由內文路徑定位]** 選項，就需要此屬性。 此屬性只對請求-回應連接埠有效。 有效值包括下列各項：<br /><br /> - **Base64**: Base64 編碼方式。<br /><br /> -                         **Hex**： 十六進位編碼。<br /><br /> -                         **字串**： 文字編碼-utf-8<br /><br /> -                         **XML**: WCF 配接器建立 BizTalk 訊息內文中的內文路徑運算式所選取之節點外部 xml**內文路徑運算式**文字方塊。<br /><br /> 預設值是 **[XML]**。|  
    |**傳播錯誤訊息**|選取此核取方塊可將輸出處理失敗的訊息路由至訂閱應用程式 (例如另一個接收埠或協調流程排程)。 清除核取方塊以擱置失敗的訊息，並產生負值通知 (NACK)。 此屬性只對請求-回應連接埠有效。<br /><br /> 預設值為選取核取方塊。|  
  
8.  按一下  **確定** 和 **確定** 以儲存設定。  
  
## <a name="add-a-proxy-to-the-send-handler"></a>將 proxy 加入至傳送處理常式

您可以將 proxy 加入至傳送埠或傳送處理常式。 如果您要新增 proxy 在傳送埠，請略過本節。

1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理、 展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**.  
  
2.  選取**Wcf-basichttprelay**，然後選取 傳送處理常式。  
  
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