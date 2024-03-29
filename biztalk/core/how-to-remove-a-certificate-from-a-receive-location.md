---
title: 如何移除憑證，以從接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates, receive locations
- receive locations, certificates
- managing [receive locations], certificates
ms.assetid: 717d41bf-4260-4df4-9d0a-07243bb9b12c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5af6db7dcbb9efb20846520db6b800f5c3226316
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991975"
---
# <a name="how-to-remove-a-certificate-from-a-receive-location"></a>如何從接收位置移除憑證
本主題說明如何使用 BizTalk Server管理主控台，從接收位置移除安全性憑證。 這樣做之後，接收位置就不再將訊息加密；訊息將會以純文字傳送。 從接收位置移除憑證並不會將它從憑證存放區中移除。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-remove-a-certificate-from-a-receive-location"></a>若要從接收位置移除憑證  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀結構中，展開您要為其從接收位置移除憑證的 BizTalk 群組與 BizTalk 應用程式。  
  
3. 依序展開**接收位置**，以滑鼠右鍵按一下接收位置，按一下**屬性**，然後按一下**憑證**。  
  
4. 按一下 **移除憑證**，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [管理接收位置](../core/managing-receive-locations.md)