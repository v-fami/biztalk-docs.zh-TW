---
title: 如何建立傳送埠群組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, send port groups
- send port groups, creating
- managing [send port groups], creating
ms.assetid: de3e72aa-83f4-4760-9f39-a488f904f1d3
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33d27914dd5d7ae59b0823c2e6009ab307c41b9b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970364"
---
# <a name="how-to-create-a-send-port-group"></a>如何建立傳送埠群組
本主題描述如何使用 BizTalk Server 管理主控台，在 BizTalk 應用程式中建立傳送埠群組，然後在其中新增傳送埠。 您只能將靜態單向傳送埠新增到傳送埠群組。 傳送埠群組必須包含至少一個傳送埠，才能路由訊息。  
  
 您可以新增存在於不同應用程式的傳送埠。 如果您這麼做，則必須從包含傳送埠群組的應用程式將參考新增到包含傳送埠的應用程式。 如需指示，請參閱[如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須為 BizTalk Server 系統管理員群組的成員登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-create-a-send-port-group"></a>建立傳送埠群組  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀結構中，展開您要在其中建立傳送埠群組的 BizTalk 群組與 BizTalk 應用程式。  
  
3.  以滑鼠右鍵按一下**傳送埠群組**，指向 **新增**，然後按一下 **傳送埠群組**。  
  
4.  在**名稱**方塊中，輸入傳送埠群組的名稱。  
  
5.  在**傳送埠**，按一下底下的下拉式清單**名稱**，然後按一下要新增傳送埠至傳送埠群組。 請為每個要新增至群組的傳送埠執行同樣的步驟。 若要建立新的傳送埠，並將它加入，請按一下**\<新傳送埠...\>**  ，然後依照中的指示[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。  
  
6.  完成新增傳送埠至傳送埠群組，請按一下**確定**。  
  
## <a name="see-also"></a>請參閱  
 [建立和設定傳送埠群組](../core/creating-and-configuring-send-port-groups.md)