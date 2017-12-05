---
title: "如何移動主要密碼伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [Master Secret server], migrating
- migrating, Master Secret server
- Master Secret server, migrating
ms.assetid: 2bc5137e-f81d-486d-bb91-7c5981896f79
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4158b59e3cce9664ca7c8c7d8ea4c5e3221b04b9
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-move-the-master-secret-server"></a>如何移動主要密碼伺服器
您可以遵循本主題所說明的步驟，將某一部伺服器上的主要密碼移動到另一部伺服器，以及將伺服器上的主要密碼移動到「Windows 伺服器叢集」。  
  
### <a name="to-move-the-master-secret-from-one-server-to-another-server"></a>將某一部伺服器上的主要密碼移動到另一部伺服器  
  
1.  若尚未在新的主要密碼伺服器上安裝「Microsoft 企業單一登入」(SSO) 伺服器，請先安裝。 啟動 Microsoft 企業單一登入伺服器安裝程式，從 BizTalk Server CD 上的 \Platform\SSO\setup.exe。  
  
2.  若尚未在新的主要密碼伺服器上設定「企業單一登入」，請先設定。 依照下列步驟來設定「企業單一登入」：  
  
    1.  開啟組態工具。 根據預設，組態工具位於\<磁碟機\>: \Program Files\Common Files\Enterprise Single On\Configuration.exe。  
  
    2.  按一下以選取**企業單一登入**的左窗格中。  
  
    3.  選取此核取方塊旁的 **啟用企業單一登入此電腦上**右窗格中。  
  
    4.  按一下選項以**加入現有的 SSO 系統**。  
  
    5.  指定現有**伺服器名稱**和**資料庫名稱**為 SSO 資料庫選項。  
  
    6.  指定現有的企業單一登入服務帳戶的**企業單一登入伺服器 Windows 服務**選項。  
  
        > [!NOTE]
        >  這必須是一個網域帳戶。  
  
    7.  按一下選項以**套用組態**按一下**設定**在組態精靈 對話方塊，以完成設定。  
  
    8.  按一下**完成**並關閉 組態工具。  
  
3.  備份現有的主要密碼中的步驟[如何重新設定主要密碼](../core/how-to-back-up-the-master-secret.md)。  
  
4.  將 SSO 資料庫中的主要密碼伺服器變更為參照新的主要密碼伺服器。 例如，新的主要密碼伺服器的名稱可能**NewMSSServer**。 若要這樣做，請在原始主要密碼伺服器上遵循下列步驟：  
  
    1.  將下列程式碼貼在文字編輯器 (如 notepad.exe) 中：  
  
        ```  
        <sso>  
        <globalInfo>  
        <secretServer>NewMSSServer</secretServer>  
        </globalInfo>  
        </sso>  
        ```  
  
    2.  將檔案儲存為 .xml 檔。 例如，將檔案儲存為**NewMSSServer.xml**。  
  
    3.  在命令提示字元，變更為「企業單一登入」安裝資料夾。 根據預設，安裝資料夾是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。  
  
    4.  型別**ssomanage-updatedb** *XMLFile*來更新資料庫中的主要密碼伺服器名稱。  
  
        > [!NOTE]
        >  取代*XMLFile*您儲存的.xml 檔案的名稱。  
  
        > [!NOTE]
        >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
5.  在新的主要密碼伺服器上重新啟動「企業單一登入」服務。  
  
6.  請依照下列中的步驟還原到新的主要密碼伺服器上備份主要密碼[如何還原主要密碼](../core/how-to-restore-the-master-secret.md)新的主要密碼伺服器上。  
  
### <a name="to-move-the-master-secret-from-one-server-to-a-windows-server-cluster"></a>將伺服器上的主要密碼移動到 Windows 伺服器叢集  
  
