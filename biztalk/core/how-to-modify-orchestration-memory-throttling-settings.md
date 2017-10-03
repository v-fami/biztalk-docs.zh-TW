---
title: "如何修改協調流程記憶體節流設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Bts10.settings.HostInstanceOrchestration
ms.assetid: f6953c68-7809-4518-87ec-e75c98884af3
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c48f1ec5e74ae577a7c1d130e22f3b4a1b53874c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-orchestration-memory-throttling-settings"></a>如何修改協調流程記憶體節流設定
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件執行個體記憶體節流機制可持續監控節流狀況、計算節流狀況的嚴重性，然後根據計算的嚴重性逐步套用主控件執行個體記憶體節流。 本主題提供使用 [設定儀表板] 修改這些設定的逐步程序。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此作業，您必須以 BizTalk Server Administrators 群組的成員身分登入。  
  
### <a name="to-modify-the-orchestration-memory-throttling-settings-of-a-host-instance"></a>若要修改主控件執行個體的協調流程記憶體節流設定  
  
1.  在**BizTalk Server 管理主控台**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **設定**。  
  
2.  在**BizTalk 設定儀表板**對話方塊**主控件執行個體**頁面上，按一下**協調流程記憶體節流** 索引標籤。  
  
3.  執行下列命令，，然後按一下**套用**以套用所做的修改，並前進到另一個索引標籤。或按一下**確定**以套用變更並結束 設定儀表板。  
  
    |使用|動作|界限值|預設值|  
    |--------------|----------------|---------------------|-------------------|  
    |**主控件執行個體**|從下拉式方塊選取 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段電腦上執行中的主控件執行個體。|-|-|  
  
     **實體**  
  
    |使用|動作|界限值|預設值|  
    |--------------|----------------|---------------------|-------------------|  
    |**最佳用量**|指定凍結節流生效時的實體記憶體用量百分比。 這是使用於主控件執行個體的實體記憶體最佳百分比。|[0 – 100]|70|  
    |**最大用量**|指定凍結節流達最大值時的實體記憶體用量百分比。 這是使用於主控件執行個體的實體記憶體最大百分比。<br /><br /> 最小值**最大用量**應該**最佳用量**。|(最佳用量 – 100]<br /><br /> 當兩者都是 0 或 100 時例外。|85|  
  
     **虛擬**  
  
    |使用|動作|界限值|預設值|  
    |--------------|----------------|---------------------|-------------------|  
    |**最佳用量**|指定凍結節流生效時的虛擬記憶體用量百分比。<br /><br /> 此時， **TestThreshold**值**MaxThreshold**和任何的記憶體使用量大於**OptimalUsage**導致**TestThreshold**是小於**MaxThreshold**。|[0 – 100]|65|  
    |**最大用量**|指定凍結節流達最大值時的虛擬記憶體用量百分比。<br /><br /> 此時， **TestThreshold**值**MinThreshold**和任何的記憶體使用量小於**MaximalUsage**導致**TestThreshold**必須大於**MinThreshold**。|(最佳用量 – 100]<br /><br /> 當兩者都是 0 或 100 時例外。|85|  
  
    > [!NOTE]
    >  若要還原預設設定，請按一下**還原預設值**。  
  
## <a name="see-also"></a>另請參閱  
 [如何修改主控件執行個體設定](../core/how-to-modify-host-instance-settings.md)