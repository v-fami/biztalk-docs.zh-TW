---
title: "如何指派憑證給傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, assigning
- managing [send ports], certificates
- assigning certificates
- certificates, send ports
ms.assetid: ba9e9c8b-f5b6-4fee-9e89-31b0f1df6ed4
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec19c845c6b0cfb5d19bd7a961fe9ddfbcf2a3d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-assign-a-certificate-to-a-send-port"></a>如何指派憑證給傳送埠
本主題描述如何使用 BizTalk Server 管理主控台來指派安全性憑證給傳送埠。 憑證必須存在於執行 BizTalk Server 之電腦的「其他人」憑證存放區，否則無法處理與此傳送埠相關的訊息，並且會有錯誤列入記錄。  
  
> [!NOTE]
>  應用程式開發人員可以使用此主題中的程序，在開發程序中指派安全性憑證給傳送埠。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-assign-a-certificate-to-a-send-port"></a>指派憑證給傳送埠  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀結構中，展開您要為其指派憑證給傳送埠的 BizTalk 群組與 BizTalk 應用程式。  
  
3.  展開**傳送埠**，以滑鼠右鍵按一下傳送埠，按一下**屬性**，然後按一下 **憑證**。  
  
4.  如果憑證存在於本機電腦上，按一下**瀏覽**，瀏覽至您想要指派給這個傳送埠，然後按一下 憑證**確定**。 否則，略過此步驟。  
  
    > [!NOTE]
    >  即使憑證存在於本機電腦，執行 BizTalk Server 的電腦 (如果是兩台不同的電腦) 上也必須有這個憑證，傳送埠才能夠處理訊息。  
  
5.  如果憑證不存在於本機電腦上**指紋**方塊中輸入或貼上憑證指紋，然後再按一下**確定**。 憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字。  
  
## <a name="see-also"></a>另請參閱  
 [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)