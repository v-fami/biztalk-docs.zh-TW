---
title: "如何部署追蹤設定檔與追蹤設定檔管理公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracking profiles, deploying
- deploying, tracking profiles
- bttdeploy.exe [BAM]
- managing [BAM], deploying tracking profiles
ms.assetid: b3023379-cae1-45fc-a773-2660d3e4abf1
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2dde3f351c583be9037127c060d02c98d12b2fcb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility"></a>如何使用追蹤設定檔管理公用程式部署追蹤設定檔
商務經理人會要求方案開發人員建立新的追蹤設定檔或修改現有的設定檔，加強對組織特定商務程序的管理與監控。  
  
 方案開發人員使用追蹤設定檔編輯器 (TPE) 定義商務分析師需要的資料。  
  
 方案開發人員建立或修改追蹤設定檔之後，系統管理員可以使用 bttdeploy.exe 命令列公用程式進行部署，以便使方案開發人員所做的變更生效並開始收集資料。 方案開發人員可以使用 TPE 部署追蹤設定檔。  
  
> [!IMPORTANT]
>  您必須部署追蹤設定檔才能部署追蹤設定檔關聯的組件。  
  
> [!IMPORTANT]
>  您必須使用此工具的 BizTalk® 系統管理員權限。  
  
### <a name="to-deploy-the-tracking-profile-from-the-command-line-utility"></a>若要從命令列公用程式部署追蹤設定檔  
  
1.  從命令提示字元中，移動到目錄\<安裝路徑\>\Program Files\Microsoft BizTalk Server\<版本\>\Tracking\\。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
2.  型別**bttdeploy.exe\<設定檔名稱\>.btt**。  
  
3.  按 ENTER 鍵。  
  
## <a name="see-also"></a>請參閱  
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 安全性建議](../core/bam-security-recommendations.md)   
 [商務活動監控 (BAM)](../core/business-activity-monitoring-bam.md)