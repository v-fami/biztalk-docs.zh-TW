---
title: 步驟 1： 安裝基底平台 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- platforms
- installing, base platform
- base platform
ms.assetid: 27da386f-90c7-414f-a4e3-e909f0c18371
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6eaae10965aa240af86ee381a3504a4ec64c8fc2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986951"
---
# <a name="step-1-installing-the-base-platform"></a>步驟 1： 安裝基底平台
基底平台，請先安裝 Microsoft[!INCLUDE[btsWinSvr2k3](../../includes/btswinsvr2k3-md.md)]和[!INCLUDE[btsWinSvr2k3](../../includes/btswinsvr2k3-md.md)]使用預設安裝選項的每部伺服器上的 Service Pack 2。 請遵循下列建議：  
  
## <a name="pre-installation"></a>預先安裝  
  
- 在安裝軟體時，停用所有防毒軟體。 某些防毒軟體程式可能會阻止正確安裝必要的軟體元件。  
  
- 請確定您輸入適當的授權資訊 （您已購買每一部伺服器的連線的數目上限）。 系統效能可能會受到可用的連線數目。  
  
- 請確定您已安裝 BizTalk Server 安裝所需的所有軟體必要條件。 如需詳細資訊，請參閱 BizTalk Server 的安裝指示，在[ http://go.microsoft.com/fwlink/?LinkId=81041 ](http://go.microsoft.com/fwlink/?LinkId=81041)。 [BizTalk 2013 R2 accelerator for SWIFT 的安裝指南](http://msdn.microsoft.com/library/d2b4a9f3-baeb-4fbc-9fda-5e4178832cd1)。  
  
- 在離線環境中測試所有重大更新，然後再安裝在您的生產伺服器上。  
  
- 請確定您已安裝所有適用的 hotfix，您將安裝為部署一部分的所有產品。 如需詳細資訊，請參閱下列來源：  
  
  - Microsoft BizTalk Server 線上說明  
  
  - 在 BizTalk Server 安裝指示[ http://go.microsoft.com/fwlink/?LinkId=81041 ](http://go.microsoft.com/fwlink/?LinkId=81041)。  
  
  - Microsoft[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]網站，網址[ http://go.microsoft.com/fwlink/?linkid=48685 ](http://go.microsoft.com/fwlink/?linkid=48685)。  
  
  - Microsoft 下載中心網站位於[ http://go.microsoft.com/fwlink/?linkid=48686 ](http://go.microsoft.com/fwlink/?linkid=48686)。  
  
  - [!INCLUDE[btsWinUpdate](../../includes/btswinupdate-md.md)] 網站，網址[ http://go.microsoft.com/fwlink/?linkid=48687 ](http://go.microsoft.com/fwlink/?linkid=48687)。  
  
- 若要避免病毒的攻擊，從 CD 安裝的平台，並透過拔除任何纜線，並停用任何網路介面卡中斷網際網路連線的每一部伺服器。  
  
- 全新的磁碟分割，使用格式[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]NTFS 檔案系統。  
  
## <a name="active-directory"></a>Active Directory  
  
-   建立的網域使用者身分**系統管理員**並將它新增至本機**系統管理員**群組部署中的每一部電腦上。 在安裝期間，登入使用此網域帳戶的部署伺服器。  
  
-   請勿設定任何網路介面卡，或在此時加入任何網域。 本指南說明如何在開始部署程序時，稍後再設定這些設定。  
  
## <a name="internal-web-servers-mrsr-site"></a>內部網頁伺服器 （MRSR 站台）  
  
-   請確定只在 MRSR 站台伺服器上已安裝 Internet Information Services (IIS)。  
  
-   請確定 Internet Security and Acceleration (ISA) Server 上未安裝，Internet Information Services (IIS)。  
  
-   請確定只在 MRSR 站台伺服器上已安裝 Message Queuing (MSMQ) 服務。 如果 BizTalk 傳訊的伺服器也會當做 MRSR 站台伺服器，請勿在這些伺服器上安裝 MSMQ。