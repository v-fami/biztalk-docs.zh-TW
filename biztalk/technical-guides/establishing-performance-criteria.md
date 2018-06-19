---
title: 建立效能準則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 181011d1-aa74-43fe-b05a-30b043956d70
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5317445a5cf7e1e0b3fc07ab6ac301c764501460
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299982"
---
# <a name="establishing-performance-criteria"></a>建立效能準則
BizTalk Server 解決方案的效能目標通常會歸類到其中的兩個類別目錄、 輸送量或延遲。 本主題說明評估輸送量或延遲的 BizTalk Server 解決方案時，應考量的因素。  
  
> [!NOTE]  
>  最佳化輸送量或延遲的 BizTalk Server 解決方案通常代表發生衝突的目標。 例如，您可能會改善輸送量的檔案接收配接器藉由增加批次大小，但這樣做會減少延遲。 在此案例中配接器會累積較大的批次大小，接著會減少指定訊息的端對端延遲的訊息較長的時間。  
  
## <a name="factors-affecting-throughput-of-a-biztalk-server-solution"></a>影響輸送量，BizTalk Server 解決方案的因素  
 **輸送量**-廣泛測量在給定的時間間隔內可以處理 BizTalk Server 解決方案的文件的數目。  
  
 影響輸送量的因素包括：  
  
-   **訊息大小**– 較大的訊息會耗用更多成本負擔比 「 較小的訊息，尤其是會以對應轉換的訊息，並使它們緩衝至檔案系統對應作業期間值大到足以。 如需如何訊息大小會影響 BizTalk Server 效能的詳細資訊，請參閱[如何 BizTalk Server 處理大型訊息](http://go.microsoft.com/fwlink/?LinkId=139293)(http://go.microsoft.com/fwlink/?LinkId=139293)。  
  
-   **訊息格式**-訊息接收至 BizTalk Server 中兩種主要格式、 XML 檔案或一般檔案之一。 一般檔案必須轉譯成可由 「 BizTalk 傳訊引擎所處理之 XML 格式，因為一般檔案處理造成額外負擔。  
  
-   **配接器需求**– 不同配接器通常會有不同的效能功能。 例如，需要 MSDTC 交易支援的配接器將會產生相較於不使用 MSDTC 交易的配接器的額外負擔/降低效能。 BizTalk 方案所使用的配接器會根據交易夥伴的需求和 （或） 內部的商務需求而有所不同。  
  
-   **協調流程處理需求**： 協調流程可提供更多的彈性來封裝，將商務程序套用至訊息 BizTalk 收到的。 同時，協調流程會耗用額外負荷，估計的輸送量，BizTalk Server 解決方案時，必須考量。  
  
-   **尖峰負載需求**– 大部分文件處理不一定會進行測量以正確順序的方式。 例如，BizTalk Server 解決方案可能承受大量百分比的在營業日結束其處理負載。 因此尖峰負載需求和最大持續輸送量 (MST) 的 BizTalk Server 解決方案應該要列入考量時建立的輸送量準則。 如需測量 MST 的 BizTalk Server 解決方案的詳細資訊，請參閱[測量最大持續引擎輸送量](http://go.microsoft.com/fwlink/?LinkID=154388)(http://go.microsoft.com/fwlink/?LinkID = 154388) 和[測量最大持續性追蹤輸送量](http://go.microsoft.com/fwlink/?LinkID=153815)(http://go.microsoft.com/fwlink/?LinkID = 153815)。  
  
-   **文件追蹤需求**– 文件追蹤會加諸的系統上的額外負擔。 文件追蹤需求估計輸送量的目標是 BizTalk 解決方案時，應該是主要的考量。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 效能測試方法](../technical-guides/biztalk-server-performance-testing-methodology.md)