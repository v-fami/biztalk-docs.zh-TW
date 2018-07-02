---
title: 如何將 BizTalk 主控件設定為叢集 Resource1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installation, high availability
- clustering, servers
- hosts, multiple
- hosts, high availability
- Windows Server cluster
- databases, clustering
- clustering, fail-overs
- Windows Server cluster, about Windows Server cluster
- installation, planning
- clustering, databases
- clustering, best practices
- clustering, unclustering
- clustering, configuring
- installation, clustering
ms.assetid: bcd656d2-8dd6-49fc-9c42-ef5c884e52c4
caps.latest.revision: 36
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 53df974ec3b0fdf93b4e1cd59c9144b5b33af424
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981983"
---
# <a name="how-to-configure-a-biztalk-host-as-a-cluster-resource"></a>如何將 BizTalk 主控件設定為叢集資源
本主題討論要將 BizTalk 主控件設定為叢集資源所必須依循的步驟。 若要完成本主題中的步驟，您必須已設定至少兩部 BizTalk Server 中的 BizTalk 群組做為 Windows Server 叢集的成員。 如需有關如何設定 Windows Server 叢集的詳細資訊，請參閱 Windows Server 線上說明。  
  
## <a name="prerequisites"></a>必要條件  
 您必須要叢集化，或取消叢集主控件的 BizTalk 系統管理員群組的成員身分登入。  
  
## <a name="considerations-and-known-issues"></a>考量與已知問題  
  
- BizTalk Server 必須設定為 Windows Server 容錯移轉叢集中的節點，才能在 BizTalk Server 上執行的叢集 BizTalk 主控件執行個體。 如需有關如何設定伺服器叢集中的叢集節點的詳細資訊，請參閱 Windows 伺服器線上說明。  
  
- 您無法容錯移轉叢集的 BizTalk 主控件，以主控件執行個體，可以選擇**停用主控件執行個體無法啟動**設定。 請確定叢集 BizTalk 主控件的所有主控件執行個體，並沒有啟用這個選項。 在 BizTalk Server 管理主控台中設定這個選項，是將它上**主控件執行個體屬性**頁面。  
  
- 當您叢集 BizTalk 主控件時，在指定的叢集資源群組中建立對應的叢集資源。 建立叢集資源時，每個可用的叢集節點都會新增為叢集資源的可能擁有者。 因為叢集資源可以容錯移轉到可能的擁有者的清單中的任何節點，您應該新增到所有可用的節點叢集的主控件執行個體，再叢集 BizTalk 主控件。 嘗試容錯移轉叢集 BizTalk 主控件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不包含主控件執行個體的電腦將會失敗。  
  
  > [!NOTE]
  >  如果您想要防止叢集的 BizTalk 主控件上執行，或容錯移轉到特定的叢集節點中，從您叢集 BizTalk 主控件時所建立的叢集資源的可能擁有者的清單中移除節點。 您可以修改使用 Windows Server 容錯移轉叢集管理介面，以叢集資源的可能擁有者的清單。  
  
- 當叢集 BizTalk 主控件，請確定您要新增主機到叢集群組、 叢集的服務或應用程式包含網路名稱和 IP 位址資源。 如果目標叢集群組包含網路名稱和 IP 位址資源，然後在網路名稱資源會加入為相依性叢集 BizTalk 主控件。 無法使用這些資源時，則 BizTalk 主控件將無法正確運作為叢集資源。  
  
- 如果您取消設定 BizTalk 伺服器/叢集節點已列為叢集 BizTalk 主控件的可能擁有者時，主控件執行個體的叢集資源離線 Windows 叢集中。 如果您需要取消設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦已列為叢集 BizTalk 主控件的可能擁有者不需要主控件執行個體的叢集資源離線，請遵循下列步驟：  
  
  - 在 Windows Server 容錯移轉叢集管理介面中，容錯移轉叢集的主應用程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以外的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會取消設定的電腦。  
  
  - 在 BizTalk Server 管理主控台中，選取 對應到叢集 BizTalk 主控件執行個體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦要取消設定。  
  
  - 刪除主控件執行個體。 若提示出現錯誤，請選擇強制刪除主控件執行個體的選項。  
  
  - 取消設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
