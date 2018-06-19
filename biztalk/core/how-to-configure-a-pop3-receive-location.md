---
title: 如何設定 POP3 接收位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive locations, POP3 adapters
- POP3 adapters, receive locations
- configuring [POP3 adapters], receive locations
ms.assetid: 259cd105-733a-4f87-be30-c02e6bd0f457
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 410bfed33402d8d810434e7ff9287fa5c01462da
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969340"
---
# <a name="how-to-configure-a-pop3-receive-location"></a>如何設定 POP3 接收位置
您可以在 BizTalk Server 管理主控台中設定 POP3 接收位置配接器變數。 若未在接收位置設定屬性，則會使用在 [BizTalk Server 管理] 主控台中設定的預設接收處理常式值。  
  
> [!NOTE]
>  完成下列程序之前，您必須已經新增接收埠。 如需詳細資訊，請參閱[如何建立接收埠](../core/how-to-create-a-receive-port.md)。  
  
 **若要設定 POP3 接收位置的變數**  
  
1.  在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開您想要在其中建立接收位置的應用程式。  
  
2.  在 BizTalk Server 管理主控台中，在左窗格中，按一下 **接收埠**節點。 然後在右窗格中，使用滑鼠右鍵按一下與現有接收位置關聯的接收埠，或是您要與新接收位置關聯的接收埠，然後按一下 **[屬性]**。  
  
3.  在**接收埠屬性**對話方塊的左窗格中，選取**接收位置**，然後在右窗格中，按兩下現有接收位置或按一下**新增**以建立新接收位置。  
  
4.  在**接收位置屬性**對話方塊中，於**傳輸**區段旁邊**類型**，選取**POP3**從下拉式清單中，然後按一下 **設定**。  
  
5.  在**POP3 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**套用 MIME 解碼**|指定是否將 MIME 解碼套用到 POP3 配接器接收的訊息。 MIME 解碼是用來將內送訊息及任何附件剖析成 Multipart BizTalk 訊息。 **重要事項：** 如果此值設為`False`則 POP3 配接器將提交包括訊息標頭至 BizTalk Server 的完整電子郵件內文。 <br /><br /> 預設值：`True`|  
    |**內文部分內容類型**|指定要提交到 BizTalk Server 的內送電子郵件訊息的內文部分內容類型。 這是選擇性設定。 請參閱[何謂 POP3 配接器？](../core/what-is-the-pop3-adapter.md)如需詳細資訊。|  
    |**內文部分索引**|指定要提交到 BizTalk Server 的內送電子郵件訊息的內文部分。 請參閱[何謂 POP3 配接器？](../core/what-is-the-pop3-adapter.md)如需詳細資訊。<br /><br /> 預設值： 0|  
    |**郵件伺服器**|指定接受 POP3 配接器輪詢之信箱所在的 POP3 郵件伺服器。 **注意：** URI 傳送埠或接收位置不能超過 256 個字元。|  
    |**[通訊埠]**|指定 POP3 郵件伺服器的連接埠。<br /><br /> 有效值：1 到 65535 (含 1 與 65535)。<br /><br /> 預設值： 0**附註：** 0 的值，表示如果使用預設 POP3 連接埠 110**使用 SSL**是`False`或通訊埠 995 如果**使用 SSL**是`True`。|  
    |**驗證配置**|指定要提供給目的地伺服器的驗證類型。<br /><br /> 有效的選項包括：<br /><br /> -   **基本**<br />-   **摘要**<br />-   **SPA** **附註：** 使用 SPA 驗證時，必須使用下列格式的其中一個指定使用者名稱： 網域帳戶必須使用下列語法輸入：\<網域名稱\>\\< 使用者名稱\>本機帳戶必須使用下列語法輸入：\<機器名稱\>\\< 使用者名稱\>|  
    |**密碼**|指定要用於 POP3 伺服器驗證的使用者密碼。|  
    |**使用 SSL**|指定是否要使用「安全通訊端層」(SSL) 與目的地伺服器通訊。<br /><br /> 預設值：`False`|  
    |**使用者名稱**|指定要用於 POP3 伺服器驗證的使用者名稱。 此屬性需要一個值。 **注意：** 指定使用者名稱屬性必須能夠登入網路的帳戶。 POP3 配接器會連接至與針對 [使用者名稱] 屬性指定之帳戶相關聯的信箱。 因此，您無法使用 POP3 配接器來連接至指派給指定之帳戶以外的信箱。 例如，即使多個帳戶擁有與特定帳戶相關聯之信箱的讀取權限，您還是只能針對 [使用者名稱] 指定實際的帳戶名稱。|  
    |**錯誤閾值**|指定在關閉配接器前需等待的網路或通訊協定錯誤的最大數目。 指定 0 值可避免配接器關閉。<br /><br /> 預設值： 10|  
    |**輪詢間隔**|指定每次嘗試從 POP3 伺服器擷取訊息之間的間隔。<br /><br /> 預設值： 5|  
    |**輪詢間隔單位**|指定要用於測量單位**輪詢間隔**。<br /><br /> 預設值：分|  
  
6.  按一下 **[確定]**。  
  
7.  在**接收位置屬性**對話方塊方塊中，輸入適當的值，以完成設定的接收位置，然後按一下**確定**儲存設定。 如需有關資訊**接收位置屬性**對話方塊中，請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。  
  
> [!NOTE]
>  若設定讀取的信箱包含超過 2,147,483,647 個電子郵件訊息，POP3 配接器將產生錯誤而無法處理任何訊息。 POP3 配接器會儲存信箱的訊息計數，其會設定讀取為 Int32 變數，且 Int32 資料型別的最大值為 2,147,483,647。  
  
> [!IMPORTANT]
>  當 POP3 配接器成功從目標信箱擷取電子郵件之後，會從信箱刪除該電子郵件。 此行為是設計用來協助避免 POP3 配接器擷取一個電子郵件的多個複本。 若不想要刪除信箱中的電子郵件，請勿設定 POP3 接收位置來監督信箱。  
  
## <a name="see-also"></a>請參閱  
 [設定 POP3 配接器](../core/configuring-the-pop3-adapter.md)