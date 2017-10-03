---
title: "正在準備嚴重損壞修復 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14c2c25d-30c5-4e90-a744-f084befa2c1d
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9379136f0845c7c4c987170747a28bd3c50206c4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="preparing-the-disaster-recovery-biztalk-servers"></a>正在準備嚴重損壞修復 BizTalk Server
安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]遵循中的建議的災害復原站台執行階段伺服器[BizTalk Server 2010 安裝和升級指南](http://go.microsoft.com/fwlink/?LinkID=194815)(http://go.microsoft.com/fwlink/?LinkID=194815)。 設定這些[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]加入實際執行的 BizTalk 群組中使用 BizTalk 組態精靈的執行階段伺服器。 設定時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在災害復原站台 （包括災害復原企業單一登入主要密碼伺服器） 的執行階段伺服器，請務必：  
  
-   選取**否**「 這是主要密碼伺服器嗎？ 」 問題的答案  
  
-   選取**聯結**問題 「 是否要建立或加入 BizTalk Server 群組？ 」  
  
 設定之後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段嚴重損壞修復伺服器，對應至生產環境網站的主控件執行個體，但不是會啟動這些主控件執行個體的災害復原站台上建立 BizTalk 主控件執行個體。 例如，如果將生產站台具有三個主控件**傳送**，**接收**，和**協調流程**server1 server2，且伺服器 3 上的執行個體，建立三個對應DRserver1，DRserver2，DRserver3 主控件執行個體。  
  
> [!NOTE]  
>  所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-相關 Windows 服務，例如，規則引擎服務在災害復原站台與 BizTalk 主控件執行個體應設為"disabled"在 服務管理員防止執行任何處理的災害復原站台。  
  
 您可以安裝和設定不同數目的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]災害復原站台比生產環境中正在執行中的執行階段伺服器。 不過，採用這個方法，以避免多載在災害復原站台伺服器，如果發生嚴重損壞修復事件時，請務必小心。 一旦完全還原所表示的一組資料庫的 BizTalk 群組，並針對 BizTalk 群組所執行的所有必要的系統變更，可以執行指令碼為聯結[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]至 BizTalk 群組的執行階段伺服器。