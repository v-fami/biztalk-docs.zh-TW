---
title: 如何停用 BAM 主要匯入資料庫參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 78d2d644-6ebb-4051-ae59-af7d0fb75753
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b89e9df78d91a6e4737b964223f81983e74dd29
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998191"
---
# <a name="how-to-disable-a-bam-primary-import-database-reference"></a>如何停用 BAM 主要匯入資料庫參考
系統管理員可以使用**停用參考**命令以停用指定的 BAM 主要匯入資料庫的參考。  
  
### <a name="to-disable-a-reference-to-a-bam-primary-import-database"></a>停用 BAM 主要匯入資料庫的參考  
  
1. 開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2. 瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。  
  
3. 在命令提示字元輸入下列命令： **bm 停用參考 TargetServer:\<目標伺服器\>-TargetDatabase:\<目標資料庫\>[-Server:\<伺服器\> ][-Database:\<資料庫\>]**，其中**\<**<em>目標伺服器</em>**\>** 以由目標 BAM 主要匯入資料庫所指定的 SQL server 名稱取代\<*目標資料庫*\>所在。 按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)