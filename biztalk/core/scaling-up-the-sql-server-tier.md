---
title: 向上擴充 SQL Server 層 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, scaling
- scaling, examples
- SQL Server, scaling
- scaling, scaling up
- scaling, strategies
ms.assetid: 4352c4af-6861-43d9-b433-9ca25668b439
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c654c4a3b1bba166ae8a49918f6ef31827cf041
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269678"
---
# <a name="scaling-up-the-sql-server-tier"></a>向上擴充 SQL Server 層
在此模式中，會將現有的 SQL MessageBox 資料庫升級，使其可依據輸送量或延遲來擴充。  
  
 下圖所顯示的實例，是將主要 MessageBox 資料庫從四個程序伺服器升級到八個程序伺服器。  
  
 ![小數位數 &#45; 向上擴充 MSGBOX](../core/media/scaleupmsgbox2.gif "ScaleUpMsgBox2")  
  
## <a name="when-to-scale-up-the-sql-tier"></a>向上擴充 SQL 層的時機  
  
-   當您向上擴充主要 MessageBox 資料庫時。  
  
-   當主要 MessageBox 資料庫成為瓶頸時。 這些瓶頸可能是：  
  
    -   **CPU**發生非常昂貴和複雜的協調流程實例中，messagebox 會消耗大量的 CPU 資源。 藉由新增更多的 CPU 來向上擴充 SQL Server，應該會擴充此實例。  
  
    -   **記憶體或 I/O**記憶體或 I/O 可能是瓶頸且可以升級。  
  
-   當向上擴充比向外擴充便宜時，向上擴充即可處理該瓶頸。 例如，若主要 MessageBox 資料庫有 SQL 鎖定爭用的問題，則此問題無法藉由向上擴充來解決。  
  
## <a name="when-do-you-decide-sql-cannot-scale-up"></a>何時決定 SQL 無法向上擴充？  
 向上擴充無法處理 SQL 層上的鎖定爭用瓶頸。 若是遇到這類瓶頸，向外擴充是比向上擴充更好的選項。  
  
## <a name="strategies-and-considerations-for-scaling-up-the-sql-tier"></a>向上擴充 SQL 層的策略與考量  
  
-   先向上擴充主要 MessageBox 資料庫之後，再向外擴充。  
  
-   主要 MessageBox 資料庫最後會成為瓶頸。 因此，主要 MessageBox 資料庫應該更快且更大 (例如，Itanium 型 64 位元或 x64 型雙核心電腦)。  
  
## <a name="see-also"></a>另請參閱  
 [向外擴充 BizTalk Server 層](../core/scaling-out-the-biztalk-server-tier.md)   
 [向上擴充 BizTalk Server 層](../core/scaling-up-the-biztalk-server-tier.md)   
 [向外擴充 SQL Server 層](../core/scaling-out-the-sql-server-tier.md)   
 [向外擴充接收主控件](../core/scaled-out-receiving-hosts.md)   
 [向外延展處理主控件](../core/scaled-out-processing-hosts.md)   
 [向外延展傳送主控件](../core/scaled-out-sending-hosts.md)   
 [使用 Windows 伺服器叢集以提供高可用性的 BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)   
 [向外延展資料庫](../core/scaled-out-databases.md)   
 [叢集 BizTalk Server 資料庫](../core/clustering-the-biztalk-server-databases1.md)