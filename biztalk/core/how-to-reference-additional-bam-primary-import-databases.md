---
title: 如何參考其他 BAM 主要匯入資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea80b32c-f2cb-4aca-89f4-d5b72e1ba021
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54982491ca8ce2c7ca7acd9e176a7341b2642c78
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992311"
---
# <a name="how-to-reference-additional-bam-primary-import-databases"></a>如何參考其他 BAM 主要匯入資料庫
系統管理員可以使用**啟用參考**命令參考其他 BAM 主要匯入資料庫。 參考多個 BAM 主要匯入資料庫有助於檢視分散式 BAM 活動。  
  
### <a name="to-enable-a-reference-to-an-additional-bam-primary-import-database"></a>啟用參考其他 BAM 主要匯入資料庫  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2. 瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。  
  
3. 在命令提示字元輸入下列命令： **bm 啟用參考 TargetServer:\<目標伺服器\>-TargetDatabase:\<目標資料庫\>**，其中\<*目標伺服器*\>會以由目標 BAM 主要匯入資料庫所指定的 SQL server 名稱取代\<目標資料庫\>所在。 按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)