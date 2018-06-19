---
title: 如何顯示管理組件的覆寫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8261a514-b4c4-4e6b-ac35-40a3e3e090e0
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a28c4ab2ef8f82fdd770203816239ad78e74418e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297686"
---
# <a name="how-to-display-overrides-for-a-management-pack"></a>如何顯示管理組件的覆寫
若要顯示的管理組件，請使用下列程序。  
  
### <a name="to-display-overrides-for-a-management-pack"></a>若要顯示覆寫管理組件  
  
1.  在 管理伺服器中，按一下 **程式**，然後按一下  **System Center**。  
  
2.  按一下**命令殼層**。  
  
3.  在命令殼層中，輸入下列命令：   
    `$mp = get-scommanagementpack -DisplayName "Operations Manager Internal Library"`   
    `$mp.GetOverrides()`  
  
4.  建立.csv 檔案。 此.csv 檔案可以在 Office Excel 中開啟。  
  
    > [!NOTE]  
    >  在 Office Excel 時，您可能需要指定此.csv 檔案為文字檔。  
  
 例如，下列命令會顯示其中一個核心管理組件的覆寫：   
`$mp = get-scommanagementpack -DisplayName "Contoso.BizTalk.Overrides.mp"`  
`$mp.GetOverrides()`