---
title: 如何設定 SMTP 傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [SMTP adapters], send ports
- send ports, SMTP adapters
- SMTP adapters, send ports
ms.assetid: b2291378-718d-4d1a-9d54-cd34c1b2e000
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f69f61af2803272c34e3f4e8a0ac4dccfb151561
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22250614"
---
# <a name="how-to-configure-an-smtp-send-port"></a>如何設定 SMTP 傳送埠
您可以使用程式設計的方式，或使用 [BizTalk Server 管理] 主控台，來設定 SMTP 傳送埠。  
  
 **如何以程式設計方式設定 SMTP 傳送埠**  
  
 SMTP 配接器會將其組態資訊儲存在「BizTalk 管理」資料庫中 (也稱為「組態」資料庫)。 組態資訊會儲存在自訂 XML 屬性包中。 在 SMTP 配接器初始化期間及其執行階段，伺服器會傳遞組態至配接器，如下：  
  
-   SMTP 傳送處理常式組態資訊傳遞至配接器藉由呼叫**負載**方法**IPersistPropertyBag**介面。  
  
-   對於 SMTP 傳送配接器，則將組態資訊視為訊息內文中的一組屬性，傳遞至配接器。 SMTP 命名空間會將這些屬性群組在一起。  
  
 「 BizTalk 總管物件模型公開 ITransportInfo 配接器組態介面傳送埠，其中包含 TransportTypeData 讀/寫屬性。 此屬性會將 SMTP 傳送埠組態屬性包接受為名稱/值組 XML 字串。 請注意，若要在 「 BizTalk 總管物件模型中設定這個屬性，它必須先設定的位址屬性**ITransportInfo**介面。  
  
 設定**TransportTypeData**屬性**ITransportInfo**介面並非必要。 若沒有設定它，SMTP 傳送埠會使用 SMTP 傳送處理常式的預設值。 SMTP 傳送埠特定屬性是在 SMTP 傳送配接器結構描述 bts_smtp_properties.xsd 中定義。  
  
 若您沒有定義重複傳送處理常式組態屬性的屬性，則會使用處理常式的組態屬性。 若您沒有定義必要的屬性，則會使用預設值。 若您沒有定義預設值，SMTP 傳送處理常式會在事件記錄檔中記錄一個錯誤，並將訊息移至備份配接器。  
  
 您可以使用程式設計的方式在訊息內容上設定這些屬性。 您可以在 BizTalk 協調流程排程或在自訂管線元件中設定這些屬性。 使用這些屬性時適用下列規則：  
  
-   若在協調流程上或接收管線的自訂管線元件中設定屬性，則：  
  
    -   若訊息傳送至靜態傳送埠，屬性值會以該傳送埠設定的值覆寫。  
  
    -   若訊息傳送至動態傳送埠，則不會覆寫屬性值。  
  
-   若在傳送管線的自訂管線元件中設定屬性，則：  
  
    -   無論訊息是傳送至靜態或動態傳送埠，都不會覆寫值。  
  
 下表列出您可以在「BizTalk 總管」物件模型中設定之 SMTP 傳送位置的組態屬性。  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|**SMTPHost**|xs:string|用來傳送訊息的 SMTP 伺服器。|最大長度：256|預設值： 空白。<br /><br /> 預設值指示 SMTP 傳送埠將會為處理常式使用組態值。|  
