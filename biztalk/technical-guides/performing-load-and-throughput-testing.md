---
title: 執行負載和輸送量測試 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2ff86ebd-a77f-4e29-bfea-0306e88bbf67
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3da46b2dc3208208305e60e9efbfadd0c60d7d32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302110"
---
# <a name="performing-load-and-throughput-testing"></a>執行負載和輸送量測試
您應該提供一個環境符合您的生產環境的效能和壓力測試。 此環境應該安裝和執行，例如監視代理程式和防毒軟體的所有標準服務。  
  
## <a name="how-adding-applications-affects-load"></a>如何新增應用程式會影響負載  
 您也應該測試新的 BizTalk 應用程式一起移至生產環境中的相同硬體上執行的其他 BizTalk 應用程式。 這是因為新的 BizTalk 應用程式放入執行的電腦上的額外負載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 SQL Server。 這點特別重要的主控件節流演算法中使用按照[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 節流演算法監視總計的可用資源，因此新的 BizTalk 應用程式所造成的額外負載可能誘使節流狀況，這會影響所有正在執行的 BizTalk 應用程式。 如需詳細資訊，請參閱[如何 BizTalk Server 實作主控件節流](http://go.microsoft.com/fwlink/?LinkId=154389)(http://go.microsoft.com/fwlink/?LinkId=154389)。  
  
## <a name="testing-load-and-determining-recovery-time"></a>測試負載，並決定復原時間  
 您應該測試所有的 BizTalk 應用程式的效能與壓力，才能將它們放入實際執行環境。 您應該執行測試對預期負載和尖峰負載。 您應該判斷 BizTalk 應用程式最大持續輸送量 (MST)。 此外，您應該決定從尖峰負載復原系統所需的時間。 如果系統不會完全復原時，從 尖峰負載下一步的尖峰負載之前，則系統會逐漸遠，並不能完全復原。 如需詳細資訊，請參閱：  
  
-   [測量最大持續性引擎輸送量](http://go.microsoft.com/fwlink/?LinkId=154388)(http://go.microsoft.com/fwlink/?LinkId=154388)  
  
-   [測量最大持續性追蹤輸送量](http://go.microsoft.com/fwlink/?LinkID=153815)(http://go.microsoft.com/fwlink/?LinkID=153815)  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單： 測試操作整備](../technical-guides/checklist-testing-operational-readiness.md)