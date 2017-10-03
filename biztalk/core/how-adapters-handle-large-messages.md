---
title: "配接器如何處理大型訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c48671fd-b6cf-4507-92b4-35a4cd135714
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fccfd1e988dc1395f14d6eb92a980ede184d0e0f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-adapters-handle-large-messages"></a>配接器如何處理大型訊息
「BizTalk 傳訊引擎」可處理非常大型的訊息，且不會限制訊息的最大大小。 但是，您應考慮限制訊息的大小，以維護最佳效能及資源管理。 隨著訊息大小的增加，每秒鐘可處理的訊息數量會跟著減少。 在設計您的案例及規劃容量時，請考慮 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所處理的平均訊息大小、訊息類型以及訊息數量。  
  
## <a name="stream-based-processing"></a>以資料流為基礎的處理  
 請注意在開發配接器時，大型訊息的處理是很重要的。 Microsoft 強烈建議您將整個資料流載入記憶體中時，務必考慮資料流的大小，否則這可能會停止 BizTalk Server 程序。 視在指定時間引擎所處理的訊息大小和數量而定，虛擬記憶體很低時可能會造成問題。 訊息應以下列資料流處理方式進行處理：  
  
-   **輸入的訊息。** 對於輸入訊息，接收配接器會將資料流的「提取」動作保留給「BizTalk 傳訊引擎」，將網路資料流附加至 BizTalk 訊息。  
  
-   **輸出訊息。** 對於輸出訊息，配接器會負責提取資料流。 這可有效地從 MessageBox 資料庫和透過傳送管線提取資料流。 配接器應透過連線以資料流處理方式傳送資料。  
  
 下圖顯示在「傳訊引擎」接收端上，以資料流為基礎的處理。  
  
 ![](../core/media/streambasedprocessing.gif "Streambasedprocessing")  
  
 配接器在提交訊息到引擎時，應會將其資料流附加到 BizTalk 訊息。 對某些配接器而言，這可能表示實作網路資料流。 訊息提交之後，引擎就會執行接收管線。 在管線執行時，想要變更資料的管線元件會複製該資料，將資料流從新訊息連線到上一個訊息上的資料流。 管線執行之後，「傳訊引擎」會從管線取出訊息，並執行迴圈，讀取該訊息上的資料流。 這個讀取資料流的動作會在上一個資料流上叫用讀取，接著又在上一個資料流叫用讀取，依此類推，一直回到網路資料流。 引擎會定期排清資料到 MessageBox，以維護一般記憶體模型。  
  
 **疑難排解秘訣：**在傳送端，配接器會負責讀取資料流。 如果傳送配接器想要讀取任何在傳送管線中升級或寫入的訊息內容屬性，在讀取整個資料流之前，這些屬性可能不會被寫入。 只有當資料流已完全讀取時，配接器才可確定所有管線元件都已完成執行。  
  
## <a name="locating-a-specific-byte-in-the-stream"></a>找出資料流中的特定位元組  
 在某些案例中，配接器可能需要從頭找回資料流，處理需要擱置的失敗訊息。 舉例來說，HTTP 配接器會使用區塊編碼接收資料，提交請求-回應組中的回應訊息。  
  
 但是，在許多案例中您可能無法追蹤資料流。 例如，請考慮使用區塊編碼接收資料的 HTTP 配接器。 如果要進行設計的資料流讓您尋找失敗的訊息，則配接器在讀取資料的同時，必須將其快取到記憶體或磁碟中。 很明顯的，這無法達到最佳效果，且需要額外的資源。 此外，許多現成的管線元件都是以 Forward-Only 資料流處理方式運作。 這些案例在 SDK 中的 BaseAdapter 會使用呼叫的協助程式類別**VirtualStream**。 包含此功能的檔案稱為 VirtualStream.cs。  
  
> [!NOTE]
>  VirtualStream.cs 檔案位於「管線 SDK 範例」下的兩個位置中 — SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler 和 SDK\Samples\Pipelines\SchemaResolverComponent\SchemaResolverFlatFileDasm。  
  
 虛擬資料流背後的概念就是資料流中的資料在到達閾值之前，會快取在記憶體資料流中，超過閾值時，資料會溢位到磁碟的安全位置。 資料流關閉之後，就會自動刪除磁碟檔案。 Forward-Only 資料流可使用這種方式設計。