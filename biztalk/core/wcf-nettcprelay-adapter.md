---
title: "Wcf-nettcprelay 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f6c6afc-6aa9-4962-91e6-1fcd92744534
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ba664facca73dc95093ee52c1026967191a58c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-nettcprelay-adapter"></a>Wcf-nettcprelay 配接器
Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用**Wcf-nettcprelay**配接器來接收和傳送 WCF 服務要求，透過[NetTcpRelayBinding 類別](https://msdn.microsoft.com/library/azure/microsoft.servicebus.nettcprelaybinding.aspx)。  

本主題列出的步驟來設定**Wcf-nettcprelay**接收位置和傳送埠使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

## <a name="before-you-begin"></a>開始之前

從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]，此配接器可以使用存取控制服務 (ACS) 或共用存取簽章 (SAS) athenticate 至服務匯流排。 我們建議使用服務匯流排驗證時使用共用存取簽章 (SAS)。 

當您建立服務匯流排命名空間時，不會自動建立的存取控制 (ACS) 命名空間。 如果您使用 ACS 驗證，您可能需要建立新的 ACS 命名空間。 請參閱[SB Messaging 配接器](../core/sb-messaging-adapter.md)如需詳細資訊，包括擷取 ACS 索引鍵值的步驟。
  
## <a name="create-the-receive-location"></a>建立接收位置
 
> [!NOTE]
>  之前完成下列程序，您必須已經新增單向接收埠。 請參閱[如何建立接收埠](../core/how-to-create-a-receive-port.md)。  
  
1.  在 BizTalk 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 應用程式您要在其中建立接收位置。  
  
2.  在 [BizTalk 管理主控台] 的左窗格中，按一下 **[接收埠]** 節點。 然後在右窗格中，使用滑鼠右鍵按一下與現有接收位置關聯的接收埠，或是您要與新接收位置關聯的接收埠，然後按一下 **[屬性]**。  
  
3.  在 [接收埠屬性]  對話方塊的左窗格中，選取 [接收位置] ，然後在右窗格中按兩下現有的接收位置，或按一下 [新增]  以建立新接收位置。  
  
4.  在 **[接收位置屬性]** 對話方塊的 **[傳輸]** 區段中，從 **[類型]** 下拉式清單選取 **[WCF-NetTcpRelay]** ，然後按一下 **[設定]** ，以設定接收位置的傳輸屬性。  
  
5.  在 [WCF-NetTcpRelay 傳輸屬性]  對話方塊的 [一般]  索引標籤上，設定端點位址和 WCF-NetTcpRelay 接收位置的端點識別。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**位址 (URI)**|必要。 指定此接收位置的完整格式 URI。 這通常會使用下列格式：<br /><br /> `sb://<Namespace>.servicebus.windows.net/`|  
    |**端點身分識別**|選擇性。 指定端點識別。 這些設定可讓端點驗證此接收位置。 在端點與接收位置之間的交握程序中，Windows Communication Foundation (WCF) 基礎結構可確保端點的識別與此元素的值相符。<br /><br /> 最小長度：00<br /><br /> 最大長度：32767<br /><br /> 預設為空字串。|  
  
