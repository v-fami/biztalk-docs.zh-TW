---
title: 向外延展處理主控件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- high availability
- hosts, processing
- hosts, high availability
- scaling, hosts
- hosts, planning
- hosts, scaling
- clustering
ms.assetid: c72ce8fc-7593-4700-8398-23d1a20515c3
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01ee36777a5c64713fd31e86fe6ef2a1886b3348
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269326"
---
# <a name="scaled-out-processing-hosts"></a>向外擴充的處理主控件
向外擴充的處理主控件藉由隔離協調流程功能在兩部或以上不同的主控件電腦上，以改善效能和提供高可用性。 此隔離可讓您新增多部電腦至處理主控件，以獲得備援。 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的處理主控件會執行一或多個主控件執行個體，以協調各種商務程序並為協調流程建立程式物件的執行個體。  
  
 下圖顯示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署，此部署具有兩部執行執行處理主控件的電腦，可為處理主控件提供高可用性。 請注意，在此圖中接收和傳送主控件不是高度可用。  
  
 ![向外延展處理主控件](../core/media/tdi-ha-scaleprocess.gif "TDI_HA_ScaleProcess")  
  
 在此組態中，處理協調流程的工作可在兩部具有處理主控件執行個體且可獨立執行的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦之間平衡負載。 若其中一部電腦發生錯誤或失敗，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會自動使用另一部電腦上的主控件執行個體來處理其餘的協調流程。  
  
## <a name="maintaining-orchestration-state"></a>維護協調流程狀態  
 BizTalk Server 是在 Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 中集中維護協調流程狀態，而不是在每一部 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上以本機方式來維護。 藉由將狀態保存在 MessageBox 資料庫中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 克服了依賴單一處理主控件執行個體處理協調流程的限制，而且讓任何處理主控件執行個體都可以處理協調流程。 若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在處理協調流程時發生錯誤，另一個相同的處理主控件執行個體將可從上次保存的狀態完成協調流程。  
  
## <a name="see-also"></a>另請參閱  
 [為 BizTalk 主控件提供高可用性](../core/providing-high-availability-for-biztalk-hosts.md)