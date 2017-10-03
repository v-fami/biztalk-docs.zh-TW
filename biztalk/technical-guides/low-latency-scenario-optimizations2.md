---
title: "低延遲案例 Optimizations2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19cd78ce-ad7d-4e4b-8188-a63d707905d5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 009b1298e90b586830f062c8e884b88995f9e33f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="low-latency-scenario-optimizations"></a>低延遲案例最佳化
根據預設，BizTalk Server 已最佳化輸送量，而不是低度延遲。 下列最佳化可以套用至 BizTalk Server 中，在案例中需要減少的延遲的地方。  
  
> [!NOTE]  
>  這些最佳化將會改善延遲，但可能在某些整體輸送量成本。  
  
## <a name="increase-the-biztalk-server-host-internal-message-queue-size"></a>增加 BizTalk Server 主控件的內部訊息佇列大小  
 每個 BizTalk 主控件都有它自己內部記憶體中佇列。 增加此佇列，從 100 到 10000 來改善低延遲案例的效能的預設值的大小。 如需修改內部訊息佇列大小值的詳細資訊，請參閱[如何修改資源基礎節流設定](http://go.microsoft.com/fwlink/?LinkID=208366)(http://go.microsoft.com/fwlink/?LinkID=208366) 中的 BizTalk Server 文件。  
  
> [!NOTE]  
>  增加內部訊息佇列大小值會增加主控件執行個體所使用的記憶體。  
  
## <a name="increase-the-biztalk-server-host-in-process-messages"></a>增加 BizTalk Server 主控件的內含式訊息  
 增加 1000年到 10000 的預設值的內含式訊息來改善效能。 如需修改內含式訊息的值的詳細資訊，請參閱[如何修改預設主控件節流設定](http://go.microsoft.com/fwlink/?LinkID=208366)(http://go.microsoft.com/fwlink/?LinkID=208366) 中的 BizTalk Server 文件。  
  
> [!NOTE]  
>  增加內部訊息佇列大小值會增加主控件執行個體所使用的記憶體。  
  
## <a name="optimize-orchestrations-for-low-latency"></a>最佳化低延遲的協調的流程  
 請遵循 < 最佳化的低延遲案例的協調流程的建議 > 一節中的建議[最佳化協調流程效能](../technical-guides/optimizing-orchestration-performance.md)。  
  
## <a name="configure-polling-intervals"></a>設定輪詢間隔  
 使用設定儀表板地在整個 BizTalk 群組中設定某個主控件的輪詢間隔。 若要變更輪詢間隔：  
  
1.  在**BizTalk Server 管理主控台**，依序展開**BizTalk Server 管理**，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **設定**.  
  
2.  在**BizTalk 設定儀表板**對話方塊**主機**頁面上**一般**索引標籤，下方**輪詢間隔**，您會發現**傳訊**和**協調流程**值。 根據預設，這兩個值會設定為 500 毫秒。  
  
 下表列出我們用於測試 BizTalk 內含式 64 位元主控件 （RxHost、 TxHost 和 PxHost） 上的輪詢值。 若要停用輪詢，您可以設定的輪詢間隔非常大的數字，做為資料表中列出。  
  
|伺服器主機|Messaging (傳訊)|協調流程|  
|------------------|---------------|-------------------|  
|**RxHost**<br /><br /> 因為我們只會發佈內送訊息，BizTalk 訊息方塊，透過單向接收位置、 RxHost 不需要輪詢 （接收主控件）。|200000|200000|  
|**TxHost**<br /><br /> 因為我們只會從 BizTalk messagebox 收到傳訊執行個體，並沒有協調流程輪詢要求 TxHost （傳送主控件）。|50|200000|  
|**PxHost**<br /><br /> 因為我們只會從 BizTalk messagebox 接收協調流程執行個體，傳訊輪詢上並不需要 PxHost （處理主控件）。|200000|50|  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 效能最佳化](../technical-guides/optimizing-biztalk-server-performance.md)