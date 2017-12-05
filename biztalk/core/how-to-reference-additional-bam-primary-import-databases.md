---
title: "如何參考其他 BAM 主要匯入資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea80b32c-f2cb-4aca-89f4-d5b72e1ba021
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fca916339e48f6bce053753111f4467a4c9ae7d5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-reference-additional-bam-primary-import-databases"></a>如何參考其他 BAM 主要匯入資料庫
系統管理員使用**啟用參考**命令參考其他 BAM 主要匯入資料庫。 參考多個 BAM 主要匯入資料庫有助於檢視分散式 BAM 活動。  
  
### <a name="to-enable-a-reference-to-an-additional-bam-primary-import-database"></a>啟用參考其他 BAM 主要匯入資料庫  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2.  瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。  
  
3.  在命令提示字元輸入下列命令： **bm 啟用參考 TargetServer:\<目標伺服器\>-TargetDatabase:\<目標資料庫\>**，其中\<*目標伺服器*\>會以所指定的目標 BAM 主要匯入資料庫的 SQL server 名稱取代\<目標資料庫\>所在。 按 ENTER 鍵。  
  
## <a name="see-also"></a>請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)