- 當 BizTalk 主控件設定為叢集的主機時，在叢集上指定的叢集資源群組中建立對應的叢集資源。  
  
   根據預設，使用下列重新啟動值的 Windows Server 容錯移轉叢集上，您可以使用哪些設定叢集的 BizTalk 主控件資源**原則**索引標籤**屬性**對話方塊叢集資源：  
  
  |選項|ReplTest1|  
  |------------|-----------|  
  |如果資源失敗，嘗試重新啟動目前的節點上。|**True** <br />若資源失敗，叢集服務會嘗試重新啟動該資源。|  
  |重新啟動 (mm: ss) 的期間：|**15:00** <br />指定計入重新啟動嘗試的期間。|  
  |將重新啟動次數上限，在指定期間內：|**1** <br />指定的期間允許的重新啟動嘗試次數上限**重新啟動 (mm: ss) 的期間**。|  
  |如果重新啟動失敗，容錯移轉這個服務或應用程式中的所有資源。|**True** <br />叢集服務會藉由將整個資源群組容錯移轉到另一個叢集節點，嘗試重新啟動資源。|  
  |如果所有重新啟動嘗試失敗，開始在指定的時間 (hh: mm) 之後，再次重新啟動：|**1:00** <br />指定延長的等待期間之後，叢集服務會開始另一系列的重新啟動嘗試。|  
  |暫止的逾時 (mm: ss):|**3:00** <br />指定資源可能需要變更之間線上及離線的狀態，才能在叢集服務會將資源處於失敗狀態的時間的長度。|  
  
   預設重新啟動值會指定在 Windows Server 容錯移轉叢集會嘗試重新啟動失敗的執行個體的叢集 BizTalk 主控件執行個體最多 1 時間為 15 分鐘的時間範圍內。 由於**如果重新啟動失敗，容錯移轉這個服務或應用程式中的所有資源**值設定為 **，則為 True**，任何重新啟動嘗試也將會容錯移轉至另一個叢集的叢集資源群組節點。 如果無法在指定次數在指定的時段內重新啟動失敗的執行個體的叢集 BizTalk 主控件，則叢集的 BizTalk 主控件將假設的狀態**失敗**在容錯移轉叢集管理介面。 如果叢集的 BizTalk 主控件會假設的狀態**失敗**則必須在容錯移轉叢集管理以手動方式啟動。  
  
   預設情況下，叢集的 BizTalk 主控件資源會設定下列重新啟動上的值為伺服器叢集上，您可以使用哪些**進階**索引標籤**屬性**叢集 對話方塊資源：  
  
  |**選項**|**ReplTest1**|  
  |----------------|---------------|  
  |重新啟動|**True**<br /><br /> 若資源失敗，叢集服務會嘗試重新啟動該資源。|  
  |影響群組|**True**<br /><br /> 叢集服務會藉由將整個資源群組容錯移轉到另一個叢集節點，嘗試重新啟動資源。|  
  |重新啟動閾值|**3**<br /><br /> 指定的期間允許的重新啟動嘗試次數上限**重新啟動期間**。 如果重新啟動嘗試次數超出**重新啟動閾值**期間**重新啟動期間**叢集資源會假設的狀態，然後**失敗**和叢集服務不會嘗試重新啟動。|  
  |重新啟動期間|**900 秒**<br /><br /> 指定計入重新啟動嘗試的期間。 **重新啟動期間**初始化時第一次重新啟動嘗試。 重新啟動嘗試次數會重設為零，如果**重新啟動閾值**的持續時間不超過**重新啟動期間**。|  
  
   預設的重新啟動值代表 Windows Server 叢集在 900 秒的時間內，最多重新啟動失敗的叢集 BizTalk 主控件執行個體 3 次。 由於**影響群組**值設定為 **，則為 True**，任何重新啟動嘗試也將會容錯移轉至另一個叢集節點的叢集資源群組。 如果無法在指定次數在指定的期間內，重新啟動失敗的執行個體的叢集 BizTalk 主控件，則叢集的 BizTalk 主控件將假設的狀態**失敗**在叢集系統管理員。 如果叢集的 BizTalk 主控件會假設的狀態**失敗**，則它必須以手動方式啟動在叢集系統管理員。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-configure-a-biztalk-host-as-a-cluster-resource"></a>若要將 BizTalk 主控件設定為叢集資源  
  
1. 在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下以展開**BizTalk Server 管理]**，按一下以展開**BizTalk 群組 [\<servername\>:\<管理資料庫\>]**，按一下以展開**平台設定**，然後按一下以展開**主機**。 主控件清單會出現在資料夾下。  
  
2. 以滑鼠右鍵按一下您想要叢集化，，然後選取 主機**叢集**。  
  
   > [!NOTE]
   >  請確定您已新增至該叢集群組的 BizTalk 主控件之前是可能的擁有者的叢集群組的所有成員節點上建立主控件執行個體。  
  
3. 從可用叢集群組的下拉式清單選取主控件執行所在的叢集群組。  
  
   > [!NOTE]
   >  主機已叢集化，因為它處於線上，並會開始處理文件的任何配接器處理常式或設定要在主機中執行的協調流程。  
  
#### <a name="to-uncluster-a-clustered-biztalk-host"></a>若要取消叢集的 BizTalk 主控件  
  
1. 在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下以展開**BizTalk Server 管理]**，按一下以展開**BizTalk 群組 [\<servername\>:\<管理資料庫\>]**，按一下以展開**平台設定**，然後按一下以展開**主機**。 主控件清單會出現在資料夾下。  
  
2. 以滑鼠右鍵按一下您想要取消，，然後選取 叢集主控件**取消叢集**。  
  
   > [!NOTE]
   >  取消叢集已叢集的主控件時，會停止任何與已叢集主控件相關的主控件執行個體，且主控件會針對設定在主控件中執行的任何配接器處理常式或協調流程，停止處理文件。