---
title: "如何列出 BAM 基礎結構的變更 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- definitions [BAM], listing infrastructure changes
- managing [BAM definitions], listing infrastructure changes
- Get-Changes command [BAM]
- infrastructure, listing changes [BAM]
ms.assetid: 3feacd7d-6f42-4626-835b-0dc3befc9fd6
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8d0ed240f156d853c18f28a52022eea585af513
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-list-changes-to-the-bam-infrastructure"></a>如何列出 BAM 基礎結構的變更
系統管理員使用**get 變更**命令，列出目前已部署 BAM 定義資訊的 BAM 管理公用程式。 您也可以使用 get-changes 命令來列出 BAM 主要匯入資料庫中目前的部署成品。  
  
 所列資訊包括成功的部署和解除部署、BAM 定義檔的名稱、BAM 組態檔的名稱、與定義檔關聯之所有活動和檢視的名稱，以及套用變更的使用者帳戶。 get-changes 清單中顯示部署和定義移除情形及其關聯識別碼。  
  
### <a name="to-list-changes-to-the-bam-definition"></a>若要列出 BAM 定義的變更  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2.  瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。  
  
3.  型別**bm 取得變更。**  
  
4.  按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 安全性建議](../core/bam-security-recommendations.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)