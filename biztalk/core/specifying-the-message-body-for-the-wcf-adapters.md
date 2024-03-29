---
title: 指定 WCF 配接器的訊息內文 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF adapters, SOAP messages
- messages, WCF adapters
- WCF adapters, message bodies
- SOAP messages, WCF adapters
ms.assetid: b20364b7-0365-4636-b4d6-bde9c69b8dcb
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32e62da213c4fceaf54773c2fe44584f43de9155
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972138"
---
# <a name="specifying-the-message-body-for-the-wcf-adapters"></a>指定 WCF 配接器的訊息內文
您可以使用**訊息**索引標籤中，指定如何將 BizTalk 訊息內文取自內送的 SOAP 訊息，則 WCF 配接器，而 BizTalk 訊息內文的方式放在為傳出 SOAP 訊息。  

## <a name="specifying-how-the-biztalk-message-body-is-extracted-from-an-incoming-soap-message"></a>指定如何從內送 SOAP 訊息擷取 BizTalk 訊息內文  
 您可以控制如何從透過 WCF 配接器內送的 SOAP 訊息建立輸入 BizTalk 訊息內文。 下圖顯示**訊息**索引標籤的 Wcf-netnamedpipe 接收配接器和傳送配接器做為範例。  

 ![[訊息] 索引標籤，在 WCF 接收配接器](../core/media/abbaccfc-092c-42c6-9207-fa1af28912ac.gif "abbaccfc-092c-42c6-9207-fa1af28912ac")  

 ![[訊息] 索引標籤，在 WCF 傳送配接器](../core/media/58e1d490-5bd9-4571-87b1-4dea6dbfe2de.gif "58e1d490-5bd9-4571-87b1-4dea6dbfe2de")  

 若要指定如何建立 BizTalk 訊息內文，選取下列選項之一**輸入 BizTalk 訊息內文**在上圖中的區段：  

- **信封--整個\<: Envelope>\>**。 使用 SOAP**信封**內送訊息建立 BizTalk 訊息內文部分的項目。 整個內送訊息會變成 BizTalk 訊息內文。 您可以使用這個選項，建立合併所有標頭的 BizTalk 訊息內文。  

  > [!NOTE]
  >  SOAP 標頭會放置在訊息內容中，但不會自動升級。 在自訂管線元件中可進行升級。  

- **內文--內容\<soap: Body&gt\>項目**。 使用內容的 SOAP**主體**內送訊息建立 BizTalk 訊息內文部分的項目。 如果 **Body** 元素有一個以上的子元素，則只有第一個元素會成為 BizTalk 訊息內文部分。  

- **路徑--內容由內文路徑放**。 使用中的內文路徑運算式**內文路徑運算式**文字方塊中，建立 BizTalk 訊息內文部分。 內文路徑運算式會依照內送訊息 SOAP **Body** 元素的直系子元素來進行評估。 當內送訊息有二進位資料時，您可以使用這個選項，讓 BizTalk 訊息內文部分只包含二進位資料，沒有任何標籤。  

  當**路徑--內容由內文路徑定位**選取選項，則**節點編碼**屬性可以設定來指定預期的編碼類型的內文路徑運算式所指定的節點**內文路徑運算式**文字方塊。 如果內文路徑運算式有一個以上相符的項目，只會使用第一個相符項目。  

