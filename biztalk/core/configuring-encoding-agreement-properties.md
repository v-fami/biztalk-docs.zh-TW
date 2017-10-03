---
title: "設定編碼協議屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.ediagreement.properties
ms.assetid: 0cb1146e-177c-42fa-b1d8-a834229c2af9
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cde69b1514b2e376a7df415befc0a686300009f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-encoding-agreement-properties"></a>設定編碼協議屬性
交易夥伴協議 (TPA) 是兩個交易夥伴之間透過特定 B2B 通訊協定交易訊息時所採用的決定性與繫結性協議。 簡單地說，TPA 指的是當兩個商務設定檔互相交換 B2B 訊息時，對於使用特定訊息編碼通訊協定 (X12 或 EDIFACT) 或特定傳輸通訊協定 (AS2) 的一種共識。 除了用來對於使用一致的編碼與傳輸通訊協議達成共識之外，協議還可以用來自訂訊息的格式與傳遞方式。  
  
-   在編碼通訊協定設定當中，您還可以定義傳送者是否預期收到通知 (不管訊息是以批次還是個別方式傳送)。  
  
-   在傳輸通訊協定設定當中，您還可以定義訊息是否應該經過簽章、加密等等。  
  
    > [!NOTE]
    >  如需傳輸通訊協定 (AS2) 設定的詳細資訊，請參閱[設定 AS2 協議屬性](../core/configuring-as2-agreement-properties.md)。  
  
 建立協議時，您必須考量下列事項：  
  
-   兩個合作對象之間的交易夥伴協議為雙向協議。 兩個合作對象 (Party A 與 Party B) 之間的單一協議可讓 Party A 傳送訊息給 Party B，且 Party A 亦可接收來自 Party B 的訊息。為了在使用者介面中呈現雙向協議，每個單向協議各以一個索引標籤來代表。因此，您也可以在協議使用者介面中，您會看到兩個索引標籤， **party a-> [partyb]** （代表單向協議的訊息會從合作對象 A 傳送至合作對象 B） 和**[partyb]-> party a** (代表單向協議從 Party b 傳送至 party a 的訊息。）  
  
-   每個單向協議皆代表一個端對端訊息交易。 另外，傳送或接收通知亦為同一個訊息交易的一部份，因此應該在同一個單向協議索引標籤上設定。例如，假設 Party A 傳送 EDI 交換給 Party B 以及回應，合作對象 B 通知傳回給合作對象 a。因此，與傳送交換並預期收到通知相關的所有屬性必須都設定**party a-> partyb**  索引標籤。  
  
    > [!NOTE]
    >  雖然通知屬於同一個訊息交易時，應如何產生通知相關的屬性中所設定**partyb-> party a**  索引標籤。這是必要的因為通知內容屬性為傳送者和接收者辨識符號都會設定為您在指定的值相反**party a-> partyb**  索引標籤。例如，如果在交換訊息所解析成的協議中，傳送者與接收者識別碼是設為 THEM 與 US，則通知裡的傳送者與接收者內容屬性將設為 US 與 THEM。 一般而言，其他單向協議索引標籤也會分別將傳送者與接收者識別項設定為 US 與 THEM。 因此，通知訊息會解析成該協議，並將挑選屬性設定。 因此，如果您想要讓通知使用不同的項目分隔符號，或是如果您想要讓通知使用 CR LF 中, 指定內容**partyb-> party a**  索引標籤。  
    >   
    >  在概念上，將會從傳送者與接收者辨識符號與在通知的內容屬性中所設定值相同的任一個單向協議索引標籤中挑選通知的屬性。 但為便於實際應用，通常會在您所建立由交換解析而成之協議的其他單向協議索引標籤中設定此屬性。  
  
-   您可以擁有一個編碼協議 (以定義訊息使用的訊息編碼) 與一個傳輸協議 (以定義交換訊息時使用的傳輸通訊協定)。 您必須擁有編碼協議。 如果兩個合作對象都要使用 AS2 通訊協定來傳輸訊息，可以選擇僅擁有 AS2 協議。 例如，如果兩個合作對象選擇透過電子郵件來傳輸訊息，則不需要 AS2 協議。  
  
    > [!NOTE]
    >  如需有關 AS2 協議的詳細資訊，請參閱[設定 AS2 協議屬性](../core/configuring-as2-agreement-properties.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定 X12 特有協議屬性](../core/configuring-x12-specific-agreement-properties.md)  
  
-   [設定 EDIFACT 特定協議屬性](../core/configuring-edifact-specific-agreement-properties.md)