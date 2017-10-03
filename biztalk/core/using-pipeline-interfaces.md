---
title: "使用管線介面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bb88d0d-23ab-4fdb-bcd2-56050456cf69
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c365a8d7bdf37564d3d9b2dceac1c8615e126ebc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-pipeline-interfaces"></a>使用管線介面
管線元件是一種 .NET 或 COM 元件，會實作一組預先定義的介面，以便與 BizTalk 傳訊引擎進行互動。 取決於元件的功能，必須實作不同的介面。 本主題討論這些介面，以及其所具有的一些方法。  
  
> [!WARNING]
>  如果您使用 COM 建置自訂管線元件，必須設定元件以使用多執行緒 Apartment (MTA) 模型。 否則，叫用您的元件便會造成具有 E_NOINTERFACE 錯誤的失敗。  
  
## <a name="ipipelinecontext"></a>IPipelineContext  
 所有的管線元件可以使用**IPipelineContext**來存取所有文件處理特定介面的方法。 **IPipelineContext**介面提供下列功能：  
  
-   讓元件能夠擷取環境管線和階段設定。  
  
-   讓元件能夠擷取訊息和訊息 Factory。 運用這些 Factory，元件可以建立執行元件時所需要的各種物件。  
  
-   讓元件能夠擷取文件規格。 文件規格是 XSD 結構描述加上其他註釋。  
  
## <a name="ibasecomponent"></a>IBaseComponent  
 所有管線元件都需要實作此介面以提供元件的基本資訊。  
  
## <a name="icomponent"></a>IComponent  
 所有的管線元件 (組合器與解譯器除外) 都會實作此介面，以便從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 引擎取得訊息並加以處理，並將處理過的訊息傳回到引擎。  
  
 **執行。** 由引擎呼叫的方法，將輸入訊息傳遞到元件，並從元件擷取處理過的訊息。  
  
## <a name="ipropertybag-ipersistpropertybag"></a>IpropertyBag、IPersistPropertyBag  
 管線元件必須實作**IPersistPropertyBag**接收其組態資訊。 這個介面和**IPropertyBag**是標準的介面。 如需這些介面的詳細資訊，請參閱 Microsoft .NET Framework 軟體開發套件 (SDK) 文件。  
  
## <a name="idisassemblercomponent"></a>IDisassemblerComponent  
 解譯元件是一種管線元件，會在輸入時接收一個訊息，並在輸出時產生零個或多個訊息。 解譯元件的用途是將交換的訊息分割成個別的文件。 解譯元件必須實作的方法**IDisassemblerComponent**介面，以取得訊息從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件進行處理，以及傳遞反組譯傳回到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
|方法|Description|  
|------------|-----------------|  
|**反組譯**|執行內送文件的解譯**pInMsg**。|  
|**GetNext**|從解譯器執行所產生的訊息集取得下一個訊息。 傳回**NULL**是否有任何訊息。|  
  
 如果您撰寫的是支援「可復原交換處理」的解譯器元件，便必須進行下列步驟：  
  
1.  將輸入資料流包裝在 VirtualStream() 中，使其變成可搜尋的。  
  
2.  在 GetNext() 中，讓邏輯判斷訊息何時錯誤。 如果訊息錯誤，請設定 BTS.MessageDestination = "SuspendQueue"，並在 GetNext() 中傳回訊息。  
  
3.  如果訊息良好，請設定 BTS.SuspendMessageOnRoutingFailure = True，並在 GetNext() 中傳回訊息。  
  
## <a name="iassemblercomponent"></a>IAssemblerComponent  
 組合元件是一種管線元件，會在輸入時接收數個訊息，並在輸出時產生一個訊息。 組合元件的用途是將個別文件收集到訊息交換批次中。  
  
> [!NOTE]
>  在這個版本的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中並沒有使用組合功能，因此 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 永遠都會將一份文件傳遞到元件輸入。  
  
 組合元件實作**IAssemblerComponent**所呼叫的方法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]引擎在執行階段。  
  
|方法|Description|  
|------------|-----------------|  
|**AddDocument**|新增的文件**pInMsg**會包含在交換的訊息清單。|  
|**組合**|從藉由上一個方法新增的訊息中建立交換。 將指標傳回到組合的訊息。|  
  
## <a name="iprobemessage"></a>IProbeMessage  
 可實作任何管線元件 （一般、 組合或解譯） **IProbeMessage**是否需要訊息探查功能。 探查元件會用於具有管線階段**FirstMatch**執行模式。 在此種階段中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會將訊息提供給元件，而**探查**方法會檢查以判斷該元件是否可識別訊息的格式訊息的開頭。  
  
|方法|Description|  
|------------|-----------------|  
|**探查**|這個方法會採用**pInMsg**訊息，並傳回**True**如果辨識的格式或**False**否則。|  
  
## <a name="inameditem"></a>INamedItem  
 這是從 Managed 和 Unmanaged 程式碼存取文件結構描述的協助程式介面。  
  
## <a name="inameditemlist"></a>INamedItemList  
 這是從 Managed 和 Unmanaged 程式碼存取文件結構描述的協助程式介面。  
  
## <a name="idocumentspec"></a>IDocumentSpec  
 管線元件可以使用的方法**IDocumentSpec**介面來執行特定文件的動作，例如將內容屬性移至內容和回、 存取文件結構描述，並依此類推。  
  
|方法|Description|  
|------------|-----------------|  
|**文件類型**|傳回目前文件的類型。|  
|**DocSpecName**|傳回目前文件的規格名稱。|  
|**GetSchemaCollection**|傳回目前文件之文件結構描述的清單。|  
|**GetBodyPath**|傳回文件中開始內文部分所在之節點的 XPath。|  
|**GetDistinguishedPropertyAnnotationEnumerator**|傳回所有辨別欄位屬性註釋的字典列舉程式。|  
|**GetPropertyAnnotationEnumerator**|傳回所有屬性註釋的列舉程式。|  
  
## <a name="icomponentui"></a>IComponentUI  
 管線元件必須實作此介面，以便在「管線設計師」環境內使用。  
  
|方法|Description|  
|------------|-----------------|  
|**圖示**|提供與此元件相關聯的圖示。|  
|**Validate**|[管線設計師] 會在管線編譯前呼叫此方法，以確認有正確設定所有的組態屬性。|  
  
 **圖示**屬性會傳回**IntPtr**。 下列 C# 範例示範如何傳回**IntPtr**。  
  
```csharp  
static   ResourceManager resManager = new ResourceManager("ResourceManager", Assembly.GetExecutingAssembly());  
...  
[Browsable(false)]  
public IntPtr Icon  
{  
   get  
   {  
      return ((Bitmap)resManager.GetObject("MyIcon")).GetHicon();  
   }  
}  
```  
  
 如需詳細資訊，請參閱**IComponentUI 介面 (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 
  
## <a name="see-also"></a>另請參閱  
 [開發自訂管線元件](../core/developing-custom-pipeline-components.md)   
 [CustomComponent （BizTalk Server 範例）](../core/customcomponent-biztalk-server-sample.md)