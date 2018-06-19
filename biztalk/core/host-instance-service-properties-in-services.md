---
title: 裝載服務的執行個體服務屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8b317161-83a9-42d5-b24f-48ff1e54b94a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26d29575e282b7e558f223733ff7e7ce562f63ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247446"
---
# <a name="host-instance-service-properties-in-services"></a>服務的主控件執行個體服務屬性
## <a name="host-instance-service-properties-in-services"></a>服務的主控件執行個體服務屬性  
 建立 a BizTalk 主控建執行個體時，也將在「服務」中建立服務。 下表說明最常見的屬性。  
  
|選項|Description|  
|------------|-----------------|  
|一般：**啟動類型**|預設值設定為**自動**允許電腦重新啟動時自動啟動主控件執行個體。 在實際執行環境中，這個屬性一律設定為**自動**。|  
|登入：**帳戶**|設定為使用者帳戶指定 BizTalk 設定時，或建立新的主控件執行個體時。 BizTalk 和 SQL Server 位於不同的電腦時，帳戶必須是網域帳戶。 如果 BizTalk 和 SQL Server 位於同一部電腦，帳戶可以是網域帳戶或本機帳戶。|  
|復原：**第一次失敗**|預設值設定為**重新啟動服務**。 如果主控件執行個體第一次意外停止，則此設定將嘗試重新啟動主控件執行個體。<br /><br /> 如果主控件執行個體成功啟動，然後立即停止，則**失敗的第二個**屬性會套用。<br /><br /> 如果主控件執行個體無法啟動，然後在**失敗的第二個**屬性將不會套用。 此後將不進行其他任何重新啟動嘗試。 主控件執行個體將保持停止。|  
|復原：**第二個失敗**|預設值設定為**重新啟動服務**。 如果主控件執行個體第二次意外停止，則此設定將嘗試重新啟動主控件執行個體。<br /><br /> 如果主控件執行個體成功啟動，然後立即停止，則**後續失敗**屬性會套用。<br /><br /> 如果主控件執行個體無法啟動，然後在**後續失敗**屬性將不會套用。 此後將不進行其他任何重新啟動嘗試。 主控件執行個體將保持停止。|  
|復原：**後續失敗**|預設值設定為**重新啟動服務**。 如果主控件執行個體第三次意外停止，則此設定將嘗試重新啟動主控件執行個體。<br /><br /> 如果主控件執行個體成功啟動，然後立即停止，則**後續失敗**屬性會繼續套用。<br /><br /> 如果主控件執行個體無法啟動，然後在**後續失敗**屬性將不會套用。 此後將不進行其他任何重新啟動嘗試。 主控件執行個體將保持停止。|  
|復原：**重新啟動服務於**|預設為 1 分鐘，必要時可增加。|  
|相依性|**所有**啟動 BizTalk 主控件執行個體之前，必須先啟動列出的元件。 這包括企業單一登入。 如果使用 Windows Server 2008，請參閱下列知識庫文章：<br /><br /> [942284](http://support.microsoft.com/kb/942284)如預期般在重新啟動正在執行 Windows Vista 或 Windows Server 2008 的電腦時，可能無法啟動 BizTalk 服務|  
  
 **請注意**服務中的 BizTalk 主控件執行個體屬性也會儲存於 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\BTSSvc$*BizTalkHostName*登錄機碼。  
  
### <a name="recovery"></a>復原  
 主控件執行個體服務無法啟動時，「服務」中的回復功能不提供不限次數的服務重新啟動嘗試。 只要修改「回復」屬性，即可改善 BizTalk 主控件執行個體的執行時間。 最常造成 BizTalk 主控件執行個體停止的情況包括：  
  
-   SQL Server 網路連線中斷  
  
-   記憶體不足例外狀況  
  
-   存取違規  
  
 **可能的案例**  
  
-   SQL Server 意外關閉。 在此情況下，**第一次失敗**屬性會套用。 使用預設**第一次失敗**和**重新啟動服務於**1 分鐘後進行設定，單一的重新啟動嘗試。 如果在 1 分鐘後仍然無法使用 SQL Server，將不進行其他任何重新啟動嘗試。 主控件執行個體將保持停止。  
  
-   SQL Server 成為叢集，而且發生容錯移轉。 容錯移轉進行的時間超過 5 分鐘。 在此案例中，預設值**第一次失敗**和**重新啟動服務於**設定將嘗試重新啟動後 1 分鐘。 由於 SQL Server 仍然離限，因此重新啟動將失敗。 結果，此後將不進行其他任何重新啟動嘗試。 主控件執行個體將保持停止。  
  
 **建議**  
  
-   停止 SQL Server 或容錯移轉至 SQL 叢集時，手動停止 BizTalk 主控件執行個體。 SQL Server 上線後，請重新啟動主控件執行個體。  
  
-   如果 SQL 叢集容錯移轉的時間超過 1 分鐘的常見項目，請增加**重新啟動服務於**花費 SQL 叢集上線的時間長度的值。  
  
-   當 SQL Server 仍會保留由非 BizTalk 系統管理員時，請考慮增加**重新啟動服務於**值。 非 BizTalk 系統管理員可以在不察覺對於 BizTalk 造成影響的情況下停止/啟動 SQL Server。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)