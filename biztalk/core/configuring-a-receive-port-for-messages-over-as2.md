---
title: 設定透過 AS2 接收訊息的連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01d4d897-d12b-4de4-a86b-e6d2718470c2
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 324d8a7faf3ce21630502f219d033fb797aa3fc6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968988"
---
# <a name="configuring-a-receive-port-for-messages-over-as2"></a>設定透過 AS2 接收訊息的接收埠
若要接收含有 EDI 或非 EDI 內容的 AS2 訊息，請建立 HTTP 接收埠，以便接收此訊息並將回應傳回給合作對象。  
  
 如果此 MDN 將以同步方式傳回，接收埠就必須是雙向要求-回應接收埠。 接收埠中的接收位置將會接收 AS2 訊息，而與雙向接收埠相關聯的傳送埠則會傳送同步 MDN。  
  
 如果此 MDN 將以非同步方式傳回，接收埠就可以是單向接收埠，因為此 MDN 必須透過個別的動態傳送埠傳回。 接收埠將會傳回 HTTP 回應，不論它是單向或雙向連接埠都一樣。 如果您設定了雙向接收埠來接收 AS2 訊息，而傳回非同步 MDN，HTTP 回應將透過雙向接收位置的傳送埠傳回。  
  
> [!NOTE]
>  用來接收 AS2 訊息的雙向接收埠不應該用來接收 MDN 訊息。 MDN 訊息應該透過靜態單向接收埠接收。 針對 MDN 使用要求/回應接收埠會讓 200OK 訊息無法在回應內送 MDN 時傳回，因而導致系統不必要地重試 MDN 傳輸作業。  
  
 請使用下列組態來建立接收埠：  
  
|位置|屬性|設定|  
|--------------|--------------|-------------|  
|**接收埠屬性： 一般**|連接埠類型|要求-回應|  
|**接收位置屬性： 一般**|傳輸類型|HTTP**附註：** 只有 HTTP 配接器可以用於傳輸 EDIINT/AS2 編碼訊息。 這種傳輸無法搭配 HTTP 配接器以外的配接器運作。|  
|**接收位置屬性： 一般**|接收處理常式|BizTalkServerIsolatedHost|  
|**接收位置屬性： 一般**|接收管線|-AS2EdiReceive (如果內容是 EDI 編碼)<br />-AS2Receive （如果內容不是 EDI 編碼）**附註：** 當使用 AS2EdiReceive 管線，您必須新增至 BizTalk 應用程式使用者群組執行 BizTalk 外掛式主控件執行個體處理序的使用者帳戶。 AS2EdiReceive 管線會在 BizTalk 外掛式主控件執行個體處理序中執行。 AS2EdiReceive 管線會存取 SSO 存放區，而此存放區會要求使用者必須是「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式使用者」群組中的成員。|  
|**接收位置屬性： 一般**|傳送管線|AS2Send|  
|**HTTP 傳輸屬性**|虛擬目錄加 ISAPI 延伸模組|/\<虛擬目錄名稱\>/BTSHTTPReceive.dll|  
|**HTTP 傳輸屬性**|要求-回應傳回內容類型|text/xml|  
  
## <a name="functionality-of-the-receive-location-in-synchronous-and-asynchronous-modes"></a>接收位置在同步與非同步模式中的功能  
 雙向接收埠會進行下列作業來接收並處理 EDI/AS2 訊息，以及傳回回應：  
  
-   透過 HTTP 接收 AS2 訊息。  
  
-   使用 AS2EDIReceive 接收管線 (針對 EDI 編碼訊息) 或 AS2Receive 接收管線 (針對不是以 EDI 編碼的訊息) 來處理 AS2 訊息。 如需這個程序的詳細資訊，請參閱[處理內送 AS2 訊息](../core/processing-an-incoming-as2-message.md)。  
  
-   針對接收的訊息設定下列內容屬性：  
  
    -   `IsAS2PayloadMessage == True` (因為它是內容訊息)  
  
    -   `IsEmptyMDNResponse == False` (因為它不是空的 MDN)  
  
-   如果此訊息是 EDI 編碼，請解譯 EDI 檔案、產生 XML 檔案，然後將它們放置在 MessageBox 中。 針對每個 XML 檔案，將 `BTS.MessageType` 的內容屬性設定為含有命名空間的結構描述名稱。  
  
-   如果此訊息不是 EDI 編碼，請以原生格式將訊息放置在 MessageBox 中。  
  
-   使用 AS2EdiReceive 接收管線來產生 MDN 檔案 (如果啟用的話)。 如需這個程序的詳細資訊，請參閱[產生外寄 MDN](../core/generating-an-outgoing-mdn.md)。 針對此訊息設定下列內容屬性：  
  
    -   `EdiIntAS.IsAS2AsynchronousMdn == False` (如果處於同步模式下)  
  
    -   `EdiIntAS.IsAS2AsynchronousMdn== True` (如果處於非同步模式下)  
  
-   如果處於同步模式下，請使用 AS2Send 傳送管線來傳送 MDN 檔案 (如果啟用的話)。 如需這個程序的詳細資訊，請參閱[傳送外寄 MDN](../core/sending-an-outgoing-mdn.md)。  
  
-   如果處於非同步模式下，請將 MDN 檔案 (如果啟用的話) 路由傳送至 MessageBox (讓個別的動態傳送埠挑選它並傳送它)。  
  
-   如果處於非同步模式下，除了以非同步方式傳回的完整 MDN 以外，請產生空的 MDN。 針對此訊息設定下列內容屬性：  
  
    -   `IsAS2PayloadMessage == False`  
  
    -   `IsEmptyMDNResponse == True`  
  
-   如果處於非同步模式下，請透過接收埠與傳送合作對象之間的 HTTP 連線，將 HTTP 回應傳回給原始傳送者，以便關閉該連線。 因為完整 MDN 不會關閉同步連線，所以這是必要條件。  
  
-   產生通知訊息 (如果啟用的話)，然後將它放置在 MessageBox 中。 將 `BTS.MessageType` 的內容屬性設定為通知控制結構描述。  
  
## <a name="see-also"></a>請參閱  
 [設定 AS2 方案的連接埠](../core/configuring-ports-for-an-as2-solution.md)   
 [處理內送 AS2 訊息](../core/processing-an-incoming-as2-message.md)   
 [產生外寄 MDN](../core/generating-an-outgoing-mdn.md)   
 [傳送外寄 MDN](../core/sending-an-outgoing-mdn.md)