---
title: "如何擷取 BAM 組態檔使用 BAM 管理公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67ce5e0c-467a-486c-8eec-217a2a26d7b4
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0eb7dee70d3a5b8dc7226203df9f48aefe1d5fc0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-retrieve-the-bam-configuration-file-using-the-bam-management-utility"></a>如何使用 BAM 管理公用程式擷取 BAM 組態檔
系統管理員和開發人員可以使用 BAM 管理公用程式，擷取目前的 BAM 基礎結構組態。 擷取的組態可以用來將 BAM 安裝移轉到新的伺服器，或可以修改並使用此組態更新現有的 BAM 安裝。  
  
## <a name="prerequisites"></a>必要條件  
 以下是執行此主題中之程序的必要條件：  
  
-   以設定的 BAM 資料庫  
  
-   讀取 BAM 主要匯入資料庫的權限  
  
### <a name="to-retrieve-the-bam-configuration-file-using-the-bam-management-utility"></a>使用 BAM 管理公用程式擷取 BAM 組態檔  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2.  瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。  
  
3.  在命令提示字元輸入下列命令： **bm get-config-FileName:\<輸出檔 >**，其中\<*輸出檔*> 取代為您的 BAM 組態的名稱檔案。 按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)