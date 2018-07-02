---
title: 如何復原企業單一登入 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 845e6ff7-88a8-4ab4-b307-f9275d44600e
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d56953fcab29b53f23ba3097296a74aeb67a17c8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973119"
---
# <a name="how-to-recover-enterprise-single-sign-on"></a>如何復原企業單一登入
在復原 BizTalk Server 之前，您必須先復原「企業單一登入」(SSO)。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須以「單一登入系統管理員」群組成員及「系統管理員」群組成員的身分登入，才可執行此工作。  
  
-   您必須具有在 SSO 組態期間使用的密碼。  
  
-   所有資料庫在遠端伺服器都保持完整。  
  
-   備份主要密碼檔要保持完整，並儲存在安全的地方。  
  
### <a name="to-recover-enterprise-single-sign-on"></a>復原企業單一登入  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 組態**。  
  
2. 在 Microsoft BizTalk Server 組態，在主控台樹狀目錄中，按一下**企業 SSO**。  
  
3. 在 [詳細資料] 窗格中，選取**啟用企業單一登入此電腦上**，然後按一下**加入現有的 SSO 系統**。  
  
4. 在 **資料存放區**，輸入裝載 SSO 資料庫與 SSO 資料庫名稱的 SQL server 的名稱。  
  
5. 在  **Windows 服務**，輸入您原來安裝和設定 BizTalk Server 時，您會使用 SSO 服務帳戶的使用者名稱和密碼。  
  
   > [!NOTE]
   >  您可使用不同的帳戶，但此帳戶必須是「單一登入系統管理員」群組的成員。  
  
6. 按一下 [套用組態]。  
  
    未擷取任何主要密碼的警告會出現。 您可使用事件檢視器檢查企業單一登入服務現在是否已啟動且在電腦上執行。  
  
7. 按一下 **檔案**，然後按一下**結束**。  
  
8. 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
9. 在命令提示字元中，輸入：  
  
     **cd Program Files\Common Files\Enterprise Single Sign-on**  
  
10. 在命令提示字元中，輸入：  
  
     **ssoconfig-restoreSecret***\<backupfile  \>*  
  
     何處*\<backupfile\>* 是您備份主要祕密檔案的名稱。  
  
     當**ssoconfig**備份檔案密碼，提示您輸入的密碼 SSO 組態期間指定。 如果密碼不正確， **ssoconfig**顯示下列訊息：  
  
     **作業已順利完成**  
  
## <a name="see-also"></a>另請參閱  
 [復原執行 BizTalk Server 的電腦](../core/recovering-a-computer-running-biztalk-server.md)   
 [設定企業 SSO 使用 BizTalk Server 組態](http://msdn.microsoft.com/library/f63d1aec-a8c7-4e76-a67f-19af69e252f0)