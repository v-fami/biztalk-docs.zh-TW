---
title: 如何移除已部署的成品 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [BAM definitions], undeploying artifacts
- Remove-All command
- undeploying, artifacts [BAM]
- artifacts, undeploying [BAM]
ms.assetid: 90135965-d18e-4a71-9877-d2b0c3caf59f
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1d3e395223840dd4caa534130061fac33e89b78
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970188"
---
# <a name="how-to-remove-deployed-artifacts"></a>如何移除已部署的成品
系統管理員使用**移除 all**命令移除 BAM 主要匯入資料庫中所部署的成品。 提供的 BAM 定義檔案必須是包含所要移除之成品相關資訊的 XML 檔案或 Excel 活頁簿。  
  
### <a name="to-remove-deployed-artifacts"></a>移除已部署的成品  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2.  瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。  
  
3.  型別**bm 移除 all-DefinitionFile:\<def 檔\>**。  
  
4.  按 ENTER 鍵。  
  
## <a name="see-also"></a>請參閱  
 [如何將 BAM 成品新增至應用程式](../core/how-to-add-a-bam-artifact-to-an-application.md)   
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 安全性建議](../core/bam-security-recommendations.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)