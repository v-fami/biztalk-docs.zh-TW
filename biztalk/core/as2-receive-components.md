---
title: "AS2 接收元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bdab87fd-15b9-4e3c-a4d7-984693262293
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c919a54a307a234237dd4086a0abf2a2c0c2fd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="as2-receive-components"></a>AS2 接收元件
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用數種元件接收 AS2 訊息。  
  
## <a name="as2-receive-pipelines"></a>AS2 接收管線  
 大部分的 AS2 接收處理都是在下列 AS2 接收管線中執行。 這些管線安裝在`Microsoft.BizTalk.EdiInt.PipelineComponents.dll`\Program Files\Microsoft 20xx\Pipeline 的 BizTalk Server 元件中\\。  
  
 **AS2EdiReceive 管線**  
  
 這個管線會處理透過 AS2 接收的 EDI 訊息，包括 MDN。 這個管線包含下列管線元件：  
  
-   AS2 解碼器  
  
-   EDI 解譯器  
  
-   BatchMarker  
  
    > [!NOTE]
    >  使用 AS2EdiReceive 管線時，您必須將用來執行 BizTalk 外掛式主控件執行個體處理序的使用者帳戶新增至 BizTalk 應用程式使用者群組。 AS2EdiReceive 管線會在 BizTalk 外掛式主控件執行個體處理序中執行。 AS2EdiReceive 管線會存取 SSO 存放區，而此存放區會要求使用者必須是「BizTalk 應用程式使用者」群組中的成員。  
  
 **AS2Receive 管線**  
  
 這個管線會處理透過 AS2 接收但非 EDI 編碼的訊息， 並且將這些訊息視為二進位訊息。 這個管線也會處理透過 AS2 接收的 MDN。 這個管線包含下列管線元件：  
  
-   AS2 解碼器  
  
-   AS2 解譯器  
  
## <a name="as2-receive-pipeline-components"></a>AS2 接收管線元件  
 AS2 接收管線會使用下列管線元件。 這些元件安裝在`Microsoft.BizTalk.EdiInt.PipelineComponents.dll`\Program Files\Microsoft 20xx\Pipeline 的 BizTalk Server 元件中\\。  
  
> [!NOTE]
>  只有在 32 位元 BizTalk 主控件程序中，才支援 AS2 接收管線。  
  
 **AS2 解碼器**  
  
 「AS2 解碼器」包含在 AS2EDIReceivePipeline 和 AS2Receive 接收管線的解碼階段中。 它使用「BizTalk S/MIME 管線元件」，為 AS2 和 MDN 訊息提供 S/MIME 解碼功能。  
  
-   處理 AS2/HTTP 標頭  
  
-   如果訊息已簽署，便驗證簽章  
  
-   如果訊息已加密，便解碼訊息 (適用於 EDI/AS2 訊息，而非 MDN)  
  
-   如果訊息已壓縮，便解壓縮訊息  
  
-   協調收到的 MDN 與原始輸出訊息  
  
-   在不可否認性的資料庫中更新記錄並使其相互關聯  
  
-   寫入 AS2 狀態報告的記錄  
  
    > [!NOTE]
    >  如果接收端處理 AS2 訊息期間發生錯誤，「AS2 解碼器」會停止進一步的下游訊息處理 (例如，EDI 解譯器將不會剖析交換)。 不過，「AS2 解譯器」或「EDI 解譯器」仍必須產生 MDN。  
  
    > [!NOTE]
    >  AS2 訊息使用八位元編碼， Base64 編碼只適用於 AS2 訊息和 MDN 中的簽章。  
  
 **AS2 解譯器**  
  
 在 AS2Receive 接收管線中，「AS2 解譯器」會執行下列動作：  
  
-   判斷 MDN 是否必要，以及 MDN 應該是同步還是非同步。  
  
-   產生 AS2 MDN。  
  
-   如果是同步 MDN，則會將 `EdiIntAS.IsAS2AsynchronousMDN` 屬性設定為 False；如果是非同步的 MDN，則會將該屬性設定為 True。  
  
-   針對 MDN 設定相互關聯 Token 和屬性。  
  
 **EDI 解譯器**  
  
 在 AS2EDIReceivePipeline 中，「EDI 解譯器」會將 EDI 訊息剖析為中繼 XML 訊息以供處理。 如需詳細資訊，請參閱[EDI 解譯器的運作方式](../core/how-the-edi-disassembler-works.md)。  
  
 **BatchMarker**  
  
 在 AS2EDIReceivePipeline 中，BatchMarker 管線元件會設定批次交換處理所需的兩個內容屬性：AgreementPartIdForSend 和 ToBeBatched。 此元件包含在 AS2EDIReceive 管線的最後一個階段 （協議解析）。 所有將批次處理 EDI 訊息的管線都應該包含 BatchMarker 管線元件。  
  
> [!NOTE]
>  BatchMarker 管線元件不會包含在用來處理非 EDI 訊息的 AS2Receive 管線中。 不過，您可以在不包含「EDI 解譯器」的自訂接收管線中加入 BatchMarker 元件。 如需詳細資訊，請參閱 「 非 EDI 訊息在 BatchMarker 元件處理 >[組合批次 EDI 交換](../core/assembling-a-batched-edi-interchange.md)。  
  
## <a name="http-adapter"></a>HTTP 配接器  
 接收埠和位置用於 AS2 處理使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HTTP 配接器。 HTTP 配接器設定適用於單向或要求-回應傳輸。  
  
## <a name="non-repudiation-database"></a>不可否認性的資料庫  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用不可否認性的資料庫 (BizTalkDTADb 資料庫的 EdiMessageContent 資料表) 來執行下列動作：  
  
> [!NOTE]
>  只有在已核取其中一個不可否認性的儲存區協議屬性時，BizTalkDTADb 資料庫中才有 EdiMessageContent 資料表。  
  
-   為已簽署的 MDN 提供不可否認性的線索  
  
-   使輸出訊息與其內送 MDN 相互關聯  
  
-   儲存各種狀態變更的訊息  
  
-   使錯誤碼與 HTTP 回應和 MDN 產生關聯  
  
-   根據篩選準則顯示記錄  
  
-   封存已標示的記錄  
  
> [!IMPORTANT]
>  為了確保不可否認性接收資料庫中所儲存訊息的真實性和完整性，資料庫中將儲存的所有訊息，包括原始 AS2 訊息和 MDN，都應使用數位簽章。 如需詳細資訊，請參閱的 9.1 節 < [RFC 1430、 」 以 MIME 為基礎安全端對端商務資料交換使用 HTTP，Applicability Statement 2 (AS2) >](http://go.microsoft.com/fwlink/?LinkID=184212) ([http://go.microsoft.com/fwlink/?LinkID=184212](http://go.microsoft.com/fwlink/?LinkID=184212))。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md)