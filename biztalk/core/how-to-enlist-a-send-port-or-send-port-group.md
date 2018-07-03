---
title: 如何登錄傳送埠或傳送埠群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- enlisting, send port groups
- enlisting, send ports
- send port groups, enlisting
- send ports, enlisting
- managing [send ports], enlisting
- managing [send port groups], enlisting
ms.assetid: d4298b8e-7dc7-4382-af86-c4db0982b7e0
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 127673659878738a57045ea1b5bd9f1d1cf16d10
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016193"
---
# <a name="how-to-enlist-a-send-port-or-send-port-group"></a>如何登錄傳送埠或傳送埠群組
本主題描述如何使用 BizTalk Server 管理主控台來登錄傳送埠或傳送埠群組。 登錄傳送埠或傳送埠群組會使傳送埠或傳送埠群組與 BizTalk 主控件產生關聯，並且為傳送埠或傳送埠群組建立訂閱。 如果傳送埠群組沒有包含傳送埠，登錄傳送埠群組並不會建立任何訂閱。 此外，登錄傳送埠群組也不會變更其包含的任何傳送埠的狀態。  
  
> [!NOTE]
>  啟動傳送埠或傳送埠群組也會自動將其登錄。 此外，啟動應用程式也會依預設登錄並啟動其所有的成品。 如需詳細資訊，請參閱 <<c0> [ 如何啟動傳送埠或傳送埠群組](../core/how-to-start-a-send-port-or-send-port-group.md)。 另請參閱[如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須為 BizTalk Server 系統管理員群組的成員登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-enlist-a-send-port-or-send-port-group"></a>登錄傳送埠或傳送埠群組  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，展開**應用程式**，然後展開包含您想要的傳送埠群組的傳送埠的應用程式登錄。  
  
3. 按一下 **傳送埠**或是**傳送埠群組**，以滑鼠右鍵按一下傳送埠或傳送埠群組，然後按一下 **登錄**。  
  
## <a name="see-also"></a>另請參閱  
 [管理傳送埠和傳送埠群組](../core/managing-send-ports-and-send-port-groups.md)