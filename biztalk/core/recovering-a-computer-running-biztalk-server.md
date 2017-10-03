---
title: "復原執行 BizTalk Server 的電腦 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a55af6d6-f11a-46e4-9b8e-0a1ca35998c4
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74d9234fa1d3a572afadcc8e8ba90dd4735eb5c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="recovering-a-computer-running-biztalk-server"></a>復原執行 BizTalk Server 的電腦
若要復原執行 BizTalk Server 的電腦，您必須能夠存取 BizTalk Server 資料庫。 如果需要，請還原 BizTalk Server 資料庫。 此外，在復原執行 BizTalk Server 的電腦之前，您必須先重新安裝 BizTalk Server 及所有必要的元件。  
  
 這些步驟完成後，您才可以使用本節中的程序復原 BizTalk Server。 復原 BizTalk Server 所需執行的程序取決於您所使用的版本。 下表列出每個版本的必要程序。  
  
|工作|Standard|開發人員|Enterprise|  
|----------|--------------|---------------|----------------|  
|**如何還原憑證存放區**|**X**|||  
|**如何復原企業單一登入 (SSO)**|**X**|**X**|**X**|  
|**如何復原 BizTalk 群組**|**X**|**X**|**X**|  
|**如何復原 BizTalk Server 組態**|**X**|**X**|**X**|  
|**如何復原 BAM 警示**<br /><br /> 除非您使用 BAM，否則不需要執行此動作。|**X**|**X**|**X**|  
|**如何復原 BAM 入口網站**<br /><br /> 除非您使用 BAM，否則不需要執行此動作。|**X**|**X**|**X**|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何還原憑證存放區](../core/how-to-restore-the-certificate-store.md)  
  
-   [如何復原企業單一登入](../core/how-to-recover-enterprise-single-sign-on.md)  
  
-   [如何復原 BizTalk 群組](../core/how-to-recover-the-biztalk-group.md)  
  
-   [如何復原 BizTalk Server 組態](../core/how-to-recover-the-biztalk-server-configuration.md)  
  
-   [如何復原 BAM 警示](../core/how-to-recover-bam-alerts.md)  
  
-   [如何復原 BAM 入口網站](../core/how-to-recover-the-bam-portal.md)