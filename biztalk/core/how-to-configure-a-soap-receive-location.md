---
title: 如何設定 SOAP 接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [SOAP adapters], virtual directories
- SOAP adapters, code samples
- configuring [SOAP adapters], receive locations
- virtual directories, SOAP adapters
- SOAP adapters, receive locations
- code samples, SOAP adapters
- configuring [SOAP adapters], code samples
- SOAP adapters, virtual directories
- receive locations, SOAP adapters
ms.assetid: 7e348409-9181-47e4-b3c0-c73eb2acffa3
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4de95a4d414cddde0812f590c84c237866772741
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999263"
---
# <a name="how-to-configure-a-soap-receive-location"></a>如何設定 SOAP 接收位置
您可以用程式設計方式或使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 來設定 SOAP 接收位置。  

 **如何設定 SOAP 接收位置以程式設計的方式**  

 「BizTalk 總管」物件模型可讓您以程式設計的方式建立和設定接收位置。 「 BizTalk 總管物件模型會公開**IReceiveLocation**接收位置組態介面具有**TransportTypeData**讀/寫屬性。 此屬性接受的 SOAP 接收位置組態屬性包格式，是成對的名稱-數值 XML 字串。 若要設定這個屬性，在 「 BizTalk 總管物件模型中，您必須設定**InboundTransportLocation**屬性**IReceiveLocation**介面。  

 **TransportTypeData**屬性**IReceiveLocation**介面沒有設定。 若不設定此屬性，SOAP 配接器會按照下列表格指示，使用預設值做為 SOAP 接收位置組態。  

 下列表格列出您可在「BizTalk 總管」物件模型中，為 SOAP 接收位置設定的組態屬性。  

|屬性名稱|類型|描述|  
|-------------------|----------|-----------------|  
|**URI**|String|包含部署伺服器上 Web 服務的虛擬目錄。|  
|**AddressableURI**|String|公用位址欄位，包含完整可呼叫的 URL。<br /><br /> 預設值： 空白|  
|**UseSSO**|布林|指定 SOAP 配接器是否發出「單一登入」票證至扺達此接收位置的訊息。<br /><br /> 預設值：False|  

 使用下列格式設定屬性：  

```  
receiveLocation.TransportTypeData = "<CustomProps><UseSSO vt=\"11\">-1</UseSSO></CustomProps>";  
```  

 **URI**並**AddressableURI**屬性會設定使用**位址**並**PublicAddress**的接收位置屬性物件。  

 下列程式碼片段示範建立 SOAP 接收位置：  

```  
// Use BizTalk Explorer object model to create new SOAP receive location.  
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
//requires project reference to \Program Files\Microsoft BizTalk Server 2009\Developer Tools\Microsoft.BizTalk.ExplorerOM.dll  
BtsCatalogExplorer explorer = new Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer();  
explorer.ConnectionString = connectionString;  

// Add a new Request-Response port  
ReceivePort receivePort = explorer.AddNewReceivePort(true);  
receivePort.Name = "SampleReceivePort";  
receivePort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  

// Add primary SOAP receive location  
ReceiveLocation receiveLocation = receivePort.AddNewReceiveLocation();  
receiveLocation.Name = "SampleReceiveLocation";  
receiveLocation.Address = "/PurchaseOrder/POOrchestration.asmx";  
receiveLocation.TransportType = explorer.ProtocolTypes["SOAP"];  
receiveLocation.TransportTypeData = "<CustomProps><UseSSO vt=\"11\">-1</UseSSO></CustomProps>";  
receiveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
foreach (ReceiveHandler receiveHandler in explorer.ReceiveHandlers)  
{  
if (receiveHandler.TransportType.Name == receiveLocation.TransportType.Name)  
{  
receiveLocation.ReceiveHandler = receiveHandler;   
}  
}  

// Save  
explorer.SaveChanges();   
```  

 **如何設定 SOAP 接收位置使用 BizTalk Server 管理主控台**  

 您可以在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 中設定 SOAP 接收位置配接器變數。 如果接收位置並未設定屬性，系統就會使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 中設定的預設接收處理常式值。  

> [!NOTE]
>  完成下列程序之前，您必須已經新增接收埠。 如需詳細資訊，請參閱 <<c0> [ 如何建立接收埠](../core/how-to-create-a-receive-port.md)。  

### <a name="to-configure-variables-for-a-soap-receive-location"></a>設定 SOAP 接收位置的變數  

1. 在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，然後展開您想要在其中建立接收位置的應用程式。  

2. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，在左窗格中，按一下**接收埠**節點。 然後在右窗格中，使用滑鼠右鍵按一下與現有接收位置關聯的接收埠，或是您要與新接收位置關聯的接收埠，然後按一下 **[屬性]**。  

3. 在 **接收埠屬性**對話方塊的左窗格中，選取**接收位置**，然後在右窗格中，按兩下現有接收位置或按一下**新增**以建立新接收位置。  

4. 在 **接收位置屬性**對話方塊的 **傳輸**區段旁邊**類型**，選取**SOAP**從下拉式清單中，然後按一下**設定**。  

5. 在  **SOAP 傳輸屬性**對話方塊方塊中，執行下列動作：  


   |                     使用                      |                                                                                                                                                                                                                                                                                                              以進行此動作                                                                                                                                                                                                                                                                                                               |
   |---------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **虛擬目錄加 Web 服務.asmx 檔案** |                                                                                                                 指示由「BizTalk Web 服務發佈精靈」所建立的 .asmx 檔案。<br /><br /> 此訊息的格式類似下列各項：<br /><br /> /PurchaseOrder/POOrchestration.asmx<br /><br /> 其中.asmx 檔案的完整位置是 http://localhost/PurchaseOrder/POOrchestration.asmx 。 **注意：** URI 傳送埠或接收位置不能超過 256 個字元。                                                                                                                 |
   |                **公用位址**                 | 指定此接收位置的完整格式 URI。 此屬性的值是由伺服器名稱與虛擬目錄所組成。 指定的 URI 應指定當訊息傳送至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，所要連接之交易夥伴的公用網站 URL。<br /><br /> 此資訊是選擇性的，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不會使用。 此參數可用來允許管理員記載接收位置所連結的公用 URL。 |
   |              **使用單一登入**               |                                                                                                                                                                                                 指示 SOAP 配接器使用「企業單一登入」。 **注意：** BizTalk Web 服務發佈精靈可讓您使用 SharePoint Portal Server 單一登入; 此屬性僅啟用 「 企業單一登入。                                                                                                                                                                                                 |


6. 按一下 [確定] 。  

7. 在 **接收位置屬性**對話方塊方塊中，輸入適當的值，以完成設定的接收位置，然後按一下 **確定**儲存設定。 如需**接收位置屬性** 對話方塊中，請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。  

   SOAP 接收位置使用的安全性設定值，是在 IIS 中設定。 依照預設，SOAP 接收位置不會設成使用匿名驗證。  

   雖然 SOAP 用戶端會呼叫 Web 服務，但 SOAP 配接器會使用「匿名」、「基本」、「摘要」或「Windows 整合」驗證來驗證 SOAP 用戶端。 若未驗證使用者，使用者內容會傳送至接收處理常式。  

> [!NOTE]
>  任何導致 SOAP 與 HTTP 共用相同程序的 IIS 組態都無效。 每個程序只能有一個隔離的接收器。  

### <a name="to-update-a-virtual-directory-to-use-aspnet-40"></a>若要更新為使用 ASP.NET 4.0 的虛擬目錄  

1.  啟動 Internet Information Services (IIS) Manager。 按一下 **開始**，按一下**所有程式**，然後按一下**Internet Information Services (IIS) 管理員**。  

2.  如果您需要連接遠端 IIS 伺服器，以滑鼠右鍵按一下**Internet Information Services**節點，然後按一下**Connect**。  

3.  如有需要，輸入遠端 IIS 伺服器的電腦名稱和認證。  

4.  展開要更新的網站或虛擬目錄所在之伺服器的伺服器名稱。  

5.  依序展開**站台**。  

6.  依序展開**Default Web Site**。  

7.  展開 [預設的網站]，以檢視網站下方的虛擬目錄。  

8.  以滑鼠右鍵按一下您要更新成使用 ASP.NET 4.0，請按一下虛擬目錄**管理的應用程式**，然後按一下**進階設定**。 **應用程式集區**欄位會顯示所選的虛擬目錄設定應用程式集區。 按一下 [確定] 。  

9. 在 [Internet Information Services (IIS) 管理員] 視窗中，按一下**應用程式集區**。 詳細資料窗格會顯示伺服器上的應用程式集區清單。  

10. 以滑鼠右鍵按一下步驟 8 中設定的應用程式集區，然後按一下**基本設定**。  

11. 在 **編輯應用程式集區**對話方塊方塊中，變更下列：  

    -   **.NET framework 版本**至**4.0**  

    -   **Managed 的管線模式**至**傳統**  

12. 按一下 **確定**以套用變更。  

## <a name="see-also"></a>另請參閱  
 [使用 Web 服務](../core/consuming-web-services.md)