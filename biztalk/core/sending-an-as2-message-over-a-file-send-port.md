---
title: "透過 FILE 傳送埠傳送 AS2 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c5ce9ff-fd73-4d5f-9b16-387c1e520c3a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 555066cb81eabe7328734e73fd9598fbd2cd418a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sending-an-as2-message-over-a-file-send-port"></a>透過 FILE 傳送埠傳送 AS2 訊息
AS2 訊息通常會透過 HTTP 配接器傳送。 然而，如果建立自訂元件，也可以透過 FILE 配接器傳送 AS2 訊息。 本主題說明這類解決方案的運作方式，並提供該解決方案的範例程式碼。  
  
 AS2 訊息透過 HTTP 傳送時，傳送管線內的 AS2 編碼器會在 `HTTP.UserHttpHeaders` 內容屬性中，填入傳送訊息所需的 HTTP (和 AS2) 標頭。 這些標頭可能取自現有的 `HTTP.UserHttpHeaders` 內容屬性、個別的內容屬性，或協議屬性 (依照此優先順序取用)。 傳送埠內的 HTTP 配接器會將標頭寫入訊息，並透過 HTTP 傳送訊息。  
  
 若傳送埠內使用的是 FILE 配接器而不是 HTTP 配接器，則不會將 `HTTP.UserHttpHeaders` 內容屬性內的標頭值寫入訊息。 您必須建立自訂管線元件，以便在訊息前面加上 `HTTP.UserHttpHeaders` 中的標頭。 這樣一來訊息就可以由 FILE 配接器放入資料夾，並成為內含必要 HTTP 標頭的 AS2 訊息。  
  
 您可能也必須建立自訂元件，以確保 `HTTP.UserHttpHeaders` 內容屬性包含全部的 AS2 標頭。 您可建立自訂協調流程或在 AS2Encoder 之前建立自訂管線元件，以設定 AS2 編碼器用來建置 `HTTP.UserHttpHeaders` 的內容屬性。  
  
## <a name="writing-headers-to-an-as2-message"></a>將標頭寫入 AS2 訊息  
 若要使用 FILE 配接器產生 AS2 訊息，而不使用 HTTP 配接器，請在自訂的 AS2 傳送管線中的 AS2 編碼器之後新增自訂管線元件。 在自訂管線元件內加入程式碼，該程式碼會將 `HTTP.UserHttpHeaders` 內容屬性中的標頭寫入訊息。 範例如下列程式碼所示：  
  
```  
public IBaseMessage Execute(IPipelineContext pContext, IBaseMessage pInMsg)  
        {  
            IPipelineContext pipelineContext = pContext;  
            IBaseMessage baseMessage = pInMsg;  
  
            //Prepend Headers  
            MemoryStream ms = new MemoryStream();  
            string strName = "UserHttpHeaders";  
            string strValue = (string)baseMessage.Context.Read(strName,  
              "http://schemas.microsoft.com/BizTalk/2003/  
              http-properties");  
  
            //Leave an empty line between the headers and the body  
            strValue += "\r\n";  
            ms.Write(Encoding.ASCII.GetBytes(strValue), 0,   
               Encoding.ASCII.GetByteCount(strValue));  
  
            //Append Body  
            Stream sr = baseMessage.BodyPart.Data;  
  
            //Read the body of the message and append it to the memory   
              stream containing the headers  
            int size = 1024;  
            byte[] buffer = new byte[size];  
            while (0 != (size = sr.Read(buffer, 0, buffer.Length)))  
            {  
                ms.Write(buffer, 0, size);  
            }  
  
            //Set the body of the message to the new memory stream  
            baseMessage.BodyPart.Data = ms;  
  
            //Rewind the stream  
            ms.Seek(0, SeekOrigin.Begin);  
  
            return baseMessage;  
        }  
```  
  
## <a name="promoting-as2-header-context-properties"></a>升級 AS2 標頭內容屬性  
 您可以使用自訂協調流程或自訂管線元件，將 AS2 標頭屬性升級為訊息內容。  
  
 若要使用自訂管線元件升級 AS2 標頭屬性，請在自訂的 AS2 傳送管線中的 AS2 編碼器之前新增自訂管線元件。 您可以使用上述範例程式碼將 `HTTP.UserHttpHeaders` 中的標頭寫入訊息，但是有一點例外，就是您必須以 Promote 方法取代 Read 方法，提供所要升級之內容屬性的名稱、值和命名空間。  
  
 若要使用自訂協調流程升級 AS2 標頭屬性，請建立具有 FILE 接收埠、「建構訊息」圖形和 FILE 傳送埠的協調流程。 針對「建構訊息」圖形，新增設定含 AS2 標頭升級屬性的程式碼。 您必須在自訂協調流程中新增 `Microsoft.BizTalk.HttpTransport.dll` 的參考。  
  
 HTTP 標頭的命名空間為 `http://schemas.microsoft.com/BizTalk/2003/http-properties` (適用於非 AS2 HTTP 標頭) 與 `http://schemas.microsoft.com/BizTalk/2003/as2-properties` (適用於 AS2 標頭)。  
  
 下列範例程式碼說明如何在協調流程的「建構訊息」圖形中升級 AS2 標頭屬性。 此範例碼升級的是 MDN 的 AS2 標頭。  
  
```  
Message_2=new System.Xml.XmlDocument();  
Message_2=Message_1;  
Message_2(EdiIntAS.IsAS2PayloadMessage)=false;  
Message_2(EdiIntAS.IsAS2AsynchronousMdn)=true;  
Message_2(EdiIntAS.IsAS2MdnResponseMessage)=true;  
Message_2(EdiIntAS.SendMDN)=true;  
Message_2(EdiIntAS.IsAS2MessageSigned)=false;  
Message_2(EdiIntAS.AS2To)="Party1";  
Message_2(EdiIntAS.AS2From)="Home";  
Message_2(EdiIntAS.MessageId)="123456";  
Message_2(EdiIntAS.OriginalMessageId)="2123456";  
Message_2(HTTP.UserHttpHeaders)="Message1-Id: xyz\r\nMyHeader: MyValue";  
```  
  
## <a name="see-also"></a>另請參閱  
 [開發和設定 BizTalk Server AS2 解決方案](../core/developing-and-configuring-biztalk-server-as2-solutions.md)