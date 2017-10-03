---
title: "協議解析、 結構描述探索和授權的收到的 EDI 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 503e307c-4cb0-49b5-8751-82dcea203151
caps.latest.revision: "45"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de5f7fd9b022daf2d123de1c971797b53df202d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="agreement-resolution-schema-discovery-and-authorization-for-received-edi-messages"></a>協議解析、 結構描述探索和授權的收到的 EDI 訊息
當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 收到 EDI 訊息時，EDI 接收管線會執行交易夥伴協議尋查、結構描述探索和授權程序，以判斷如何處理訊息。  
  
## <a name="agreement-resolution"></a>協議解析  
 EDI 接收管線會執行一系列的步驟來進行交易夥伴協議解析，以判斷訊息中的標頭欄位和協議定義中的屬性是否相符。 一旦 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 判斷出協議，就會決定套用到交換的文件結構描述 (請參閱下文)。 它會使用與相符協議關聯的屬性以及相關的結構描述，來驗證和處理收到的訊息。  
  
 為執行協議解析，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行的步驟如下：  
  
1.  將交換標頭中的傳送者辨識符號和識別碼以及接收者辨識符號和識別碼，與協議屬性中的相同項目比對，以解析協議。  
  
2.  如果步驟 1 未成功，則只比對交換標頭與協議屬性中的傳送者辨識符號和識別碼，以解析協議。 另外，因為步驟 1 未成功，可以放心地假設 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將接收訊息。 因此，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會嘗試將接收者辨識符號和識別碼與下列項目比對：  
  
    -   值 "BT" 與 "HostX12Recvr" (對於 X12 編碼訊息) 和  
  
    -   值 "BT" 與 "HostEdifactRecvr" (對於 EDIFACT 編碼訊息)  
  
    > [!IMPORTANT]
    >  -   **BizTalk Server 2013 R2 2013 和 2010年**： 是必要的協議設定中的 ISA5、 ISA6、 ISA7、 ISA8、 UNB2.1、 UNB2.2、 UNB3.1 和 UNB3.2 欄位。  
    > -   **BizTalk Server 2009 和 2006 R2**: ISA7、 ISA8、 UNB3.1 和 UNB3.2 欄位並非強制的合作對象設定中。 如果欄位保留空白，將 EDI 引擎會提供根據 ISA5、 ISA6、 UNB2.1 和 UNB2.2 值解析。  
    > -   若要支援較新版本的 BizTalk Server 從 BizTalk Server 2009 和 2006 R2 的解決方式，硬式編碼識別碼 （HostX12Recvr 和 HostEdifactRecvr） 和辨識符號 (BT) 導入。  
    > -   EDIFACT 訊息應該遵循[UNECE 指導方針](http://www.unece.org/tradewelcome/areas-of-work/un-centre-for-trade-facilitation-and-e-business-uncefact/outputs/standards/unedifact/tradeedifactrules.html)訊息語法和規則。  
  
3.  如果步驟 2 未成功，則使用後援協議屬性。  
  
 在步驟 1 中，對於 X12，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將使用下列值來比對：  
  
-   ISA05 (傳送者辨識符號)  
  
-   ISA06 (傳送者識別碼)  
  
-   ISA07 (接收者辨識符號)  
  
-   ISA08 (接收者識別碼)  
  
 對於 EDIFACT，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用下列值來比對：  
  
-   UNB2.1 （傳送者識別項）  
  
-   UNB2.2 (傳送者辨識符號)  
  
-   UNB3.1 (接收者識別碼)  
  
-   UNB3.2 (接收者辨識符號)  
  
 用於比對的協議屬性中定義**識別碼**方向特定協議索引標籤頁面**協議屬性** 對話方塊。  
  
 這四個接收端和傳送端屬性可唯一識別交易夥伴協議。 使用這四個屬性，可讓您在接收端處理時有更大的彈性。 例如，這種協議解析方式可讓您將通知傳送給多個合作對象，而無須建立多個傳送埠。  
  
 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]無法解析協議使用全部四個傳送者和接收者辨識符號和識別項，它會嘗試解析協議使用傳送者辨識符號和識別項。 若為 X12，這些欄位是 ISA05 和 ISA06；若為 EDIFACT，這些欄位則是 UNB2.1 和 UNB2.2。 如同傳送者和接收者屬性比對[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中定義的協議屬性比對交換標頭中的值**識別碼**方向特定協議索引標籤頁面**協議屬性** 對話方塊。 如果只是傳送者辨識符號和識別項來解析協議，接收者辨識符號和識別項不應定義之雙向協議索引標籤中**協議屬性** 對話方塊。  
  
 如果找不到協議，除非連接埠設定需要驗證，否則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用遞補交易夥伴協議。 如果通訊埠設定需要驗證 (如果有任一個**驗證失敗時捨棄訊息**或**驗證失敗時保留訊息**上選取了 **一般**頁面**接收埠屬性**)，都需要接收埠收到的任何交換的協議。 在此狀況下，如果協議不是透過比對交換標頭和協議屬性來解析的，則不允許使用後援協議屬性來判斷協議。 如果找不到協議，交換會視為驗證失敗並遭擱置。  
  
> [!NOTE]
>  EDI 管線中的訊息會進入協議解析的後續步驟，直到訊息在協議為啟用狀態的步驟中獲得解析為止。 例如，如果訊息在協議解析的第一個步驟獲得解析，但協議處於停用狀態，則訊息會進入後續解析步驟。  
  
## <a name="schema-discovery"></a>結構描述探索  
 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 判斷解析為訊息的協議之後，它接著必須判斷應使用哪個結構描述來驗證和處理訊息。 它會使用所識別的屬性以**本機主機設定**頁面的單向 （傳送端） 協議索引標籤的**協議屬性** 對話方塊。  
  
 為判斷結構描述，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必須先判斷結構描述命名空間。 「EDI 解譯器」會使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 隨附的標準結構描述預設命名空間，或判斷要用於自訂結構描述的命名空間。  
  
 **本機主機設定**單向協議索引標籤的頁面**協議屬性**對話方塊可讓您設定之值的方格，以判斷自訂命名空間。 如果找到相符項目在方格中，EDI 解譯器會使用預設的命名空間中**目標命名空間**欄位標示為預設列。  
  
### <a name="x12-schema-discovery"></a>X12 結構描述探索  
 若為 X12 編碼訊息，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用內送交換之標頭的應用程式傳送者識別項 (GS02) 和交易集識別碼 (ST01) 來判斷自訂命名空間。 它會嘗試尋找這些值和值之間相符項目中的 GS02 和 ST01 屬性**自訂目標命名空間**方格中的**本機主機設定**頁面 (在**交易設定設定**) 之雙向協議索引標籤**協議屬性** 對話方塊。 如果找到相符項目，它會使用格線同一列中指定的目標命名空間，來判斷用來驗證和處理訊息的結構描述。 如果未判斷出目標命名空間，則會使用預設目標命名空間。 如果沒有命名空間中**目標命名空間**欄位標示為預設列，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會使用後援協議屬性中針對指定 X12 編碼訊息，其預設值是目標命名空間`http://schemas.microsoft.com/BizTalk/Edi/X12/2006`.  
  
 對於 X12 交換，在找到目標命名空間後，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用下列資訊判斷結構描述：  
  
-   找到的目標命名空間  
  
-   ST03 (如果 GS07 == X - Accredited Standards Committee X12) 的前五個字元代表的版本/版次。 如果 ST03 不存在/無效，或未產生結構描述解析，則使用 GS08 或 ISA12 (如果 GS07 != X) 的前五個字元判斷版本。  
  
-   ST01 中的 DocType  
  
 「EDI 解譯器」會將編碼類型、版本/版次和 DocType 串連在一起來判斷結構描述名稱，例如 "X12_00401_864"。 接著會將目標命名空間與結構描述名稱 (例如，`http://schemas.microsoft.com/BizTalk/Edi/X12/2006/X12#X12_00401_864`) 串連。  
  
 對於內送 HIPAA 837 交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援三種 HIPAA 837 結構描述：  
  
|837 結構描述|版本 4010 中的 GS08 值|版本 5010 中的 GS08/ST03 值|  
|----------------|--------------------------------|--------------------------------------|  
|Claim-Dental_837D|004010X097A1|005010X224A1|  
|Claim-Institutional_837I|004010X096A1|005010X223A1|  
|Claim-Professional_837P|004010X098A1|005010X222|  
  
> [!NOTE]
>  在 HIPAA 版本中，對於交易集 278 (健康照護服務檢視)，要求與回應配對會針對 GS08 與 ST01 共用相同的值。 依據 BHT02 欄位中的觸發值，您可以區別版本 5010 中的 278 要求/回應：  
>   
>  1.  BHT02 中的 01、13 與 36 的任一個值各代表一個健康照護服務檢視要求  
> 2.  BHT02 中的 11 代表健康照護服務檢視回應  
  
### <a name="edifact-schema-discovery"></a>EDIFACT 結構描述探索  
 對於 EDIFACT 編碼訊息，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 判斷自訂命名空間的方式是使用內送交換之標頭的訊息類型 (UNH2.1)、訊息版本號碼 (UNH2.2)、訊息版次號碼 (UNH2.3)、指定代碼 (UNH2.5)、功能群組識別碼 (UNG2.1) 以及應用程式傳送識別碼辨識符號 (UNG2.2)。 接著它會嘗試尋找這些值和值之間相符項目中的 UNH2.1、 UNH2.2、 UNH2.3、 UNH2.5、 UNG2.1 和 UNG2.2 屬性**自訂目標命名空間**方格 (下方**交易集設定**)雙向協議索引標籤的**協議屬性** 對話方塊。 如果找到相符項目，它會使用格線同一列中指定的目標命名空間，來判斷用來驗證和處理訊息的結構描述。 如果未判斷出目標命名空間，則會使用預設目標命名空間。 如果沒有命名空間中**目標命名空間**欄位標示為預設列，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將使用的目標命名空間在後援協議屬性，對於 EDIFACT 編碼訊息，其預設值是`http://schemas.microsoft.com/BizTalk/Edi/EDIFACT/2006`.  
  
 對於 EDIFACT 交換，在找到目標命名空間後，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用下列資訊判斷結構描述：  
  
-   找到的目標命名空間。  
  
-   UNH2.2 中的訊息版本號碼。  
  
-   UNH2.3 中的訊息版次號碼。  
  
-   UNH2.1 中的訊息類型。  
  
-   UNH2.5 中的指定代碼。  
  
 「EDI 解譯器」會將編碼類型、版本、版次和訊息類型串連在一起來判斷結構描述名稱，例如 " EFACT_D94A_CONTEN"。 接著會將目標命名空間與結構描述名稱 (例如，`http://schemas.microsoft.com/BizTalk/Edi/Edifact/2006/EFACT#EFACT_D94A_CONTEN`) 串連。  
  
 如果訊息中有 UNH2.5，EDI 解譯器會先嘗試使用結構描述名稱中的 UNH2.5 值 (例如，EFACT_D94A_CONTEN_TEST) 來尋找相符的結構描述。 如果找不到相符的結構描述，EDI 解譯器會回復為尋找不含 UNH2.5 值的結構描述。  
  
## <a name="authorization"></a>授權  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會將協議的授權和安全性欄位定義值與訊息中的欄位比對。 如果有不相符的項目，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會擱置交換。 若為 EDIFACT 編碼訊息，這些欄位是收件者參考密碼 (UNB6.1 和 UNB6.2)。 若為 X12 編碼訊息，這些欄位則是 [授權辨識符號和資訊] (ISA1-2) 以及 [安全性辨識符號和資訊] (ISA3-4)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何接收 EDI 訊息](../core/how-biztalk-server-receives-edi-messages.md)