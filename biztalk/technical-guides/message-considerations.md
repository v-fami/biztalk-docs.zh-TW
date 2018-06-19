---
title: 訊息考量 |Microsoft 文件
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
ms.openlocfilehash: a277149a47fa60dda4df9291ec437ac67c518fdd
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010831"
---
# <a name="message-considerations"></a>訊息的考量
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供傳送、 接收、 轉換和處理訊息的一組廣泛的功能。 這些功能包括：  
  
-   傳送和接收訊息使用的多個產業標準傳輸例如 HTTP、 SMTP、 FTP/FTPS 和 WCF 的功能。 使用完成的傳送和接收訊息的傳輸層級支援[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器。 整合[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]訊息處理的各種 「 商務營運 」 (LOB) 應用程式使用其中許多可用來完成[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作用的快速鍵或配接器，例如 BizTalk Accelerator for HIPAA，BizTalk Accelerator for SWIFT或 SAP BizTalk 配接器。 這些快速鍵和配接器符合業界標準依次適用於直接整合[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以符合特定的業界標準的系統。  
  
-   處理多個訊息格式，例如純文字、 XML、 二進位和其他人的能力。 這項功能非常重要提供的整合[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]相當廣泛的交易夥伴使用。  
  
-   訊息轉換或文件對應的支援。 對應可容納資料不同的結構描述之間的轉換。 例如，對應可用於將收到的客戶訂單的內容轉換成接收具有已傳送的通知送回給客戶。  
  
-   BizTalk Server 協調流程會提供建立跨越時間、 組織、 應用程式與人員的商務程序的功能。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供的協調流程設計師 」 圖形化介面來開發商務程序包含交易 （傳統 「 不可部分完成 」 的 MSDTC 型別和長時間執行），支援例外狀況處理、 偵錯、 追蹤，以及用於呼叫擴充性外部程式碼。  
  
    > [!NOTE]  
    >  請參閱[最佳化協調流程效能](../technical-guides/optimizing-orchestration-performance.md)如需有關使用中的協調流程時要遵循的最佳作法指導[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 請參閱主題[協調流程使用協調流程設計師建立](http://go.microsoft.com/fwlink/?LinkId=158997)(http://go.microsoft.com/fwlink/?LinkId=158997) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件，如需使用協調流程設計師 」 的深入資訊。  
  
 本主題的其餘部分描述的 BizTalk Server 環境中處理的訊息大小、 複雜度和發佈設定檔相關的效能考量。  
  
## <a name="message-size-considerations"></a>訊息大小的考量  
 BizTalk Server 不會限制訊息大小，而實際限制與相依性可能會要求您的訊息大小降到最低，因為大型訊息需要較多處理資源。 做為訊息大小增加，整體輸送量 （每秒處理的訊息） 則會減少。 當設計您的案例及規劃容量，請考慮平均訊息大小、 訊息類型以及 BizTalk Server 處理的訊息數目。 請勿使用不必要地過長的屬性和標記名稱。可能的話，請保留在 50 個字元長度。 例如，請勿選取 只有 1 個位元組的訊息大小的 200 個字元的標記名稱。  
  
 如果接收訊息的記憶體中大小超過指定的大型訊息分割大小 （可在 BizTalk Server 管理主控台中的 BizTalk 群組的群組屬性 頁面上設定） 的位元組數目，訊息會分割成片段指定的大小。 此外，片段會寫入至 Messagebox 的 Microsoft Distributed Transaction Coordinator (MSDTC) 交易內容下，如下所示：  
  
1.  如果內送訊息正在現有 MSDTC 交易的內容中發行，寫入 BizTalk MessageBox 資料庫中的訊息片段時使用此交易。 例如，如果內送訊息由設定為必要交易的交易配接器發佈，在現有的交易時，會使用訊息分割寫入 MessageBox 資料庫。  
  
2.  如果不在現有 MSDTC 交易的內容中發佈內送訊息，將訊息分割寫入 MessageBox 資料庫建立新的 MSDTC 交易。 在此案例中，適用下列考量：  
  
    -   增加的值**大型訊息分割大小**減少頻率與大型訊息片段化並減少建立關聯的 MSDTC 交易的發生率。 您應該執行此動作，因為從效能觀點來看，過度使用 MSDTC 交易的代價很高。 請注意，增加此值也可能增加使用的可用記憶體量。  
  
    -   如果花費超過最大可允許 MSDTC 交易逾時的 60 分鐘的時間才能將訊息寫入 MessageBox，異動會逾時，發生錯誤，而且嘗試將訊息寫入失敗，而是回復。 **大型訊息分割大小**值應該增加足夠處理非常大型的訊息時，避免發生這個問題。 視可用的記憶體而定，此值最多可增加到 1000000 個位元組的值。  
  
    -   訊息中的每個訊息分割都會對 MessageBox 資料庫建立一或多個 SQL Server 資料庫鎖定。 當鎖定數目超過數十萬時，很可能在 SQL Server 將會產生 「 鎖定不足 」 錯誤。 如果發生這個問題，增加的值**大型訊息分割大小**来減少片段的數目 （這會降低對 MessageBox 資料庫的 SQL Server 資料庫鎖定數目），或考慮外罩您在 64 位元版本的 SQL Server 上的 MessageBox 資料庫。 可用鎖定數目是明顯較嚴重的 32 位元版本的 SQL Server 上比 SQL Server 的 64 位元版本上。 下列公式可用來估計每個交換的訊息數目上限，MessageBox 資料庫就會放在 32 位元版本的 SQL Server 上時：  
  
        ```  
        200,000 / (Number of CPUs * BatchSize * MessagingThreadPoolSize)  
        ```  
  
 如需有關 BizTalk Server 如何處理大型訊息，包括下列方針： 處理大型訊息，請參閱[如何 BizTalk Server 處理大型訊息](http://go.microsoft.com/fwlink/?LinkID=154680)(http://go.microsoft.com/fwlink/?LinkID=154680)。  
  
## <a name="message-type-considerations"></a>訊息類型考量  
 訊息接收至 BizTalk Server 中有兩種主要格式： XML 檔或一般檔案。 訊息類型應該一律納入訊息發佈設定檔因為不同的資源需求的 XML 和一般檔案訊息。  
  
-   **XML 檔案**為了讓 BizTalk Server 可以執行任何處理以外傳遞路由訊息，訊息必須是 XML 檔案格式。  
  
-   **一般檔案**一般檔案必須剖析成 XML 格式，BizTalk Server 才能執行任何處理，而不傳遞路由。 將一般檔案剖析為 XML 檔案會大幅增加檔案大小。 一般檔案不包含 XML 標記及其資料的描述性資訊。 XML 檔案，相反地，包裝其所有資料中描述的 XML 標記。 在某些情況下，剖析可以增加的大小一般檔案中之檔案的 XML 標記包含 10 個或以上，取決於描述性資料多寡倍。  
  
-   **一般檔案文件包裝在 XML 文件中單一 CDATA 區段節點**這種類型的文件是 XML 和一般檔案的組合，通常是需要大量記憶體，因為 BizTalk Server 必須載入整個包裝成一般檔案文件處理它之前的記憶體。  
  
## <a name="overload-considerations"></a>多載考量  
 大部分的 BizTalk Server 應用程式不會收到訊息特定的固定的速率。 一般而言，訊息處理受限於尖峰和低峰期。 例如線上銀行應用程式可能會處理更大量的郵件首先在早上，然後在中間天，並在一天結束時。 BizTalk Server 解決方案應該經過測試，以確保它們能能夠處理這些多載案例。 若要判斷 BizTalk Server 方案可以處理多載案例程度，您應該決定 BizTalk Server 解決方案的最大持續輸送量 (MST)。 MST 是在生產環境中的系統可無限處理的訊息流量的最高負載。 如需 MST 的詳細資訊，請參閱[規劃維持效能](http://go.microsoft.com/fwlink/?LinkID=158065)(http://go.microsoft.com/fwlink/?LinkID=158065) 和[何謂持續性效能？](http://go.microsoft.com/fwlink/?LinkID=132304) (http://go.microsoft.com/fwlink/?LinkID=132304) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件。  
  
## <a name="schema-complexity"></a>結構描述複雜度  
 結構描述複雜度會影響訊息剖析 （特別是一般檔案剖析） 的輸送量。 當結構描述複雜度增加，則會減少整體效能。 在設計結構描述時，減少節點名稱的長度，然後移至結構描述頂端的 升級的屬性。 這可減少擷取時間，並藉此提升效能。  
  
## <a name="map-complexity"></a>對應複雜度  
 根據對應的複雜度，對應 」 轉換可以是需要大量資源。 為對應的複雜度增加，整體效能會降低。 若要改善整體效能，最小化連結與運算質用於您的對應，特別是呼叫外部資源，例如 「 資料庫尋查 」 運算質的運算質的數目。  
  
## <a name="flat-file-parsing-considerations"></a>一般檔案剖析的考量  
 一般檔案剖析的效能造成最高的影響力的兩個因素是檔案大小和結構描述複雜度。 模稜兩可的結構描述是結構描述，其中包含許多選擇性欄位。 大型檔案的大小使用時，具有許多選擇性欄位的結構描述會降低效能，因為較大的檔案可能符合的結構描述的不同分支。 結構描述複雜度會將較不會影響對比在更大的檔案較小的檔案。  
  
## <a name="see-also"></a>請參閱  
 [最佳化 BizTalk Server 應用程式](../technical-guides/optimizing-biztalk-server-applications.md)