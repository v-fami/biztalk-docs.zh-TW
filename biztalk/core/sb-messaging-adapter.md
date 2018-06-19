---
title: 服務匯流排傳訊配接器 |Microsoft 文件
description: 傳送和接收 BizTalk Server 中使用 Azure SB Messaging 配接器的訊息
ms.custom: ''
ms.date: 11/21/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c06c4934-45b2-4f6f-9d19-3ebd937c32ae
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1775606a911d8ce23fd2999ad367053c4f8f72de
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
ms.locfileid: "25497871"
---
# <a name="sb-messaging-adapter"></a>SB Messaging 配接器
服務匯流排 (**Sb-messaging**) 配接器用來接收和傳送來自服務匯流排實體，例如佇列、 主題和轉送。 您可以使用**Sb-messaging**配接器連接在內部[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]至 Azure。

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]Feature Pack 2**，支援服務匯流排 Premium。 設定使用此配接器傳送埠時，您可以傳送訊息至資料分割的佇列和主題。 

## <a name="authenticating-with-service-bus"></a>使用服務匯流排驗證
服務匯流排提供兩種方法來驗證： 

- 存取控制服務 (ACS) 
- 共用存取簽章 (SAS)

我們建議使用共用存取簽章 (SAS) 來向服務匯流排。 共用存取金鑰值都會列在[Azure 入口網站](https://portal.azure.com)。

當您建立服務匯流排命名空間時，不會自動建立的存取控制 (ACS) 命名空間。 若要使用存取控制，您需要此命名空間的簽發者名稱和簽發者金鑰值。 這些值可用，當您建立新的 ACS 命名空間使用 Windows PowerShell。 這些值不會列出在 Azure 入口網站。

若要使用 ACS 進行驗證，並取得簽發者名稱和簽發者金鑰值，整體的步驟包括：

1. 安裝[Azure Powershell cmdlet](https://azure.microsoft.com/documentation/articles/powershell-install-configure/)。
2. 加入您的 Azure 帳戶：`Add-AzureAccount`
3. 傳回訂用帳戶名稱：`get-azuresubscription`
4. 選取您的訂用帳戶：`select-azuresubscription <name of your subscription>` 
5. 建立新的命名空間：`new-azuresbnamespace <name for the service bus> "Location" -CreateACSNamespace $true -NamespaceType Messaging`

    範例：`new-azuresbnamespace biztalksbnamespace "South Central US" -CreateACSNamespace $true -NamespaceType Messaging`
      
5. （這可能要花費幾分鐘的時間） 建立新的 ACS 命名空間時，連接字串中列出的 IssuerName 和 IssuerKey 值： 

    ```
    Name                  : biztalksbnamespace
    Region                : South Central US
    DefaultKey            : abcdefghijklmnopqrstuvwxyz
    Status                : Active
    CreatedAt             : 10/18/2016 9:36:30 PM
    AcsManagementEndpoint : https://biztalksbnamespace-sb.accesscontrol.windows.net/
    ServiceBusEndpoint    : https://biztalksbnamespace.servicebus.windows.net/
    ConnectionString      : Endpoint=sb://biztalksbnamespace.servicebus.windows.net/;SharedSecretIssuer=owner;SharedSecretValue=abcdefghijklmnopqrstuvwxyz
    NamespaceType         : Messaging
    ```

請參閱[New-azuresbnamespace](https://docs.microsoft.com/powershell/module/Azure/New-AzureSBNamespace)指導方針。

## <a name="receive-messages-from-service-bus"></a>接收來自服務匯流排的訊息
  
1. 在 BizTalk Server 管理主控台中，展開  **BizTalk 群組**，依序展開**應用程式**，然後展開您的應用程式。 

2. 以滑鼠右鍵按一下**接收埠**，選取**新增**，然後選取**單向接收埠**。 

3. 提供一個名稱，並選取**接收位置**。 

4. 選取**新增**，不妨**名稱**。 在**傳輸**區段中，選取**Sb-messaging**從**類型**下拉式清單，然後選取**設定**。  
  
5. 設定**一般**屬性：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**佇列或訂閱 URL**|指定已部署服務匯流排佇列的 URL。 URL 通常會使用下列格式：<br /><br /> `sb://<namespace>.servicebus.windows.net/<queue_name>`|  
    |**開啟逾時**|指定時間值，表示可供完成通道開啟作業的時間。<br /><br /> **預設值：** 1 分鐘|  
    |**關閉逾時**|指定時間值，表示可供完成通道關閉作業的時間。<br /><br /> **預設值：** 1 分鐘|  
    |**接收逾時**|指定時間值，表示可供完成接收作業的時間。<br /><br /> **預設值：** 10 分鐘|  
    |**預先擷取計數**|指定同時從服務匯流排佇列或主題接收的訊息數目。 預先擷取可讓佇列或訂閱用戶端在執行接收作業時從服務載入其他訊息。 用戶端會將這些訊息存放在本機快取中。 快取大小是由您在此指定的 [預先擷取計數] 屬性值所決定。<br /><br /> 如需詳細資訊，請參閱章節 < 預先擷取 」 在[https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements/](https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements/)<br /><br /> **預設值：** -1|  
    |**使用工作階段**|選取此核取方塊以使用服務匯流排工作階段從佇列或訂閱接收訊息。|  
  
6.  設定**驗證**屬性：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**存取控制服務**|選取此項目以使用 ACS 進行驗證並提供下列值：<br /><br /> 輸入服務匯流排存取控制服務 STS URI。 URI 通常會使用下列格式：<br /><br /> `https://<namespace>-sb.accesscontrol.windows.net/`<br /><br /> 輸入服務匯流排命名空間的簽發者名稱。<br /><br /> 輸入服務匯流排命名空間的簽發者金鑰。|  
    |**共用存取簽章**(新開頭[!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)])|選取此項目以使用共用存取簽章 (SAS) 以進行驗證，並提供 SAS 金鑰和金鑰值。|  
  
7.  在**屬性**索引標籤的**仲介訊息屬性的命名空間**，輸入配接器用來撰寫代理的訊息屬性做為訊息內容屬性的命名空間所接收的訊息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 如果您想要升級仲介的訊息屬性，選取**升級仲介訊息屬性**核取方塊。  
  
8.  選取 [確定]。  
  
9. 選取您**接收處理常式**，而**接收管線**。 選取 [確定] 儲存您的變更。 [建立接收位置](../core/how-to-create-a-receive-location.md)提供一些指引。  
  
## <a name="send-messages-to-service-bus"></a>將訊息傳送至服務匯流排
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，選取**新增**，然後選取**靜態單向傳送埠**。

    [建立傳送埠](../core/how-to-create-a-send-port2.md)提供一些指引。

2. 輸入**名稱**。 在**傳輸**，將**類型**至**Sb-messaging**，然後選取**設定**。 
  
3.  設定**一般**屬性：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**目的地 URL**|輸入部署服務匯流排佇列所在的 URL。 URL 通常會使用下列格式：<br /><br /> `sb://<namespace>.servicebus.windows.net/<queue_name>`|  
    |**批次排清間隔**|指定時間值，表示將傳送至佇列或主題的訊息批次排清的間隔。 預設值是 20 毫秒。<br /><br /> 如需批次處理相對於服務匯流排佇列和主題的詳細資訊，請參閱**用戶端批次處理**區段在[https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements](https://azure.microsoft.com/documentation/articles/service-bus-performance-improvements)。|  
    |**開啟逾時**|指定時間值，表示可供完成通道開啟作業的時間。<br /><br /> **預設值：** 1 分鐘|  
    |**傳送逾時**|指定時間值，表示可供完成傳送作業的時間。<br /><br /> **預設值：** 1 分鐘|  
    |**關閉逾時**|指定時間值，表示可供完成通道關閉作業的時間。<br /><br /> **預設值：** 1 分鐘|  
  
4.  設定**驗證**屬性： 
  
    |使用|動作|  
    |--------------|----------------|  
    |**存取控制服務**|選取此項目以使用 ACS 進行驗證並提供下列值：<br /><br /> 輸入服務匯流排存取控制服務 STS URI。 URI 通常會使用下列格式：<br /><br /> `https://<namespace>-sb.accesscontrol.windows.net/`<br /><br /> 輸入服務匯流排命名空間的簽發者名稱。<br /><br /> 輸入服務匯流排命名空間的簽發者金鑰。|  
    |**共用存取簽章**(新開頭[!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)])|選取此項目以使用共用存取簽章 (SAS) 以進行驗證，並提供 SAS 金鑰和金鑰值。|  
  
5.  在**屬性**索引標籤上，輸入**命名空間，使用者定義的仲介訊息屬性**，其中包含您想要寫入至外寄訊息的 BizTalk 訊息內容屬性服務匯流排。 訊息會寫入所有命名空間屬性為使用者定義的仲介訊息屬性。 配接器將屬性寫入為仲介訊息屬性時，會忽略此命名空間。 它僅使用命名空間來確定要寫入的屬性。  
  
     您也可以輸入 BrokeredMessage 屬性的值。 在描述這些屬性[BrokeredMessage 屬性](https://docs.microsoft.com/dotnet/api/microsoft.servicebus.messaging.brokeredmessage)，包括**資料分割索引鍵**。
  
6.  選取 [確定] 儲存您的變更。  
  
## <a name="see-also"></a>另請參閱
[使用配接器](../core/using-adapters.md)