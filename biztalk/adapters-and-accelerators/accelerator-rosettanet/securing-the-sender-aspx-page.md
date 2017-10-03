---
title: "保護傳送者 ASPX 頁面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ASPX pages, protocol rules
- security, ASPX pages
- RNIFSend.aspx
- ASPX pages, security
- protocol rules [ASPX pages]
ms.assetid: 8214e3f5-a8e9-4d71-957d-ed0852035030
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0c5d5ec97d4d4aed862ffc1dbc0d75d0c0430d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="securing-the-sender-aspx-page"></a>保護傳送者 ASPX 頁面
本主題說明如何保護 RNIFSend.aspx 頁面，避免未經授權的使用。 您可以使用下列兩個程序：  
  
-   在網際網路資訊服務 (IIS) 管理員中，保護 RNIFSend.aspx 以確保未經授權的伺服器，無法使用 RNIFSend.aspx 頁面從您的網路傳輸未經授權的訊息。  
  
-   使用 Microsoft Internet Security and Acceleration (ISA) Server 建立外寄 HTTP 要求的通訊協定規則。  
  
### <a name="to-secure-rnifsendaspx"></a>保護 RNIFSend.aspx  
  
1.  在 Web 伺服器上您用於 RNIF 訊息傳輸，按一下 **啟動**，指向**所有程式**，指向 **系統管理工具**，然後按一下  **Internet Information Services (IIS) 管理員**。  
  
2.  在 [IIS 管理員] 中，展開 [本機電腦] 節點，再展開**網站**，然後展開**Default Web Site**。  
  
3.  按一下**BTARNApp**，然後在右窗格中，以滑鼠右鍵按一下**RNIFSend.aspx**。  
  
4.  按一下 **[屬性]**。 在**檔案安全性**索引標籤的**IP 位址及網域名稱限制**區段中，按一下**編輯**。  
  
5.  在 IP 位址和網域名稱限制 對話方塊中，按一下**拒絕存取**，然後按一下 **新增**。  
  
6.  在**授與存取權**對話方塊中，新增全部 BizTalk Servers 執行傳送作業。 如果新增單一伺服器，請按一下**單一電腦**。 在**IP 位址**方塊中，輸入電腦的 IP 位址，然後按一下**確定**。  
  
7.  如果新增的伺服器群組，按一下 **電腦群組**，然後執行下列步驟：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**網路識別碼**|輸入您想使用的網路。|  
    |**子網路遮罩**|輸入您想使用的子網路遮罩。|  
  
8.  按一下 **[確定]**。  
  
    > [!NOTE]
    >  如果您將所有的傳送作業放到另一台執行不同執行個體的主機上，只要新增這台電腦就可以了。 您可以拒絕其他電腦的存取。  
  
9. 按一下**確定**，然後按一下 **確定**一次。  
  
### <a name="to-create-a-protocol-rule-of-outgoing-http-requests"></a>建立外寄 HTTP 要求的通訊協定規則  
  
1.  在 ISA 管理按一下**存取原則**，然後按一下 **通訊協定規則**。  
  
2.  建立新的通訊協定規則，名為**HTTP**使用 TCP 通訊協定。  
  
3.  在屬性頁面中的新的 HTTP 通訊協定規則，在**套用至**索引標籤上，選取**適用於下面指定的用戶端位址組**。 輸入您想要存取該頁面的用戶端 IP。  
  
## <a name="see-also"></a>另請參閱  
 [管理設定、 憑證、 資料庫和安全性](manage-configuration-certificates-databases-security.md)