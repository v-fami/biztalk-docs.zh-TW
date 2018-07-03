---
title: 如何設定協調流程的追蹤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, tracking
- orchestrations, HAT
- managing [orchestrations], tracking
- configuring [HAT tracking], orchestrations
- tracking, orchestrations
- HAT, orchestrations
ms.assetid: 8f5ed525-11f8-4bef-95c4-cfe9c971b663
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c64d7521bf6d65458f66bb0ef06d08421edf1b4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013191"
---
# <a name="how-to-configure-tracking-for-an-orchestration"></a>如何設定協調流程的追蹤
本主題描述如何使用 BizTalk Server 管理主控台，以設定協調流程的追蹤。  
  
 如需有關建立和使用查詢的詳細資訊，請參閱 <<c0> [ 使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)。 如需追蹤功能的詳細資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-configure-tracking-for-an-orchestration"></a>設定協調流程的追蹤  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]、 BizTalk 群組、 展開**應用程式**，然後展開包含您要設定追蹤之協調的流程的應用程式。  
  
3. 按一下 **協調流程**，以滑鼠右鍵按一下您要設定追蹤，然後按一下協調的流程**屬性**。  
  
4. 按一下 **追蹤**索引標籤上，選取您要的追蹤選項下, 表中所述，然後按一下**確定**。  
  
   |選項|描述|  
   |------------|-----------------|  
   |**追蹤事件-協調流程開始和結束**|選取此核取方塊，在處理整個商務程序之前及之後追蹤協調流程執行個體。 協調流程追蹤可讓您查看的執行個體中追蹤查詢結果檢視。|  
   |**追蹤事件-訊息傳送與接收**|選取此核取方塊以追蹤訊息傳送與接收事件。 此核取方塊才會提供您所選取**協調流程開始和結束**核取方塊。|  
   |**追蹤事件-流程化開始與結束**|當您需要在「協調流程偵錯工具」中偵錯協調流程執行個體時，請選取此核取方塊。 當您選取此核取方塊，會填入此「協調流程偵錯工具」中的事件清單。 此核取方塊才會提供您所選取**協調流程開始和結束**核取方塊。|  
   |**追蹤訊息內文-協調流程處理之前**|選取此核取方塊以在協調流程執行個體處理之前儲存和追蹤實際訊息內容。 此核取方塊才會提供您所選取**訊息傳送與接收**核取方塊。|  
   |**追蹤訊息內文-協調流程處理之後**|選取此核取方塊以在協調流程執行個體處理之後儲存和追蹤實際訊息內容。 此核取方塊才會提供您所選取**訊息傳送與接收**核取方塊。|  
   |**追蹤訊息屬性-連入訊息**|選取此核取方塊，可追蹤輸入訊息的升級屬性。|  
   |**追蹤訊息屬性-外寄訊息**|選取此核取方塊以追蹤輸出訊息的升級的屬性。|  
  
## <a name="see-also"></a>另請參閱  
 [管理協調流程](../core/managing-orchestrations.md)