---
title: 表示為 XLANGMessage 的訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aadca870-2f93-4be3-8733-a0cd3815add7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62c5b4b192602896d0cfe301834844b4b7cab12b
ms.sourcegitcommit: c3070a7a3f332857357f056dc632829b43869c17
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2018
ms.locfileid: "51630323"
---
# <a name="messages-represented-as-xlangmessage"></a>表示為 XLANGMessage 的訊息
**XLANGMessage**物件代表以 XLANG 服務宣告的訊息執行個體。 這個物件的取得方式，是在方法引動過程中將訊息的參考傳遞為參數。 **XLANGPart**物件都代表在 XLANG 服務中的訊息執行個體中所包含的訊息部分。 此物件取自藉由傳遞部分參考中的方法引動過程，其中的接收參數類型**XLANGPart**或傳遞的參考上列舉**XLANGMessage**。  
  
 協調流程訊息變數，可能會傳遞給使用者元件，並以接收**XLANGMessage**物件。 **XLANGMessage**物件可用來存取部分和存取訊息屬性。使用者可能會 「 保留 」 **XLANGMessage** ，進而擴充到宣告的範圍超過其生命週期。 接著， **XLANGMessage**可能從方法傳回並指派給協調流程中的訊息變數。  
  
## <a name="constructing-an-xlangmessage"></a>建構 XLANGMessage  
 在建構時**XLANGMessage**使用的資料流的資料流類型必須實作**IStreamFactory**也**MemoryStream**。 下列程式碼範例示範如何建構**XLANGMessage**:  
  
```csharp
public class FileStreamFactory : IStreamFactory  
{  
    string _fname;  
  
    public FileStreamFactory(string fname)  
    {  
        _fname = fname;  
    }  
  
    public Stream CreateStream()  
    {  
        return new FileStream  
        (  
            _fname,  
            FileMode.Open,  
            FileAccess.Read,  
            FileShare.Read  
        );  
    }  
}  
  
public static void AssignStreamFactoryToPart(XLANGMessage msg)  
{  
    IStreamFactory sf = new FileStreamFactory( @”c:\data.xml” );  
    msg[0].LoadFrom( sf );  
}  
```  
  
 您有時可能會想要建立新的訊息，而不要轉換來源訊息。 您可以使用類型的變數**System.Xml.XmlDocument**和載入或否則建構適當的內容。 在下列範例中，XML 從字串使用載入**LoadXml**方法**XmlDocument**:  
  
```csharp
XmlVariable.LoadXml("<ns0:Root PONumber="047745351122111" xmlns:ns0="http://BTSHTTPSend.SimpleSchema"><MyChildRecord SubAttr1="Simple Attribute " /></ns0:Root>");  
XLANGMessage XmlMsg = XmlVariable;  
  
```  
  
 下列範例從檔案載入 XML，利用**負載**方法**XmlDocument**:  
  
```csharp
XmlVariable.Load("C:\MyData.xml");  
XLANGMessage XmlMsg = XmlVariable;  
  
```  
  
> [!NOTE]
>  如果您想要建構更大的訊息，使用其中一種資料流上一節中所示範的方法，或考慮使用**轉換**協調流程設計師中的圖形。  
  
## <a name="considerations-when-using-xlangmessage-and-xlangpart"></a>使用 XLANGMessage 和 XLANGPart 時的考量  
 使用時**XLANGMessage**並**XLANGPart**在使用者程式碼，請考慮下列：  
  
-   請勿將傳遞做為訊息部分**XLANGPart**引數或傳回型別的值**XLANGPart**。 您應傳入**XLANGPart**做為組件的類型。 例如：  
  
    ```csharp
    Message String msg;  
    Class.Test(msg);  
    // or you can do the following  
    Messagetype mt  
    {  
         String part;  
    };  
    Message mt msg;  
    Class.Test(msg,part);  
  
    ```  
  
     您也可以傳遞訊息本身做**XLANGMessage**並用**XLANGMessage**註標運算子來存取函式呼叫的部分。 不過，您不應該放置**XLANGPart**存留期會延伸超過函式呼叫的存留期集合中。 相反地，您應該在其中放置**XLANGMessage**集合中。 例如：  
  
    ```csharp
    Void Test(XLANGMessage xlm)  
    {  
         try  
         {  
          XLANGPart xlp = xlm[0];  
          String sval = (String) xlp.RetrieveAs(typeof(string));  
         }  
         finally  
         {  
          Xlm.Dispose();  
         }  
    }  
    ```  
  
-   不會定義為協調流程參數**XLANGMessage**或是**XLANGPart**。 如果您要傳遞訊息，請使用訊息類型參數來傳遞訊息。 如果您要傳遞某個部分，請改為傳遞訊息，然後再使用此部分。 如果您只想要此部分值，請使用此部分類型來傳遞此部分。  
  
-   不會傳回**XLANGMessage**方法呼叫的參數。 如果您傳回**XLANGMessage**無法呼叫，會傳入的參數，然後**處置**方法上方法呼叫內的參數，它會直覺式地違反存留期間的假設，而且也擲回例外狀況。 傳遞到訊息時**XLANGMessage**參數加入使用者程式碼，參考的特殊的內容，通常不會具有訊息參考訊息。 此內容的存留期間就是協調流程執行個體的存留期間。 這是因為 BizTalk Server 並不知道使用者程式碼是否會保留此訊息。  
  
     當協調流程執行個體結束時，該執行個體中建立的任何訊息便不再有效，所以這類集合的存留期間應該小於或等於此執行個體的存留期間。 不過，如果您想要透過傳遞訊息時，釋放迴圈中的訊息參考**XLANGMessage**有相同的存留期，與協調流程執行個體，則您可以呼叫的引數**XLANGMessage.Dispose**以釋出的參考。 此外，如果在使用者程式碼方法中， **XLANGMessage**只有在本機使用參數和參數的存留期包含在函式呼叫中，您也可以呼叫**XLANGMessage.Dispose**釋出根內容的參考，並回到正常的存留期間行為讓對應的訊息。 例如：  
  
    ```csharp
    void Test(XLANGMessage xlm)  
    {  
         try  
         {  
          //XLANGMessage is only used locally  
         }  
         finally  
         {  
          xlm.Dispose();  
         }  
    }  
    ```  
  
     如果您在集合中，放置此 xlm，則必須有類別本身**處置**方法來進行清除。 例如：  
  
    ```csharp
    Public class A  
    {  
         Hashtable h = new Hashtable();  
         Public Test(XLANGMessage xlm)  
         {  
          h[xlm] = 1;  
         }  
         //You can have more methods here  
         Public Dispose()  
         {  
          foreach (XLANGMessage xlm in h.Keys)  
           Xlm.Dispose();  
         }  
    }  
    ```  
  
     您可以呼叫**xlangmessages**當您已完成的集合**A.dispose**。  
  
## <a name="see-also"></a>另請參閱  
 [表示為 XSD 結構描述的訊息](../core/messages-represented-as-xsd-schemas.md)   
 [表示為.NET 類別的訊息](../core/messages-represented-as-net-classes.md)   
 [在使用者程式碼中建構訊息](../core/constructing-messages-in-user-code.md)
