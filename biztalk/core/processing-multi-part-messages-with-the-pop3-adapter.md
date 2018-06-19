---
title: 使用 POP3 配接器的處理多部分訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56ad041f-f155-4c1c-ab87-1405c80d9b68
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26aff4569414103ad8c4f37a9e4699a85874e481
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22266438"
---
# <a name="processing-multi-part-messages-with-the-pop3-adapter"></a>使用 POP3 配接器處理多部分訊息
POP3 配接器可以處理符合在 IETF 標準的 MIME 編碼訊息[RFC 2045](http://go.microsoft.com/fwlink/?LinkId=58810)， [RFC 2046](http://go.microsoft.com/fwlink/?LinkId=58811)，和[RFC 2047](http://go.microsoft.com/fwlink/?LinkId=58812)。 MIME 編碼訊息可以有一或多個內容類型不同的部分。 本主題將討論 POP3 配接器如何處理多部分 MIME 編碼訊息。  
  
## <a name="receiving-multi-part-messages-with-the-pop3-adapter"></a>使用 POP3 配接器接收多部分訊息  
 使用 POP3 配接器的接收位置是否有**套用 MIME 解碼**選項設定為**True**則 POP3 配接器接收 MIME 編碼訊息時，請執行下列動作：  
  
1.  從收到的 MIME 編碼訊息部分建立多部分 BizTalk 訊息。 這個多部分訊息可能包含一或多個部分，包含的部分數目會與所收到 MIME 編碼訊息的部分數目相同。  
  
2.  掃描 MIME 編碼訊息的標頭。 如果任何標頭符合所列主題中的屬性清單[POP3 配接器屬性結構描述和屬性](../core/pop3-adapter-property-schema-and-properties.md)然後這些標頭升級至多部分 BizTalk 訊息內容屬性。  
  
3.  使用可設定的演算法，將 MIME 編碼訊息的其中一個部分指定為 BizTalk 訊息內文部分。 用來決定哪一個訊息部分將 BizTalk 訊息內文部分的演算法如下一節所述**POP3 配接器所使用的內文部分選取演算法**。  
  
4.  將多部分 BizTalk 訊息發佈至 MessageBox。  
  
## <a name="body-part-selection-algorithm-used-by-the-pop3-adapter"></a>POP3 配接器使用的內文部分選取演算法  
 當 POP3 配接器從所收到 MIME 編碼訊息的部分建立多部分 BizTalk 訊息時，它會選取其中一個訊息部分做為 BizTalk 訊息內文部分。 BizTalk Server 會使用 BizTalk 訊息內文部分來執行訊息驗證、對應、屬性升級、一般檔案組合以及其他作業。 多部分 BizTalk 訊息的訂閱者會收到所有訊息部分，但除非使用可以瞭解多部分訊息的協調流程、自訂管線或配接器，否則只會使用指定的 BizTalk 訊息內文部分。 例如，您可以設定協調流程讀取多部分訊息的所有部分、SMTP 配接器可以讀取多部分訊息的所有部分，以及自訂管線經過設定後便可以使用 MIME/SMIME 編碼器管線元件。 如需使用協調流程取用多部分訊息詳細資訊，請參閱下節，**協調流程中處理多部分訊息**。  
  
 POP3 配接器會從提供的值為基礎的可用的內文部分選取 BizTalk 訊息內文部分**內文部分索引**和**內文部分內容類型**。  
  
> [!NOTE]
>  POP3 配接器可辨識的內文部分內容類型中定義的[RFC 2046](http://go.microsoft.com/fwlink/?LinkId=119569)。  
  
 下面說明用來選取電子郵件之 BizTalk 訊息內文部分的演算法：  
  
1.  如果**內文部分索引**設為 0 和**內文部分內容類型**為空白，則會使用下列演算法來選取 BizTalk 訊息內文部分：  
  
    -   使用 Content-Description 標頭設定為 "body" 的第一個 MIME 部分。  
  
    -   否則使用 Content-Type 標頭設定為 "text/xml" 的第一個 MIME 部分。  
  
    -   否則使用 Content-Type 標頭設定為 "text/plain" 的第一個 MIME 部分。  
  
    -   否則使用 Content-Type 標頭設定為 "text/" 的第一個 MIME 部分。  
  
    -   否則使用第一個 MIME 部分。  
  
2.  否則如果**內文部分索引**設為 0 和**內文部分內容類型**，則符合指定的內送訊息的第一個內文部分**內文部分內容類型**選定為 BizTalk 訊息內文部分。 如果沒有部分具有相符的內容類型，則訊息將遭擱置。  
  
3.  否則如果**內文部分索引**設為值大於 0 和**內文部分內容類型**為空白，則具有指定之索引的內文部分當做 BizTalk 訊息內文部分。 如果指定的索引大於內文部分數目，則訊息將遭擱置。  
  
4.  否則如果**內文部分索引**設為值大於 0 和**內文部分內容類型**設定，然後在**內文部分索引**僅會套用的主體組件的符合指定**內文部分內容類型**和對應的內文部分當做 BizTalk 訊息內文部分。 如果指定的索引大於內容類型相符的內文部分數目，則訊息將遭擱置。 如果沒有部分具有相符的內容類型，則訊息將遭擱置。  
  
5.  選取做為 BizTalk 訊息內文部分的部分會成為發佈至 MessageBox 之多部分 BizTalk 訊息的第一個部分，訊息的其餘部分則保留當初在原始 MIME 編碼訊息中的順序。  
  
## <a name="processing-multi-part-messages-in-orchestrations"></a>在協調流程中處理多部分訊息  
 當 POP3 配接器從接收的 MIME 編碼訊息建立多部分 BizTalk 訊息時，所有部分都會發佈至 MessageBox 資料庫，即使其中只有一個部分會指定為 BizTalk 訊息內文部分也一樣。 這些部分接著會由訂閱多部分訊息的協調流程使用。 本節將說明在協調流程中處理多部分訊息的一些考量。  
  
### <a name="processing-multi-part-messages-with-a-known-number-of-parts-and-known-part-types"></a>處理部分數目已知且部分類型已知的多部分訊息  
 如果協調流程接收的多部分訊息是已知部分數目且已知部分類型，則您可以在協調流程中宣告多部分訊息，然後在設計階段設定部分數目和部分類型。  
  
### <a name="processing-multi-part-messages-with-unknown-part-types"></a>處理部分類型未知的多部分訊息  
 如果您的協調流程接收多部分訊息部分類型未知，則您可以宣告多部分訊息在協調流程並使用**XmlDocument**每個組件的類型是未知的類型。  
  
### <a name="processing-multi-part-messages-with-an-unknown-number-of-parts-and-all-of-the-part-types-are-unknown"></a>處理部分數目未知且所有部分類型都未知的多部分訊息  
 如果您的協調流程接收多部分訊息的部分數目未知，則您可以宣告多部分訊息的單一組件與**XmlDocument**協調流程中接收訊息的類型。 如果收到包含大於宣告的部分數目的多部分訊息時，有多少部分是在訊息中的協調流程引擎讀取然後建構適當的部分類型符合的組件中宣告的訊息數目的組件類型，然後建構**XmlDocument**組件的其餘部分。