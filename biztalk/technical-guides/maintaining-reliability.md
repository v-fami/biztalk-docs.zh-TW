---
title: 維護可靠性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 09cdce13-a75b-44d7-8388-7a868bb51c69
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb1f956c0f3b09ee51d3dd9d05f64dbd3eeeab3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299646"
---
# <a name="maintaining-reliability"></a>維護可靠性
本節提供有關如何解決的可靠性問題的資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。 這些問題可能會發現在會執行例行的維護工作檢查[常式維護檢查清單](../technical-guides/routine-maintenance-checklists.md)本文件一節。  
  
 除了本節中的主題，這份文件中的其他主題位址可靠性問題。 這些主題中所列[相關章節](../technical-guides/maintaining-reliability.md#BKMK_Related)下方。  
  
## <a name="testing-group-failover"></a>測試群組容錯移轉  
 執行本節中的程序，應每月執行的可靠性檢查的一部分。 這些程序包括測試群組的容錯移轉原則，以及測試是否可以進行容錯移轉群組資源。  
  
> [!NOTE]  
>  如果電腦已加入網域，Domain Admins 群組的成員才能執行此程序。  
  
> [!NOTE]  
>  本章節內容中執行的程序，您必須登入本機電腦上 Administrators 群組的成員身分，或者必須已被委派適當的權限。  
  
 執行下列步驟，以測試在執行 Windows Server 2008 電腦上的群組容錯移轉。  
  
#### <a name="to-test-a-group-failover-policy"></a>若要測試群組容錯移轉原則  
  
1.  請確定您已安裝**容錯移轉叢集**功能在至少兩部電腦上執行 Windows Server 2008，以便建立 Windows 容錯移轉叢集的兩個節點。 如需有關如何安裝這項功能的指示，請參閱[安裝容錯移轉叢集功能](http://go.microsoft.com/fwlink/?LinkId=157259)(http://go.microsoft.com/fwlink/?LinkId=157259)。  
  
2.  開啟 依序按一下 容錯移轉叢集管理**啟動**，然後按一下**系統管理工具**，然後按一下**容錯移轉叢集管理**。  
  
3.  在主控台樹狀目錄中，展開 [叢集節點，再展開**服務和應用程式**] 節點，以滑鼠右鍵按一下要容錯移轉，然後按一下應用程式的叢集執行個體**屬性**。  
  
4.  在**容錯移轉**索引標籤上，設定**指定期間內的最大失敗次數**為 0，然後按一下**確定**。  
  
5.  在主控台樹狀目錄中，依序展開**服務和應用程式**節點。  
  
6.  在詳細資料窗格中，以滑鼠右鍵按一下資源，然後**屬性**。  
  
7.  在**原則**索引標籤上，設定**指定期間內重新啟動次數上限**為 0，然後按一下**確定**。  
  
8.  以滑鼠右鍵按一下資源，請按一下**其他動作**，然後按一下**模擬的失敗，此資源的**。 請確認是否群組會做出反應根據您在上一個步驟中指定的原則。  
  
9. 以滑鼠右鍵按一下要容錯移轉，然後按一下應用程式的叢集執行個體**屬性**。  
  
10. 在**容錯移轉**索引標籤上，設定**指定期間內的最大失敗次數**為 1，然後按一下**確定**。  
  
11. 以滑鼠右鍵按一下資源，並選取**將此資源上線**。  
  
#### <a name="to-test-whether-group-resources-can-fail-over"></a>若要測試是否可以進行容錯移轉群組資源  
  
1.  請確定您已安裝**容錯移轉叢集**執行 Windows Server 2008 的電腦上的功能。 如需有關如何安裝這項功能的指示，請參閱[安裝容錯移轉叢集功能](http://go.microsoft.com/fwlink/?LinkId=157259)(http://go.microsoft.com/fwlink/?LinkId=157259)。  
  
2.  開啟 依序按一下 容錯移轉叢集管理**啟動**，然後按一下**系統管理工具**，然後按一下**容錯移轉叢集管理**。  
  
3.  在主控台樹狀目錄中，展開 [叢集節點，再展開**服務和應用程式**] 節點，然後按一下應用程式容錯移轉叢集執行個體。  
  
4.  在**動作**功能表上，按一下 **將此服務或應用程式到另一個節點移動**，然後按一下目標應用程式的容錯移轉節點。  
  
5.  在**請確認動作**對話方塊方塊中，選擇將移至所選節點的應用程式。  
  
6.  確定您移至應用程式的節點會列出針對**目前擁有者**應用程式的詳細資料窗格中。  
  
##  <a name="BKMK_BTSGrp"></a>確保多部伺服器是 BizTalk 群組的一部分  
 若要確保系統的可靠性，至少兩個實體 BizTalk 伺服器應該是 BizTalk 群組的一部分。  如果您要將伺服器新增至 BizTalk 群組，請注意下列事項：  
  
-   一部伺服器僅能與一個 BizTalk 群組關聯。 如果伺服器已經屬於其他群組，您必須先從目前的群組移除該伺服器，才可將其新增至新群組。 如需從 BizTalk 群組移除伺服器的詳細資訊，請參閱 < 如何將移除伺服器從群組"[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkId=155577](http://go.microsoft.com/fwlink/?LinkId=155577)。  
  
-   與 BizTalk Server 環境中不同伺服器建立關聯的 BizTalk 群組，除了交換訊息之外並不會互動。  
  
-   BizTalk Server 執行階段必須安裝在您想新增至 BizTalk 群組的電腦上。  
  
> [!NOTE]  
>  若要執行本主題中的程序，您必須為 SSO 系統管理員群組的成員，以及 Windows Administrators 群組的成員登入。  
  
#### <a name="to-determine-whether-at-least-two-physical-biztalk-servers-are-part-of-the-biztalk-group"></a>若要判斷是否在至少兩部實體 BizTalk 伺服器屬於 BizTalk 群組  
  
1.  開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台按一下**啟動**、 指向**所有程式**、 指向**Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下**BizTalk Server 管理**。  
  
2.  展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]] 節點，展開 [ **BizTalk 群組** 節點，然後展開**平台設定**節點。  
  
3.  按一下**伺服器**節點。 請確認多部伺服器會列在**伺服器**窗格。  
  
    > [!NOTE]  
    >  若要檢視伺服器的相關資訊，請以滑鼠右鍵按一下伺服器，指向**檢視**，然後按一下**群組中樞頁面**。  
  
#### <a name="to-add-a-server-to-a-biztalk-group"></a>將伺服器新增至 BizTalk 群組  
  
1.  您想要新增至 BizTalk 群組的電腦，按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下 **BizTalk Server 組態**。  
  
2.  在**Microsoft BizTalk Server 2010 組態**，選取**自訂組態**。  
  
3.  在**資料庫伺服器名稱**，輸入伺服器正要的 BizTalk 群組的 SQL server 的名稱。  
  
4.  在**服務認證**，輸入適當的使用者名稱和密碼，服務會使用，然後按一下**設定**。  
  
5.  在畫面左側的導覽樹狀目錄中，按一下 **企業單一登入**。  
  
6.  在**企業單一登入**頁面上，按一下**加入現有的 SSO 系統**。  
  
    > [!NOTE]  
    >  確定伺服器名稱和資料庫名稱是指向伺服器正要的 BizTalk 群組的主要 SSO 資料庫伺服器。  
  
7.  在畫面左側的導覽樹狀目錄中，按一下 **群組**。  
  
8.  在**群組**頁面上，按一下**加入現有的 BizTalk 群組**。  
  
    > [!NOTE]  
    >  確定伺服器名稱和資料庫名稱是指向伺服器正要 BizTalk 群組的資料庫。  
  
9. 在功能表列上，按一下 **套用組態**設定這部電腦上的企業單一登入和群組。  
  
##  <a name="BKMK_Related"></a> 相關章節  
  
-   檢查硬體 RAID 中失敗的磁碟的相關資訊，請參閱 < 檢視磁碟屬性 > 中的 Windows Server 2003 產品說明在[http://go.microsoft.com/fwlink/?linkid=104161](http://go.microsoft.com/fwlink/?linkid=104161)。  
  
-   如需手動檢查擱置的訊息資訊，請參閱 < Investigating 協調流程、 連接埠和訊息失敗 」 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkID=154512](http://go.microsoft.com/fwlink/?LinkID=154512)。  
  
-   如需確保每個主機有兩個以上的實體 BizTalk 伺服器上執行的執行個體資訊，請參閱[高可用性的 BizTalk 主控件](../technical-guides/high-availability-for-biztalk-hosts.md)。  
  
-   如需確保每個主機有兩個以上的實體 BizTalk 伺服器上執行的執行個體資訊，請參閱[調整出接收主機](../technical-guides/scaling-out-receiving-hosts.md)。  
  
-   如需已經過測試，確保所有的叢集服務該容錯移轉的相關資訊，請參閱[叢集主要密碼伺服器](../technical-guides/clustering-the-master-secret-server.md)。  
  
-   如需確保 SQL 服務 下，叢集的 BizTalk 資料庫資訊，請參閱[叢集 BizTalk Server Databases2](../technical-guides/clustering-the-biztalk-server-databases2.md)。  
  
-   如需判斷是否 （需要不同的主控件） 正在使用任何不穩定的程式碼的詳細資訊，請參閱[高可用性的 BizTalk 主控件](../technical-guides/high-availability-for-biztalk-hosts.md)。  
  
-   如需執行的所有新的 BizTalk 應用程式功能測試的資訊，請參閱[測試應用程式](../technical-guides/testing-an-application.md)