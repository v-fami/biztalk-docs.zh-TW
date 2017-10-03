---
title: "如何將憑證指派給接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, receive locations
- receive locations, certificates
- managing [receive locations], certificates
ms.assetid: 54ae300e-62c5-480f-a9b7-e5c3457a0f80
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94554aa5781ed609e5129d58ab75e5709e432278
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-assign-a-certificate-to-a-receive-location"></a>如何將憑證指派給接收位置
本主題說明如何使用「BizTalk Server管理」主控台，將安全性憑證指派給接收位置。 您只能在雙向接收位置上執行此程序。 憑證必須存在於執行 BizTalk Server 之電腦的「其他人」憑證存放區，否則無法處理與此接收位置相關的訊息，並且會有錯誤列入記錄。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-assign-a-certificate-to-a-receive-location"></a>若要將憑證指派給接收位置  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀結構中，展開您要為其指派憑證給接收位置的 BizTalk 群組與 BizTalk 應用程式。  
  
3.  展開**接收位置**，以滑鼠右鍵按一下接收位置，按一下**屬性**，然後按一下 **憑證**。  
  
4.  如果憑證存在於本機電腦上，按一下**瀏覽**，瀏覽至您想要指派給此憑證的接收位置，然後再按一下**確定**。 否則，略過此步驟。  
  
    > [!NOTE]
    >  如果您是從遠端電腦執行此作業，請確定憑證不僅存在於本機電腦，也存在於執行 BizTalk Server 的電腦。 否則，接收位置將無法處理訊息。  
  
5.  如果憑證不存在於本機電腦上**指紋**方塊中輸入或貼上憑證指紋，然後再按一下**確定**。 憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字。  
  
## <a name="see-also"></a>另請參閱  
 [管理接收位置](../core/managing-receive-locations.md)