---
title: 如何叢集化 SSO 與 BizTalk 主控件在相同的叢集 Group1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 413cc8f4-f343-4c1c-8b79-3b15cb4c101d
caps.latest.revision: 44
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 554f6a6515b9b586387c85e040b051e528a9db8b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966967"
---
# <a name="how-to-cluster-sso-and-a-biztalk-host-in-the-same-cluster-group"></a>如何叢集化 SSO 與 BizTalk 主控件使其位於相同的叢集群組
使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您可以在相同的 Windows Server 叢集上叢集一或多個 BizTalk 主控件 」 和 「 企業單一登入 (SSO) 服務。  
  
> [!NOTE]
>  正確實作此策略需要為叢集資源相同的叢集群組中建立任何 BizTalk 主控件執行個體和 SSO 服務。  
  
 使用 Windows 叢集，搭配一或多個 BizTalk 主控件和 SSO 通常採用下列其中一種類別：  
  
1. 叢集化 SSO 主要密碼伺服器與相同的叢集群組中的一或多個 BizTalk 主控件。  
  
    在此案例中，叢集的 BizTalk 主控件和叢集的 SSO 服務之間的相依性便能維繫，讓所有資源的叢集群組發生容錯移轉時，隨群組都移動。  
  
    如果 SSO 服務設定為叢集資源上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦，您必須在相同的叢集群組中建立叢集的 IIS web 服務。 這必須為了確保所有外掛式主控件執行個體將 SSO 服務正在執行的叢集節點上執行。 這可確保任何外掛式主控件執行個體中執行的配接器將會有 SSO 服務的存取權，因為在 IIS 中執行的外掛式主控件執行個體。  
  
   > [!NOTE]
   >  如果非叢集的 BizTalk 主控件執行個體正在執行相同的 SSO 服務的叢集執行個體正在執行的叢集節點上，SSO 服務的叢集執行個體無法容錯移轉，除非叢集的 BizTalk 主控件執行個體已停止。 非叢集的 BizTalk 主控件執行個體維護時執行叢集節點上的 SSO 服務的叢集執行個體的相依性，並防止容錯移轉中的 SSO 服務的叢集執行個體。 基於這個理由，建議您不要建立非叢集的 BizTalk 主控件執行 SSO 服務的叢集執行個體的同一個叢集節點上執行的執行個體。  
  
2. 叢集化 SSO 服務 （非主要密碼伺服器） 與相同的叢集群組中的一或多個 BizTalk 主控件。 採行此類做法時，必須要有遠端主要密碼伺服器可供使用。 在此案例中，被維護叢集的 BizTalk 主控件和叢集的 SSO 服務之間的相依性，因此所有資源的叢集群組發生容錯移轉時，隨群組都移動。  
  
    如果 SSO 服務設定為叢集資源上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦，您必須在相同的叢集群組中建立叢集的 IIS web 服務。 這必須為了確保所有外掛式主控件執行個體將 SSO 服務正在執行的叢集節點上執行。 這可確保任何外掛式主控件執行個體中執行的配接器將會有 SSO 服務的存取權，因為在 IIS 中執行的外掛式主控件執行個體。  
  
   > [!NOTE]
   >  如果非叢集的 BizTalk 主控件執行個體正在執行相同的叢集節點上的 SSO 服務的叢集執行個體執行然後 SSO 服務的叢集執行個體無法能夠容錯移轉叢集的 BizTalk 主控件執行個體已停止。 非叢集 BizTalk 主控件執行個體保持相依，SSO 服務的叢集節點上執行的叢集執行個體時，並防止容錯移轉中的 SSO 服務的叢集執行個體。 基於這個理由，建議您不要建立 BizTalk 主控件執行 SSO 服務的叢集執行個體的同一個叢集節點上執行的非叢集執行個體。  
  
