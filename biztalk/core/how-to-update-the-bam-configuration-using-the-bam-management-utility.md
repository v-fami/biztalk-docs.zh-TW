---
title: 如何更新 BAM 組態使用 BAM 管理公用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 714a834e-1879-4019-9b54-e511705bd67a
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b08209d3b3a1555bbc674e469ea9f8a4b1f81a9d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971036"
---
# <a name="how-to-update-the-bam-configuration-using-the-bam-management-utility"></a>如何使用 BAM 管理公用程式更新 BAM 組態
系統管理員可以使用 BAM 管理公用程式更新現有的 BAM 安裝。  
  
## <a name="prerequisites"></a>必要條件  
 您必須具有要進行更新之 BAM 資料庫的系統管理員權限。  
  
### <a name="to-update-the-bam-configuration-using-the-bam-management-utility"></a>使用 BAM 管理公用程式更新 BAM 組態  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2.  瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。  
  
3.  在命令提示字元輸入下列命令： **bm 更新-config-FileName:\<組態檔\>**，其中\<*組態檔*\>是取代為您的 BAM 組態檔的名稱。 按 ENTER 鍵。  
  
## <a name="see-also"></a>請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)