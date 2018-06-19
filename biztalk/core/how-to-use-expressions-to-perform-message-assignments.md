---
title: 如何使用運算式執行訊息指派 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, distinquished fields
- orchestrations, expressions
- messages, manipulating
- messages, assigning messages
- messages, expressions
- messages, message parts
- orchestrations, messages
- messages, components
ms.assetid: 9989caf5-012c-4fc4-b5d8-981ca9a69f43
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f423e1b797cfff95bae1d9b1dd862d28210cd26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256742"
---
# <a name="how-to-use-expressions-to-perform-message-assignments"></a>如何使用運算式執行訊息指派
您可使用運算式在協調流程中以各種方式處理訊息。  
  
## <a name="referring-to-message-fields"></a>指稱訊息欄位  
 您可將欄位名稱附加至訊息名稱，來指稱訊息中的不同欄位，方法如下：  
  
```  
MyMsg.Amount  
```  
  
 在此範例中，MyMsg 是訊息，Amount 是已被識別為 MyMsg 所依據之訊息類型的辨別欄位。  
  
## <a name="assigning-to-messages-and-message-parts"></a>指派至訊息和訊息部分  
 您可以將訊息直接指派至另一訊息，或將訊息部分直接指派至另一個訊息部分：  
  
```  
MyMsg=IncomingMsg;  
MyMsg.Invoice=IncomingMsg.Invoice;  
```  
  
 在此範例中，Invoice 是以結構描述為依據的訊息部分。  
  
 若您想修改已建構的訊息 (例如已接收之訊息) 之屬性，您必須在 [建構訊息] 圖形中，將第一個訊息指派至第二個訊息來建構新訊息，然後在相同的 [建構訊息] 圖形內修改新訊息的屬性。  
  
> [!NOTE]
>  您不能對訊息欄位進行指稱或指派 (例如 MyMsg.Invoice.MyField)，除非這些訊息欄位已經升級；您只能對整個訊息、訊息部分、升級的訊息屬性或辨別欄位進行指稱或指派。  
  
## <a name="adding-message-parts"></a>新增訊息部分  
 您可以將其他組件加入現有的 multipart 訊息使用**XLANGs.BaseTypes.XLANGMessage.AddPart**方法。 若要這樣做，請執行以下動作：  
  
-   建立 C# 專案，並將參考加入**Microsoft.XLANGs.BaseTypes**。  
  
-   實作類似於以下的公用類別：  
  
    ```  
    public class MyAddPartHelper  
    {  
         public static void AddPart(XLANGMessage msg, object part, String partName)  
         {  
              msg.AddPart(part, partName);  
         }  
    }  
    ```  
  
     有三個多載的方法，如**Microsoft.XLANGs.BaseTypes.AddPart**:  
  
    ```  
    public void AddPart(object part, String partName);  
    public void AddPart(XLANGPart part);  
    public void AddPart(XLANGPart part, String partName);  
    ```  
  
-   在 BizTalk 專案中，新增參考的公用類別和呼叫**AddPart**方法從**運算式**圖形在協調流程中，如下所示：  
  
    ```  
    MyAddPartHelper.AddPart(myMessage, myStringObject, “StringObject1”);  
    ```  
  
> [!NOTE]
>  您無法將非可序列化的物件或自訂格式化物件新增為訊息部分。 必須先初始化所有的靜態部分新增其他部分使用**AddPart**方法。 只有在訊息的建構陳述式中，您才可以新增任意部分至此訊息。 不支援在訊息建構陳述式的外面新增其他部分。  
  
## <a name="retrieving-message-parts"></a>擷取訊息部分  
 您可以從現有的 multipart 訊息擷取訊息部分使用**RetrieveAs**方法從**Microsoft.XLANGs.BaseTypes**。 若要這樣做，請執行以下動作：  
  
-   建立 C# 專案，並將參考加入**Microsoft.XLANGs.BaseTypes**。  
  
-   實作類似於以下的公用類別：  
  
    ```  
    Public class MyAddPartHelper  
    {  
         public static Object GetPart(XLANGMessage msg, string sName, Type t)  
         {  
              XLANGPart p =  msg[sName];  
              return p.RetrieveAs(t);  
         }  
         public static Object GetPart(XLANGMessage msg, int partIndex, Type t)  
         {  
               XLANGPart p = msg[partIndex];  
               return p.RetrieveAs(t);  
          }  
    }  
    ```  
  
    > [!NOTE]
    >  **RetrieveAs**方法支援擷取訊息部分，依名稱和索引。  
  
-   在 BizTalk 專案中，新增參考的公用類別和呼叫**GetPart**方法從**運算式**圖形在協調流程中，如下所示：  
  
    ```  
    sPart = (System.String) MyAddPartHelper.GetPart(msg, "StringObject1" , typeof(System.String));  
    //sPart is a type of System.String  
    sPart = (System.String) MyAddPartHelper.GetPart(msg, 1, typeof(System.String));  
    //Retriving the message part with index = 1  
    ```  
  
## <a name="message-part-context-property-access"></a>訊息部分內容屬性存取  
 訊息部分的內容與訊息內容不同。 當您設定時，您可以建構訊息部分內容屬性，透過結構描述編輯器**Property Schema Base**屬性相關聯的項目**PartContextPropertyBase。**  
  
 存取和訊息屬性類似，都是透過如下的運算式：  
  
```  
Msg.PartName(myPartContextProperty)  
```  
  
 例如：  
  
```  
Str=Msg.PartName(myPartContextProperty); //assumes myPartContextProperty is of type string  
```  
  
## <a name="xlangmessage-context-property-access"></a>XLANGMessage 內容屬性存取  
 如果您想要存取訊息屬性**XLANGMessage**介面從程式碼中，您可以將訊息傳遞做為參數的型別**Microsoft.XLANGs.BaseTypes.XLANGMessage**方法從運算式圖形，然後使用**Microsoft.XLANGs.BaseTypes.XLANGMessage**方法**SetPropertyValue**和**GetPropertyValue**來達成此。 若要這樣做，請執行以下動作：  
  
-   建立 C# 專案，並將參考加入**Microsoft.XLANGs.BaseTypes**和**Microsoft.BizTalk.GlobalPropertySchemas**。  
  
-   使用類似以下的程式碼來存取內容屬性：  
  
    ```  
    MyMsg.GetPropertyValue(typeof(BTS.MessageID));  
    MyMsg.SetPropertyValue(typeof(MIME.IsMultipartRelated), true);  
    ```  
  
> [!NOTE]
>  如果您想要取得或設定自訂內容屬性，您需要新增對屬性結構描述專案的參考，或是新增對組件 (此組件包含 C# 專案中的屬性結構描述) 的參考。  
  
## <a name="assigning-to-message-properties"></a>指派至訊息屬性  
 您可以將某個值指派至訊息屬性：  
  
```  
MyMessage(MySchemaNamespace.MyProperty)=True;  
```  
  
 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，您可以對多部分訊息的 MIME 屬性進行指稱和指派值。  
  
```  
Message_Out.MessagePart_1(MIME.FileName)="document.doc";  
```  
  
> [!NOTE]
>  BizTalk 訊息是由訊息內容和訊息部分所組成。 您必須先初始化訊息部分，然後才可以取得或設定任何訊息內容屬性，否則您在 XLANG 編譯時會收到錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [協調流程中使用訊息](../core/using-messages-in-orchestrations.md)   
 [使用者程式碼中建構的訊息](../core/constructing-messages-in-user-code.md)   