3. 叢集 Windows 伺服器叢集上的一或多個 BizTalk 主控件，而不叢集化 SSO 服務。 在此案例中，一或多個 BizTalk 主控件設定為叢集資源，但 SSO 服務不會設定為叢集資源。 這項設計為叢集 BizTalk 主控件提供高可用性，但並不提供供 SSO 服務的高可用性。 在此案例中，如果節點上的 SSO 服務失敗然後 BizTalk Server 元件依賴該節點上的 SSO 也會失敗。 如需如何將 BizTalk Server 主控件設定為叢集資源的詳細資訊，請參閱[如何將 BizTalk 主控件設定為叢集資源](http://msdn.microsoft.com/library/6e9aab00-7623-4175-bb12-ba916306f1e3)。  
  
   下列程序會說明您應該遵循相同的 Windows Server 叢集上叢集化 BizTalk 主控件和 SSO 服務的步驟。  
  
### <a name="to-cluster-a-biztalk-host-and-the-sso-master-secret-server-on-the-same-windows-server-cluster"></a>叢集 BizTalk 主控件和 SSO 主要祕密伺服器相同的 Windows Server 叢集上  
  
1. 如果叢集未設定叢集的 Distributed Transaction Coordinator (MSDTC) 資源，在 Windows Server 容錯移轉叢集上叢集 MSDTC 依照中的步驟[檢查清單： 在 Windows Server 2008 中建立 MS DTC 資源容錯移轉叢集](http://go.microsoft.com/fwlink/p/?LinkID=129677)(http://go.microsoft.com/fwlink/p/?LinkID=129677)。  
  
2. 安裝和設定 Windows Server 叢集上的 SSO 服務，依照下列中的步驟[如何叢集化主要密碼伺服器](http://msdn.microsoft.com/library/59895616-4178-46d0-b9ff-95589b809ff5)。 由於您將 Windows Server 叢集上執行 BizTalk Server，安裝所有必要的 BizTalk Server 元件，即使您將只是要設定 SSO 元件在此階段。  
  
3. 叢集上的 IIS[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦，依照下列所述的步驟[Microsoft 知識庫文章 970759 「 設定 IIS 7.0 中 Microsoft Windows Server 2008 容錯移轉叢集 」](http://go.microsoft.com/fwlink/p/?LinkId=152793) (<http://go.microsoft.com/fwlink/p/?LinkId=152793>)。 在叢集的 SSO 服務的相同叢集群組中建立叢集的 IIS Web 服務。  
  
4. 移動叢集群組包含叢集的 SSO 服務，其中一個叢集節點中，並登入到這個叢集節點。  
  
5. 啟動 BizTalk Server 組態程式，並完成此叢集節點上的 BizTalk Server 設定。 由於這是第一部 BizTalk Server 電腦群組中的，按一下**建立新的 BizTalk 群組**設定 BizTalk 群組時。  
  
6. BizTalk Server 組態已成功完成之後，將包含叢集的 SSO 服務的其他叢集節點和登入叢集節點的叢集群組。  
  
7. 啟動 BizTalk Server 組態程式，並完成此叢集節點上的 BizTalk Server 設定。 按一下 **加入現有的 BizTalk 群組**這個叢集在節點上，設定 BizTalk 群組元件時，指定您建立第一個節點的 BizTalk 群組。  
  
8. BizTalk Server 組態已成功完成之後，建立一或多個叢集 BizTalk 主控件依照中的步驟[如何將 BizTalk 主控件設定為叢集資源](http://msdn.microsoft.com/library/6e9aab00-7623-4175-bb12-ba916306f1e3)。  
  
   > [!NOTE]
   >  在此案例中，則必須建立為叢集化 SSO 服務資源的相同叢集群組中的叢集資源的所有 BizTalk 主控件。 已在叢集化 SSO 服務的 Windows Server 叢集節點上執行的非叢集的 BizTalk 主控件執行個體不支援的設定。 這是因為叢集的 SSO 服務容錯移轉至 BizTalk 主控件執行個體上的 SSO 服務的相依性的另一個節點時，非叢集的 BizTalk 主控件執行個體將會失敗。  
  
### <a name="to-cluster-a-biztalk-host-and-sso-non-master-secret-server-on-the-same-windows-server-cluster-when-the-sso-master-secret-server-is-remote"></a>叢集化 BizTalk 主控件和 SSO （非主要密碼伺服器） 相同的 Windows Server 叢集上遠端 SSO 主要密碼伺服器時  
  
1. 如果叢集未設定叢集的 Distributed Transaction Coordinator (MSDTC) 資源，在 Windows Server 容錯移轉叢集上叢集 MSDTC 依照中的步驟[檢查清單： 在 Windows Server 2008 中建立 MS DTC 資源容錯移轉叢集](http://go.microsoft.com/fwlink/p/?LinkID=129677)(http://go.microsoft.com/fwlink/p/?LinkID=129677)。  
  
2. 建立網域群組名稱**SSO 系統管理員**並**SSO 分支機構系統管理員**。 若要建立 SSO 服務的叢集執行個體，您必須建立**SSO 系統管理員**並**SSO 分支機構系統管理員**做為網域群組的群組。  
  
3. 建立或指定成員的網域帳戶**SSO 系統管理員**網域群組。 每個節點上的 SSO 服務會設定為此網域帳戶登入。 此帳戶必須具備**登入為服務**直接在叢集中的每個節點上。  
  
4. 新增您用來登入網域的安裝和設定程序期間使用的帳戶**SSO 系統管理員**群組。  
  
   > [!IMPORTANT]
   >  若未完成步驟 3 和 4，SSO 服務的組態將會失敗。  
  
5. 登入其中一個叢集節點，並安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 選取 安裝成功完成時，啟動組態程式的選項。  
  
6. 選擇**自訂組態**選項，然後輸入適當的值，如**資料庫伺服器名稱**，**使用者名稱**並**密碼**欄位。 輸入這些值之後，按一下**設定**按鈕以繼續。  
  
7. 設定 SSO 功能的下列選項：  
  
   1.  選取核取方塊旁**啟用企業單一登入此電腦上**。  
  
   2.  按一下選項以**加入現有的 SSO 系統**。  
  
   3.  為現有的 SSO 資料庫伺服器名稱和資料庫名稱輸入值。  
  
   4.  指定要使用企業單一登入服務的帳戶時，請輸入現有的 SSO 服務帳戶。  
  
8. 由於這是第一部 BizTalk 伺服器群組中選擇的選項**建立新的 BizTalk 群組**設定 BizTalk 群組元件時。  
  
9. 視需要指定其餘的組態選項，然後將 BizTalk Server 組態套用至該節點。  
  
10. BizTalk Server 組態一旦在第一個節點上順利設定完成後，請登入第二個節點並安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 選取 安裝成功完成時，啟動組態程式的選項。  
  
11. 選擇**自訂組態**選項，然後再輸入適當的值，如**資料庫伺服器名稱**，**使用者名稱**並**密碼**欄位。 輸入這些值之後，按一下**設定**按鈕以繼續。  
  
12. 設定 SSO 功能的下列選項：  
  
    1.  選取核取方塊旁**啟用企業單一登入此電腦上**。  
  
    2.  按一下 **加入現有的 SSO 系統**。  
  
    3.  為現有的 SSO 資料庫伺服器名稱和資料庫名稱輸入值。  
  
    4.  指定要使用企業單一登入服務的帳戶時，請輸入現有的 SSO 服務帳戶。  
  
13. 選擇的選項**加入現有的 BizTalk 群組**這個叢集在節點上，設定 BizTalk 群組元件時，指定您建立第一個節點的 BizTalk 群組。  
  
14. 視需要指定其餘的組態選項，然後將 BizTalk Server 組態套用至該節點。  
  
15. BizTalk Server 組態已順利完成之後，請遵循下列步驟來叢集化 SSO 服務：  
  
    1.  停止每個叢集節點上的 SSO 服務，輸入下列命令，從命令：  
  
        ```  
        net stop entsso  
        ```  
  
    2.  在 容錯移轉叢集管理，將所有的叢集群組移到其中一個節點，並登入此節點。  
  
    3.  在左側窗格中，按一下以選取叢集的服務或應用程式中包含的 IP 位址和網路名稱資源。 此叢集的服務或應用程式將包含叢集的 SSO 服務和叢集的 BizTalk 主控件。  
  
        > [!NOTE]
        >  叢集的 SSO 服務不明確需要使用相同群組中叢集實體磁碟資源。  
  
    4.  叢集的服務或應用程式上按一下滑鼠右鍵，指向**將資源新增**，然後按一下**泛型服務**顯示**新增資源精靈**  對話方塊。  
  
    5.  上**選取服務**頁面**新資源精靈**，選取**企業單一登入服務**，然後按一下**下一步**。  
  
    6.  在 [**確認**頁面上，按一下**下一步]**。  
  
    7.  在 **摘要**頁面上，按一下**完成**。 「 企業單一登入服務的叢集執行個體將會出現**其他資源**中的中間窗格**容錯移轉叢集管理**介面。  
  
    8.  以滑鼠右鍵按一下 「 企業單一登入服務的叢集執行個體，然後選取**屬性**顯示**企業單一登入服務屬性** 對話方塊。  
  
    9. 按一下 **相依性** 索引標籤的屬性 對話方塊中，然後按一下**插入**。  
  
    10. 按一下下拉式清單方塊底下**Resource**，選取**名稱：** 資源，然後按一下**確定**。  
  
        > [!IMPORTANT]
        >  如果您需要新增相依性**名稱：** 資源，當使用者試著連絡 SSO 服務的這個叢集執行個體 SSO 用戶端電腦會產生類似下面的錯誤：  
        >   
        >  無法擷取主要密碼。  
        >   
        >  確認主要密碼伺服器名稱是否正確以及是否可用。 祕密伺服器名稱： ENTSSO 錯誤碼： 0x800706D9，沒有可用的終點的多個端點。  
  
16. 叢集上的 IIS[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦，依照下列所述的步驟[Microsoft 知識庫文章 970759 「 設定 IIS 7.0 中 Microsoft Windows Server 2008 容錯移轉叢集 」](http://go.microsoft.com/fwlink/p/?LinkId=152793) (<http://go.microsoft.com/fwlink/p/?LinkId=152793>)。 在叢集的 SSO 服務的相同叢集群組中建立叢集的 IIS web 服務。  
  
17. 在容錯移轉叢集管理，以滑鼠右鍵按一下叢集的服務或應用程式，包含叢集 「 企業單一登入服務，然後按一下 **將此服務或應用程式上線**啟動中的所有資源叢集的服務或應用程式。  
  
18. 叢集的服務或應用程式上按一下滑鼠右鍵，指向**將此服務或應用程式到另一個節點移動**，然後按一下第二個節點。 此步驟中將叢集的服務或應用程式中包含叢集的企業單一登入服務的第一個節點從第二個節點。  
  
19. 以滑鼠右鍵按一下叢集的企業單一登入服務，然後按一下 **讓此服務或應用程式離線**，然後以滑鼠右鍵按一下 SSO 服務的叢集執行個體，並按一下**使這項服務或應用程式上線**。  
  
20. 在叢集的 SSO 服務使用 ssomanage 命令列公用程式中設定所有使用者的 SSO 伺服器名稱。 此命令應該從 SSO 安裝資料夾中執行，每個 BizTalk server 群組中。 比方說，下列的命令列會設定為叢集的 SSO 服務的所有使用者的 SSO 伺服器名稱：  
  
    ```  
    ssomanage -serverall SSOCLUSTER  
    ```  
  
    > [!NOTE]
    >  *SSOCLUSTER*是在包含叢集的 SSO 服務的叢集群組中建立實際網路名稱資源的預留位置。  
  
21. 更新存取的 SSO 伺服器名稱**BizTalk 群組屬性**頁面，即可參考叢集的 SSO 服務。 開啟**BizTalk Server 管理]**，以滑鼠右鍵按一下 [BizTalk 群組，然後選取**屬性**功能表項目，更新 SSO 伺服器名稱的項目，然後按一下**確定**。  
  
22. 請依照下列中的步驟[如何將 BizTalk 主控件設定為叢集資源](http://msdn.microsoft.com/library/6e9aab00-7623-4175-bb12-ba916306f1e3)您已建立叢集的 SSO 服務的相同叢集群組中建立一或多個叢集的 BizTalk 主控件執行個體。  
  
    > [!NOTE]
    >  在此案例中，則必須建立為叢集化 SSO 服務資源的相同叢集群組中的叢集資源的所有 BizTalk 主控件。 已在叢集化 SSO 服務的 Windows Server 叢集節點上執行非叢集的 BizTalk 主控件執行個體不支援的設定。 這是因為叢集的 SSO 服務容錯移轉至 BizTalk 主控件執行個體上的 SSO 服務的相依性的另一個節點時，非叢集的 BizTalk 主控件執行個體將會失敗。