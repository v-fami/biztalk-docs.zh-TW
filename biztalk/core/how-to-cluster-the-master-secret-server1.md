---
title: 如何叢集化主要密碼 Server1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Master Secret server, second node
- Master Secret server, restoring
- clustering, Master Secret server
- Master Secret server, clustering
ms.assetid: ef817fa4-e43d-4e3d-8686-5bd675708001
caps.latest.revision: 47
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9740bb1c73dd5f416dda3c2f29bb15fbc7241a51
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25972948"
---
# <a name="how-to-cluster-the-master-secret-server"></a>如何叢集化主要密碼伺服器
我們建議您依照本節的指示，在主要密碼伺服器上對「企業單一登入」(SSO) 服務進行成功的叢集化處理。  
  
 當您對主要密碼伺服器進行叢集化時，「單一登入」伺服器會與主要密碼伺服器的作用中叢集執行個體通訊。 同樣的，主要密碼伺服器的作用中叢集執行個體也會與 SSO 資料庫通訊。  
  
 您必須是 SSO 系統管理員，才能執行此程序。  
  
> [!CAUTION]
>  您不能在「網路負載平衡」(NLB) 叢集上安裝主要密碼伺服器。  
  
### <a name="to-install-and-configure-enterprise-sso-on-the-cluster-nodes"></a>在叢集節點上安裝和設定企業單一登入  
  
1.  在每個叢集節點上安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 在**元件安裝**，選取**企業單一登入管理模組**和**企業單一登入主要密碼伺服器**。 已順利完成安裝之後，請執行**不**執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態。  
  
2.  建立**SSO 系統管理員**和**SSO 分支機構系統管理員**網域群組。 若要建立企業單一登入服務的叢集執行個體，您必須建立這些群組，做為網域群組。  
  
3.  建立或指定成員的網域帳戶**SSO 系統管理員**網域群組。 每個節點上的企業單一登入服務設定為以網域帳戶登入。 此帳戶必須具有**以服務方式登入**叢集中的每個節點上的權限。  
  
4.  新增的帳戶，您用來登入加入網域的設定程序期間**SSO 系統管理員**群組。  
  
    > [!IMPORTANT]
    >  如果未完成步驟 3 和 4，企業單一登入服務的組態將會失敗。  
  
5.  啟動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態。  
  
6.  選取**自訂組態**選項，然後輸入**資料庫伺服器名稱**，**使用者名**，和**密碼**值。 選取**設定**才能繼續。  
  
    > [!NOTE]
    >  因為您只會設定企業單一登入服務，此時，您只需輸入您稍早在此建立的網域帳戶。  
  
7.  選取**企業單一登入**從左窗格的選項，以及設定 「 企業單一登入 」 功能的下列選項：  
  
    1.  選取**啟用企業單一登入此電腦上**核取方塊。  
  
    2.  選取**建立新的 SSO 系統**。  
  
    3.  輸入**資料存放區**如**伺服器名稱**和**資料庫名稱**值。  
  
    4.  確認您稍早建立的網域帳戶是與「企業單一登入」服務相關聯的帳戶。  
  
    5.  輸入您稍早為 SSO 系統管理員 」 角色相關聯的群組建立的網域 SSO 系統管理員群組。  
  
    6.  輸入您稍早為 SSO 分支機構系統管理員 」 角色相關聯的群組建立的網域 SSO 分支機構系統管理員群組。  
  
8.  選取**企業單一登入密碼備份**選項從左窗格，並提供適當的參數來備份企業單一登入密碼。 根據預設，企業單一登入密碼備份至*\<磁碟機\>*: Files\Enterprise Single Sign-on \Program Files\Common\\*SSOxxxx*.bak。  
  
9. 按一下**套用組態**和檢閱摘要。  
  
10. 按一下**下一步**套用設定。  
  
11. 按一下**完成**以關閉 組態精靈。  
  
