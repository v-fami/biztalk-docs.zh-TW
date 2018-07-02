---
title: 如何啟動傳送埠或傳送埠群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- starting, send port groups
- starting, send ports
- managing [send port groups], starting
- managing [send ports], starting
- send port groups, starting
- send ports, starting
ms.assetid: f17c0b7c-cad7-4c5e-a08c-3ebf838faa54
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f3f88eca5a0c919de2c278bf1a11f8565de3f0f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971439"
---
# <a name="how-to-start-a-send-port-or-send-port-group"></a>如何啟動傳送埠或傳送埠群組
本主題描述如何使用 BizTalk Server 管理主控台來啟動傳送埠或傳送埠群組。 傳送埠或傳送埠群組必須被啟動，才能處理訊息。 如果您啟動已取消登錄的傳送埠或傳送埠群組，BizTalk 便會在啟動傳送埠或傳送埠群組之前將其登錄。 傳送埠群組必須包含至少一個處於已登錄狀態的傳送埠，才能加以啟動。 啟動和停止傳送埠群組不會影響它所包含的任何傳送埠的狀態。  
  
> [!NOTE]
>  依照預設，啟動 BizTalk 應用程式時將會啟動它所包含的所有成品。 如需詳細資訊，請參閱 <<c0> [ 如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須以「BizTalk Server 操作員」群組或「BizTalk Server 系統管理員」群組的成員身分登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-start-a-send-port-or-send-port-group"></a>啟動傳送埠或傳送埠群組  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，展開**應用程式**，然後展開包含您想要的傳送埠群組的傳送埠的應用程式啟動。  
  
3. 按一下 **傳送埠**或是**傳送埠群組**，以滑鼠右鍵按一下傳送埠或傳送埠群組，然後按一下 **啟動**。  
  
## <a name="see-also"></a>另請參閱  
 [管理傳送埠和傳送埠群組](../core/managing-send-ports-and-send-port-groups.md)