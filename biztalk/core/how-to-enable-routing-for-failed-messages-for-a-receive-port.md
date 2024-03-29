---
title: 如何啟用的路由失敗訊息的接收埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive ports, routing
- managing [receive ports], errors
- managing [receive ports], failed messages
- enabling, routing
- messages, failed messages
- routing, messages
- managing [receive ports], routing
- messages, routing
- receive ports, errors
- routing, receive ports
- routing, failed messages
- errors, receive ports
ms.assetid: 22366664-545d-4981-9bde-4df48b115002
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ac7ee9ef22ee3d0c452e47c886ff3298570d2c5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974535"
---
# <a name="how-to-enable-routing-for-failed-messages-for-a-receive-port"></a>如何啟用接收埠之失敗訊息的路由
本主題描述如何使用 BizTalk Server 管理主控台來啟用接收埠處理之訊息的路由。 當您啟用這個選項時，BizTalk Server 會嘗試將處理失敗的訊息路由至訂閱應用程式 (例如另一個接收埠或協調流程排程)。 未啟用這個選項時 (預設值)，BizTalk Server 會擱置失敗的訊息，並產生負值通知 (NACK)。 如需管理失敗的訊息的背景資訊，請參閱 <<c0> [ 使用失敗訊息路由](../core/using-failed-message-routing.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-enable-routing-for-failed-messages-for-a-receive-port"></a>啟用接收埠之失敗訊息的路由  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，展開您要為接收埠設定失敗訊息路由的 BizTalk 群組與 BizTalk 應用程式。  
  
3. 按一下 **接收連接埠**，以滑鼠右鍵按一下接收埠，然後按一下 **屬性**。  
  
4. 選取 **啟用的路由失敗的訊息**核取方塊，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [管理接收埠](../core/managing-receive-ports.md)