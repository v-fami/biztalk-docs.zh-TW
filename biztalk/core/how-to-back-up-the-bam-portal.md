---
title: "如何備份 BAM 入口網站 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cea02e6-e387-4048-a1f3-d7c3c562f470
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27e7308e54505c795e35ffa2fbb2d287c1a49ec4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-the-bam-portal"></a>如何備份 BAM 入口網站
如果您使用商務活動監控 (BAM)，必須備份 BAM 入口網站做為備份 BizTalk Server 的一部分。 如果您未使用 BAM，則此程序是選擇性的。  
  
 網際網路資訊服務 (IIS) 版本而定您要備份的備份程序的某些部分與相當不同。 IIS 6.0 可讓您分別備份應用程式集區設定和網站組態，您可以加密組態備份檔案使用的密碼。  
  
 IIS 7.0 會將應用程式集區和網站的組態設定儲存至單一檔案，applicationHost.config。ApplicationHost.config 檔案並未加密，但帳戶密碼，如果有的話，會加密檔案中。 加密會使用您要備份的電腦中的憑證來執行。 此設定無法還原到它的來源以外的電腦。  
  
 您無法備份 BAM 入口網站設定使用 IIS 7.0 管理員;您必須使用**Appcmd.exe**命令列工具。 如需 Appcmd 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=147497](http://go.microsoft.com/fwlink/?LinkId=147497)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「系統管理員」群組成員的身分登入，才能執行此程序。  
  
### <a name="to-back-up-the-bam-portal-iis-70"></a>若要備份 BAM 入口網站 (IIS 7.0)  
  
1.  按一下 **[開始]**，然後按一下 **[執行]**。  
  
2.  在 執行 對話方塊中，開啟 方塊中，輸入下列命令： `runas /user:` *computername*`\`*accountname* `cmd`，然後按一下 **確定**或按下**Enter**。  
  
     *Accountname*必須是本機電腦上 administrators 群組的成員。  
  
3.  出現提示時，輸入的密碼*accountname*，然後按下**Enter**。  
  
4.  型別`cd %windir%\system32\inetsrv`，然後按下**Enter**。  
  
5.  型別`appcmd add backup “` *backupname*`”`，然後按下**Enter**。  
  
     您沒有輸入備份的名稱。 如果未設定，就會自動產生。 自動產生的備份名稱的範例是"20090224T123302。 」  
  
     若要查看現有的設定備份清單，請輸入`appcmd list backup`，然後按下**Enter**。 使用者所建立的備份會儲存在**%windir%\system32\inetsrv\backup**目錄。 若要查看所提供的備份選項的清單**appcmd.exe**，型別`appcmd backup /?`，然後按下**Enter**。  
  
## <a name="see-also"></a>另請參閱  
 [備份執行 BizTalk Server 的電腦](../core/backing-up-a-computer-running-biztalk-server.md)   
 [復原執行 BizTalk Server 的電腦](../core/recovering-a-computer-running-biztalk-server.md)   
 [BAM 入口網站](../core/bam-portal.md)