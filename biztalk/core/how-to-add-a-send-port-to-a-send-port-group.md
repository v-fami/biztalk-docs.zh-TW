---
title: 如何將傳送埠新增至傳送埠群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [send port groups], adding send ports
- managing [send ports], adding to send port groups
- send port groups, send ports
- send ports, send port groups
- adding, send ports
ms.assetid: a61b3b32-c05e-40b9-abf1-09b7065fb6a2
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6c2b616952aa4f24e40ddd56e035a6de4a77c58
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007175"
---
# <a name="how-to-add-a-send-port-to-a-send-port-group"></a>如何新增傳送埠至傳送埠群組
本主題描述如何使用 BizTalk Server 管理主控台，將一個或多個傳送埠新增至傳送埠群組。 您只能在傳送埠群組中新增單向靜態傳送埠。  
  
 您可以新增存在於不同應用程式的傳送埠。 如果您這麼做，則必須從包含傳送埠群組的應用程式將參考新增到包含傳送埠的應用程式。 如需相關指示，請參閱 <<c0> [ 如何加入另一個應用程式的參考](../core/how-to-add-a-reference-to-another-application.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-add-a-send-port-to-a-send-port-group"></a>在傳送埠群組新增傳送埠  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀結構中，展開您要在其中將傳送埠新增至埠群組的 BizTalk 群組和 BizTalk 應用程式。  
  
3. 按一下 **傳送埠群組**，以滑鼠右鍵按一下傳送埠群組，然後按一下 **屬性**。  
  
4. 在 **傳送埠**，按一下底下的下拉式清單**名稱**，然後按一下要新增傳送埠至傳送埠群組。 請為每個要新增至群組的傳送埠執行同樣的步驟。 若要建立新的傳送埠，並將它，按一下**\<新傳送埠...\>**  ，然後依照中的指示[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。  
  
5. 完成新增傳送埠至傳送埠群組，請按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [建立和設定傳送埠群組](../core/creating-and-configuring-send-port-groups.md)   
 [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)