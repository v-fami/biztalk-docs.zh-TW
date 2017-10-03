---
title: "管理 BizTalk Server 中的 BAM 入口網站 |Microsoft 文件"
Description: "安裝和設定 BizTalk Server 中的 BAM 入口網站的概觀"
ms.custom: 
ms.date: 08/15/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a08aa85-3a45-4a8c-bdb5-5615ca097ce1
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d7908c9c7ce8e4b731e0b88569e3dc3fb228a1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="manage-the-bam-portal"></a>管理 BAM 入口網站

## <a name="set-up-bam-portal"></a>設定 BAM 入口網站
系統管理員設定 BAM 入口網站執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。 請使用 BizTalk Server 組態工具指定是否啟用 BAM，並指定 Web 服務帳戶、可檢視入口網站的 Windows 群組，以及裝載入口網站的網站。 當設定好 BAM 入口網站而又需要更新 BAM 入口網站組態時，您可以使用組態工具更新組態設定，例如入口網站使用者群組、應用程式集區帳戶和管理 Web 服務使用者。  
  
 如需有關安裝 BAM 入口網站的詳細資訊，請參閱[安裝及設定在多重電腦環境中的 BAM](http://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx)。  
  
 如需有關如何設定 BAM 入口網站的詳細資訊，請參閱[設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)。
  
 BAM 入口網站有許多可自訂的設定，可以透過修改 webconfig.xml 檔案來存取。 這些設定控制了 BAM 入口網站的效能和運作。 本節的其餘部分將說明如何自訂 BAM 入口網站組態。  
  
## <a name="next-steps"></a>後續的步驟 
  
-   [自訂 BAM 入口網站組態](../core/customizing-the-bam-portal-configuration.md)  
  
-   [如何在 NLB 叢集上設定 BAM 入口網站工作](../core/how-to-configure-the-bam-portal-to-work-on-an-nlb-cluster.md)  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)