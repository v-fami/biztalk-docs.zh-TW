---
title: 如何設定 ENTSSO 以進行 MIIS 密碼同步 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 89438935-37c1-4ac9-9ca2-7af8d9bfd3ae
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9aed37b5b3883242005f46dcc6a0253a4971d680
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005223"
---
# <a name="how-to-configure-entsso-for-miis-password-sync"></a>如何設定 ENTSSO 以進行 MIIS 密碼同步
在設定 XML 檔案和 Microsoft Identity Integration Server (MIIS) 之後，剩下的組態步驟是在企業單一登入 (ENTSSO) 系統中執行。  
  
### <a name="to-allow-password-sync-from-miis"></a>若要允許從 MIIS 進行密碼同步  
  
1.  在 企業單一登入，請按一下**伺服器**節點。  
  
2.  以滑鼠右鍵按一下適當的伺服器，然後按一下 **屬性**。  
  
3.  按一下 [**密碼同步處理**] 索引標籤。  
  
4.  選取 **允許從 MIIS 進行密碼同步處理**。  
  
5.  按一下 [確定] 。  
  
### <a name="to-enable-password-sync-on-the-system-level"></a>若要啟用系統層級的密碼同步  
  
1. 在 企業單一登入，請以滑鼠右鍵按一下**系統**節點。  
  
2. 按一下 **[屬性]**。  
  
    **屬性** 對話方塊隨即出現。  
  
3. 按一下 [**選項**] 索引標籤。  
  
4. 在 **啟用密碼同步處理**欄位中，選取**從 Windows 到配接器**。  
  
    **其他設定**  
  
    最後，您必須設定下列其中一項：  
  
   - 接受 Windows 密碼同步的密碼同步配接器。  
  
   - 至少在一個應用程式上啟用的直接密碼同步。  
  
     如需如何進行這項設定的詳細資訊，請參閱密碼同步相關文件。  
  
### <a name="to-configure-the-entsso-ma-for-miis-password-sync"></a>若要設定 EntSSO MA 以進行 MIIS 密碼同步  
  
1.  在 ENTSSO 管理代理程式**屬性**頁面上，按一下**Configure Extensions**。  
  
2.  在 **密碼延伸模組的連接資訊**欄位中，按一下**設定**。  
  
3.  在 **連接到**欄位中，輸入將接收密碼變更電腦的名稱。  
  
     電腦名稱的格式必須與在網域中為 ENTSSO 服務建立服務主要名稱 (SPN) 時使用的格式相同。  
  
     例如：  
  
     若簡短格式為 SPN = ENTSSO/ABCD1411，則輸入 ABCD1411  
  
4.  若長格式為 SPN = ENTSSO/ABCD1411.CompanyName.com，則輸入 ABCD1411.CompanyName.com  
  
### <a name="additional-configuration-steps"></a>其他組態步驟  
  
1.  按一下 **開始**，指向**所有程式**，指向**Microsoft Identity Integration Server**，然後按一下**Identity Manager**。  
  
2.  在 **[工具]** 功能表上，按一下 **[選項]**。  
  
3.  選取 **啟用密碼同步處理**。  
  
4.  在 **管理代理程式檢視**，選取**ADMA**。  
  
5.  在 **動作**窗格中，選取**屬性**。  
  
6.  在 **屬性**頁面上，選取**設定目錄分割**，然後選取**啟用此磁碟分割做為密碼同步處理來源**。  
  
7.  按一下 **目標**，然後選取 entssoma2，讓它能夠從 MIIS 接收密碼變更。 取消選取 ENTSSOMA。 按一下  **確定**，然後按一下**確定**一次。  
  
8.  在 **管理代理程式**檢視中，選取**entssoma2**。 在右窗格中，選取**屬性**。 在上**屬性**頁面上，按一下**Configure Extensions**。  
  
9. 確認**啟用密碼管理**已選取，然後按一下**設定**。  
  
10. 在 [**連線設定**] 對話方塊中，指定下列項目：  
  
    -   連接到： INTSVR1.fabrikam.com  
  
    -   使用者： fabrikam\ssosvcact  
  
    -   密碼： ssosvcact  
  
        > [!NOTE]
        >  這個帳戶應該符合 INTSVR1.fabrikam.com 上設定的 ENTSSO 服務帳戶。  
  
11. 按一下  **確定**，然後按一下**確定**一次。  
  
12. 您也可以停用 MIIS 的密碼同步。 若要這樣做，請在**Identity Manager**，按一下**工具**功能表上，按一下 **選項**，然後取消選取**Enable Password Synchronization**。  
  
     適用的限制如下：  
  
    -   您必須在與 ENTSSO 管理代理程式通訊的 ENTSSO 服務帳戶上設定 SPN，密碼同步才能正常運作。  
  
    -   MIIS 和 ENTSSO 服務之間的通訊需要 Kerberos。  
  
13. 在 ENTSSO 管理代理程式的 MIIS 連線組態中設定密碼延伸模組時，指定的帳戶必須符合從 MIIS 接收密碼之 ENTSSO 伺服器的服務帳戶。  
  
## <a name="see-also"></a>另請參閱  
 [如何使用 ENTSSO 管理代理程式](../core/how-to-use-the-entsso-management-agent.md)