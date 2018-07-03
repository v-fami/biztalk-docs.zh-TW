---
title: 管理 BAM 警示執行 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [BAM definitions], executing alerts
- Notification Services, configuration files
- BAM Management utility
- alerts, executing
ms.assetid: 44bb738e-fa2c-4b32-9e8d-e756d6c3778e
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d8dca3f99480b6875253eb6aca102977935160b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021980"
---
# <a name="managing-bam-alert-execution"></a>管理 BAM 警示的執行
您可以透過三種途徑修改 BAM 警示的執行：BAM 入口網站、BAM 管理公用程式和 ProcessBamNSFiles.vbs 指令碼。  
  
## <a name="bam-portal"></a>BAM 入口網站  
 知識工作者和系統管理員可以使用 BAM 入口網站中的警示管理員修改警示的傳遞方式。 透過 BAM 入口網站可以啟用或停用警示，並可修改閾值層級、傳遞位置以及影響警示執行的其他參數。  
  
 如需有關如何修改警示的詳細資訊，請參閱 < [BAM 入口網站頁面上的警示管理員](../core/alert-manager-on-the-bam-portal-page.md)並[BAM 入口網站中的警示](../core/alerts-in-the-bam-portal.md)。  
  
### <a name="bam-management-utility"></a>BAM 管理公用程式  
 系統管理員可以使用 BAM 管理公用程式啟用、停用和移除警示。  
  
 如需有關使用 BAM 管理公用程式管理警示的詳細資訊，請參閱下列主題：  
  
-   [如何啟用警示](../core/how-to-enable-alerts.md) 
  
-   [如何停用警示](../core/how-to-disable-alerts.md)  
  
-   [如何移除 BAM 警示](../core/how-to-remove-bam-alerts.md)  
  
### <a name="modifying-notification-services-configuration-files"></a>修改 Notification Services 組態檔  
 系統管理員可以使用 ProcessBamNSFiles.vbs 指令碼，變更 Notification Services 傳遞警示的方式。 Notification services 的相關資訊的應用程式定義檔 (ADF)，請參閱[ http://go.microsoft.com/fwlink/?LinkId=127016 ](http://go.microsoft.com/fwlink/?LinkId=127016)。  
  
 若要修改與 BAM 關聯的 ADF，請依照下列一般步驟執行：  
  
1. 執行指令碼以取得目前組態和 ADF 檔案。  
  
2. 修改檔案。  
  
3. 執行指令碼以套用變更。  
  
   如需 ProcessBamNSFiles.vbs 指令碼的詳細資訊，請參閱[通知服務組態檔的 BAM 命令列指令碼](../core/bam-command-line-script-for-notification-services-configuration-files.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 入口網站](../core/managing-the-bam-portal.md)   
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)