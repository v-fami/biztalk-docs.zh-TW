---
title: 低延遲案例 Optimizations2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19cd78ce-ad7d-4e4b-8188-a63d707905d5
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9e5c8c5e225239461c9509aa50c105e4181ba12
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978623"
---
# <a name="low-latency-scenario-optimizations"></a>低延遲案例最佳化
根據預設，BizTalk Server 會適合輸送量，而不是低延遲而定。 下列最佳化可以套用至 BizTalk Server，在案例中需要較低的延遲的情況。  
  
> [!NOTE]  
>  這些最佳化會改善延遲，但貴用戶得於某些整體輸送量成本。  
  
## <a name="increase-the-biztalk-server-host-internal-message-queue-size"></a>增加 BizTalk Server 主控件的內部訊息佇列大小  
 每個 BizTalk 主控件都有它自己內部的記憶體中佇列。 增加此佇列從 100 到 10000 以提升效能的低延遲案例的預設值的大小。 如需有關如何修改的內部訊息佇列大小值的詳細資訊，請參閱[修改資源型節流設定如何](http://go.microsoft.com/fwlink/?LinkID=208366)(http://go.microsoft.com/fwlink/?LinkID=208366) BizTalk Server 文件。  
  
> [!NOTE]  
>  增加內部訊息佇列大小值會增加主控件執行個體所使用的記憶體。  
  
## <a name="increase-the-biztalk-server-host-in-process-messages"></a>增加 BizTalk Server 主控件的內含式訊息  
 增加同處理序訊息從 1000年到 10,000 的預設值，以改善效能。 如需有關如何修改值的內含式訊息的詳細資訊，請參閱[如何修改預設主控件節流設定](http://go.microsoft.com/fwlink/?LinkID=208366)(http://go.microsoft.com/fwlink/?LinkID=208366) BizTalk Server 文件。  
  
> [!NOTE]  
>  增加內部訊息佇列大小值會增加主控件執行個體所使用的記憶體。  
  
## <a name="optimize-orchestrations-for-low-latency"></a>最佳化低延遲的協調的流程  
 請遵循 < 最佳化的低延遲案例的協調流程的建議 > 一節中的建議[協調流程的效能最佳化](../technical-guides/optimizing-orchestration-performance.md)。  
  
## <a name="configure-polling-intervals"></a>設定輪詢間隔  
 若要設定輪詢間隔，指定主控件的 BizTalk 群組中使用設定儀表板。 若要變更輪詢間隔：  
  
1. 在  **BizTalk Server 管理主控台**，展開**BizTalk Server 管理**，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **設定**.  
  
2. 在  **BizTalk 設定儀表板**對話方塊的 **主機**頁面上**一般**索引標籤之下**輪詢間隔**，您會發現**Messaging**並**協調流程**值。 根據預設，這兩個值會設定為 500 毫秒。  
  
   下表列出我們用於測試 BizTalk 內含式 64 位元主控件 （RxHost，把 TxHost 和 PxHost） 上的輪詢值。 停用輪詢，您可以設定輪詢間隔，到非常大的數字，以列出資料表中。  
  
|伺服器主機|Messaging (傳訊)|協調流程|  
|------------------|---------------|-------------------|  
|**RxHost**<br /><br /> 因為我們只會發佈內送訊息到 BizTalk 訊息方塊，透過單向接收位置、 RxHost 上不需要輪詢 （接收主控件）。|200000|200000|  
|**把 TxHost**<br /><br /> 因為我們只會從 BizTalk messagebox 接收傳訊執行個體，把 TxHost （傳送主機） 上不需要輪詢的協調流程。|50|200000|  
|**PxHost**<br /><br /> 因為我們只會從 BizTalk messagebox 接收協調流程執行個體，通訊輪詢上不需要 PxHost （處理主控件）。|200000|50|  
  
## <a name="see-also"></a>另請參閱  
 [最佳化 BizTalk Server 效能](../technical-guides/optimizing-biztalk-server-performance.md)