1.  安裝和設定 Windows Server 叢集上的企業單一登入服務的中的步驟[如何叢集化主要密碼伺服器](../core/how-to-cluster-the-master-secret-server1.md)。 完成所有步驟，本主題中所述的步驟除了**還原第二個叢集節點上的主要密碼**> 一節。 您將會移動現有的主要密碼伺服器叢集因為未選擇選項以**建立新的 SSO 系統**設定企業單一登入叢集節點上時。 在設定每個叢集節點時，請在 BizTalk Server 組態程式中設定下列企業 SSO 功能的選項：  
  
    1.  核取方塊旁的 **啟用企業單一登入此電腦上**。  
  
    2.  按一下選項以**加入現有的 SSO 系統**。  
  
    3.  為現有的 SSO 資料庫伺服器名稱和資料庫名稱輸入值。  
  
    4.  在指定「企業單一登入」服務使用的帳戶時，輸入現有的 SSO 服務帳戶。  
  
2.  將現有的主要密碼備份檔案複製到每個叢集節點上的 \Enterprise Single Sign-On 資料夾。  
  
3.  如果此 Windows Server 叢集將裝載一或多個叢集 BizTalk 主控件，請使用 ssomanage 命令列公用程式，將所有使用者的 SSO 伺服器名稱設定為叢集的主要密碼伺服器。 此命令應該會從群組中每個 BizTalk Server 的企業 SSO 安裝資料夾執行。 例如，以下的命令列會將所有使用者的 SSO 伺服器名稱設定為叢集式的主要密碼伺服器。  
  
    ```  
    ssomanage -serverall SSOCLUSTER  
    ```  
  
    > [!NOTE]
    >  *SSOCLUSTER*實際網路名稱資源的預留位置，在含有叢集主要密碼伺服器資源的叢集群組中建立這種情況下，所有 BizTalk 主控件必須都建立為在相同的叢集資源叢集 「 企業單一登入 」 服務資源的叢集群組。 在已叢集化「企業單一登入」服務的 Windows Server 叢集節點上執行非叢集 BizTalk 主控件執行個體，並不是支援的組態。 這是因為非叢集 BizTalk 主控件執行個體將在已叢集化的「企業單一登入」服務容錯移轉至另一個節點時，因為 BizTalk 主控件執行個體對單一登入服務的相依性而失敗。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
4.  在 叢集系統管理員，以滑鼠右鍵按一下包含叢集 「 企業單一登入服務資源，叢集群組，然後按一下**上線**以啟動叢集群組中所有的資源。  
  
5.  如果此 Windows Server 叢集將裝載一或多個叢集 BizTalk 主控件，更新 SSO 伺服器名稱存取**BizTalk 群組屬性**頁面，即可參考叢集的主要密碼伺服器。 啟動**BizTalk Server 管理**，以滑鼠右鍵按一下 BizTalk 群組，然後選取**屬性**功能表項目，然後更新的項目**SSO 伺服器名稱**按一下**確定**。  
  
    > [!NOTE]
    >  在此實例中，所有 BizTalk 主控件都必須建立為與叢集化「企業單一登入」服務資源位於相同叢集群組中的叢集資源。 在已叢集化「企業單一登入」服務的 Windows Server 叢集節點上執行非叢集 BizTalk 主控件執行個體，並不是支援的組態。 這是因為非叢集 BizTalk 主控件執行個體將在已叢集化的「企業單一登入」服務容錯移轉至另一個節點時，因為 BizTalk 主控件執行個體對單一登入服務的相依性而失敗。  
  
6.  以滑鼠右鍵按一下企業 SSO 服務的叢集執行個體，然後按一下**離線**、 以滑鼠右鍵按一下企業 SSO 服務的叢集執行個體，然後按一下 **上線**。  
  
    > [!NOTE]
    >  如果此步驟未完成，嘗試還原主要密碼可能不會成功。  
  
7.  在含有叢集式主要密碼伺服器之 Windows 叢集的各個節點上復原備份的主要密碼。 請依照[如何還原主要密碼](../core/how-to-restore-the-master-secret.md)含有叢集主要密碼伺服器的 Windows 叢集的每個節點上。  
  
## <a name="see-also"></a>請參閱  
 [管理主要密碼](../core/managing-the-master-secret.md)