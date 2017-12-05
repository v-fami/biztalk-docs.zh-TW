---
title: "如何停用 BAM 主要匯入資料庫參考 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d2d644-6ebb-4051-ae59-af7d0fb75753
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc9afef7bdcfad84f105abda158c5ed5c6461619
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-disable-a-bam-primary-import-database-reference"></a>如何停用 BAM 主要匯入資料庫參考
系統管理員使用**停用參考**命令以停用指定的 BAM 主要匯入資料庫的參考。  
  
### <a name="to-disable-a-reference-to-a-bam-primary-import-database"></a>停用 BAM 主要匯入資料庫的參考  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2.  瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。  
  
3.  在命令提示字元輸入下列命令： **bm 停用參考 TargetServer:\<目標伺服器\>-TargetDatabase:\<目標資料庫\>[-Server:\<伺服器\> ][-Database:\<資料庫\>]**，其中 **\<** *目標伺服器* **\>** 會以所指定的目標 BAM 主要匯入資料庫的 SQL server 名稱取代\<*目標資料庫*\>所在。 按 ENTER 鍵。  
  
## <a name="see-also"></a>請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)