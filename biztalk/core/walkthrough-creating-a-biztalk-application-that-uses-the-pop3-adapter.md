---
title: 逐步解說： 建立 BizTalk 應用程式使用 POP3 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tutorials, POP3 adapters
- configuring [POP3 adapters], mailboxes
- configuring [POP3 adapters], tutorials
- POP3 adapters, mailboxes
- POP3 adapters, tutorials
- configuring [POP3 adapters], Outlook Express
ms.assetid: b44c3b1d-7b4f-425c-831a-1ce5f6379595
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3bd79682f78591b066fe1e6db671c3dab4a8333
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985303"
---
# <a name="walkthrough-creating-a-biztalk-application-that-uses-the-pop3-adapter"></a>逐步解說： 建立使用 POP3 配接器的 BizTalk 應用程式
本節將帶領您使用 POP3 配接器來建立簡單的 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式。  
  
> [!NOTE]
>  此應用程式假設您可以存取執行 Microsoft [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 且已安裝與設定電子郵件服務的電腦。 如需設定具備電子郵件服務的 [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 之相關資訊，請參閱 Windows Server 說明。  
> 
> [!NOTE]
>  在此範例中，將使用 Microsoft Outlook Express 做為電子郵件用戶端，而 [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 則做為電子郵件伺服器。 不過，任何 POP3 電子郵件用戶端與 RFC 相容 POP3 伺服器皆可以用於此實例。  
  
 此應用程式假設您尚未建立任何傳送埠或接收位置。 若您有現有的傳送埠或接收位置，當逐步進行這些步驟時請以適當的名稱來替代。  
  
 此應用程式是一個簡單以內容為基礎的路由應用程式，只使用一個接收位置和傳送埠。 接收位置讀取從執行的伺服器上的信箱[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]或是[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]("Windows server"\)。 傳送埠會從接收位置拾取訊息，然後將訊息傳送到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之本機檔案系統上的資料夾。  
  
 若要建立應用程式，您必須建立信箱、設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置和傳送埠、啟動傳送埠與啟用接收位置，以及傳送測試訊息到信箱。 請遵循下列步驟來建立應用程式。  
  
## <a name="create-a-mailbox-on-windows-server-2003"></a>在 Windows Server 2003 上建立信箱  
 若要在已安裝「電子郵件服務」的 Windows Server 2003 上安裝信箱，請遵循下列步驟：  
  
1. 按一下 **開始**，指向**程式**，指向**系統管理工具**，然後按一下**POP3 服務**。  
  
2. 依序展開*\<servername\>* ，按一下您想要建立信箱的網域。  
  
3. 在  **POP3 服務**對話方塊中，在右窗格中，按一下**新增信箱**選項。  
  
4. 在 **新增信箱**對話方塊中，於**信箱名稱**方塊中，輸入**EmailTest**。  
  
5. 選取 **建立關聯的使用者為此信箱**核取方塊。  
  
6. 在 **密碼**並**確認密碼**方塊中，輸入密碼，然後按一下**確定**。  
  
7. 請記下的**帳戶名稱**並**郵件伺服器**登入使用純文字驗證中所顯示資訊**POP3 服務**對話方塊，然後再按一下**確定**。 您以 POP3 傳輸類型設定的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置將會使用此資訊。  
  
## <a name="create-the-receive-location"></a>建立接收位置  
 請遵循下列步驟來建立接收位置：  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中按兩下預設的資料庫**\<** <em>machine_name</em>**\>。BizTalkMgmtDb.dbo**，其中*machine_name*是您電腦的名稱。 按一下 **應用程式**，然後按一下**BizTalk.Application.1**。  
  
2. 以滑鼠右鍵按一下**接收連接埠**，按一下**新增**，按一下 **單向接收埠**。  
  
3. 在 **接收埠屬性**對話方塊中，於**名稱**方塊中，輸入**POP3Receive**。  
  
4. 按一下 **接收位置**，然後按一下**新增**。  在 **接收位置屬性**對話方塊中，於**名稱**方塊中，輸入**POP3Receive**。  
  
5. 在 **傳輸類型**方塊中，選取**POP3**。  
  
6. 在 **接收處理常式**方塊中，選取**BizTalkServerApplication**。  
  
7. 在 **接收管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruReceive**。  
  
8. 在 [**傳輸**方塊中，按一下**設定**] 按鈕。  
  
9. 在  **POP3 傳輸屬性**對話方塊中，於**套用 MIME 解碼**方塊中，選取**False**。  
  
10. 在 **郵件伺服器**方塊中，輸入您在其中建立信箱的 Windows Server 伺服器的名稱。  
  
11. 在 **驗證配置**方塊中，選取**基本**。  
  
12. 在 **密碼**，按一下下拉箭號，然後輸入信箱的密碼。  
  
13. 在 **使用者名**方塊中，輸入信箱的完整的使用者名稱，例如 <em>username@host.domain.toplevel_domain。</em>  
  
14. 中**輪詢間隔**方塊中，輸入**1**，按一下  **確定**，然後按一下**確定**一次。  
  
## <a name="create-the-send-port-and-destination-folder-on-the-biztalk-server"></a>在 BizTalk 伺服器上建立傳送埠與目的地資料夾  
 請遵循下列步驟，在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上建立傳送埠與目的資料夾：  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 檔案系統上建立資料夾。 這將是傳送埠的目的地。  
  
2. 以滑鼠右鍵按一下**傳送埠**，按一下**新增**然後按一下 **靜態單向傳送埠。**  
  
3. 在 **傳送埠屬性**對話方塊中，於**傳輸類型**方塊中，選取**檔案**。  
  
4. 在 **名稱**方塊中，輸入**SendToFile**。  
  
5. 在 [**傳輸**方塊中，按一下**設定**] 按鈕。  
  
6. 旁**目的地資料夾**方塊中，按一下**瀏覽**，選取您在建立資料夾[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，然後按一下 **確定**。  
  
7. 在 **檔名**方塊中，輸入 **%MessageID%.txt**，然後按一下  **確定**。  
  
8. 在 **傳送管線**方塊中，選取**Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**。  
  
9. 按一下 **[篩選]**。  
  
10. 在 **屬性**方塊中，選取**BTS。ReceivePortName**。  
  
11. 在 **值**方塊中，輸入**POP3Receive**，然後按一下 **確定**。  
  
## <a name="enable-the-receive-location-and-start-the-send-port"></a>啟用接收位置並啟動傳送埠  
 請依照以下步驟執行，啟用接收位置和啟動傳送埠：  
  
1. 以滑鼠右鍵按一下**POP3Receive**接收位置，然後按一下**啟用**。  
  
2. 以滑鼠右鍵按一下**SendToFile**傳送埠，然後**開始**。  
  
   下一個步驟會傳送測試訊息到接收位置監控的信箱來測試應用程式。  
  
## <a name="configure-outlook-express-to-send-an-e-mail-message-to-the-mailbox"></a>設定 Outlook Express 以傳送一封電子郵件到信箱  
 請遵循下列步驟設定 Outlook Express，將電子郵件訊息傳送至信箱：  
  
1.  按一下 **開始**，指向**程式**，然後按一下**Outlook Express**。  
  
2.  在 Outlook Express 中，在**工具**功能表上，按一下**帳戶**。  
  
3.  按一下 **新增**，然後按一下**郵件**。  
  
4.  在 [**顯示名稱**方塊中輸入顯示名稱，然後再按一下**下一步]**。  
  
5.  在 **網際網路電子郵件地址**對話方塊中，於**電子郵件地址**方塊中，輸入**EmailTest @< 網域名稱 >**，然後按一下 **下一步**.  
  
     請務必輸入適當的值 *< 網域名稱 >*。 這個值應該符合在 Windows 伺服器上的 POP3 服務管理介面中建立此信箱時所依據的網域名稱。  
  
6.  在**電子郵件伺服器名稱**對話方塊中，於**內送郵件**並**外寄郵件**方塊中，輸入伺服器名稱或 Windows server 中，IP 位址，然後按一下 [ **下一步]**。  
  
7.  在 **網際網路郵件登入**對話方塊中，於**帳戶名稱**方塊中，輸入**EmailTest**。  
  
8.  在**密碼**方塊中，輸入 EmailTest 帳戶密碼，選取**記住密碼**選項，請按一下**下一步]**，然後按一下 [**完成**.  
  
9. 按一下以選取您剛才建立的帳戶，然後按一下**屬性**。  
  
10. 在**屬性**] 對話方塊中，按一下**進階**索引標籤中，按一下以選取的選項**保留訊息的複本伺服器上**，然後按一下 [ **[確定]**.  
  
11. 在 [**網際網路帳戶**] 對話方塊中，按一下**關閉**。  
  
12. 使用 Outlook Express 來編輯測試訊息，型別**測試**成**主旨**欄位，然後輸入**EmailTest @< 網域名稱 >** 到**到**欄位。  
  
13. 按一下 **傳送**傳送測試訊息。 若要確保 Outlook Express 會傳送測試訊息立即，按一下**傳送/接收**Outlook Express 工具列中的按鈕。  
  
## <a name="view-the-message"></a>檢視訊息  
 請依照以下步驟執行來檢視訊息：  
  
1.  若要開啟的資料夾，您指定為使用 Windows 檔案總管**目的地資料夾**傳送埠。  
  
2.  按兩下資料夾中的文件，在 [記事本] 中檢視文件的內容。  
  
## <a name="see-also"></a>另請參閱  
 [何謂 POP3 配接器？](../core/what-is-the-pop3-adapter.md)