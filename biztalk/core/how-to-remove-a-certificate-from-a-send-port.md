---
title: "如何從傳送埠移除憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, certificates
- managing [send ports], certificates
- certificates, deleting
- deleting, certificates
ms.assetid: fd93a83f-c2aa-4de2-9996-4ca4ec6d4a4c
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5193b1b6003660aac0e0b427da0f0a338b56d8ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-certificate-from-a-send-port"></a>如何從傳送埠移除憑證
本主題描述如何使用 BizTalk Server 管理主控台，從傳送埠移除安全性憑證。 這樣做之後，傳送埠就再也不會將訊息加密；訊息將會以純文字傳送。 從傳送埠移除憑證並不會將它從憑證存放區中移除。  
  
> [!NOTE]
>  應用程式開發人員可以使用此主題中的程序，在開發程序中從傳送埠移除安全性憑證。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-remove-a-certificate-from-a-send-port"></a>從傳送埠移除憑證  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀結構中，展開您要為其從傳送埠移除憑證的 BizTalk 群組與 BizTalk 應用程式。  
  
3.  展開**傳送埠**，以滑鼠右鍵按一下傳送埠，按一下**屬性**，然後按一下 **憑證**。  
  
4.  按一下**移除憑證**，然後按一下 **確定**。  
  
## <a name="see-also"></a>另請參閱  
 [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)