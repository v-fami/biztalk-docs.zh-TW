---
title: 向外擴充 BizTalk Server 層 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, scaling
- scaling, planning
- scaling, load balancing
- host instances, scaling
- scaling, examples
- fault tolerance
- scaling, scaling out
- scaling, fault tolerance
- NLB system, scaling
- scaling, host instances
ms.assetid: 01d1ab20-d7a9-4d0b-a61e-65e56fe5010e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15439696cef510820d7e2354a5b0175537ab9d79
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023828"
---
# <a name="scaling-out-the-biztalk-server-tier"></a>向外擴充 BizTalk Server 層
若要向外擴充 BizTalk 層，請新增更多硬體至現有的拓撲。 建議您在下列情況下新增硬體：  
  
- BizTalk Server 成為瓶頸。 瓶頸本身可能是由於以下其中一個問題所造成：  
  
- CPU：若實例使用大量 CPU 管線、對應或協調流程，BizTalk Server 將不會有額外的 CPU 空間。  
  
- 記憶體和 I/O：若現有的電腦已經到達記憶體和 IO 的上限，增加資源的唯一方法是新增另一部實體電腦。  
  
- 擴充的成本太昂貴。 例如，考量一個 BizTalk CPU 處於最大容量的 BizTalk Server 拓撲。 若新增額外的雙處理器機器比將雙處理器升級為四處理器便宜，您應該向外擴充系統。  
  
- 擴充無法解決瓶頸。 下列情況下擴充可能無法解決問題：  
  
  -   BizTalk 電腦的 IO 已達最高層次，因此您需要另一台機器來擴充 IO。  
  
  -   作業系統的記憶體已達最高層次。 在此情況下，擴充系統的唯一方法是加入額外的 BizTalk 電腦到拓撲。  
  
  在某些情況下，您可能想要專用的伺服器來接收訊息、傳送訊息以及處理訊息。 當您擁有專用伺服器時，較容易在一台電腦上隔離問題和進行維護，不影響其他電腦。 您可以向外擴充 BizTalk 層來新增這些電腦。  
  
## <a name="when-you-cant-scale-out-the-biztalk-tier"></a>當您無法向外擴充 BizTalk 層時  
  
- MessageBox 資料庫成為瓶頸。  
  
- 配接器成為瓶頸。 例如，若使用的是 SQL 配接器，則在增加 BizTalk 接收器的數量之後，BizTalk SQL 配接器從中提取資料之 SQL 資料庫上的鎖定爭用會增加。 這樣會限制您向外擴充 SQL 配接器的能力。  
  
  下表顯示如何向外擴充 BizTalk 層的範例。  
  
  ![向外擴充 BTS](../core/media/scaleoutbts.gif "ScaleOutBTS")  
  
  下表顯示一個向外擴充的 BizTalk 拓撲，從一台 BizTalk Server 擴充成兩台 BizTalk Server。 在一台 BizTalk Server 拓撲中，三個主控件執行個體共用 BizTalk 電腦資源。 在兩台 BizTalk Server 拓撲中，傳輸主控件分別在不同伺服器上，以獲得更大的輸送量。  
  
## <a name="considerations-when-scaling-out-the-biztalk-tier"></a>向外擴充 BizTalk Server 層的考量  
 在您新增其他 BizTalk Server 電腦之前，必須考慮下列問題：  
  
#### <a name="how-do-i-configure-the-system-for-load-balancing-and-fault-tolerance-when-i-scale-out-the-biztalk-tier"></a>向外擴充 BizTalk 層時，如何設定系統以達負載平衡和容錯？  
 負載平衡和容錯技術的選擇取決於實例中使用的配接器。 對於 SOAP 和 HTTP 配接器，建議的方式是使用 NLB。 請參閱 NLB 文件以取得詳細資訊。  
  
#### <a name="how-do-i-refactor-the-host-instances"></a>如何重整主控件執行個體？  
 當您向外擴充 BizTalk 層時，並沒有一定的規則可決定應如何重整主控件執行個體。 建構主控件執行個體的時機取決於實例的複雜性。 以下是如何建構主控件執行個體的一些範例。  
  
