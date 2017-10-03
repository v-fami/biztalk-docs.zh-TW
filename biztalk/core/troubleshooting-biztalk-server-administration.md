---
title: "BizTalk Server 管理疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9dfb56b0-352f-4012-b030-087bbcfe09d4
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d89f81bbaf15dfb0c87de91659888d70a2345a6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-biztalk-server-administration"></a>BizTalk Server 管理疑難排解
本章節提供一個集中的位置來保存使用 BizTalk Server 管理主控台時經常遇到之問題的相關資訊。  
  
 除了下列的已知問題，[常見的問題和解決方式與 BizTalk Server 管理主控台](http://social.technet.microsoft.com/wiki/contents/articles/common-issues-and-resolutions-with-the-biztalk-server-administration-console.aspx)提供其他資訊。  
  
## <a name="known-issues"></a>已知問題  
  
#### <a name="delay-in-entsso-service-prevents-biztalk-server-service-from-starting"></a>ENTSSO 服務中的延遲會使 BizTalk Server 服務無法啟動  
  
##### <a name="problem"></a>問題  
 未設定為自動啟動 dtc，重新啟動電腦可能會禁止 BizTalk Server 服務無法啟動。  
  
##### <a name="cause"></a>原因  
 這是因為 ENTSSO 服務可能需要更多的時間才能啟動超過所允許的 BizTalk Server 服務逾時持續期間。  
  
##### <a name="solution"></a>方案  
 若要解決此問題，請將 DTC 設定為自動。  
  
#### <a name="sql-resources-may-become-locked"></a>SQL 資源可能會變成鎖定  
  
##### <a name="problem"></a>問題  
 可能會發生下列錯誤：  
  
 **交易 (處理序識別碼 95) 另一個處理序的鎖定資源上發生死結，而且已被選為死結的犧牲者。請重新執行交易。**  
  
##### <a name="cause"></a>原因  
 這是非常罕見的情況下，由一位使用者中被鎖定的資料庫管理的另一位使用者的結果執行的系統管理作業中。  
  
##### <a name="solution"></a>方案  
 問題應補救本身很快。 再試一次在幾分鐘的時間。  
  
#### <a name="sql-database-may-become-locked"></a>SQL 資料庫可能會變成鎖定  
  
##### <a name="problem"></a>問題  
 使用者可能會被鎖定之外的 SQL 資料庫。 可能傳回不同的錯誤訊息的數目。  
  
##### <a name="cause"></a>原因  
 在某些情況下寫入資料庫的一位使用者將會有效地鎖定移出資料庫的另一位使用者。  
  
##### <a name="solution"></a>方案  
 問題應補救本身很快。 再試一次在幾分鐘的時間。  
  
#### <a name="termination-of-multiple-service-instances-in-a-multiple-messagebox-environment-fails-with-an-error"></a>在多個 messagebox 環境中的多個服務執行個體的終止失敗並發生錯誤  
  
##### <a name="problem"></a>問題  
 若要從 BizTalk Server 管理主控台的多個服務執行個體的嘗試失敗，並顯示類似下列的錯誤：  
  
 SQL Server 已封鎖存取程序的元件 'Agent XPs' 的' sys.xp_sqlagent_enum_jobs'，因為此元件關閉這部伺服器的安全性組態的一部分。  
  
> [!NOTE]
>  在多個 messagebox 環境中，會發生這個問題。  
  
##### <a name="cause"></a>原因  
 在多個 messagebox 環境中會發生此問題，如果 SQL 代理程式工作 ' Operations_OperateOnInstances_OnMaster_\<*dbName*>' 不次要 messagebox 資料庫上執行。 必須執行此作業，才能傳播到主要 messagebox 資料庫的次要 messagebox 資料庫資訊。 這項作業將無法執行，如果未啟用，或發生登入失敗。  
  
##### <a name="solution"></a>方案  
 如果您使用 BizTalk 管理主控台中同時執行多個服務執行個體上的作業，而且您的 BizTalk Server 環境具有多個 messagebox 資料庫設定，請確認 SQL Server Agent 作業名稱為 ' Operations_OperateOnInstances_OnMaster_\<*dbName*>' 在所有的次要 （非主要） messagebox 資料庫上啟用。 此外，在裝載次要 messagebox 資料庫的 SQL Server 電腦上的 SQL Server Agent 服務必須執行包含 BTS_SQLAGENT_USER 資料庫角色的次要 messagebox 資料庫中的帳戶。  
  
> [!NOTE]
>  \<*dbname*> 是 BizTalk messagebox 資料庫的實際名稱的預留位置。  
  
 請遵循下列步驟以加入次要 messagebox 資料庫的 BTS_SQLAGENT_USER 資料庫角色中的 SQL Server Agent 服務帳戶  
  
 **SQL Server 2008 上**  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft SQL Server 2008**，然後按一下  **SQL Server Management Studio**。  
  
2.  出現提示時選擇**伺服器類型**的**Database Engine**然後輸入或選取**伺服器名稱**裝載的次要 messagebox 資料庫。  
  
3.  按一下以展開**資料庫**，按一下以展開次要 messagebox 資料庫，按一下以展開**安全性**，按一下以展開**角色**，按一下以展開**資料庫角色**，然後按兩下 BTS_SQLAGENT_USER 資料庫角色。  
  
4.  按一下 **[加入]** 按鈕。  
  
5.  按一下**瀏覽**選取 SQL Server Agent 服務帳戶是的成員的群組，然後按一下 **確定**。  
  
> [!NOTE]
>  如果 SQL Server Agent 服務帳戶不是指定群組的成員將會需要將它新增至群組。  
  
#### <a name="changes-applied-in-one-instance-of-the-biztalk-administration-console-are-not-automatically-updated-in-other-instances-of-the-biztalk-administration-console"></a>套用到 BizTalk 管理主控台之一個執行個體的變更不會自動更新到 BizTalk 管理主控台的其他執行個體  
  
##### <a name="problem"></a>問題  
 如果有多個 BizTalk 管理主控台的執行個體同時連接到相同的 BizTalk Server 群組，則在 BizTalk 管理主控台的一個執行個體中所做的變更不會自動反映到 BizTalk 管理主控台的其他執行個體。 當您嘗試修改顯示於 BizTalk 管理主控台的執行個體內的成品，而該成品的狀態不符合 BizTalk 管理資料庫中儲存之成品的實際狀態時，這樣會造成並行違規錯誤。  
  
##### <a name="cause"></a>原因  
 BizTalk 管理主控台的每一個執行個體都會維護其自身的 BizTalk 群組組態快取，而且只會在快取中反映變更。 只有當重新整理 BizTalk 管理主控台檢視時，才會更新此快取。  
  
##### <a name="resolution"></a>解決方案  
 如果您在 BizTalk 管理主控台中收到並行違規錯誤，請依序按一下更新 BizTalk 管理主控台的執行個體的快取**重新整理**BizTalk 管理主控台上的按鈕工具列或按**F5**索引鍵。  
  
#### <a name="failed-to-execute-action-stop-error-occurs-when-you-attempt-to-stop-an-orchestration-with-the-biztalk-administration-console"></a>當嘗試使用 BizTalk 管理主控台停止協調流程時，發生無法執行動作 '停止' 錯誤  
  
##### <a name="problem"></a>問題  
 當您嘗試使用 BizTalk 管理主控台停止協調流程時，會產生類似以下的錯誤訊息：  
  
```  
Failed to execute action 'Stop'.  
------------------------------  
ADDITIONAL INFORMATION:  
A transport-level error has occurred when sending the request to the server. (provider: TCP Provider, error: 0 - An existing connection was forcibly closed by the remote host.) (Microsoft SQL Server, Error: 10054)  
```  
  
 如果下列條件成立，可能就會發生這個問題：  
  
-   BizTalk 管理主控台已開啟。  
  
-   在叢集的 SQL Server 執行個體上安裝 BizTalk 管理資料庫。  
  
-   容錯移轉叢集的 SQL Server 執行個體。  
  
-   在完成容錯移轉之後，您嘗試使用 BizTalk 管理主控台來停止執行中的協調流程執行個體。  
  
##### <a name="cause"></a>原因  
 BizTalk 管理主控台就會維持連接[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理資料庫。 當連接[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理資料庫的容錯移轉期間已中斷，某些管理工作可能會傳回 「 無法連線 」 或 「 無法執行 」 錯誤，直到已關閉並重新開啟 BizTalk 管理主控台。  
  
##### <a name="resolution"></a>解決方案  
 關閉 BizTalk 管理主控台，並將它重新開啟。 重新開啟 BizTalk 管理主控台時它會建立新連接，以便指定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理資料庫。  
  
#### <a name="windows-group-names-that-were-previously-deleted-do-not-have-access-to-the-biztalk-server-databases"></a>之前已刪除的 Windows 群組名稱無法存取 BizTalk Server 資料庫  
  
##### <a name="problem"></a>問題  
 如果您在重新安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，使用了之前已刪除的 Windows 群組名稱，該 Windows 群組將無法存取 BizTalk Server 資料庫。  
  
##### <a name="cause"></a>原因  
 刪除某個 Windows 群組，然後建立相同名稱的 Windows 群組時，會針對該 Windows 群組產生新的安全性識別碼 (SID)。 但是，舊的 SID 仍然會在 SQL Server 中快取，所以新的 Windows 群組無法登入 SQL Server。  
  
##### <a name="resolution"></a>解決方案  
 當您刪除 Windows 群組時，也必須一併移除此 Windows 群組的 SQL Server 登入。  
  
#### <a name="biztalk-administrator-cannot-start-the-biztalk-server-administration-console"></a>BizTalk 系統管理員無法啟動 BizTalk Server 管理主控台  
  
##### <a name="problem"></a>問題  
 BizTalk 系統管理員 (BizTalk 系統管理員 Windows 群組的成員) 如果不是本機電腦上 Windows 系統管理員群組的成員，則可能無法開啟 BizTalk Server 管理主控台。  
  
##### <a name="cause"></a>原因  
 如果您已經重新安裝或重新設定 BizTalk Server，可能會發生這個問題。 這是因為 SQL Server 使用了快取的安全性識別碼。  
  
##### <a name="resolution"></a>解決方案  
 暫時將 BizTalk 系統管理員加入本機電腦上的 Windows 系統管理員群組。 當成功開啟 BizTalk Server 管理主控台時，請從本機電腦上的本機 Windows 系統管理員群組中移除 BizTalk 系統管理員。  
  
#### <a name="cannot-start-a-host-instance-on-a-remote-computer"></a>無法在遠端電腦上啟動主控件執行個體  
  
##### <a name="problem"></a>問題  
 當您在遠端電腦上建立的 BizTalk 主控件執行個體時，啟動 BizTalk 主控件執行個體時，您可能會看到下列錯誤: 「 無法啟動，因為發生登入失敗。 」  
  
##### <a name="cause"></a>原因  
 如果您已經針對執行 BizTalk 主控件執行個體所用的服務帳戶輸入了無效的認證，或是此服務帳戶沒有具備服務權限的登入，則可能會發生這個錯誤。  
  
##### <a name="resolution"></a>解決方案  
 將具有服務權限的登入指派給遠端電腦中的服務帳戶，然後再啟動 BizTalk 主控件執行個體。 這會自動在本機電腦上執行，但是遠端電腦上則必須以手動方式執行。  
  
#### <a name="creating-or-configuring-a-host-instance-on-an-x64-computer-with-the-32-bit-only-option-selected-fails"></a>選取僅 32 位元選項在 X64 電腦上建立或設定主控件執行個體會失敗  
  
##### <a name="problem"></a>問題  
 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，建立具有 32 位元唯一選取的選項 （預設值） 的電腦可能無法在 X64 上的 BizTalk 主控件執行個體。  
  
 在 BizTalk Server 組態管理員中，選取 [僅 32 位元] 選項在 X64 電腦上設定 BizTalk Server 執行階段、建立內含式或外掛式主控件執行個體時，會導致服務無法啟動。  
  
##### <a name="cause"></a>原因  
 Unknown  
  
##### <a name="resolution"></a>解決方案  
 這個問題會斷續發生。 嘗試再次建立或設定主控件，或者取消選取 [僅 32 位元] 選項。  
  
#### <a name="host-instance-deletion-does-not-clear-registry-information"></a>刪除主控件執行個體未清除登錄資訊  
  
##### <a name="problem"></a>問題  
 如果您不是本機電腦上的系統管理員，當您刪除內含式或外掛式主控件時，會出現拒絕存取錯誤訊息。 您可以強制刪除此主控件； 但是，以這種方式刪除主控件不會清除所有相關的登錄資訊。  
  
##### <a name="cause"></a>原因  
 刪除與主控件執行個體有關的登錄資訊需要系統管理員權限。  
  
##### <a name="resolution"></a>解決方案  
 以本機系統管理員帳戶登入，然後再刪除主控件，如此也會一併移除相關的登錄資訊。  
  
#### <a name="cannot-delete-a-messagebox-database"></a>無法刪除 MessageBox 資料庫  
  
##### <a name="problem"></a>問題  
 您可能無法刪除 MessageBox 資料庫； 如果刪除失敗，則可能是以下其中一個問題所造成：  
  
-   快取重新整理間隔尚未過期。  
  
-   MessageBox 資料庫包含未完成的執行個體。  
  
 刪除失敗時，如果快取重新整理間隔尚未過期，會出現下列錯誤訊息: 「 由於仍包含未完成工作在 MessageBox 中的，無法刪除 MessageBox。 請確定 MessageBox 沒有未完成的執行個體，然後再試一次。"  
  
##### <a name="cause"></a>原因  
 在您於 MessageBox 資料庫中停用新的訊息發佈與刪除此資料庫的兩段時間之間，快取重新整理間隔必須過期。 根據預設，快取重新整理間隔為 60 秒。  
  
##### <a name="resolution"></a>解決方案  
 若要刪除 MessageBox 資料庫，您必須先停用該 MessageBox 資料庫的新訊息發佈，然後等候快取重新整理間隔過期，再刪除 MessageBox 資料庫。  
  
 如果 MessageBox 資料庫包含未完成的服務執行個體，就會出現下列錯誤訊息: 「 MessageBox 無法刪除，因為它可能仍然會包含不完整的執行個體。 請確定 MessageBox 沒有未完成的執行個體，然後再試一次。"  
  
 您可以使用 BizTalk Server 管理主控台中的 [群組中樞] 頁面，檢視 MessageBox 資料庫中未完成的服務執行個體。 如需在 [群組中樞] 頁面中檢視服務執行個體的狀態資訊，請參閱[如何搜尋追蹤服務執行個體](../core/how-to-search-for-tracked-service-instances.md)。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解](../core/troubleshooting.md)