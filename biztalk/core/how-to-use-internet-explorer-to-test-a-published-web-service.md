---
title: 測試 BizTalk web 服務 |Microsoft Docs
description: 設定接收位置以及要在 web 瀏覽器中測試 BizTalk web 服務的 web.config
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4dc2171d-4abe-43db-b4bc-e484048c6430
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbf7e57d163b5729685c4103a8a3e5da78e37355
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979687"
---
# <a name="test-a-biztalk-web-service"></a>測試 BizTalk Web 服務

## <a name="overview"></a>概觀
您不需要撰寫 Web 用戶端應用程式，就可以測試已發佈的 Web 服務。 您可以使用如 Internet Explorer 這類 Web 瀏覽器來測試已發佈的 Web 服務。 雖然您可以使用 Web 瀏覽器來存取任何已發佈的 Web 服務，但只能測試擁有包含簡單型別參數之 Web 方法的 Web 服務。 若要在網頁瀏覽器測試 Web 方法，您會在接收埠的要求和回應訊息的訊息部分只能是簡單型別，例如**System.String**或是**System.Int32**。 如果任何訊息部分使用結構描述做為訊息類型，就不能使用瀏覽器測試 Web 方法。  
  
 如果您要使用 HTTP-GET 或 HTTP-POST 測試已發佈的 Web 服務，則必須設定 SOAP 配接器的 BizTalk 接收位置，並修改已發佈之 Web 服務的 Web.config 檔案。  
  
 **修改接收位置**  
  
 當 SOAP 配接器設定接收位置時，SOAP 配接器一般會指定虛擬目錄和 Web 服務的 .asmx 檔案名稱，來設定接收位置的 URI：  
  
```  
/PurchaseOrder/POOrchestration.asmx  
```  
  
 這可讓 SOAP 配接器使用 HTTP-SOAP 通訊協定接收 Web 服務要求。 若要設定接收位置使用 HTTP-GET 或 HTTP-POST 通訊協定，您必須將方法名稱附加到 URI：  
  
```  
/PurchaseOrder/POOrchestration.asmx/Operation_1  
```  
  
 方法名稱與協調流程中的連接埠作業名稱相同。  
  
 **修改 Web.config 檔案**  
  
 根據預設，精靈會設定 Web 服務使用 HTTP-SOAP 通訊協定。 HTTP-GET 和 HTTP-POST 則會明確停用。 若要使用 Web 瀏覽器測試 Web 服務，您必須啟用 HTTP-GET。  
  
## <a name="update-the-webconfig"></a>更新 Web.config
  
1. 開啟已發佈之 Web 服務的 Web.config 檔案。  
  
   > [!NOTE]
   >  您可以在設成 IIS 虛擬根目錄來包含 Web 服務的目錄中找到 Web.config 檔案。  
  
2. 尋找\<通訊協定\>區段：  
  
   ```  
   <webServices>  
      <protocols>  
        <remove name="HttpPost" />  
        <remove name="HttpGet" />  
        <remove name="HttpPostLocalhost" />  
      </protocols>  
  
   </webServices>  
   ```  
  
3. 測試 HTTP-GET、 HTTP-POST 或從本機電腦的 HTTP-POST 移除對應的行從\<通訊協定\>一節。  
  
   如需詳細的組態選項的詳細資訊，請參閱[XML Web 服務使用 ASP.NET 建立的組態選項](https://msdn.microsoft.com/library/b2c0ew36.aspx)。 
  
#### <a name="access-a-web-service-with-internet-explorer"></a>存取與 Internet Explorer 的 Web 服務  
  
- 在 Internet Explorer 中**地址**方塊中，輸入使用的格式為 Web 服務 URL **http://<em>servername</em>/*apppath* /*webservicename*.asmx**。  
  
  |參數|ReplTest1|  
  |---------------|-----------|  
  |***servername***|您已部署 XML Web Service 之伺服器的名稱。|  
  |***apppath***|虛擬目錄的名稱和 Web 應用程式路徑。|  
  |***webservicename.asmx***|XML Web Service .asmx 檔案的名稱。|  
  
  Web 服務的描述會顯示該特定 Web 服務支援的所有 Web 服務方法。 Web 服務描述頁面包含每個可用的 Web 方法和 Web 服務的服務描述的連結。  
  
#### <a name="test-a-web-service-with-internet-explorer-using-http-get"></a>使用 Internet Explorer 使用 HTTP-GET 測試 Web 服務  
  
1.  存取 Web 服務描述頁面之後，按一下 Web 服務描述頁面中所列的其中一個 Web 方法。  
  
2.  輸入 Web 方法，針對必要的參數，然後按一下**Invoke**。  
  
3.  伺服器會將 XML 回應傳回瀏覽器。 如果 Web 服務的傳回資料型別是雙精度浮點數，結果可能看起來如下：  
  
    ```  
    <?xml version="1.0" ?>  
    <double>74.5</double>  
    ```  
  
#### <a name="test-a-web-service-with-internet-explorer-using-http-get-alternate-method"></a>使用 Internet Explorer HTTP-GET （替代方法） 和測試 Web 服務  
  
1.  在 Internet Explorer 中**地址**方塊中，輸入使用的格式為 Web 服務 URL ***http://servername/vdir/webservicename.asmx/Methodname?parameter=value***。  
  
    |參數|ReplTest1|  
    |---------------|-----------|  
    |***servername***|您已部署 XML Web Service 之伺服器的名稱。|  
    |***apppath***|虛擬目錄的名稱和 Web 應用程式路徑。|  
    |***webservicename.asmx***|XML Web Service .asmx 檔案的名稱。|  
    |***方法名稱***|XML Web Service 公開的公用方法名稱。 若將它留白，XML Web Service 的描述頁面將會出現，並列出 .asmx 檔案中可用的每個公用方法 (選擇性)|  
    |***parameter***|您的方法所需之任何參數的適當參數名稱和值。 若將它留白，XML Web Service 的描述頁面將會出現，並列出 .asmx 檔案中可用的每個公用方法 (選擇性)|  
  
    > [!NOTE]
    >  此語法中的 XML Web Service 方法名稱區分大小寫，但伺服器、專案和 XML Web Service 名稱則不區分大小寫。  
  
2.  按 Enter 鍵。 Web 瀏覽器會顯示伺服器傳回的 XML 回應。  
  
    > [!NOTE]
    >  您也可以使用 HTTP-POST 來呼叫 Web 服務。 資訊和從網頁瀏覽器呼叫 XML Web service 的詳細範例，請參閱[從瀏覽器存取 XML Web Service](https://msdn.microsoft.com/library/45fez2a8.aspx)。  
  
## <a name="see-also"></a>另請參閱  
 [測試已發佈的 Web 服務](../core/testing-published-web-services.md)