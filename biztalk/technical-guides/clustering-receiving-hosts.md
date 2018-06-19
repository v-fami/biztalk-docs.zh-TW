---
title: 叢集接收主控件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93544f39-836f-4a4f-9587-230bfa3a9d4e
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 488a87539228a90ac427339e260653a141eb7121
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26008303"
---
# <a name="clustering-receiving-hosts"></a>叢集接收主控件
BizTalk Server 提供的功能，可讓您將 BizTalk 主控件設定為叢集資源內[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]叢集群組。 主控件叢集支援可為以支援高可用性的整合式 BizTalk 接收配接器應該不會在多個主控件執行個體中同時執行，例如 FTP 接收處理常式，或在某些情況下，POP3 接收處理常式。 在需要叢集 MSMQ 服務的實例中，主控件叢集支援也可確保 MSMQ 配接器所傳送或所接收訊息的交易一致性。  
  
> [!NOTE]  
>  只能在 BizTalk Server Enterprise Edition 中使用主機叢集。  
  
> [!NOTE]  
>  您可以叢集化 BizTalk 主控件之前，您必須設定至少兩個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]BizTalk 群組中的電腦做為成員的[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]叢集。 如需有關設定[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]叢集，請參閱[Windows Server 2008 叢集文件、 白皮書、 網路廣播、 群組](http://go.microsoft.com/fwlink/?LinkId=156818)(http://go.microsoft.com/fwlink/?LinkId=156818)。  
  
 BizTalk 主控件叢集支援可為五個整合式 BizTalk 配接器提供高可用性： FTP 配接器、 MSMQ 配接器、 POP3 配接器、 SQL 配接器和 SAP 配接器。 在執行配接器的單一執行個體時也提供主控件叢集支援，以提供高可用性，進行排序的傳遞。  
  
 所有的 BizTalk 配接器處理常式可以執行在叢集主控件，但沒有任何好處，如下所述但在叢集主控件執行配接器處理常式。 如果您的處理需求包含任何下一節中所述的案例，您應該在叢集主控件執行配接器處理常式。 如需詳細步驟，設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]叢集，請參閱[改善在 BizTalk Server 中使用 Windows Server 2008 容錯移轉叢集或 Windows Server 2003 伺服器叢集的容錯功能](http://go.microsoft.com/fwlink/?LinkId=156819)(http://go.microsoft.com/fwlink/?LinkId=156819)。  
  
## <a name="scenarios-for-running-adapter-handlers-in-clustered-hosts"></a>在叢集主機中執行配接器處理常式的案例  
 如果您的處理需求包含任何下列案例，您應該在叢集主控件執行配接器處理常式。  
  
-   在叢集 BizTalk 主控件中執行 FTP 配接器接收處理常式  
  
-   在叢集 BizTalk 主控件中執行 MSMQ 配接器處理常式  
  
-   在叢集 BizTalk 主控件中執行 POP3 配接器接收處理常式  
  
-   執行支援以叢集 BizTalk 主控件執行排序傳遞的接收配接器  
  
 如需有關這些案例的詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](http://go.microsoft.com/fwlink/?LinkId=151284)(http://go.microsoft.com/fwlink/?LinkId=151284)。  
  
## <a name="see-also"></a>請參閱  
 [向外擴充接收主控件](../technical-guides/scaling-out-receiving-hosts.md)   
 [向外延展處理主控件](../technical-guides/scaling-out-processing-hosts.md)   
 [向外擴充傳送主控件](../technical-guides/scaling-out-sending-hosts.md)