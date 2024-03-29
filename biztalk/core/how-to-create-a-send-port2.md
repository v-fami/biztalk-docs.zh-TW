---
title: 如何建立傳送 Port2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.procedure.createsendport
helpviewer_keywords:
- managing [send ports], creating
- creating, send ports
- send ports, creating
ms.assetid: 7f0d07b8-1ac5-4032-bb08-2f7e05185f86
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2b3e988f9ce9df01a4fb854711340896ba28f46
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983031"
---
# <a name="how-to-create-a-send-port"></a>如何建立傳送埠
本主題描述如何使用 BizTalk Server 管理主控台來建立傳送埠。 建立傳送埠時，您必須選取要建立的傳送埠類型，如下所示：  

- 靜態單向 — 僅供傳送的連接埠。  

- 靜態請求-回應 — 等候目的地回覆的傳送埠。  

- 動態單向 — 僅供傳送的連接埠，可根據訊息屬性於執行階段繫結至通訊協定和位置。  

- 動態請求-回應 — 等候回覆的傳送埠，可根據訊息屬性於執行階段繫結至通訊協定和位置。  

  建立傳送埠之後，您可以執行下列其他步驟來完成設定：  

- 設定進階傳輸選項，例如重試一次傳送訊息的訊息失敗，以及連接埠，服務窗口排程中所述的次數[如何設定傳輸進階選項傳送埠](../core/how-to-configure-transport-advanced-options-for-a-send-port.md)。  

- 設定備份傳輸，萬一主要傳輸無法正常運作，如中所述[如何設定備份傳輸選項傳送埠](../core/how-to-configure-backup-transport-options-for-a-send-port.md)。  

- 設定篩選，以判斷哪些訊息要從訊息方塊中，路由至此傳送埠中所述[如何設定傳送埠的篩選](../core/how-to-configure-filters-for-a-send-port.md)。  

- 指派安全性憑證給傳送埠，來加密或簽署由傳送埠，處理的文件中所述[如何指派憑證給傳送埠](../core/how-to-assign-a-certificate-to-a-send-port.md)。  

- 設定傳送埠，處理訊息的追蹤選項，如中所述[如何設定傳送埠的追蹤](../core/how-to-configure-tracking-for-a-send-port.md)。  

## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。 此外，您必須擁有「企業單一登入」(SSO) 資料庫上的 SSO 分支機構系統管理員權限。 如需詳細資訊，請參閱 < [SSO 使用者群組](../core/sso-user-groups.md)。  

### <a name="to-create-a-send-port"></a>建立傳送埠  

1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  

2. 在主控台樹狀目錄中，展開您要建立傳送埠的 BizTalk 群組和 BizTalk 應用程式。  

3. 以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 建立的連接埠類型。  

4. 在 [**傳送埠屬性**] 視窗中，執行下列動作：  


   |       使用       |                                                                                                                                                                                                                                以進行此動作                                                                                                                                                                                                                                 |
   |----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |       **名稱**       |                                                                                                                                                                                            輸入新傳送埠的名稱。 這個名稱必須是 BizTalk 群組中唯一的名稱。                                                                                                                                                                                             |
   |  **傳輸類型**  |                                                                                                       從下拉式清單選取適當的傳輸類型或傳輸通訊協定。 若連接埠是請求-回應連接埠，則清單中只會顯示支援請求-回應的傳輸類型。 此屬性只會針對靜態連接埠而顯示。                                                                                                        |
   |    **設定**     |                                                                                          選取傳輸類型之後，請按一下**設定**顯示**傳輸屬性**對話方塊中，提供傳輸特定的組態選項。 此屬性只會針對靜態連接埠而顯示。 按一下 **協助**在對話方塊中的設定指示。                                                                                           |
   |   **傳送處理常式**   |                                                                                                                                                                  從下拉式清單選取傳送配接器執行所在的主控件執行個體。 此屬性只會針對靜態連接埠而顯示。                                                                                                                                                                  |
   |  **傳送管線**   |                                            從下拉式清單選取管線以處理透過此連接埠傳送的訊息。 您選取管線後，您可以按一下相鄰的省略符號 (**...**) 按鈕，以顯示**設定管線**對話方塊中，您用來設定這個特定的連接埠的每個執行個體管線屬性。 按一下 **協助**在對話方塊中的設定指示。                                             |
   | **接收管線** | 從下拉式清單選取管線以處理透過此連接埠接收的訊息。 透過此管線收到的訊息回應也將會透過此管線傳送。 您選取管線後，您可以按一下相鄰的省略符號 (**...**) 按鈕，以顯示**設定管線**對話方塊中，您用來設定這個特定的連接埠的每個執行個體管線屬性。 此屬性只會針對請求-回應連接埠而顯示。 |


5. 如果您正在建立請求-回應傳送埠，在左窗格中，按一下**輸入對應**並執行下列動作，視需要重複如果您想要新增多個對應：  


   |      使用       |                                                                             以進行此動作                                                                              |
   |---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **來源文件** | 從下拉式清單選取輸入對應的來源文件。 傳送埠可以有一個以上的對應，但是每個對應只能有唯一的來源文件。 |
   |       **對應**       |                                     從下拉式清單選取與來源及目標文件關聯的對應。                                      |
   | **目標文件** |                                              從下拉式清單選取輸入對應的目標文件。                                               |


6. 在左窗格中，按一下**輸出對應**並執行下列動作，視需要重複如果您想要新增多個對應：  


   |      使用       |                                         以進行此動作                                         |
   |---------------------|--------------------------------------------------------------------------------------------|
   | **來源文件** |         從下拉式清單選取輸出對應的來源文件。          |
   |       **對應**       | 從下拉式清單選取與來源及目標文件關聯的對應。 |
   | **目標文件** |         從下拉式清單選取輸出對應的目標文件。          |


7. 完成設定傳送埠，請按一下**確定**。  

## <a name="see-also"></a>另請參閱  
 [建立和設定傳送埠](../core/creating-and-configuring-send-ports.md)   
 [管理管線](../core/managing-pipelines.md)   
 [管理對應](../core/managing-maps.md)