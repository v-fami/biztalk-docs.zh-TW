---
title: 選擇性設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3f4b0b51-2cad-4cb5-b6cd-4db92bd199fa
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b19646c9c83eff4a3171b4d25763a6b581d45b1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25976756"
---
# <a name="optional-configurations"></a>選擇性設定
您匯入 BizTalk Server 管理組件之後，瀏覽窗格的 [監視] 窗格會顯示自動探索的物件類型。 如需物件類型的清單，請參閱[物件管理組件會探索](../technical-guides/objects-the-management-pack-discovers.md)> 一節。 您可以修改所探索之物件的預設探索組態[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件。 您可以使用 Operations Manager 2007 R2/2012年的覆寫功能來變更組態設定。  
  
 不會自動探索的物件類型，您可以啟用自動探索中設定**製作**Operations 主控台中的窗格。  
  
#### <a name="to-use-an-override-to-change-the-setting-for-automatic-discovery"></a>若要使用覆寫來變更自動探索的設定  
  
1.  在 撰寫中 窗格中展開 **管理組件物件**，然後按一下 **物件探索**。  
  
2.  Operations Manager 工具列上，按一下**範圍**，篩選只包含 BizTalk Server 物件的詳細資料窗格中顯示的物件。  
  
3.  在 [詳細資料] 窗格中，按一下您想要變更的設定物件類型。  
  
4.  Operations Manager 工具列上，按一下**會覆寫**，按一下 **覆寫物件探索**，然後按一下 **類型的所有物件：** \< *物件類型的名稱*\>，**為群組，請針對類型的特定物件：** \<*物件類型的名稱*\>，或**針對另一種類型的所有物件**。  
  
5.  在**覆寫內容**對話方塊中，按一下 **覆寫**方塊**啟用**您想要變更的參數。  
  
6.  在下**管理組件**，按一下**新增**來建立未密封的版本的管理組件，然後按一下**確定**。  
  
 變更覆寫設定之後，物件類型將會自動探索和會出現在 [監視中] 窗格下[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
 如需設定會覆寫資訊，請參閱[Operations Manager 2007 R2/2012年中的覆寫](http://go.microsoft.com/fwlink/?LinkId=86870)(http://go.microsoft.com/fwlink/?LinkId=86870)。