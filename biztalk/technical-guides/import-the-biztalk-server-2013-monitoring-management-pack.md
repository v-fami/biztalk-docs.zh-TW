---
title: 匯入 BizTalk Server 2013 監視管理組件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bee2bfe9-4eb0-46d4-8eee-75182202080c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7756a6ca4301f7536a0e4964117f11cb92eb2fcd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993783"
---
# <a name="import-the-biztalk-server-2013-monitoring-management-pack"></a>匯入 BizTalk Server 2013 監視管理組件
如需如何匯入管理組件的指示，請參閱 「 如何匯入管理組件中[Operations Manager 2007 R2/2012年](http://go.microsoft.com/fwlink/?LinkId=142351)(<http://go.microsoft.com/fwlink/?LinkId=142351>)。 之後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]匯入管理組件，請遵循下列程序來完成初始設定：  
  
### <a name="to-configure-the-management-pack"></a>若要設定的管理組件  
  
1.  建立新的管理組件儲存覆寫和其他自訂項目。  
  
2.  若要啟用代理程式 Proxy 設定，請遵循下列步驟：  
  
    1.  開啟 Operations 主控台，然後按一下 [系統管理] 按鈕。  
  
    2.  在 [系統管理員] 窗格中，按一下**代理程式管理**。  
  
    3.  按兩下清單中的代理程式。  
  
    4.  在 [安全性] 索引標籤上選取**允許此代理程式作為 proxy 並探索其他電腦上的受管理的物件**。  
  
    5.  針對每個 BizTalk 伺服器已安裝的代理程式重複步驟 3 到 4。