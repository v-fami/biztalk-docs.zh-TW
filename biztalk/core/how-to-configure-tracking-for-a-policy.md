---
title: "如何設定原則的追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- policies, tracking
- HAT, policies
- managing [policies], tracking
- tracking, policies
- managing [policies], configuring
- policies, configuring
- configuring [HAT tracking], policies
- tracking, configuring
ms.assetid: f126e541-c183-4544-8b9d-ca07d2af303e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96fb7607bcdce8143901dabd3cdf6358f21a6a8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-tracking-for-a-policy"></a>如何設定原則的追蹤
本主題描述如何使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來設定原則的追蹤。 您可以在管理主控台 [群組中樞] 頁面的查詢檢視中選取選項，以檢視執行個體資料、條件結果、動作以及議程更新。  
  
 如需有關建立和使用查詢的詳細資訊，請參閱[使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)。 如需有關追蹤功能的訊息和服務執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[檢視追蹤的訊息和執行個體資料](../core/viewing-tracked-message-and-instance-data.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-configure-tracking-for-a-policy"></a>設定原則的追蹤  
  
1.  按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀結構中，展開您要為原則設定追蹤的 BizTalk 群組與 BizTalk 應用程式。  
  
3.  按一下**原則**，以滑鼠右鍵按一下原則，按一下**屬性**，然後按一下 **追蹤**。  
  
4.  下表中所述，選取您要的追蹤選項，然後按一下**確定**。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**快速活動**|選取此核取方塊，追蹤原則運作所在之處的執行個體資料。|  
    |**條件評估**|選取此核取方塊，追蹤所選取原則的條件結果值是 True 或 False。|  
    |**規則引發**|選取此核取方塊，追蹤原則所啟動的動作。|  
    |**議程更新**|選取此核取方塊，追蹤議程的更新。 議程包含一份值為 "True" 且需要引發的動作清單。|  
  
## <a name="see-also"></a>另請參閱  
 [管理原則](../core/managing-policies.md)