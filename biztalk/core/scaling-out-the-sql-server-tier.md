---
title: 向外擴充 SQL Server 層 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scaling, MessageBox database
- scaling, scaling out
- SQL Server, scaling
- MessageBox database, scaling
- scaling, strategies
ms.assetid: d5b2ebba-401e-4fde-8818-407fa626043a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8d8059f405907690f210191d60fee60af69f019
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972519"
---
# <a name="scaling-out-the-sql-server-tier"></a>向外擴充 SQL Server 層
針對每個 BizTalk 群組，加入一個主要 MessageBox 資料庫。 所有之後加入的 MessageBox 資料庫都稱為次要 MessageBox。 主要 MessageBox 會處理所有的訂閱和訊息路由， 而且還可以發佈訊息。 次要 MessageBox 資料庫只有在經過特別設定時，才會發佈訊息。  
  
## <a name="how-to-add-a-secondary-messagebox-database"></a>如何加入次要 MessageBox 資料庫  
 有兩個方式可以加入次要 MessageBox 資料庫：  
  
- 在相同的實體伺服器上加入次要 MessageBox 資料庫。  
  
   若現有的 MessageBox 實體伺服器有足夠的 CPU 與 I/O 資源，但是因鎖定爭用而遇到瓶頸。 請在個別的 IO 磁碟機上建立次要 MessageBox 資料庫。  
  
   優點：  
  
  -   另一個 message-box 可以利用額外的 CPU 空間  
  
  -   需要的 SQL Server 授權數目較少  
  
  -   網路躍點已排除  
  
- 在不同的實體伺服器上加入次要 MessageBox 資料庫  
  
   在此情況下，使用具有自己 IO 的專用實體伺服器做為額外的 MessageBox 資料庫。  
  
  下圖顯示一個實例，其中 SQL 層從 MessageBox 資料庫向外擴充為三個 MessageBox 資料庫。  
  
  ![向外擴充 MSGBOX](../core/media/scaleoutmsgbox.gif "ScaleOutMSGBOX")  
  
## <a name="when-to-scale-out-the-messagebox-database"></a>向外擴充 MessageBox 資料庫的時機  
  
-   MessageBox 資料庫變成瓶頸。 這些瓶頸可能是：  
  
    -   **CPU**非常昂貴和複雜的協調流程的情況下，如果 MessageBox 資料庫會耗用大量的 CPU 資源。 加入另一個發佈的 MessageBox 資料庫應該可以協助提升輸送量。  
  
    -   **鎖定爭用**具有多個主控件執行個體或協調流程的複雜案例通常會建立 MessageBox 資料庫上的鎖定爭用。 同樣的，加入另一個發佈的 MessageBox 資料庫應該可以協助提升輸送量。  
  
-   擴大資料庫不能處理瓶頸。 例如，如果主要 MessageBox 資料庫受限於鎖定爭用，唯一的選擇就是向外擴充。  
  
-   擴大資料庫的成本太高。 例如，如果升級現有的四處理器伺服器到 8 方式伺服器成本高於新增另一個四程序，向外延展是更好的選項。  
  
## <a name="when-you-cant-scale-out-the-sql-tier"></a>無法向外擴充 SQL 層時  
 理論上，只要主要 MessageBox 資料庫不是瓶頸，SQL 層應該可以無限擴充。 為了達成此目標，請考慮讓主要 MessageBox 資料庫變成非發佈資料庫，使它只能處理路由作業。 但是，如果主要資料庫因為鎖定爭用而產生瓶頸，您就再也不能向外擴充 SQL 層。  
  
## <a name="scale-out-strategies-and-considerations"></a>向外擴充策略與考量  
  
-   先擴大主要 MessageBox 資料庫然後再向外擴充。  
  
-   相應放大 1 至 3 的 SQL MessageBox 資料庫，而不是 1 到 2。 請考慮 1 如上圖所示的 SQL server 拓樸標題為"4 的 BizTalk Server，1 的 SQL Server 拓撲中，"，並假設 SQL server 是受 CPU 限制，也就是說，CPU 處理是瓶頸。 如果您只在這個拓樸中加入一個 MessageBox 資料庫，主要 Messagebox 仍然會受限於 CPU 處理能力，而且次要 MessageBox 資料庫的利用率也會偏低。 因此，縮放比例是幾近於 1。 如果您停用主要 MessageBox 資料庫的發行，並設定專用主要 MessageBox 資料庫只是用來進行路由，次要 MessageBox 資料庫會處理發佈。 不過由於次要 MessageBox 資料庫是唯一的發佈者，而且仍然會成為瓶頸，因此這種方法對於提高整體輸送量並無任何幫助。 因此，在這個案例中，建議的向外擴充方法為加入 2 個次要 MessageBox 資料庫，並停用主要 MessageBox 資料庫的發佈功能。  
  
-   主要 MessageBox 資料庫最後都會變成瓶頸。 因此，裝載主要 MessageBox 資料庫的實體電腦應該具有較快的執行速度與較大的容量。  
  
-   為了讓透過網路傳送的資料量 (以及相關的 DTC 負擔) 降到最低，請考慮將多個 MessageBox 資料庫放在具有專用磁碟機的同一部實體電腦上。 同時，請確定儲存這些多個資料庫的電腦未遇到瓶頸，因為多個 MessageBox 資料庫會共用資源。  
  
-   所有的次要 MessageBox 資料庫都應該使用同等級的硬體，因為工作量會平均分配給這些 MessageBox 發佈資料庫。  
  
-   只要主要 MessageBox 資料庫沒有產生瓶頸，您就可以向外擴充次要 MessageBox 資料庫，因此在執行次要 MessageBox 資料庫的電腦上，其 CPU 資源可以低於主要 MessageBox 資料庫伺服器的需求。  
  
## <a name="see-also"></a>另請參閱  
 [向外擴充 BizTalk Server 層](../core/scaling-out-the-biztalk-server-tier.md)   
 [向上擴充 BizTalk Server 層](../core/scaling-up-the-biztalk-server-tier.md)   
 [向上擴充 SQL Server 層](../core/scaling-up-the-sql-server-tier.md)   
 [相應放大的接收主控件](../core/scaled-out-receiving-hosts.md)   
 [相應放大處理主控件](../core/scaled-out-processing-hosts.md)   
 [向外傳送主控件](../core/scaled-out-sending-hosts.md)   
 [使用 Windows Server 叢集為 BizTalk Server Hosts2 提供高可用性](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)   
 [相應放大的資料庫](../core/scaled-out-databases.md)   
 [叢集 BizTalk Server 資料庫](../core/clustering-the-biztalk-server-databases1.md)