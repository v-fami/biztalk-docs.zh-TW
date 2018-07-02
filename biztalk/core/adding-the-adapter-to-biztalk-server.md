---
redirect_url: /biztalk/core/adding-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: e075bfbfdb082887ea746ee81e24a5176d9ad98d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976599"
---
# <a name="adding-the-adapter-to-biztalk-server"></a>新增配接器至 BizTalk Server
Microsoft BizTalk Adapter for JD Edwards OneWorld 包含 [接收處理常式] 和 [傳送處理常式] 資料夾。 [傳送處理常式] 資料夾包含 BizTalkServerApplication。 BizTalk Adapter for JD Edwards OneWorld 是可建立的；它會在與 BizTalk Server 相同的程序中執行，而且不會在外掛式主控件程序中執行。  
  
 請使用下列程序將此配接器新增至 BizTalk Server。  
  
### <a name="to-add-biztalk-adapter-for-jd-edwards-oneworld"></a>若要新增 BizTalk Adapter for JD Edwards OneWorld  
  
1. 在上**開始**功能表上，指向**Program Files**，指向[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**啟動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
2. 依序展開**BizTalk Server 管理**，展開**BizTalk 群組**，然後展開**平台設定**。  
  
3. 以滑鼠右鍵按一下**配接器**，指向**新增**，然後按一下**配接器**。  
  
4. 在 [**配接器屬性**] 對話方塊中，輸入配接器的名稱。 例如，JDEdwards。  
  
5. 選取  **jdeoneworld**從**配接器**清單，然後再按**確定**。  
  
## <a name="verifying-the-adapter"></a>確認配接器  
 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以確認配接器藉由查看正確運作**邏輯系統**視窗。 在初次安裝時，因為您尚未建立與伺服器系統的連線，也尚未建立任何邏輯系統，所以這個視窗會是空的。  
  
#### <a name="to-verify-that-the-adapter-is-running-correctly"></a>若要確認配接器已正確執行  
  
1. 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk 群組**，展開**平台設定**，依序展開**配接器**，然後選取  **[Jdeoneworld]**。  
  
2. 在 [詳細資料] 窗格中，以滑鼠右鍵按一下**BizTalkServerApplication**，然後選取**屬性**。  
  
3. 按一下 **[屬性]** 索引標籤。  
  
4. 設定 SQL 連線參數。  
  
   -   **定義 SQL 資料庫參數-** 的 SQL Server 名稱和資料庫是您在安裝期間設定。 您可以在這個文字區域中重新定義此配接器的伺服器與資料庫。  
  
5. 按一下 **關閉**以結束**邏輯系統**視窗。  
  
    下一個步驟是要使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 來新增邏輯系統。  
  
## <a name="see-also"></a>另請參閱  
 [規劃與架構](../core/planning-and-architecture17.md)   
 [BizTalk Adapter for JD Edwards OneWorld 中的安全性](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)   
 [新增 BizTalk Adapter for JD Edwards OneWorld](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)