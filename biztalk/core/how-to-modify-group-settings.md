---
title: 更新群組設定 |Microsoft Docs
description: 變更使用 BizTalk Server 管理群組的效能設定
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe0cbeb8-23d6-45cf-8535-c989914f5124
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a22bdc81d3db5a9b64d500d90c428339c0ebfc09
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966671"
---
# <a name="how-to-update-the-biztalk-group-settings"></a>如何更新 BizTalk 群組設定
使用「設定儀表板」，您可以修改在所指定 BizTalk 群組中的所有電腦上使用的組態資訊。 本主題提供在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中修改群組層級效能設定的逐步程序。 這些設定適用指定群組中的所有電腦。  

> [!NOTE]
>  您也可以修改主機與主控件執行個體設定。 如需詳細資訊，請參閱 <<c0> [ 如何修改主控件設定](../core/how-to-modify-host-settings.md)並[如何修改主控件執行個體設定](../core/how-to-modify-host-instance-settings.md)。  

 您可以將目前的 BizTalk Server 設定匯出至 XML 檔案。 稍後您可以將這些設定匯入到「設定儀表板」，而不需設定新值。 如需匯入或匯出[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定，請參閱[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)並[匯入或匯出 BizTalk 設定使用 BTSTask](how-to-import-biztalk-settings-using-btstask.md)。 

## <a name="prerequisites"></a>必要條件  
 若要執行這項作業，您必須為 BizTalk Server 系統管理員群組的成員登入。  

## <a name="update-the-group-level-settings"></a>更新群組層級設定  

1. 在  **BizTalk Server 管理主控台**，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**設定**。  

2. 在  **BizTalk 設定儀表板**對話方塊的 **群組**頁面上，執行下列動作：  


   |                       使用                        |                                                                                                                                                                                          以進行此動作                                                                                                                                                                                           |          界限值          | 預設值 |                                                升級邏輯                                                |
   |-------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------|---------------|-------------------------------------------------------------------------------------------------------------|
   |          **組態重新整理間隔**           |                                                                                                                        設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 重新整理傳訊組態的間隔。                                                                                                                        |             1 - 43200             |       -       |                                                      -                                                      |
   |              **訊息批次閾值**              |                                                                                                                                    若內送訊息批次的總大小超過此值，則系統會將它分割成較小的批次處理。                                                                                                                                    |           1 - 10000000            |    102400     | 住 HKEY_LOCAL_MACHINE\Software\Microsoft\BizTalk Server\3.0\Administration\TransformThreshold 值 |
   |                **大型訊息大小**                 |                                                                                                                                       設定閾值大小以觸發資料流處理的批次中，和/或在轉換期間的個別訊息。                                                                                                                                       |           1 - 10000000            |    1000000    |           最大的現有**大型訊息大小**並**LargeMessageFragmentSize**值。           |
   |              **追蹤和報告**               |                                                                                                                                                                                                                                                                                                                                                                                               |                 -                 |       -       |                                                      -                                                      |
   | **訊息方塊效能計數器取樣間隔** |                                                                       設定效能計數器重新整理的間隔。<br /><br /> 設定此間隔時，需在對資料庫的負擔會不會太重與計數器的資料夠不夠新之間做取捨。 值越高表示越少更新資料，但是對資料庫的負擔也越輕。                                                                        | 1 – 整數型別的最大值 |       -       |               BizTalk 群組中任何電腦上的最大值 (如果有的話)。 否則為預設值。                |
   |            **啟用群組層級追蹤**            | 選取此選項會開啟 BizTalk Server 的群組層級追蹤功能。<br /><br /> 關閉全域追蹤功能會停用整個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組的追蹤攔截器。 這表示 BizTalk Server 將不會在其追蹤表格中追蹤事件。 **注意：** 這項設定不會影響 BAM 追蹤。 |              開啟、關閉              |      開啟       |                                                      -                                                      |


3. 按一下 **套用**以套用所做的修改，並前進到另一個索引標籤。或按一下**確定**以套用所做的修改並結束 設定儀表板。  

   > [!NOTE]
   >  若要還原預設設定，請按一下**還原預設值**。  

## <a name="see-also"></a>另請參閱  
 [使用設定儀表板調整 BizTalk Server 效能](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)