12. 關閉[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態。  
  
13. 登入被動叢集節點並開始[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態。  
  
14. 選擇**自訂組態**選項，然後輸入相同的值**資料庫伺服器名稱**，**使用者名**，和**密碼**，您輸入時設定第一個叢集節點。 輸入這些值後, 按一下**設定**才能繼續。  
  
15. 選取**企業單一登入**從左窗格的選項，以及設定 「 企業單一登入 」 功能的下列選項：  
  
    1.  選取**啟用企業單一登入此電腦上**選項。  
  
    2.  選取**加入現有的 SSO 系統**。  
  
    3.  輸入的相同值的 SSO 資料庫**伺服器名稱**和**資料庫名稱**您輸入時設定第一個叢集節點。  
  
    4.  為網域帳戶輸入您在設定第一個叢集節點時所輸入的相同值。  
  
16. 選取**套用組態**顯示摘要。  
  
17. 選取**下一步**套用設定。  
  
18. 選取**完成**以關閉 組態精靈。  
  
19. 關閉[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態。  
  
### <a name="to-update-the-master-secret-server-name-in-the-sso-database"></a>若要更新在 SSO 資料庫中的主要密碼伺服器名稱  
  
1.  從命令提示字元，對主動叢集節點輸入下列命令，以停止和重新啟動「企業單一登入」服務：  
  
    ```  
    net stop entsso  
    ```  
  
     和  
  
    ```  
    net start entsso  
    ```  
  
2.  請依照以下步驟執行，將 SSO 資料庫中的主要密碼伺服器名稱變更為叢集名稱：  
  
    > [!NOTE]
    >  叢集名稱是定義您要建立叢集的網路名稱資源的名稱群組 / 叢集服務或將包含叢集 「 企業單一登入 」 服務的應用程式。 例如，此名稱可能是*BIZTALKCLUSTER*。  
  
    1.  將下列程式碼貼在文字編輯器中：  
  
        ```  
        <sso>  
          <globalInfo>  
            <secretServer>BIZTALKCLUSTER</secretServer>  
          </globalInfo>  
        </sso>  
        ```  
  
        > [!NOTE]
        >  *BIZTALKCLUSTER*是叢集中建立實際網路名稱資源的預留位置群組 / 叢集服務或應用程式。  
  
    2.  將檔案儲存為.xml 檔案。 例如，將檔案儲存為 SSOCLUSTER.xml。  
  
    3.  在命令提示字元，變更為「企業單一登入」安裝資料夾。 根據預設，安裝資料夾是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
    4.  在命令提示字元輸入下列命令，以更新資料庫中的主要密碼伺服器名稱：  
  
        ```  
        ssomanage -updatedb XMLFile  
        ```  
  
        > [!NOTE]
        >  *XMLFile*是您稍早儲存的.xml 檔案名稱的預留位置。  
  
### <a name="to-create-the-clustered-enterprise-sso-resource"></a>建立叢集化企業單一登入資源  
  
1.  如果未設定叢集與叢集的分散式交易協調器 (MSDTC) 資源遵循 「 改善錯誤中 BizTalk Server 所使用 Windows 伺服器叢集容錯 」 白皮書中的步驟[http://go.microsoft.com/fwlink/ 嗎？LinkId = 69207](http://go.microsoft.com/fwlink/?LinkId=69207)建立叢集的 MSDTC 資源。  
  
2.  按一下**啟動**，**程式**，**系統管理工具**，然後**容錯移轉叢集管理**啟動容錯移轉叢集管理程式。  
  
3.  在左窗格中，以滑鼠右鍵按一下**容錯移轉叢集管理**按一下**管理叢集**。  
  
4.  在**選取以管理叢集**對話方塊方塊中，輸入叢集，以進行管理，然後按一下**確定**。  
  
5.  在左窗格中，按一下以選取叢集的服務或應用程式中包含 IP 位址與網路名稱資源。 請依照[如何建立使用磁碟、 IP 位址和名稱資源的叢集群組](../core/how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource1.md)與 IP 位址和網路名稱資源建立群組，如果不存在。  
  
    > [!NOTE]
    >  叢集「企業單一登入」服務不會明確要求在相同群組中使用實體叢集磁碟資源。  
  
6.  叢集的服務或應用程式上按一下滑鼠右鍵，指向**將資源加入**，然後按一下**泛型服務**顯示**新增資源精靈**對話方塊。  
  
    > [!IMPORTANT]
    >  在**一般服務參數**對話方塊中，如果您沒有按一下以選取**網路名稱作為電腦名稱**核取方塊，SSO 用戶端電腦將會產生類似下列的錯誤時它們請嘗試連絡企業單一登入服務的這個叢集執行個體：  
    >   
    >  無法擷取主要密碼。  
    >   
    >  確認主要密碼伺服器名稱是否正確以及是否可用。 密碼伺服器名稱： ENTSSO 錯誤碼： 0x800706D9，沒有可從端點對應程式的多個端點。  
  
7.  在**選取服務**頁面**新增資源精靈**，按一下以選取**企業單一登入服務**按一下**下一步**。  
  
8.  在**確認**頁面上，按一下**下一步**。  
  
9. 在**摘要**頁面上，按一下**完成**。 「 企業單一登入服務的叢集執行個體將會出現在**其他資源**在中央窗格中**容錯移轉叢集管理**介面。  
  
10. 以滑鼠右鍵按一下 「 企業單一登入服務的叢集執行個體，然後選取**屬性**顯示**企業單一登入服務內容** 對話方塊。  
  
11. 按一下**相依性** 索引標籤的內容 對話方塊中，然後按一下**插入**。  
  
12. 按一下下拉式方塊底下**資源**，選取**名稱：** 資源，然後按一下**確定**。  
  
### <a name="to-restore-the-master-secret-on-the-second-cluster-node"></a>還原第二個叢集節點上的主要密碼  
  
1.  在容錯移轉叢集管理，以滑鼠右鍵按一下叢集的服務或應用程式中包含叢集 「 企業單一登入 」 服務，然後按一下**將此服務或應用程式上線**以啟動所有中的資源叢集的服務或應用程式。  
  
2.  叢集的服務或應用程式上按一下滑鼠右鍵，指向**將此服務或應用程式到另一個節點移動**，然後按一下第二個節點。 這個步驟會將移動叢集的服務或應用程式中包含叢集的企業單一登入服務的第一個節點從第二個節點。  
  
3.  以滑鼠右鍵按一下叢集 「 企業單一登入 」 服務，然後按一下**讓此服務或應用程式離線**、 以滑鼠右鍵按一下企業 SSO 服務的叢集執行個體，然後按一下 **讓此服務或應用程式上線**。  
  
    > [!NOTE]
    >  如果沒有完成這個步驟，嘗試還原主要密碼可能就無法成功。  
  
4.  將主要密碼備份檔案從第一個節點複製到第二個節點上的 \Enterprise Single Sign-On 安裝資料夾。 根據預設，安裝資料夾是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
5.  登入第二個節點，然後在命令提示中變更至「企業單一登入」安裝資料夾。  
  
6.  從命令提示字元輸入下列命令，以還原主要密碼至第二個節點：  
  
    ```  
    ssoconfig -restoresecret RestoreFile  
    ```  
  
    > [!NOTE]
    >  取代*RestoreFile*使用的路徑以及包含主要密碼備份檔案的名稱。  
  
     主要密碼儲存在下列位置的登錄中：  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS  
  
7.  將包含叢集化「企業單一登入」服務的叢集化服務或應用程式從此叢集節點移至其他叢集節點，以確保容錯移轉功能運作正常。 接著將叢集群組移回，以確認容錯移轉回復功能也運作正常。  
  
## <a name="see-also"></a>請參閱  
 [如何建立使用磁碟、 IP 位址和名稱資源的叢集群組](../core/how-to-create-a-cluster-group-with-a-disk-ip-address-and-name-resource1.md)
