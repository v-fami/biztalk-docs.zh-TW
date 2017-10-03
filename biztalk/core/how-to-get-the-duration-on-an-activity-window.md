---
title: "如何取得活動視窗的持續時間 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], time intervals
- managing [BAM], time intervals
- Get-ActivityWindow command [BAM]
ms.assetid: d70f6767-f6f7-4ecf-ad9d-4a9d8c76edea
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0dbef138603421a46edd4b2d17a5123116cece6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-get-the-duration-on-an-activity-window"></a>如何取得活動視窗的持續時間
系統管理員使用**get activitywindow**命令，以取得指定之活動的持續時間。 這個命令會傳回持續時間的長度以及測量持續時間所用的單位。  
  
### <a name="to-get-the-duration-on-an-activity"></a>若要取得活動的持續時間  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2.  瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。  
  
3.  輸入 bm get activitywindow-活動：\<活動名稱 >。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
4.  按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)   
 [如何設定活動視窗的持續時間](../core/how-to-set-the-duration-on-an-activity-window.md)