|**來源**|xs:string|SMTP 傳送埠的電子郵件地址放置於 SMTP**從**標頭。|最大長度：256|預設值： 空白。<br /><br /> 預設值指示 SMTP 傳送埠將會為處理常式使用組態值。|  
|**[副本]**|xs:string|訊息複本傳送目的地的電子郵件地址。|最大長度： 1024年|預設值： 空白<br /><br /> 您可以列出數個電子郵件地址。|  
|**主旨**|xs:string|訊息的主旨標題。|最小長度：00<br /><br /> 最大長度：256|預設值: %messageid%。|  
|**SMTPAuthenticate**|xs:int|要使用的驗證類型。|無|有效值：<br /><br /> -0-沒有驗證<br />-1-基本驗證<br />-2-處理序帳戶 (NTLM)<br /><br /> 預設值指示 SMTP 傳送埠將會為處理常式使用組態值。 若要套用的預設值，請省略此屬性，從屬性包，設定 TransportTypeData 屬性時。|  
|**UserName**|xs:string|要提供給 SMTP 伺服器驗證的使用者名稱。|最小長度：00<br /><br /> 最大長度：256|預設值： 空白<br /><br /> 需要的值，如果**SMTPAuthenticate**等於 1 （基本驗證）。|  
|**密碼**|xs:string|要提供給 SMTP 伺服器驗證的使用者密碼。|最小長度：00<br /><br /> 最大長度：256|預設值： 空白<br /><br /> 需要的值，如果**SMTPAuthenticate**等於 1 （基本驗證）。|  
|**ReadReceipt**|xs:boolean|為來自此傳送埠的訊息要求一個讀取回條。|無|預設值：False|  
|**DeliveryReceipt**|xs:boolean|為來自此傳送埠的訊息要求一個送達回條。|無|預設值：False|  
|**EmailBodyText**|xs:string|指定傳送的電子郵件內文所使用的文字。|最大長度： 64kb|預設值： 空白|  
|**EmailBodyTextCharset**|xs:string|指定要用於編碼傳送之電子郵件內文的字元集**EmailBodyText**選項使用。 SMTP 配接器會將轉換**EmailBodyText**設定所指定的字元**EmailBodyTextCharset**。|無|預設值： 無。 您必須明確設定該值，例如設為 UTF-8。<br /><br /> 如果沒有設定一個值，則可能會發生本主題末尾所示範的錯誤。|  
|**EmailBodyFile**|xs:string|指定將用於傳送的電子郵件內文的檔案內容，以及檔案的完整路徑。 在執行階段，SMTP 配接器的主控件必須可以存取此路徑。|路徑最大長度：256 個字元|預設值： 空白|  
|**EmailBodyFileCharset**|xs:string|指定要用於編碼傳送之電子郵件內文的字元集**EmailBodyFile**屬性設定。 SMTP 配接器不會在檔案執行任何轉換；檔案必須已經使用此字元集編碼。 若檔案有一個「位元順序標記」(Byte-Order-Mark，BOM)，SMTP 配接器會移除它。|無|預設值：UTF-8 (65001)|  
|**附加檔案**|xs:string|指定要附加一或多個檔案至電子郵件訊息，以及檔案的完整路徑。 在執行階段，SMTP 配接器的主控件必須可以存取指定的一或多個路徑。|路徑最大長度：256 個字元|預設值： 空白|  
|**MessagePartsAttachments**|xs:int|指定如何將 BizTalk 訊息部分附加到電子郵件訊息|無|有效值：<br /><br /> -0-沒有 BizTalk 訊息部分會當成附件。<br />-1-以電子郵件附件傳送 BizTalk 訊息內文部分。 在此情況下， **EmailBodyFile**或**EmailBodyText**應該指定屬性。 若沒有指定這些屬性的任何一個，則會將 BizTalk 訊息內文部分當做電子郵件內文，而非附件來傳送。<br />-2-所有部分會當成附件來都傳送。 不過，如果**EmailBodyText**或**EmailBodyFile**未指定，則 BizTalk 訊息內文部分傳送為電子郵件內文和其他部分會當成附件來傳送。<br /><br /> 預設值： 0|  
|**ReplyBy**|xs:dateTime|於其中填入**Reply-by**中具有指定值外寄訊息的標頭欄位。|此屬性無法在傳送埠屬性頁面中設定。 可以從管線或協調流程中設定此屬性。|預設值： 空白|  
  
 下列程式碼顯示要用來設定這些屬性的 XML 字串格式：  
  
```  
<CustomProps>  
   <DeliveryReceipt vt="11">-1</DeliveryReceipt  
   <SMTPHost vt="8">sfdsadf</SMTPHost>  
   <Subject vt="8">Some subject</Subject>  
   <From vt="8">username@domain.com</From>  
   <SMTPAuthenticate vt="19">2</SMTPAuthenticate>  
   <ReadReceipt vt="11">-1</ReadReceipt>  
</CustomProps>  
```  
  
 **如何使用 BizTalk Server 管理主控台設定 SMTP 傳送埠**  
  
 您可以在 [BizTalk Server 管理] 主控台中設定 SMTP 傳送埠配接器變數。 若未設定傳送埠的屬性，則使用 [BizTalk Server 管理] 主控台中所設定的預設傳送處理常式值。  
  
 若要使用 [BizTalk Server 管理] 主控台設定 SMTP 傳送埠，請使用下列程序。  
  
### <a name="to-configure-variables-for-an-smtp-send-port"></a>設定 SMTP 傳送埠的變數  
  
1.  在 [BizTalk Server 管理] 主控台中，建立新傳送埠，或按兩下現有的傳送埠以進行修改。 如需詳細資訊，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。 設定所有傳送埠選項，並指定**SMTP**如**類型**選項**傳輸**區段**一般** 索引標籤。  
  
2.  在**一般**索引標籤的**傳輸**區段中，旁邊**類型**，按一下 **設定**。  
  
