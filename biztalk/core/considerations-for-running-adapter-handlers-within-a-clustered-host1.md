---
title: "執行叢集 Host1 內的配接器處理常式的考量 |Microsoft 文件"
ms.custom: 
ms.date: 2016-03-17
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- high availability
- receive adapters, clustering
- clustering, POP3 adapters
- FTP adapters, clustering
- clustering, receive adapters
- NLB system
- MSMQ send handler
- MSMQ receive handler
- clustering, FTP adapters
- handlers [adapters], best practices
- hosts, clustering
- MSMQ adapters
- clustering, MSMQ adapters
- adapters, best practices
- adapters, handlers
- POP3 adapters, clustering
- MSMQ adapters, clustering
- clustering
ms.assetid: ee66663c-4f4d-4515-9df1-aacf4fc72be4
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1fc93db61cddae43023f5c25eec62ecebd46e69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-for-running-adapter-handlers-within-a-clustered-host"></a>在叢集主控件中執行配接器處理常式的考量
BizTalk 主控件叢集支援可為下列整合 BizTalk 配接器提供高可用性： FTP 配接器、 SFTP 配接器、 MSMQ 配接器和 POP3 配接器。 在執行配接器的單一執行個體時也提供主控件叢集支援，以提供高可用性，進行排序的傳遞。  
  
 所有的 BizTalk 配接器處理常式都可以在叢集主控件上執行，但是除了在下述情況之外，在叢集主控件上執行配接器處理常式並沒有任何益處。 若您的處理需求不包括下列所述的任何實例，那麼您不應該在叢集主控件中執行配接器處理常式。  
  
## <a name="running-the-ftp-or-sftp-adapter-receive-handler-within-a-clustered-biztalk-host"></a>執行的 FTP 或 SFTP 配接器接收處理常式，叢集 BizTalk 主控件中  
 對於大部分的 BizTalk 整合配接器，只要建立多個配接器處理常式，以便在 BizTalk 群組中不同的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 伺服器的 BizTalk 主控件執行個體上執行，即可達到高可用性。 FTP 或 SFTP 配接器接收處理常式不應，不過，設定為同時執行多個 BizTalk 主控件執行個體。 此建議的理由，因為 FTP 或 SFTP 接收配接器使用 FTP 或 sftp 傳送通訊協定，從目標系統擷取檔案。 FTP 或 sftp 傳送的通訊協定不會鎖定檔案，以確保多份相同的檔案都不會同時的擷取時執行的 FTP 或 sftp 傳送的多個執行個體接收配接器。  
  
 提供高可用性的 FTP 或 SFTP 接收配接器，您應該設定的 FTP 或 SFTP 接收配接器在已叢集 BizTalk 主控件執行個體中執行。  
  
## <a name="running-msmq-adapter-handlers-within-a-clustered-biztalk-host"></a>在叢集 BizTalk 主控件中執行 MSMQ 配接器處理常式  
 若要確保能為 MSMQ 配接器提供高可用性，並確保能為 MSMQ 配接器所傳送或接收的訊息提供交易一致性，應執行以下動作：  
  
1.  設定為叢集資源的 Windows 叢集群組中的訊息佇列 (MSMQ) 上您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。  
  
2.  為叢集 BizTalk 主控件將叢集 MSMQ 服務新增至資源依存性清單。 這可確保叢集的 BizTalk 主控件永遠在容錯移轉案例在叢集 MSMQ 服務之後啟動。  
  
3.  在已設定為叢集資源，並和叢集 MSMQ 資源屬於同一個叢集群組的 BizTalk 主控件執行個體中設定 MSMQ 配接器傳送與接收處理常式。  
  
 建議這些步驟是基於下列理由：  
  
 **MSMQ 配接器接收處理常式**– MSMQ 4.0 (Windows Server 2008) 之前的 MSMQ 版本不支援遠端交易讀取，則為支援只有本機交易式讀取。 在此情況下，MSMQ 配接器接收處理常式必須完成與 MSMQ 配接器的本機交易式讀取叢集訊息佇列服務的本機主控件執行個體中執行。  
  
> [!IMPORTANT]
>  MSMQ 配接器接收處理常式需要「訊息佇列」服務的本機非叢集執行個體在執行接收處理常式主控件執行個體的同一部電腦上執行。  
  
 **MSMQ 配接器傳送處理常式**-為了確保 MSMQ 配接器，MSMQ 配接器傳送處理常式所使用的外寄佇列所做的交易式傳送的一致性必須提供高可用性，以便可如果 MSMQ 服務，針對外寄佇列失敗繼續執行。 在 叢集群組中設定叢集的訊息 Queuingresource 和 MSMQ 配接器處理常式，可確保 MSMQ 配接器傳送處理常式所使用的外寄佇列仍有高可用性。 這將可在「訊息佇列」服務失敗時降低訊息遺失的可能性。  
  
> [!NOTE]
>  如果 MSMQ 接收位置是**只**接收來自遠端 MSMQ 伺服器上的 MSMQ 佇列，則可以透過執行 MSMQ 達成高可用性 BizTalk 群組中接收多個 BizTalk 電腦上的主機。  若要 MSMQ 提供高可用性，您必須確定遠端 MSMQ 伺服器正在使用容錯移轉叢集的 Windows。  遠端 MSMQ 伺服器使用交易式佇列，如果必須執行 MSMQ 4.0 (Windows Server 2008) 或更新版本。  
  
## <a name="running-the-pop3-adapter-receive-handler-within-a-clustered-biztalk-host"></a>在叢集 BizTalk 主控件中執行 POP3 配接器接收處理常式  
 POP3 配接器接收處理常式不需設定為在叢集 BizTalk 主控件中執行，除非配接器正在讀取的 POP3 伺服器允許多個並行連線同時連接到相同信箱。 如果 POP3 配接器所連接的 POP3 伺服器允許其郵件信箱有多個並行連線，則建議您將單一 POP3 配接器接收處理常式設定為在叢集的 BizTalk 主控件執行個體上執行，以確保 POP3 配接器的高可用性。 此建議的理由是，如此一來可以確保在執行 POP3 接收配接器的多個執行個體時，不會同時擷取相同電子郵件訊息的多個副本。  
  
## <a name="running-a-receive-adapter-that-supports-ordered-delivery-with-a-clustered-biztalk-host"></a>執行支援以叢集 BizTalk 主控件執行排序傳遞的接收配接器  
 MSMQ 與 MQSeries 整合配接器將能讓您依接收的順序將文件提交給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 只要讓這些接收配接器的單一執行個體能在任何指定的時間執行，即可正確地實作此功能。 若要為這些配接器的單一執行個體提供高可用性，應將它們設定為在叢集 BizTalk 主控件執行個體中執行。