6.  在 [WCF-NetTcpRelay 傳輸屬性]  對話方塊的 [繫結]  索引標籤上，設定逾時和交易屬性。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**開啟逾時 (hh: mmss)**|指定時間值，表示可供完成通道開啟作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**傳送逾時 (hh: mmss)**|指定時間值，表示可供完成傳送作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。 如果您使用要求-回應接收埠，這個值會指定完成整個互動的時間長度，即使服務傳回很大的訊息也是如此。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**關閉逾時 (hh: mmss)**|指定時間值，表示可供完成通道關閉作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**接收的訊息大小上限 （位元組）**|以位元組為單位，指定可在網路上接收的訊息大小上限 (含標頭)。 訊息的大小受限於配置給每個訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。<br /><br /> Wcf-nettcprelay 配接器會利用[NetTcpRelayBinding](https://msdn.microsoft.com/library/azure/microsoft.servicebus.nettcprelaybinding.aspx)類別與端點進行通訊的緩衝的傳輸模式中。 緩衝的傳輸模式下， [NetTcpRelayBindingBase.MaxBufferSize](https://msdn.microsoft.com/library/azure/microsoft.servicebus.nettcprelaybindingbase.maxbuffersize.aspx)屬性會一律等於這個屬性的值。<br /><br /> 預設值：65536<br /><br /> 最大值：2147483647|  
    |**同時呼叫上限**|指定對單一服務執行個體的並行呼叫數目。 超出上限的呼叫將排入佇列。 將這個值設定為 0 的效果與設定為 **Int32.MaxValue**相同。<br /><br /> 預設值：200|  
  
7.  在 [WCF-NetTcpRelay 傳輸屬性]  對話方塊的 [安全性]  索引標籤上，定義 WCF-NetTcpRelay 接收位置的安全性功能。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**安全性模式**|指定使用的安全性類型。 有效值包括下列各項：<br /><br /> -                          **無**： 訊息傳輸期間並未受到保護。<br /><br /> - **傳輸**： 使用傳輸安全性來提供**TLS over TCP**或**SPNego**。 您可以使用此模式來控制保護等級。 如果您在此安全性模式下，為 **[傳輸用戶端認證類型]** 屬性選取 **[無]** 或 **[憑證]** ，則必須透過 **[服務憑證 - 憑證指紋]** 屬性來提供此接收位置的服務憑證。<br /><br /> - **訊息**： 使用 SOAP 訊息安全性來提供安全性。 根據預設，SOAP **Body** 會進行加密及簽署。 這個模式提供了各種功能，例如當用戶端超出範圍時是否可以使用服務認證，以及所要使用的演算法組合。 如果您在此安全性模式下，為 **[訊息用戶端認證類型]**屬性選取 **[無]**、 **[UserName]** 或 **[憑證]** ，則必須透過 **[服務憑證 - 憑證指紋]** 屬性來提供此接收位置的服務憑證。<br /><br /> -                          **TransportWithMessageCredential**： 傳輸安全性與訊息安全性組合。 傳輸安全性由 **TLS over TCP** 或 **SPNego** 提供，並可確保完整性、機密性和伺服器驗證。 如果您在此安全性模式下，為 **[訊息用戶端認證類型]**屬性選取 **[Windows]**、 **[UserName]** 或 **[憑證]** ，則必須透過 **[服務憑證 - 憑證指紋]** 屬性來提供此接收位置的服務憑證。<br /><br /> **注意：**此安全性模式下不能與**傳輸用戶端認證類型**屬性，**無**。<br /><br /> 預設值為 **[傳輸]**。|  
    |**傳輸保護等級**|定義在 TCP 傳輸層的安全性。 簽署訊息可以降低訊息在傳輸時遭到第三者竄改的風險。 加密可在傳輸時提供資料等級的隱私權。 有效值包括下列各項：<br /><br /> -                          **無**： 無保護。<br /><br /> - **符號**： 簽署訊息。<br /><br /> - **EncryptAndSign**： 加密及簽署訊息。<br /><br /> 預設值為 **[EncryptAndSign]**。|  
    |**訊息用戶端認證類型**|指定當使用以訊息為基礎的安全性來執行用戶端驗證時，所要使用的認證類型。 只有當 [安全性模式]  設為 [訊息]  或 [TransportWithMessageCredential] 時，才需要指定認證類型。 有效值包括下列各項：<br /><br /> -                          **無**： 這會允許服務與匿名用戶端互動。 這表示，此用戶端不會提供任何用戶端認證。<br /><br /> - **Windows**： 允許 SOAP 交換加入 Windows 認證的已驗證的內容。 此用戶端認證是使用 **WSS SOAP Message Security Kerberos Token Profile 1.0** 通訊協定，透過 SOAP **Header** 元素傳遞。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。 此外，必須以執行此接收處理常式的使用者帳戶名稱，來設定用戶端的 **userPrincipalName** 項目。<br /><br /> - **使用者名稱**： 至此驗證用戶端使用接收位置**UserName**認證。 此認證是使用 **WSS SOAP Message Security UsernameToken Profile 1.0** 通訊協定，透過 SOAP **Header** 元素傳遞。 您必須建立對應到用戶端認證的網域或本機使用者帳戶。<br /><br /> -**憑證**： 用戶端會驗證此接收位置使用的用戶端憑證，透過指定**服務憑證-憑證指紋**屬性。 此認證是使用 **WSS SOAP Message Security X509 Token Profile 1.0** 通訊協定，透過 SOAP **Header** 元素傳遞。 若要驗證用戶端憑證，用戶端憑證的 CA 憑證鏈結必須安裝在這部電腦的「信任的根憑證授權單位」憑證存放區中。 此外，您必須透過 **[用戶端憑證 - 憑證指紋]** 屬性，提供此位置的服務驗證。<br /><br /> 預設值是 **[Windows]**。|  
    |**演算法套件**|指定訊息加密和 Key Wrap 演算法。 這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。 可能的值為：<br /><br /> -                          **Basic128**： 使用 Aes128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                          **Basic128Rsa15**： 使用 aes128 代表訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> -                          **Basic128Sha256**： 使用 aes256 代表訊息加密，Sha256 用於訊息摘要，並 Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                          **Basic128Sha256Rsa15**： 使用 aes128 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> - **Basic192**： 使用 Aes192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> - **Basic192Rsa15**： 使用 aes192 代表訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> -                          **Basic192Sha256**： 使用 aes192 代表訊息加密，Sha256 用於訊息摘要，並 Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                          **Basic192Sha256Rsa15**： 使用 aes192 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> - **Basic256**： 使用 Aes256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                          **Basic256Rsa15**： 使用 aes256 代表訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> - **Basic256Sha256**： 使用 aes256 代表訊息加密，Sha256 用於訊息摘要，並 Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> - **Basic256Sha256Rsa15**： 使用 aes256 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> - **TripleDes**： 使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                          **TripleDesRsa15**： 使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> - **TripleDesSha256**： 使用 TripleDes 代表訊息加密，Sha256 用於訊息摘要，並 Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                          **TripleDesSha256Rsa15**： 使用 TripleDes 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> 預設值為 **[Basic256]**。|  
    |**服務憑證-指紋**|針對此接收位置指定用戶端用來驗證服務之 X.509 憑證的憑證指紋。 您可以使用 **[瀏覽]** 按鈕瀏覽至 **「目前使用者」** 位置的 **My** 存放區，以選取憑證指紋。<br /><br /> **注意：**您必須將服務憑證安裝到**目前使用者**裝載此接收位置的接收處理常式的使用者帳戶的位置。<br /><br /> 最小長度：00<br /><br /> 最大長度：40<br /><br /> 預設為空字串。|  
    |**轉接用戶端驗證類型**|指定用於驗證接收訊息之服務匯流排轉接端點的選項。 有效值包括下列各項：<br /><br /> -                          **無**： 都不需要驗證。<br /><br /> -                          **RelayAccessToken**： 指定此選項可使用授權與服務匯流排轉接端點的安全性權杖。<br /><br /> 預設值為 **RelayAccessToken**。|  
    |**啟用服務探索**|選取此核取方塊，指定是否在服務登錄中發佈此服務的行為。<br /><br /> -                          **顯示名稱**– 指定與服務發行至服務登錄的名稱。<br /><br /> - **探索模式**– 設定服務登錄中發佈服務的探索模式。 如需探索模式的詳細資訊，請參閱[https://msdn.microsoft.com/library/microsoft.servicebus.discoverytype.aspx](https://msdn.microsoft.com/library/microsoft.servicebus.discoverytype.aspx)。|  
    |**存取控制服務**|適用於[!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]2013年。<br/><br/>如果將 **[轉接用戶端驗證類型]** 設定為 **[RelayAccessToke]**，請按一下 **[編輯]** 按鈕並指定下列詳細資料：<br /><br /> - **存取控制服務 STS Uri** – 將此設`https://<Namespace>-sb.accesscontrol.windows.net/`，其中\<命名空間 > 是您的服務匯流排命名空間。<br /><br /> - **簽發者名稱**– 指定簽發者名稱。 此值通常設定為擁有者。<br /><br /> - **簽發者金鑰**– 指定簽發者金鑰。<br /><br /> |  
        |**服務匯流排連接資訊** | 新開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]。<br/><br/>選擇要使用的共用存取簽章 (SAS) 或存取控制服務 (ACS) 的服務匯流排命名空間。 <br/><br/>選取一個選項，然後選取**編輯**輸入索引鍵的資訊：<br/><br/> - **共用存取簽章**： 輸入存取索引鍵名稱和存取金鑰。 這兩個值會列在[Azure 入口網站](https://portal.azure.com)。<br/> - **存取控制服務**： 輸入 STS URI (`https://<yourNamespace>-sb.accesscontrol.windows.net/`)，簽發者名稱和簽發者金鑰。 中所述，使用 Windows PowerShell 來擷取這些值， [SB Messaging 配接器](../core/sb-messaging-adapter.md)。 |
  
8.  在 [WCF-NetTcpRelay 傳輸屬性]  對話方塊的 [訊息]  索引標籤上，指定 SOAP **Body** 項目的資料選取範圍。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**信封--整個\<soap: Envelope >**|從內送訊息的整個 SOAP **信封** 建立 BizTalk 訊息內文部分。<br /><br /> 預設值為清除核取方塊。|  
    |**內文--內容\<soap: Body > 項目**|使用內送訊息的 SOAP **Body** 元素內容來建立 BizTalk 訊息內文部分。 如果 **Body** 元素有一個以上的子元素，則只有第一個元素會成為 BizTalk 訊息內文部分。<br /><br /> 這是預設值。|  
    |**路徑--內容由內文路徑定位**|使用 **[內文路徑運算式]** 文字方塊中的內文路徑運算式，建立 BizTalk 訊息內文部分。 內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子元素來進行評估。<br /><br /> 預設值為清除核取方塊。|  
    |**內文路徑運算式**|輸入內文路徑運算式，以識別用來建立 BizTalk 訊息內文部分的內送訊息特定部分。 這個內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子項目來進行評估。 如果此內文路徑運算式傳回一個以上的節點，則只會為 BizTalk 訊息內文部分選擇第一個節點。 如果選取了 **[路徑 -- 內容由內文路徑定位]** 選項，就需要此屬性。<br /><br /> 類型：字串<br /><br /> 最小長度：00<br /><br /> 最大長度：32767<br /><br /> 預設為空字串。|  
    |**節點編碼**|指定 WCF-NetTcpRelay 接收配接器針對 **[內文路徑運算式]** 文字方塊中的內文路徑運算式所識別的節點，用來解碼的編碼類型。 如果選取了 **[路徑 -- 內容由內文路徑定位]** 選項，就需要此屬性。 有效值包括下列各項：<br /><br /> - **Base64**: Base64 編碼方式。<br /><br /> - **Hex**： 十六進位編碼。<br /><br /> -                          **字串**： 文字編碼-utf-8<br /><br /> -                          **XML**: WCF 配接器建立 BizTalk 訊息內文中的內文路徑運算式所選取之節點外部 xml**內文路徑運算式**文字方塊。<br /><br /> 預設值是 **[XML]**。|  
    |**內文--BizTalk 回應訊息內文**|使用 BizTalk 訊息內文部分建立外寄回應訊息的 SOAP **內文** 元素內容。 此屬性只適用於要求-回應接收位置。<br /><br /> 這是預設值。|  
    |**範本--由範本指定的內容**|使用 [XML]  文字方塊中提供的範本來建立外寄訊息的 SOAP **內文** 元素內容。 此屬性只適用於要求-回應接收位置。<br /><br /> 預設值為清除核取方塊。|  
    |**XML**|針對外寄訊息的 SOAP **內文** 元素內容，輸入 XML 格式的範本。 如果選取了 **[範本 -- BizTalk 回應訊息本文]** 選項，就需要此屬性。 此屬性只適用於要求-回應接收位置。<br /><br /> 類型：字串<br /><br /> 最小長度：00<br /><br /> 最大長度：32767<br /><br /> 預設值是 **\<bts 訊息主體 xmlns ="http://www.microsoft.com/schemas/bts2007"encoding ="xml"/ >**。|
    |**擱置失敗的要求訊息**|指定是否擱置因接收管線失敗或路由失敗而造成輸入處理失敗的要求訊息。<br /><br /> 預設值為清除核取方塊。|  
    |**錯誤中包含例外狀況詳細資料**|指定是否要將在錯誤發生時傳回 SOAP 錯誤以方便偵錯。<br /><br /> 預設值為清除核取方塊。|  
  
9. 按一下 **[確定]**。  
  
10. 在 **[接收位置屬性]** 對話方塊中輸入適當的值，以完成接收位置的組態，然後按一下 **[確定]** 儲存設定值。 如需有關資訊**接收位置屬性**對話方塊中，請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。 
  
## <a name="create-the-send-port"></a>建立傳送埠
  
1.  在 [BizTalk 管理主控台] 中建立新的傳送埠，或按兩下現有的傳送埠進行修改。 如需詳細資訊，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 設定所有傳送埠選項，並指定**Wcf-nettcprelay**如**類型**選項**傳輸**區段**一般** 索引標籤。  
  
2.  在**一般**索引標籤的**傳輸**區段中，按一下**設定** 按鈕。  
  
3.  在**Wcf-nettcprelay 傳輸屬性**對話方塊**一般**索引標籤上，指定下列項目：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**位址 (URI)**|必要。 指定傳送埠的完整格式的 URI。 這通常會使用下列格式：<br /><br /> `sb://<Namespace>.servicebus.windows.net/`<br /><br /> 最大長度： 255<br /><br /> 預設值： net.tcp://localhost/|  
    |**端點身分識別**|選擇性。 指定此傳送埠傳送訊息的端點身分識別。 這些設定可讓此傳送埠驗證端點。 端點，並將傳送埠之間的交握程序，在 Windows Communication Foundation (WCF) 基礎結構可確保端點的身分識別符合此項目的值。 可以針對指定的值**端點身分識別**屬性，則根據安全性組態而有所不同。<br /><br /> 預設值為清除核取方塊。|  
    |**動作**|指定**SOAP 動作**外寄訊息的標頭欄位。 這個屬性也可以透過訊息內容屬性設定**WCF。動作**管線或協調流程中。 您可以將這個值指定兩個不同的方式： 單一動作格式和動作對應格式。 如果您設定這個屬性中的單一動作格式-例如，http://contoso.com/Svc/Op1- **SOAPAction**標頭外寄訊息一定會設定這個屬性中指定的值。<br /><br /> 如果您設定此屬性以動作對應格式，傳出**SOAPAction**標頭由**BTS。作業**內容屬性。 例如，如果此屬性設定為下列 XML 格式和**BTS。作業**屬性設定為 Op1，WCF 傳送配接器`uses http://contoso.com/Svc/Op1`針對外寄**SOAPAction**標頭。<br /><br /> `<BtsActionMapping> <Operation Name="Op1" Action="http://contoso.com/Svc/Op1" /> <Operation Name="Op2" Action="http://contoso.com/Svc/Op2" /> </BtsActionMapping>`<br /><br /> 如果外寄訊息是來自協調流程連接埠，協調流程執行個體動態設定**BTS。作業**與連接埠的作業名稱的屬性。 如果外寄訊息都會路由傳送，以內容為基礎的路由，您可以設定**BTS。作業**管線元件中的屬性。<br /><br /> 最小長度：00<br /><br /> 最大長度：32767<br /><br /> 預設為空字串。|  
  
4.  在 [WCF-NetTcpRelay 傳輸屬性]  對話方塊的 [繫結]  索引標籤上，設定逾時和交易屬性。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**開啟逾時 (hh: mmss)**|指定時間值，表示可供完成通道開啟作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**傳送逾時 (hh: mmss)**|指定時間值，表示可供完成傳送作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。 如果您使用請求-回應傳送埠，這個值會指定完成整個互動的時間長度，即使服務傳回很大的訊息也是如此。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**關閉逾時 (hh: mmss)**|指定時間值，表示可供完成通道關閉作業的時間間隔。 這個值應大於或等於 **System.TimeSpan.Zero**。<br /><br /> 預設值：00:01:00<br /><br /> 最大值：23:59:59|  
    |**接收的訊息大小上限 （位元組）**|以位元組為單位，指定可在網路上接收的訊息大小上限 (含標頭)。 訊息的大小受限於配置給每個訊息的記憶體數量。 您可以使用這個屬性來限制遭受拒絕服務 (DoS) 攻擊的風險程度。<br /><br /> Wcf-nettcprelay 配接器會利用[NetTcpRelayBinding](https://msdn.microsoft.com/library/azure/microsoft.servicebus.nettcprelaybinding.aspx)類別與端點進行通訊的緩衝的傳輸模式中。 緩衝的傳輸模式下， [NetTcpRelayBindingBase.MaxBufferSize](https://msdn.microsoft.com/library/azure/microsoft.servicebus.nettcprelaybindingbase.maxbuffersize.aspx)屬性會一律等於這個屬性的值。<br /><br /> 預設值：65536<br /><br /> 最大值：2147483647|  
  
5.  在**Wcf-nettcprelay 傳輸屬性**對話方塊**安全性**索引標籤上，定義 Wcf-nettcprelay 傳送埠的安全性功能。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**安全性模式**|指定使用的安全性類型。 有效值包括下列各項：<br /><br /> - **無**： 訊息傳輸期間並未受到保護。<br /><br /> - **傳輸**： 使用傳輸安全性來提供**TLS over TCP**或**SPNego**。 您可以使用此模式來控制保護等級。<br /><br /> -                          **訊息**： 使用 SOAP 訊息安全性來提供安全性。 根據預設，SOAP **Body** 會進行加密及簽署。 這個模式提供了各種功能，例如當用戶端超出範圍時是否可以使用服務認證，以及所要使用的演算法組合。<br /><br /> - **TransportWithMessageCredential**： 傳輸安全性與訊息安全性組合。 傳輸安全性由提供**TLS over TCP**，或**SPNego**，並確保完整性、 機密性和伺服器驗證。 SOAP 訊息安全性會提供用戶端驗證。 若要使用此模式，此服務之 X.509 憑證的 CA 憑證鏈結必須安裝在這部電腦的「信任的根憑證授權單位」憑證存放區中，才可以向傳送埠驗證此服務。<br /><br /> **注意：**此安全性模式下不能與**傳輸用戶端認證類型**屬性，**無**。<br /><br /> 預設值為 **[傳輸]**。|  
    |**傳輸保護等級**|定義在 TCP 傳輸層的安全性。 簽署訊息可以降低訊息在傳輸時遭到第三者竄改的風險。 加密可在傳輸時提供資料等級的隱私權。 有效值包括下列各項：<br /><br /> -                          **無**： 無保護。<br /><br /> - **符號**： 簽署訊息。<br /><br /> -                          **EncryptAndSign**： 加密及簽署訊息。<br /><br /> 預設值為 **[EncryptAndSign]**。|  
    |**訊息用戶端認證類型**|指定當使用以訊息為基礎的安全性來執行用戶端驗證時，所要使用的認證類型。 只有當 [安全性模式]  設為 [訊息]  或 [TransportWithMessageCredential] 時，才需要指定認證類型。 有效值包括下列各項：<br /><br /> - **無**： 這會允許服務與匿名用戶端互動。 這表示，此傳送埠不會提供任何用戶端認證。 服務 X.509 憑證的 CA 憑證鏈結必須安裝在這部電腦的「信任的根憑證授權單位」憑證存放區中，才可以向這個傳送埠驗證服務。<br /><br /> -                          **Windows**： 允許 SOAP 交換加入 Windows 認證的已驗證的內容。 執行此傳送埠所用的使用者帳戶會用於驗證此傳送埠的服務。 此用戶端認證是使用 **WSS SOAP Message Security Kerberos Token Profile 1.0** 通訊協定，透過 SOAP **Header** 元素傳遞。 您必須設定**使用者主體名稱**屬性，以使用執行目的地服務的使用者帳戶名稱**識別編輯器** 對話方塊。<br /><br /> - **使用者名稱**： 此傳送埠驗證服務與**UserName**認證。 此認證是使用 **WSS SOAP Message Security UsernameToken Profile 1.0** 通訊協定，透過 SOAP **Header** 元素傳遞。 這個選項需要設定**用戶端認證**屬性。 服務 X.509 憑證的 CA 憑證鏈結必須安裝在這部電腦的「信任的根憑證授權單位」憑證存放區中，才可以向這個傳送埠驗證服務。<br /><br /> - **憑證**： 此傳送埠會使用透過所指定的用戶端憑證的服務進行驗證**用戶端憑證-憑證指紋**屬性。 此認證是使用 **WSS SOAP Message Security X509 Token Profile 1.0** 通訊協定，透過 SOAP **Header** 元素傳遞。 服務 X.509 憑證的 CA 憑證鏈結必須安裝在這部電腦的「信任的根憑證授權單位」憑證存放區中，才可以向這個傳送埠驗證服務。<br /><br /> 預設值是 **[Windows]**。|  
    |**演算法套件**|指定訊息加密和 Key Wrap 演算法。 這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。 可能的值為：<br /><br /> - **Basic128**： 使用 Aes128 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> - **Basic128Rsa15**： 使用 aes128 代表訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> -                          **Basic128Sha256**： 使用 aes256 代表訊息加密，Sha256 用於訊息摘要，並 Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                          **Basic128Sha256Rsa15**： 使用 aes128 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> - **Basic192**： 使用 Aes192 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                          **Basic192Rsa15**： 使用 aes192 代表訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> - **Basic192Sha256**： 使用 aes192 代表訊息加密，Sha256 用於訊息摘要，並 Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                          **Basic192Sha256Rsa15**： 使用 aes192 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> -                          **Basic256**： 使用 Aes256 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> - **Basic256Rsa15**： 使用 aes256 代表訊息加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> - **Basic256Sha256**： 使用 aes256 代表訊息加密，Sha256 用於訊息摘要，並 Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> - **Basic256Sha256Rsa15**： 使用 aes256 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> -                          **TripleDes**： 使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> - **TripleDesRsa15**： 使用 TripleDes 加密，Sha1 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> - **TripleDesSha256**： 使用 TripleDes 代表訊息加密，Sha256 用於訊息摘要，並 Rsa-oaep-mgf1p 用於金鑰包裝。<br /><br /> -                          **TripleDesSha256Rsa15**： 使用 TripleDes 代表訊息加密，Sha256 用於訊息摘要，Rsa15 用於金鑰包裝。<br /><br /> 預設值為 **[Basic256]**。|  
    |**用戶端憑證-指紋**|指定 X.509 憑證的指紋，以便向服務驗證此傳送埠。 您可以使用 **[瀏覽]** 按鈕瀏覽至 **「目前使用者」** 位置的 **My** 存放區，以選取憑證指紋。<br /><br /> **注意：**您必須將用戶端憑證安裝到**目前使用者**裝載此傳送處理常式的使用者帳戶的位置的傳送埠。<br /><br /> 最小長度：00<br /><br /> 最大長度：40<br /><br /> 預設為空字串。|  
    |**使用者名稱認證**|指定傳送訊息時使用的認證**UserName**如**訊息用戶端認證類型**屬性。 您可以指定的屬性，即可**編輯認證** 按鈕。<br /><br /> 預設值是**不會使用單一登入**。|  
    |**使用 ACS 服務識別**|適用於[!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]2013年。<br/><br/>選取此核取方塊，然後按一下**編輯**並提供下列值來向服務匯流排。<br /><br /> - **存取控制服務 STS Uri** – 將此設`https://<Namespace>-sb.accesscontrol.windows.net/`，其中\<命名空間 > 是您的服務匯流排命名空間。<br /><br /> - **簽發者名稱**– 指定簽發者名稱。 此值通常設定為擁有者。<br /><br /> - **簽發者金鑰**– 指定簽發者金鑰。|  
    |**服務匯流排連接資訊** | 新開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]。<br/><br/>選擇要使用的共用存取簽章 (SAS) 或存取控制服務 (ACS) 的服務匯流排命名空間。 <br/><br/>選取一個選項，然後選取**編輯**輸入索引鍵的資訊：<br/><br/> - **共用存取簽章**： 輸入存取索引鍵名稱和存取金鑰。 這兩個值會列在[Azure 入口網站](https://portal.azure.com)。<br/> - **存取控制服務**： 輸入 STS URI (`https://<yourNamespace>-sb.accesscontrol.windows.net/`)，簽發者名稱和簽發者金鑰。 中所述，使用 Windows PowerShell 來擷取這些值， [SB Messaging 配接器](../core/sb-messaging-adapter.md)。 |
  
6.  在 [WCF-NetTcpRelay 傳輸屬性]  對話方塊的 [訊息]  索引標籤上，指定 SOAP **Body** 項目的資料選取範圍。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**內文--BizTalk 要求訊息內文**|使用 BizTalk 訊息內文部分建立的 soap 內容**主體**外寄訊息的項目。<br /><br /> 這是預設值。|  
    |**範本--由範本指定的內容**|使用 [XML]  文字方塊中提供的範本來建立外寄訊息的 SOAP **內文** 元素內容。<br /><br /> 預設值為清除核取方塊。|  
    |**XML**|針對外寄訊息的 SOAP **內文** 元素內容，輸入 XML 格式的範本。 如果選取了 **[範本 -- BizTalk 回應訊息本文]** 選項，就需要此屬性。<br /><br /> 類型：字串<br /><br /> 最小長度：00<br /><br /> 最大長度：32767<br /><br /> 預設值是 < bts 訊息主體<br /><br /> xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/>|  
    |**信封--整個\<soap: Envelope >**|建立 BizTalk 訊息內文部分的整個 SOAP 從**信封**的傳入。 此屬性只對請求-回應連接埠有效。<br /><br /> 預設值為清除核取方塊。|  
    |**內文--內容\<soap: Body > 項目**|使用內送訊息的 SOAP **Body** 元素內容來建立 BizTalk 訊息內文部分。 如果 **Body** 元素有一個以上的子元素，則只有第一個元素會成為 BizTalk 訊息內文部分。 此屬性只對請求-回應連接埠有效。<br /><br /> 這是預設值。|  
    |**路徑--內容由內文路徑定位**|使用 **[內文路徑運算式]** 文字方塊中的內文路徑運算式，建立 BizTalk 訊息內文部分。 內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子元素來進行評估。 此屬性只對請求-回應連接埠有效。<br /><br /> 預設值為清除核取方塊。|  
    |**內文路徑運算式**|輸入內文路徑運算式，以識別用來建立 BizTalk 訊息內文部分的內送訊息特定部分。 此內文路徑運算式評估的 soap 的直系子元素**主體**節點內送訊息。 如果此內文路徑運算式傳回一個以上的節點，則只會為 BizTalk 訊息內文部分選擇第一個節點。 如果選取了 **[路徑 -- 內容由內文路徑定位]** 選項，就需要此屬性。 此屬性只對請求-回應連接埠有效。<br /><br /> 類型：字串<br /><br /> 最小長度：00<br /><br /> 最大長度：32767<br /><br /> 預設為空字串。|  
    |**節點編碼**|指定 Wcf-nettcprelay 傳送配接器的內文路徑運算式所識別的節點用來解碼的編碼類型**內文路徑運算式**文字方塊。 如果選取了 **[路徑 -- 內容由內文路徑定位]** 選項，就需要此屬性。 此屬性只對請求-回應連接埠有效。 有效值包括下列各項：<br /><br /> -                          **Base64**: Base64 編碼方式。<br /><br /> - **Hex**： 十六進位編碼。<br /><br /> - **字串**： 文字編碼-utf-8<br /><br /> -                          **XML**: WCF 配接器建立 BizTalk 訊息內文中的內文路徑運算式所選取之節點外部 xml**內文路徑運算式**文字方塊。<br /><br /> 預設值是 **[XML]**。|  
    |**傳播錯誤訊息**|選取此核取方塊可將輸出處理失敗的訊息路由至訂閱應用程式 (例如另一個接收埠或協調流程排程)。 清除核取方塊以擱置失敗的訊息，並產生負值通知 (NACK)。 此屬性只對請求-回應連接埠有效。<br /><br /> 預設值為選取核取方塊。|  
  
7.  按一下**確定**和**確定**以儲存設定。  
  
## <a name="set-maxconnections-in-the-handler"></a>在處理常式組 MaxConnections

1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理、 展開**BizTalk 群組**，展開**平台設定**，然後展開**配接器**.  
  
2.  在配接器清單中，選取**Wcf-nettcprelay**，然後選取傳送或接收處理常式。  
  
3.  在**配接器處理常式屬性**上**一般**索引標籤上，選取**屬性**。  
  
4.  在**處理常式** 索引標籤：   
  
    |使用|動作|  
    |--------------|----------------|  
    |**連線數目上限**|指定 （接收處理常式） 的輸入的連線和指定之連接集區中快取每個端點的傳出連線 （傳送處理常式） 的最大數目。 這會限制每個唯一遠端端點快取中的連線數目。 您應該將這個值設定為大於您預計要為任何特定遠端端點快取存放的最大連線數。 如果作用中連線數目超過這個最大值，服務可能會在此傳送處理常式下執行的 Wcf-nettcprelay 傳送埠沒有回應。<br /><br /> 預設值是 10。|  
  
5.  選取 [確定] 儲存您的變更。  

## <a name="see-also"></a>另請參閱
[SB Messaging 配接器](../core/sb-messaging-adapter.md)

[使用配接器](../core/using-adapters.md)