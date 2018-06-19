---
title: 執行 BizTalk Server 的電腦備份 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70f53b41-8083-4b56-8698-e75a13b21a69
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 537ea40b39ecd35127b62f8d96f0175e98a1f3b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230502"
---
# <a name="backing-up-a-computer-running-biztalk-server"></a>對執行 BizTalk Server 的電腦進行備份
執行 BizTalk Server 的電腦若發生無法修復的硬體失敗，您就必須用一模一樣的電腦予以替換。 您應該設定在替換的電腦具有基底平台軟體、 軟體必要元件，BizTalk Server 元件和相同的組態設定。 這些組態設定可能包括適用的登錄項目、檔案和資料夾，還有 BizTalk 應用程式正常運作所需的相關 Windows 服務。  
  
 除了備份 BizTalk Server 資料庫之外，請一併備份下列 BizTalk Server 元件，以確保硬體失敗後能夠復原 BizTalk Server：  
  
-   BizTalk Server 組態  
  
-   企業單一登入 (SSO) 主要密碼  
  
-   商務活動監控 (BAM) 入口網站 (若有使用 BAM 才需要)  
  
-   BizTalk 應用程式  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何備份 BizTalk Server 組態](../core/how-to-back-up-the-biztalk-server-configuration.md)  
  
-   [如何備份主要密碼](../core/how-to-back-up-the-master-secret.md)  
  
-   [如何備份 BAM 入口網站](../core/how-to-back-up-the-bam-portal.md)  
  
-   [備份 BizTalk Server 應用程式](../core/backing-up-biztalk-server-applications.md)