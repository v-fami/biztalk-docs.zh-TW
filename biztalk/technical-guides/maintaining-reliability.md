---
title: 維護可靠性 |Microsoft Docs
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
ms.openlocfilehash: faf58e24442d2a17bace7b0d56393d1c793b9cd9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985671"
---
# <a name="maintaining-reliability"></a>維護可靠性
本節提供有關如何解決可靠性問題的資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。 這些問題可能會執行例行的維護檢查所探索到[常式維護檢查清單](../technical-guides/routine-maintenance-checklists.md)這份文件的區段。  

 在本節中的主題，除了這份文件中的其他主題會解決可靠性問題。 這些主題所述[相關章節](../technical-guides/maintaining-reliability.md#BKMK_Related)如下。  

## <a name="testing-group-failover"></a>測試群組的容錯移轉  
 在本節中執行的程序，應該每月執行的可靠性檢查的一部分。 這些程序包括測試群組的容錯移轉原則，以及測試是否可以容錯移轉群組的資源。  

> [!NOTE]  
>  如果電腦已加入網域，Domain Admins 群組的成員應該能夠執行此程序。  

> [!NOTE]  
>  在本節中執行的程序，您必須登入本機電腦上的 Administrators 群組的成員身分，或者必須已被委派適當的權限。  

 執行下列步驟，以測試在執行 Windows Server 2008 的電腦上的群組容錯移轉。  

#### <a name="to-test-a-group-failover-policy"></a>若要測試群組的容錯移轉原則  

1.  請確定您已安裝**容錯移轉叢集**功能在至少兩部電腦上執行 Windows Server 2008，以便建立兩個節點 Windows 容錯移轉叢集。 如需有關如何安裝此功能的指示，請參閱 <<c0> [ 安裝容錯移轉叢集功能](http://go.microsoft.com/fwlink/?LinkId=157259)(http://go.microsoft.com/fwlink/?LinkId=157259)。  

2.  開啟容錯移轉叢集管理，依序按一下**開始**，再按一下**系統管理工具**，然後按一下**容錯移轉叢集管理**。  

3.  在主控台樹狀目錄中，展開 叢集節點，展開**服務和應用程式**節點，以滑鼠右鍵按一下以進行容錯移轉，然後按一下 應用程式的叢集執行個體**屬性**。  

4.  在上**容錯移轉**索引標籤上，設定**指定的期間內的失敗次數上限**為 0，然後按一下**確定**。  

5.  在主控台樹狀目錄中，依序展開**服務和應用程式**節點。  

6.  在詳細資料窗格中，以滑鼠右鍵按一下資源，然後**屬性**。  

7.  在上**原則**索引標籤上，設定**指定的期間內重新啟動次數上限**為 0，然後按**確定**。  

8.  以滑鼠右鍵按一下資源，請按一下**其他動作**，然後按一下**模擬的失敗，這項資源的**。 請確認群組在回應您在上一個步驟中指定的原則是否根據。  

9. 以滑鼠右鍵按一下以進行容錯移轉，然後按一下 應用程式的叢集執行個體**屬性**。  

10. 在上**容錯移轉**索引標籤上，設定**指定的期間內的失敗次數上限**為 1，然後按一下**確定**。  

11. 以滑鼠右鍵按一下資源，然後選取**將此資源上線**。  

#### <a name="to-test-whether-group-resources-can-fail-over"></a>若要測試是否可以容錯移轉群組的資源  

1.  請確定您已安裝**容錯移轉叢集**執行 Windows Server 2008 的電腦上的功能。 如需有關如何安裝此功能的指示，請參閱 <<c0> [ 安裝容錯移轉叢集功能](http://go.microsoft.com/fwlink/?LinkId=157259)(http://go.microsoft.com/fwlink/?LinkId=157259)。  

2.  開啟容錯移轉叢集管理，依序按一下**開始**，再按一下**系統管理工具**，然後按一下**容錯移轉叢集管理**。  

3.  在主控台樹狀目錄中，展開 叢集節點，展開**服務和應用程式** 節點，然後按一下 應用程式以進行容錯移轉叢集執行個體。  

4.  在上**動作**功能表上，按一下**將此服務或應用程式到另一個節點移動**，然後按一下 要將應用程式容錯移轉的節點。  

5.  在 **請確認動作**對話方塊方塊中，選擇 移動選取的節點應用程式。  

6.  請確定您移至應用程式的節點會列出針對**目前的擁有者**應用程式的詳細資料窗格中。  

##  <a name="BKMK_BTSGrp"></a> 確保多部伺服器是 BizTalk 群組的一部分  
 若要確保系統的可靠性，至少兩個實體的 BizTalk server 應該是 BizTalk 群組的一部分。  如果您需要將伺服器新增至 BizTalk 群組，請注意下列：  

- 一部伺服器僅能與一個 BizTalk 群組關聯。 如果伺服器已經屬於其他群組，您必須先從目前的群組移除該伺服器，才可將其新增至新群組。 如需有關如何從 BizTalk 群組移除伺服器的詳細資訊，請查看 < 如何將移除伺服器從群組 」 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在幫助[ http://go.microsoft.com/fwlink/?LinkId=155577 ](http://go.microsoft.com/fwlink/?LinkId=155577)。  

- 與 BizTalk Server 環境中不同伺服器建立關聯的 BizTalk 群組，除了交換訊息之外並不會互動。  

- BizTalk Server 執行階段必須安裝在您想新增至 BizTalk 群組的電腦上。  

> [!NOTE]  
>  若要執行本主題中的程序，您必須為 SSO 系統管理員群組的成員，以及 Windows Administrators 群組的成員登入。  

#### <a name="to-determine-whether-at-least-two-physical-biztalk-servers-are-part-of-the-biztalk-group"></a>若要判斷是否至少兩個實體的 BizTalk 伺服器是 BizTalk 群組的一部分  

1. 開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中的，按一下**開始**、 指向**所有程式**，指向**Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下**BizTalk Server 管理**。  

2. 依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]節點中，展開**BizTalk 群組** 節點，然後展開**平台設定**節點。  

3. 按一下 **伺服器**節點。 確認所列出的多部伺服器是在**伺服器**窗格。  

   > [!NOTE]  
   >  若要檢視伺服器的相關資訊，以滑鼠右鍵按一下伺服器，並指向**檢視**，然後按一下**群組中樞頁面**。  

#### <a name="to-add-a-server-to-a-biztalk-group"></a>將伺服器新增至 BizTalk 群組  

1. 您想要新增至 BizTalk 群組的電腦，按一下 **開始**，按一下**所有程式**，按一下  **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下  **BizTalk Server 組態**。  

2. 在  **Microsoft BizTalk Server 2010 組態**，選取**自訂組態**。  

3. 在 **資料庫伺服器名稱**，輸入伺服器正要加入 BizTalk 群組的 SQL server 的名稱。  

4. 在 **服務認證**，輸入適當的使用者名稱和密碼，服務會使用，然後按一下**設定**。  

5. 在畫面左側的導覽樹狀目錄中，按一下**企業 SSO**。  

6. 在 **企業單一登入**頁面上，按一下**加入現有的 SSO 系統**。  

   > [!NOTE]  
   >  請確定伺服器名稱和資料庫名稱指向伺服器正要加入 BizTalk 群組的主要 SSO 資料庫伺服器。  

7. 在畫面左側的導覽樹狀目錄中，按一下**群組**。  

8. 在 **群組**頁面上，按一下**加入現有的 BizTalk 群組**。  

   > [!NOTE]  
   >  請確定伺服器名稱和資料庫名稱指向伺服器正要加入 BizTalk 群組的資料庫。  

9. 在功能表列上，按一下**套用組態**來設定 這台電腦上的 企業單一登入和群組。  

##  <a name="BKMK_Related"></a> 相關章節  

- 如需檢查硬體 RAID 中失敗的磁碟資訊，請參閱 < 檢視磁碟屬性 「 Windows Server 2003 產品說明中在[ http://go.microsoft.com/fwlink/?linkid=104161 ](http://go.microsoft.com/fwlink/?linkid=104161)。  

- 如需以手動方式檢查擱置的訊息資訊，請參閱 「 Investigating 協調流程、 連接埠和訊息失敗 」 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在幫助[ http://go.microsoft.com/fwlink/?LinkID=154512 ](http://go.microsoft.com/fwlink/?LinkID=154512)。  

- 確保每個主機有至少兩個實體的 BizTalk 伺服器上執行的執行個體的相關資訊，請參閱[高可用性的 BizTalk 主控件](../technical-guides/high-availability-for-biztalk-hosts.md)。  

- 確保每個主機有至少兩個實體的 BizTalk 伺服器上執行的執行個體的相關資訊，請參閱[相應放大接收主機](../technical-guides/scaling-out-receiving-hosts.md)。  

- 如需確保所有的叢集服務該容錯移轉的資訊已經過測試，請參閱[叢集主要密碼伺服器](../technical-guides/clustering-the-master-secret-server.md)。  

- 如需確保 BizTalk 資料庫已叢集化 SQL 服務下的資訊，請參閱[叢集 BizTalk Server 資料庫 2](../technical-guides/clustering-the-biztalk-server-databases2.md)。  

- 如需判斷是否會 （需要不同的主控件） 使用任何不穩定的程式碼的詳細資訊，請參閱 <<c0> [ 高可用性的 BizTalk 主控件](../technical-guides/high-availability-for-biztalk-hosts.md)。  

- 執行功能測試的所有新的 BizTalk 應用程式的詳細資訊，請參閱[測試應用程式](../technical-guides/testing-an-application.md)