##### <a name="scenario-1"></a>實例 1  
 一個 BizTalk Server 組態，接收和傳輸主控件執行個體在同一台電腦上。  
  
 假設有 CPU 瓶頸存在。 您新增另一部相同的 BizTalk 電腦到群組以向外擴充，如此可有兩種方式來建構主控件執行個體。  
  
 此問題有兩個解決方案：  
  
- **解決方案 1**： 您將在此案例中的最簡單方法是複製主控件執行個體建構從第一部電腦至第二部電腦。 這樣，就功能而言，第二台電腦就完全是第一台電腦的複本；也有接收和傳送主控件。 假設沒有其他瓶頸，CPU 資源加倍，您便得到兩倍的擴充。  
  
- **解決方案 2**： 建構主控件執行個體的另一個方式是將接收和傳送功能分置在不同的電腦。 如此，一台 BizTalk Server 專用於接收，而另一台專用於傳送。  
  
  **比較方案 1 及方案 2**  
  
  在解決方案 1 中，主控件執行個體的數目比 1 BTS 組態增加一倍。 這表示 SQL 伺服器上的鎖定爭用會增加。 鎖定爭用增加的量決定擴充比例。 若鎖定爭用剛好在變成瓶頸的限制內，您會看到兩倍的擴充。  
  
  解決方案 2 的好處是您有只有兩個主控件執行個體，因此 SQL server 上的鎖定爭用應該小於比解決方案 1。 不過，擴充比例完全取決於接收的複雜性和傳送主控件執行個體。 考慮解決方案 2 的下列情況：  
  
  假設接收和傳輸主控件執行個體使用同樣大量的 CPU，各使用一個 BizTalk Server 拓撲上 50% 的 CPU。 在兩個 BizTalk Server 拓撲中，您將傳輸主控件執行個體移動到不同電腦，現在接收和傳輸都得到雙倍的資源。 假設沒有其他瓶頸，這樣應該會提供兩倍的擴充。 此實例比解決方案 1 為佳，因為只有兩個主控件執行個體，因此鎖定爭用較少。  
  
  假設傳輸耗費的資源比接收多，它使用一個 BizTalk Server 拓撲上 80% 的 CPU。 將傳輸主控件執行個體移動到另一台機器，您只會多取得 20% 的 CPU 資源，因此最大擴充比例是 1.2。 此外，擁有接收主控件執行個體的電腦僅使用 20-30% CPU 資源，因此向外擴充的優點少很多。  
  
  考慮下圖有四台 BizTalk Server。 每個電腦都有接收方與傳送方，就有四個屬於各種類型的主控件執行個體 (接收和傳輸)。  
  
  ![Re&#45;主控件執行個體的建構](../core/media/refactoringhostinstances.gif "RefactoringHostinstances")  
  
  此拓撲或許不是最好的。 您也應該測試其他建構排列，視實例的複雜性而定。 例如：  
  
- 兩台電腦專門用於接收、兩台用於傳輸。 這樣可在接收和傳送等量時，提供您最佳的可能擴充。  
  
- 若接收量較傳輸量大，三台電腦專門用於接收、一台用於傳輸。  
  
- 若傳輸量較接收量大，三台電腦專門用於傳輸、一台用於接收。  
  
  在所有實例中，建議您將各個主控件的主控件執行個體數目減至最少，如此可減少 MessageBox 資料庫上的爭用，同時最充分的使用電腦資源。 最佳建構排列取決於實例的複雜性以及瓶頸的類型。 在完成排列之前，請永遠要測試您的建構。  
  
## <a name="see-also"></a>另請參閱  
 [向上擴充 BizTalk Server 層](../core/scaling-up-the-biztalk-server-tier.md)   
 [向上擴充 SQL Server 層](../core/scaling-up-the-sql-server-tier.md)   
 [向外擴充 SQL Server 層](../core/scaling-out-the-sql-server-tier.md)   
 [相應放大的接收主控件](../core/scaled-out-receiving-hosts.md)   
 [相應放大處理主控件](../core/scaled-out-processing-hosts.md)   
 [向外傳送主控件](../core/scaled-out-sending-hosts.md)   
 [使用 Windows Server 叢集為 BizTalk Server Hosts2 提供高可用性](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)   
 [相應放大的資料庫](../core/scaled-out-databases.md)   
 [叢集 BizTalk Server 資料庫](../core/clustering-the-biztalk-server-databases1.md)