3.  在**SMTP 傳輸屬性**對話方塊**一般**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**若要**|必要。 指定傳送訊息目標的電子郵件地址。<br /><br /> 您可以指定多個地址。<br /><br /> 最大長度：256<br /><br /> 如需有關這個屬性的詳細資訊，請參閱[屬性至 SMTP 的限制](../core/restrictions-on-the-smtp-to-property.md)。|  
    |**[副本]**|指定傳送訊息副本的電子郵件地址。<br /><br /> 您可以指定多個地址。<br /><br /> 最大長度： 1024年|  
    |**主旨**|指定訊息的主旨標題。<br /><br /> 最小長度：00<br /><br /> 最大長度：256|  
    |**通知**|指定通知回條的類型。 您可以選取一或兩種類型的回條。 通知回條的類型有：<br /><br /> -   **讀取回條**。 讀取訊息時會傳送確認電子郵件訊息。<br />-   **送達回條**。 傳送訊息時會傳送確認電子郵件訊息。|  
  
4.  在**SMTP 傳輸屬性**對話方塊**撰寫**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**BizTalk 訊息內文部分**|指定此選項，可使用 BizTalk 訊息內文部分做為傳送的電子郵件內文。|  
    |**Text**|指定傳送的電子郵件內文所使用的文字。 之後**文字**選取選項時您可以將文字輸入的電子郵件內文到文字方塊。<br /><br /> **最大長度：** 64 Kb|  
    |**文字字元集**|-指定用於編碼傳送之電子內文的字元集。 這個選項才可用如果**文字**選取選項。<br />-   **預設值：** utf-8 (65001)|  
    |**檔案**|指定將用於傳送的電子郵件內文的檔案內容，並指定該檔案路徑。 之後**檔案**選取選項時您可以按一下省略符號 (**...**) 按鈕來瀏覽至檔案。<br /><br /> 最大路徑長度： 256 個字元**附註：** ，建議的最佳做法是從用於生產環境中的 BizTalk Server 群組中的所有 BizTalk 伺服器存取的檔案共用上指定的路徑。|  
    |**檔案的字元集**|指定正在傳送之檔案的字元集編碼。 **注意：** SMTP 配接器不會套用至檔案的指定編碼方式。 此選項只用於指定正在傳送之檔案是如何已經編碼。 <br /><br /> 這個選項才可用如果**檔案**選取選項。<br /><br /> 預設值：UTF-8 (65001)|  
  
5.  在**SMTP 傳輸屬性**對話方塊**附件**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**剩餘的 BizTalk 訊息部分**|指定如何將 BizTalk 訊息部分附加到電子郵件訊息。<br /><br /> 選項：<br /><br /> -   **不要附加部分**<br />-   **附加只內文部分**<br />-   **附加所有部分**<br /><br /> 預設值： 不要附加部分。|  
    |**加入**|指定將一或多個檔案附加到電子郵件訊息。 按一下後**新增**您可以瀏覽選取的檔案，並將它加入至要附加的檔案清單。<br /><br /> 最大路徑長度： 256 個字元**附註：** ，建議的最佳做法是從用於生產環境中的 BizTalk Server 群組中的所有 BizTalk 伺服器存取的檔案共用上指定的路徑。|  
    |**移除**|將選取的檔案從要附加到電子郵件訊息的檔案清單移除。|  
  
6.  在**SMTP 傳輸屬性**對話方塊**處理常式覆寫**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**SMTP 伺服器名稱**|指定傳送訊息時要使用的 SMTP 伺服器名稱。<br /><br /> 最大長度： 256**附註：** URI 傳送埠或接收位置不能超過 256 個字元。|  
    |**（電子郵件地址）**|指定要置於 SMTP 電子郵件地址**從**標頭。<br /><br /> 最大長度：256|  
    |**驗證類型**|指定要用於 SMTP 伺服器的驗證類型。<br /><br /> 選項：<br /><br /> -   **（預設值）**<br />-   **無驗證**<br />-   **基本驗證**<br />-   **處理序帳戶 (NTLM)**<br /><br /> 預設值指示 SMTP 傳送埠將會使用在傳送處理常式中指定的組態值。|  
    |**使用者名稱**|指定要用於 SMTP 伺服器驗證的使用者名稱。<br /><br /> 此屬性需要一個值，如果**驗證類型**是**基本驗證**。<br /><br /> 最小長度：00<br /><br /> 最大長度：256|  
    |**密碼**|指定要用於 SMTP 伺服器驗證的密碼。<br /><br /> 此屬性需要一個值，如果**驗證類型**是**基本驗證**。<br /><br /> 最小長度：00<br /><br /> 最大長度：256|  
  
7.  按一下**確定**和**確定**以儲存設定。  
  
## <a name="see-also"></a>另請參閱  
 [設定 SMTP 配接器](../core/configuring-the-smtp-adapter.md)