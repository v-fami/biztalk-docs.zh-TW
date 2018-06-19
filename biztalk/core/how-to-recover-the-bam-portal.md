---
title: 如何復原 BAM 入口網站 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a5df99-6d03-4f1f-8540-1700d3a0b9db
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 781191047e0ee99b0000c7b773d46aa035a7e1d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254598"
---
# <a name="how-to-recover-the-bam-portal"></a>如何復原 BAM 入口網站
如果您使用商務活動監控 (BAM)，您必須復原 BAM 入口網站的復原一部分您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 如果您未使用 BAM，則此程序是選擇性的。  
  
 復原 BAM 入口網站組態的程序的差異您使用的 IIS 版本而定。 當您還原適用於 IIS 7 設定時，您會使用**Appcmd.exe**，而且您還原整個預設網站上，而不只是 BAM 入口網站的組態。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「系統管理員」群組成員的身分登入，才能執行此程序。  
  
### <a name="to-recover-the-bam-portal-configuration-iis-70"></a>若要復原 BAM 入口網站組態 (IIS 7.0)  
  
1.  在 執行 對話方塊中，開啟 方塊中，輸入下列命令： `runas /user:` *computername*`\`*accountname* `cmd`，然後按一下 **確定**或按下**Enter**。  
  
     *Accountname*必須是本機電腦上 administrators 群組的成員。  
  
2.  出現提示時，輸入的密碼*accountname*，然後按下**Enter**。  
  
3.  型別`cd %windir%\system32\inetsrv`，然後按下**Enter**。  
  
4.  型別`appcmd restore backup “` *backupname*`”`，然後按下**Enter**。  
  
     *Backupname*是您先前使用建立的備份名稱**Appcmd.exe**。 此備份必須存在於 **%windir%\system32\inetsrv\backup**目錄。 備份無法用於還原不同電腦上建立的密碼。 如果 BAMAppPool 設定為預設值以外的身分識別執行**NetworkService**帳戶，您必須分別進行設定的帳戶和密碼下, 一個步驟中所述。  
  
5.  使用**網際網路資訊服務 (IIS) 管理員**，選取**應用程式集區**中**連線**窗格。  
  
6.  在**應用程式集區**] 窗格中，以滑鼠右鍵按一下**BAMAppPool**，然後按一下 [**進階設定**  
  
7.  在**進階設定**s 對話方塊中，向下捲動至**處理序模型**> 一節。 按一下**識別**方塊。 這會導致出現方塊右邊的省略符號按鈕。 按一下**省略符號** 按鈕。  
  
8.  在**應用程式集區識別** 對話方塊中，按一下 **自訂帳戶**按鈕，然後按一下**設定** 按鈕。  
  
9. 在**設定認證**對話方塊方塊中，輸入您想要用於 BAMAppPool 的密碼與帳戶名稱。 帳戶名稱應該輸入為*電腦名稱*`\`*accountname*，或*網域*`\`*accountname*. 按一下**確定**關閉**設定認證**對話方塊。  
  
10. 按一下**確定**關閉**應用程式集區識別**對話方塊。  
  
11. 按一下**確定**關閉**進階設定**對話方塊。  
  
12. 確認**BAMAppPool**應用程式集區的清單中選取。 在**動作**] 右邊的窗格**網際網路資訊服務 (IIS) 管理員**畫面上，於**應用程式集區工作**，按一下 [**啟動**.  
  
## <a name="see-also"></a>另請參閱  
 [復原執行 BizTalk Server 的電腦](../core/recovering-a-computer-running-biztalk-server.md)   
 [BAM 入口網站](../core/bam-portal.md)