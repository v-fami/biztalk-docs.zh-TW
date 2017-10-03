---
title: "設定連接埠使用 Wcf-siebel 配接器 |Microsoft 文件"
description: "建立 WCF Siebel BizTalk Server 中使用 Siebel eBusiness 應用程式配接器的傳送埠"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6314104-c742-440c-b530-b5a82295353a
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 486e33b6c8f61a315548a84f145dc45824300710
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-a-port-using-the-wcf-siebel-adapter"></a>設定使用 Wcf-siebel 配接器的連接埠
如何設定 WCF Siebel 輸出上執行作業使用 Siebel 系統的傳送埠[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
## <a name="prerequisites"></a>必要條件  
使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。 如需詳細的權限的相關資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，和[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。
  
## <a name="deploy-adapters-for-sending-messages-to-a-siebel-system"></a>部署配接器將訊息傳送至 Siebel 系統  
 執行下列步驟來設定 Wcf-siebel 傳送埠將訊息傳送至 Siebel 系統使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
1.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2.  新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需指示，請參閱[新增 Siebel 配接器至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md)。  
  
3.  在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。  
  
4.  展開您要在其下部署的應用程式[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
5.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，並指向您想要根據 BizTalk Server 和 Siebel 系統之間的通訊模式設定的連接埠類型。  
  
6.  在**傳送埠屬性**對話方塊**一般**索引標籤上，輸入傳送埠的名稱。  
  
7.  從**類型**下拉式清單，選取 Wcf-siebel 配接器中，使用您先前加入，然後按一下**設定**。  
  
8.  在傳輸屬性對話方塊中，執行下列動作：  
  
    1.  按一下**一般**索引標籤上，按一下 **設定**按鈕，並提供連接參數的值。 如需連線 URI 的詳細資訊，請參閱[建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。  
  
    2.  在**一般**索引標籤的**動作**文字方塊中，輸入作業的動作。 請參閱[訊息與訊息結構描述](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)的每個作業的動作清單。 例如，叫用的帳戶業務元件的 Insert 作業的動作是：  
  
        ```  
        http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
        ```  
  
    3.  按一下**繫結**索引標籤上，指定繫結屬性的值。 如需詳細資訊，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。  
  
    4.  按一下**認證**索引標籤，然後執行下列其中一項：  
  
        -   選取**不會使用單一登入**選項，並指定使用者名稱和密碼來連接至 Siebel 系統。  
  
        -   選取**使用單一登入**選項，並指定分支機構 ESSO 應用程式。  
  
         如需相對於 BizTalk Server 安全性的詳細資訊，請參閱[Siebel 配接器與 BizTalk Server 安全性](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md)。  
  
    5.  若要返回**傳送埠屬性**對話方塊中，按一下 **確定**。  
  
9. 從**傳送處理常式**下拉式清單中，選取**BizTalkServerApplication**。  
  
10. 如果您在步驟 5 中選擇靜態單向傳送埠，指定傳送管線。 從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。  
  
11. 如果您在步驟 5 中選擇靜態請求-回應連接埠，指定傳送和接收管線。  
  
    1.  從**傳送管線**下拉式清單中，選取對應至 XMLTransmit 管線。  
  
    2.  從**接收管線**下拉式清單中，選取對應至 XMLReceive 管線。  
  
12. 按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
[手動設定在 Siebel 介面卡的實體連接埠繫結](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md)