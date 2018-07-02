---
title: 準備災害復原 BizTalk Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14c2c25d-30c5-4e90-a744-f084befa2c1d
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f9d806f3f757200e425b2f922032cb8f8d26bc6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981567"
---
# <a name="preparing-the-disaster-recovery-biztalk-servers"></a>準備災害復原 BizTalk Server
安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在下列中的建議災害復原站台的執行階段伺服器[BizTalk Server 2010 安裝和升級指南](http://go.microsoft.com/fwlink/?LinkID=194815)(<http://go.microsoft.com/fwlink/?LinkID=194815>)。 設定這些[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用 BizTalk 組態精靈 將它們加入實際執行的 BizTalk 群組的執行階段伺服器。 設定時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在災害復原站台 （包括災害復原企業單一登入主要密碼伺服器） 的執行階段伺服器請務必：  
  
- 選取  **No** "這是主要密碼伺服器嗎？ 」 問題  
  
- 選取 **聯結**問題 「 是否要建立或加入 BizTalk Server 群組？ 」  
  
  設定之後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段嚴重損壞修復伺服器，建立對應至生產環境網站的主控件執行個體，但不會啟動這些主控件執行個體的災害復原網站上的 BizTalk 主控件執行個體。 例如，如果生產網站有三個主控件**傳送**，**接收**，並**協調流程**server1、 server2，以及 server3 的執行個體，建立三個對應DRserver1，DRserver2，DRserver3 主控件執行個體。  
  
> [!NOTE]
>  所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-相關的 Windows 服務，例如在災害復原站台的規則引擎服務與 BizTalk 主控件執行個體應設為"disabled"在 服務管理員防止執行任何處理災害復原站台。  
  
 您可以安裝和設定不同數目的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]非生產環境中執行，才會進行災害復原網站中的執行階段伺服器。 不過，採用這種方法，以避免災害復原事件發生時，多載的災害復原網站中的伺服器時，請務必小心。 指令碼完全還原 BizTalk 群組表示的一組資料庫，並執行所有必要的系統變更為 BizTalk 群組之後, 可以加入執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]BizTalk 群組的執行階段伺服器。