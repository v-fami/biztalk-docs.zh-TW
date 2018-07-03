---
title: 如何取得 RTA 視窗的持續時間 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [BAM], aggregations
- aggregations [BAM], time intervals
- managing [BAM], time intervals
- Get-RTAWindow command [BAM]
ms.assetid: 4e7ad0fd-e7ed-47f7-9435-ef01bbe17afa
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6893200c498fc387d9a1948d332db409cf3b4d61
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992695"
---
# <a name="how-to-get-the-duration-on-an-rta-window"></a>如何取得 RTA 視窗上的持續時間
系統管理員可以使用**get rtawindow**命令來取得指定即時彙總 (RTA) 的持續時間。 這個命令會傳回持續時間的長度以及測量持續時間所用的單位。  
  
### <a name="to-get-the-duration-on-an-aggregation"></a>若要取得彙總的持續時間  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2. 瀏覽至資料夾 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。  
  
3. 型別**bm get rtawindow-檢視：\<檢視表名稱\>-活動：\<活動名稱\>Rta:\<RTA 名稱\>**。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
4. 按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)   
 [如何設定 RTA 視窗的持續時間](../core/how-to-set-the-duration-on-an-rta-window.md)