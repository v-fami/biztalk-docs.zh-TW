---
title: 訊息考量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ca466fa-426c-46f6-a400-747ff51ff8f4
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d8a9bcf8b2910f12183db33aa27a74b550c72b8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979679"
---
# <a name="message-considerations"></a>訊息考量
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供傳送、 接收、 轉換和處理訊息的一組廣泛的功能。 這些功能包括：  
  
- 傳送和接收訊息使用多個業界標準傳輸例如 HTTP、 SMTP、 FTP/FTPS 及 WCF 的能力。 使用完成的傳送和接收訊息的傳輸層級支援[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器。 整合[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]訊息處理與各種 「 企業營運 」 (LOB) 應用程式使用任一種可用來完成[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]加速器或配接器，例如 BizTalk Accelerator for HIPAA，BizTalk Accelerator for SWIFT或 SAP BizTalk 配接器。 這些加速器和配接器符合業界標準，可接著將直接整合[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與符合特定的業界標準的系統。  
  
- 處理多個訊息格式，例如純文字、 XML、 二進位和其他人的能力。 這項功能，請務必提供整合[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與廣泛的交易夥伴。  
  
- 訊息轉換或文件對應的支援。 對應可容納資料不同的結構描述之間的轉換。 例如，對應可以用於將收到的客戶訂單的內容轉換成要傳送回給客戶的出貨通知的回條。  
  
- BizTalk Server 協調流程會提供建立跨越時間、 組織、 應用程式和人員的商務程序的功能。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供協調流程設計師 」 圖形化介面，以開發包含交易 （傳統 「 不可部分完成 」 的 MSDTC 類型和長時間執行），支援的商務程序的例外狀況處理、 偵錯、 追蹤和擴充性呼叫外部程式碼。  
  
  > [!NOTE]
  >  請參閱[協調流程的效能最佳化](../technical-guides/optimizing-orchestration-performance.md)如需有關使用中的協調流程時要遵循的最佳作法指導[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 請參閱主題[建立協調流程使用協調流程設計師](http://go.microsoft.com/fwlink/?LinkId=158997)(<http://go.microsoft.com/fwlink/?LinkId=158997>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件，如需使用協調流程設計師 」 的深入資訊。  
  
  本主題的其餘部分說明 BizTalk Server 環境中處理訊息的大小、 複雜度和發佈設定檔相關的效能考量。  
  
## <a name="message-size-considerations"></a>訊息大小的考量  
 雖然 BizTalk Server 不會限制訊息大小，實際限制和相依性可能會需要您的訊息大小降到最低，因為大型訊息需要更多的處理資源。 做為訊息大小增加，整體輸送量 （每秒處理的訊息） 會降低。 當設計您的案例和規劃容量，請考慮平均訊息大小、 訊息類型和 BizTalk Server 處理的訊息數目。 請勿使用不必要地過長的屬性和標記的名稱;可能的話，請保留長度達 50 個字元。 比方說，不使用訊息的大小只有 1 個位元組的 200 個字元的標記名稱。  
  
 如果接收的訊息之記憶體中大小超過的大型訊息分割大小 （可在 BizTalk 群組，BizTalk Server 管理主控台中的 群組屬性 頁面上設定） 所指定的位元組數目，訊息會分割成片段指定的大小。 此外，片段會寫入至 Messagebox 的 Microsoft Distributed Transaction Coordinator (MSDTC) 交易內容下，如下所示：  
  
1. 如果內送訊息正在現有 MSDTC 交易的內容中發行，寫入 BizTalk MessageBox 資料庫中的訊息片段時，就是會使用這筆交易。 例如，若內送訊息在設定為需要交易的交易配接器發佈，現有的交易時，會使用訊息分割寫入 MessageBox 資料庫。  
  
2. 如果不在現有 MSDTC 交易的內容中發佈內送訊息，將訊息分割寫入 MessageBox 資料庫建立新的 MSDTC 交易。 在此案例中，適用下列考量：  
  
   -   增加的值**大型訊息分割大小**以減少與大型訊息會分割並降低建立關聯的 MSDTC 交易的發生率的頻率。 您應該執行此動作，因為從效能觀點來看，過度使用 MSDTC 交易的代價很高。 請注意，增加此值也可能增加使用的可用記憶體量。  
  
   -   如果花超過最大允許 MSDTC 交易的逾時 60 分鐘的時間才能將訊息寫入 MessageBox，異動會逾時，發生錯誤，而且嘗試將訊息寫入失敗，且會回復。 **大型訊息分割大小**值應該增加足夠處理非常大型的訊息時避免發生這個問題。 視可用的記憶體而定，此值最多可增加到 1000000 個位元組的值。  
  
   -   訊息中的每個訊息分割都會對 MessageBox 資料庫建立一或多個 SQL Server 資料庫鎖定。 當鎖定數目超過數十萬時，就可以在 SQL Server，將會產生 「 鎖定不足 」 錯誤。 如果發生此問題，請增加值**大型訊息分割大小**来減少片段的數目 （這會降低對 MessageBox 資料庫的 SQL Server 資料庫鎖定數目），或考慮罩您在 64 位元版本的 SQL Server 上的 MessageBox 資料庫。 可用鎖定數目遠比 SQL Server 64 位元版本，在 32 位元版本的 SQL Server 上。 下列公式可用來估計時的 MessageBox 資料庫就會放在 32 位元版本的 SQL Server 上的每個交換的訊息數目上限：  
  
       ```  
       200,000 / (Number of CPUs * BatchSize * MessagingThreadPoolSize)  
       ```  
  
   如需有關 BizTalk Server 如何處理大型訊息，包括指導方針處理大型訊息，請參閱[如何 BizTalk Server 處理大型訊息](http://go.microsoft.com/fwlink/?LinkID=154680)(http://go.microsoft.com/fwlink/?LinkID=154680)。  
  
## <a name="message-type-considerations"></a>訊息類型考量  
 訊息接收至 BizTalk Server 中有兩種主要格式： XML 檔或一般檔案。 訊息類型應該永遠納入訊息發佈設定檔因為 XML 和一般檔案訊息的不同資源需求。  
  
-   **XML 檔案**為了讓 BizTalk Server 可以執行任何處理以外傳遞路由訊息，訊息必須是 XML 檔案格式。  
  
-   **一般檔案**一般檔案必須先剖析為 XML 格式，BizTalk Server 才能執行任何處理，而不傳遞路由。 將一般檔案剖析為 XML 檔案會大幅增加檔案大小。 一般檔案不包含 XML 標記及其資料的描述性資訊。 XML 檔案，相反地，可包裝其所有資料具描述性的 XML 標記。 在某些情況下，剖析可以增加一般檔案的大小的 10 個或以上，取決於描述性資料包含檔案的 XML 標記中。  
  
-   **一般檔案文件包裝在 XML 文件中單一 CDATA 區段節點**此文件類型的 XML 和一般檔案組合，而且通常是需要大量的記憶體，因為 BizTalk Server 必須載入整個包裝成一般檔案文件處理它之前的記憶體。  
  
## <a name="overload-considerations"></a>多載考量  
 大部分的 BizTalk Server 應用程式不會收到訊息的速率特定的常數。 一般而言，訊息處理受限於尖峰和離峰期。 例如線上銀行應用程式可能會處理更大量的訊息第一件事在早上，然後在中間一天，並在一天結束時。 BizTalk Server 解決方案應該經過測試，以確保它們將會無法處理這些多載案例。 若要判斷以及 BizTalk Server 解決方案可以處理多載案例，應該決定 BizTalk Server 解決方案的最大持續輸送量 (MST)。 MST 是在生產環境中的系統可無限處理的訊息流量最高的負載。 如需 MST 的詳細資訊，請參閱[持續性效能規劃](http://go.microsoft.com/fwlink/?LinkID=158065)(<http://go.microsoft.com/fwlink/?LinkID=158065>) 和[何謂持續性效能？](http://go.microsoft.com/fwlink/?LinkID=132304) (<http://go.microsoft.com/fwlink/?LinkID=132304>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件。  
  
## <a name="schema-complexity"></a>結構描述複雜度  
 結構描述的複雜性會影響 （尤其是一般檔案剖析） 剖析訊息輸送量。 當結構描述複雜度增加時，會降低整體效能。 在設計結構描述時，減少的節點名稱的長度，並移至結構描述頂端的 升級的屬性。 這可減少擷取時間，並藉此提高效能。  
  
## <a name="map-complexity"></a>對應複雜度  
 根據對應的複雜度，對應 」 轉換可以是需要大量資源。 做為對應複雜度增加，整體效能會降低。 若要改善整體效能，最小化連結和運算質用於您的對應，特別是呼叫外部的資源，例如 「 資料庫尋查 」 運算質的運算質的數目。  
  
## <a name="flat-file-parsing-considerations"></a>一般檔案剖析的考量  
 最高影響效能的一般檔案剖析的兩個因素是檔案大小和結構描述的複雜度。 模稜兩可的結構描述是結構描述，其中包含許多的選擇性欄位。 大型檔案大小時使用時，有許多選擇性欄位的結構描述會降低效能，因為較大的檔案可能符合的結構描述的不同分支。 結構描述複雜性會影響較少上比在較大的檔案較小的檔案。  
  
## <a name="see-also"></a>另請參閱  
 [最佳化 BizTalk Server 應用程式](../technical-guides/optimizing-biztalk-server-applications.md)