> [!NOTE]
>  針對**內文路徑運算式**屬性，僅支援適用於順向處理 XML 的運算式的 XPath。 適用於此屬性的 XPath 運算式的詳細資訊，請參閱 「 最佳的兩個世界:: 結合 XPath 與 XmlReader 」，網址[ http://go.microsoft.com/fwlink/?LinkID=75701 ](http://go.microsoft.com/fwlink/?LinkID=75701)。  

 如果**路徑--內容由內文路徑定位**選項並**節點編碼**屬性設定為**字串**，WCF 配接器預期相符的節點有 utf-8編碼字元資料。 如果內送訊息包含逸出 XML 特殊字元的字元資料這類\<和\>，WCF 配接器建立 BizTalk 訊息內文部分時，請還原逸出的字元資料。 例如，如果相符的節點有逸出字元資料這類**&lt;FirstName&gt;CONTOSO&lt;/FirstName&gt;** WCF 配接器建立**\<FirstName\>CONTOSO\</FirstName\>** 中輸入 BizTalk 訊息內文。  

 如果**路徑--內容由內文路徑定位**選項並**節點編碼**屬性設定為**Hex**或**Base64**，相符的節點可以擁有有效**BinHex**或是**Base64**順序。 如果相符的節點有無效序列，WCF 用戶端會收到**FaultException**、 BizTalk Server 電腦上，事件記錄檔會記錄一則錯誤訊息，並不會擱置訊息。  

 如果**路徑--內容由內文路徑定位**選項並**節點編碼**屬性設定為**XML**，WCF 配接器建立 BizTalk 訊息內文與中的內文路徑運算式所選取之節點外部 XML**內文路徑運算式**文字方塊。  

 如果相符的節點沒有編碼形式的資料中的指定**節點編碼**屬性，建立空白的輸入的 BizTalk 訊息內文。  

 例如，假設 WCF 傳送配接器從 WCF 用戶端接收下列 SOAP 訊息：  

```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/OrderRefresh</a:Action>   
    <a:MessageID>urn:uuid:59e74507-66d0-4d50-be70-c3ec248b6f78</a:MessageID>   
    <a:ReplyTo>  
       <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>   
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessServiceBizTalk</a:To>   
  </s:Header>  
  <s:Body>  
    <Order xmlns="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
     <OrderDetail>  
       <CustomerID>CONTOSO</CustomerID>   
       <OrderID>00000000</OrderID>   
     </OrderDetail>  
    </Order>  
  </s:Body>  
</s:Envelope>  
```  

 如果您設定**輸入 BizTalk 訊息內文**下表中，先前的內送 SOAP 訊息中所示的區段會變成輸入的 BizTalk 訊息內文部分。  

|輸入 BizTalk 訊息內文|[內文路徑運算式]|節點編碼|  
|----------------------------------|--------------------------|-------------------|  
|**信封--整個\<: Envelope>\>**|不適用|不適用|  

 如果您設定**BizTalk 訊息內文**一節下表所示，WCF 配接器會建立輸入的 BizTalk 訊息內文部分使其只包含**順序**在上一個項目內送 SOAP 訊息。  

|輸入 BizTalk 訊息內文|[內文路徑運算式]|節點編碼|  
|----------------------------------|--------------------------|-------------------|  
|**內文--內容\<soap: Body&gt\>項目**|不適用|不適用|  

 如果您設定**BizTalk 訊息內文** 區段下表所示，WCF 配接器會預期內文路徑運算式相符的連入節點將有 utf-8 編碼字元資料。  

|輸入 BizTalk 訊息內文|[內文路徑運算式]|節點編碼|  
|----------------------------------|--------------------------|-------------------|  
|**路徑--內容由內文路徑定位**|/ * [local-name = 'Order'] /\*[local-name = 'OrderDetail'] /\*[local-name = 'CustomerID']|**String**|  

 如上面的內送 SOAP 訊息，WCF 配接器使用的字元資料**CONTOSO**的**CustomerID**元素，來建立輸入的 BizTalk 訊息內文部分。  

> [!NOTE]
>  您無法使用 XPath 縮寫的語法 **/Order/OrderDetail/CustomerID**，如上面的內送 SOAP 訊息。 這是因為 XPath 縮寫的語法會傳回未宣告的命名空間中的節點並**CustomerID**上面的 SOAP 訊息中的項目中宣告**http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess**命名空間預設命名空間。  

 如果您設定**BizTalk 訊息內文**區段下表所示**CustomID**上面的內送 SOAP 訊息中的項目應具有有效**BinHex**或是**Base64**順序。  

|輸入 BizTalk 訊息內文|[內文路徑運算式]|節點編碼|  
|----------------------------------|--------------------------|-------------------|  
|**路徑--內容由內文路徑定位**|/ * [local-name = 'Order'] /\*[local-name = 'OrderDetail'] /\*[local-name = 'CustomerID']|**Hex**或**Base64**|  

 如果您設定**BizTalk 訊息內文** 區段下表所示，WCF 配接器建立輸入的 BizTalk 訊息內文，如上面的內送 SOAP 訊息中所示的程式碼表格之後。  

|輸入 BizTalk 訊息內文|[內文路徑運算式]|節點編碼|  
|----------------------------------|--------------------------|-------------------|  
|**路徑--內容由內文路徑定位**|/ * [local-name = 'Order'] /\*[local-name = 'OrderDetail'] /\*[local-name = 'CustomerID']|**XML**|  

```  
<CustomerID xmlns="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">CONTOSO</CustomerID>   
```  

## <a name="specifying-the-source-of-the-outbound-wcf-message-body"></a>指定輸出 WCF 訊息內文的來源  
 您可以控制如何從 BizTalk 訊息內文建立輸出 WCF 訊息內文，以透過 WCF 配接器傳送。 若要指定 BizTalk 訊息內文放置在 輸出 WCF 訊息內文的方式，您可以使用下列選項之一**輸出 WCF 訊息內文**區段**訊息**索引標籤中所示上一節中的數字：  

- **內文--BizTalk 回應訊息內文**。 使用 BizTalk 訊息內文部分建立的內容的 soap**主體**外寄訊息的項目。 外寄 BizTalk 訊息內文會變成輸出 SOAP 訊息的內文。  

- **範本--內容由範本指定**。 使用中提供的範本**XML**文字方塊中，若要建立內容的 SOAP**主體**外寄訊息的項目。 使用 WCF 配接器**內文--BizTalk 回應訊息內文**（預設值） 選項不允許傳送非 XML 訊息，例如字元資料和點陣圖影像。 您可以使用**範本--由範本指定的內容**選項，WCF 配接器傳送非 XML 訊息編碼**base64**，**十六進位**，或**字串**.  

  當**範本--由範本指定的內容**選項，您必須提供任意範本 XML 項目中的**輸出 WCF 訊息內文-XML**文字方塊。 範本 XML 項目必須包含下列**bts 訊息主體**唯一的一次的項目除非範本 XML 項目保留為空白：  

```  
<bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2010" encoding="[base64|hex|string|xml]"/>  
```  

 WCF 配接器編碼 BizTalk 訊息內文，根據**編碼**屬性中的 XML 範本，並取代**bts 訊息主體**編碼 BizTalk 訊息內文建立時的項目輸出 WCF 訊息。 如果**輸出 WCF 訊息內文-XML**文字方塊留為空白，則 WCF 配接器編碼 BizTalk 訊息內文中的**Base64**，然後將放置**Base64**中序列輸出的 SOAP 訊息內文。  

 如果**編碼**XML 範本中的屬性設定為**字串**，WCF 配接器會將 BizTalk 訊息內文部分編碼為 utf-8 編碼字元資料，在其中 XML 特殊字元，如\<和\>會逸出。  

 如果**編碼**XML 範本中的屬性設定為**base64**或是**十六進位**，WCF 配接器編碼 BizTalk 訊息內文部分，做為**BinHex**或是**Base64**順序。  

 如果**編碼**XML 範本中的屬性設定為**xml**，則 WCF 配接器取代**bts 訊息主體**輸出 BizTalk 訊息內文，若要建立的項目外寄 WCF 訊息。  

 例如，假設 WCF 配接器必須將下列 BizTalk 訊息內文部分傳送至 WCF 用戶端：  

```  
<ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
  <ns0:OrderDetail>  
    <ns0:CustomerID>CONTOSO</ns0:CustomerID>  
    <ns0:OrderID>01A2c</ns0:OrderID>  
  </ns0:OrderDetail>  
</ns0:Order>  
```  

 如果您設定**輸出 WCF 訊息內文**一節中所示的程式碼的資料表之後，WCF 配接器下表所示，建立輸出 WCF 訊息。  

|輸出 WCF 訊息內文|XML|  
|-------------------------------|---------|  
|**內文--BizTalk 回應訊息內文**|不適用|  

```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/Request</a:Action>  
    <a:MessageID>urn:uuid:6a706a54-c4f5-4767-909d-a992c7c26dba</a:MessageID>  
    <a:ReplyTo>  
<a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessService</a:To>  
  </s:Header>  
  <s:Body>  
    <ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
  <ns0:OrderDetail>  
    <ns0:CustomerID>CONTOSO</ns0:CustomerID>  
    <ns0:OrderID>01A2c</ns0:OrderID>  
  </ns0:OrderDetail>  
</ns0:Order>  
  </s:Body>  
</s:Envelope>  
```  

 如果您設定**輸出 WCF 訊息內文**一節中所示的程式碼的資料表之後，WCF 配接器下表所示，建立輸出 WCF 訊息。  


|         輸出 WCF 訊息內文         |                                                                    XML                                                                    |
|-------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| **內文--BizTalk 回應訊息內文** | \<活頁簿\><br /><br /> \<**bts-msg-body** xmlns="<http://www.microsoft.com/schemas/bts2010>" encoding="**string**"/\><br /><br /> \</Book\> |

```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/Request</a:Action>  
    <a:MessageID>urn:uuid:05dde292-eedd-467e-b0d2-f1b8f0757410</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessService</a:To>  
  </s:Header>  
  <s:Body>  
    <Book><ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  <ns0:OrderDetail>    <ns0:CustomerID>CONTOSO</ns0:CustomerID>    <ns0:OrderID> 01A2c</ns0:OrderID>  </ns0:OrderDetail></ns0:Order>  
    </Book>  
  </s:Body>  
</s:Envelope>  
```  

 如果您設定**輸出 WCF 訊息內文**一節中所示的程式碼的資料表之後，WCF 配接器下表所示，建立輸出 WCF 訊息。  


|         輸出 WCF 訊息內文         |                                                                    XML                                                                    |
|-------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| **內文--BizTalk 回應訊息內文** | \<活頁簿\><br /><br /> \<**bts-msg-body** xmlns="<http://www.microsoft.com/schemas/bts2010>" encoding="**base64**"/\><br /><br /> \</Book\> |

```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://ww  
w.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe  
/OrderProcess/IOrderProcess/Request</a:Action>  
    <a:MessageID>urn:uuid:cb3cac6d-a542-4a90-bad8-cdbfa8251112</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessSer  
vice</a:To>  
  </s:Header>  
  <s:Body>  
    <Book>77u/PG5zMDpPcmRlciB4bWxuczpuczA9Imh0dHA6Ly9NaWNyb3NvZnQuU2FtcGxlcy5CaX  
pUYWxrLk5ldE5hbWVkUGlwZS9PcmRlclByb2Nlc3MiPg0KICA8bnMwOk9yZGVyRGV0YWlsPg0KICAgID  
xuczA6Q3VzdG9tZXJJRD5DT05UT1NPPC9uczA6Q3VzdG9tZXJJRD4NCiAgICA8bnMwOk9yZGVySUQ+MD  
FBMmM8L25zMDpPcmRlcklEPg0KICA8L25zMDpPcmRlckRldGFpbD4NCjwvbnMwOk9yZGVyPg==</Book  
>  
  </s:Body>  
</s:Envelope>  
```  

 如果您設定**輸出 WCF 訊息內文**一節中所示的程式碼的資料表之後，WCF 配接器下表所示，建立輸出 WCF 訊息。  


|         輸出 WCF 訊息內文         |                                                                  XML                                                                   |
|-------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| **內文--BizTalk 回應訊息內文** | \<活頁簿\><br /><br /> \<**bts-msg-body** xmlns="<http://www.microsoft.com/schemas/bts2010>" encoding="**xml**"/\><br /><br /> \</Book\> |

```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess/IOrderProcess/Request</a:A  
ction>  
    <a:MessageID>{513C123C-0600-4A1C-BEE2-EF83E0EFEB15}</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
    </a:ReplyTo>  
    <a:To s:mustUnderstand="1">net.pipe://mycomputer/NetNamedPipeOrderProcessServiceBizTalk</a:To>  
  </s:Header>  
  <s:Body>  
    <Book>  
      <ns0:Order xmlns:ns0="http://Microsoft.Samples.BizTalk.NetNamedPipe/OrderProcess">  
  <ns0:OrderDetail>  
    <ns0:CustomerID>CustomerID_0</ns0:CustomerID>  
    <ns0:OrderID>OrderID_0</ns0:OrderID>  
  </ns0:OrderDetail>  
</ns0:Order>  
    </Book>  
  </s:Body>  
</s:Envelope>  
```